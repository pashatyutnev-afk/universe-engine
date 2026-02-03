FILE: UE_V2/03_ENT/30_ORC_ENT/00_GOVERNANCE_ORC_ENT/07__GVN__AUDIT_LOG_BRIDGE__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 00_GOVERNANCE_ORC_ENT
DOC_TYPE: ORC_MODULE
DOMAIN: GVN_ORC_ENT
MODULE: GVN.AUDIT_LOG_BRIDGE
UID: UE.V2.ENT.ORC.GVN.AUDIT_LOG_BRIDGE.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-03
OWNER: ORC_ENT
NAV_RULE: Use KEYS only (RAW resolved via INDEX_MANIFEST)

---

## [M] ROLE
Audit log bridge module for governance runs.

Задача модуля:
- связать решения и шаги governance-run с LOG-реалмом через KEYS
- определить минимально-нужные записи (RUN_LOG / DECISION_LOG / TOKEN_ARCHIVE)
- в MODE REPO: строго “record-plan only”
  - не “писать” лог (потому что NO-EDIT)
  - а вернуть детерминированный LOG_PLAN, что именно должно быть записано, и где

Этот модуль не меняет решения (не меняет APPROVAL_TOKEN), только оформляет аудит-след.

---

## [M] INPUT
- GOVN_TASK_TOKEN (required): object
  - token_id
  - domain (must be GVN_ORC_ENT)
  - mode (REPO|EDIT|…)
  - task_text
  - constraints (optional)

- ROUTE_TOKEN (required): object
  - domain
  - artifact_type
  - mode
  - required_idx[]
  - required_checks[]
  - exec_mode
  - pipe_selected

- CHANGE_CLASS (required): object
  - change_type
  - change_level
  - touches_realms[]
  - target_keys_count
  - can_execute_now

- RISK_TOKEN (required): object
  - risk_level
  - risk_reasons[]
  - blocked
  - block_reason
  - required_safeguards[]

- APPROVAL_TOKEN (required): object
  - approval_level
  - decision_kind
  - decision_reason
  - required_approvers[]
  - required_decision_log_fields[]
  - required_run_log_fields[]
  - required_safeguards_confirm[]
  - blocked
  - block_reason

- LOG_CONTEXT (optional): object
  - log_keys_available (bool)
  - run_log_key (string)        # e.g. "LOG.RUN_LOG"
  - decision_log_key (string)    # e.g. "LOG.DECISION_LOG"
  - token_archive_key (string)   # e.g. "LOG.TOKEN_ARCHIVE"
  - log_rules_key (string)       # e.g. "LOG.RULES"
  - current_run_id (string, optional)

---

## [M] OUTPUT
- AUDIT_BRIDGE_TOKEN: object
  - audit_level: MIN|FULL
  - log_plan: array[LOG_ACTION]
  - required_log_keys: array[string]
  - ready: true|false
  - defer_reason: string (if not ready)
  - notes: short string

Where LOG_ACTION:
- kind: WRITE|APPEND|LINK|ARCHIVE|NOOP
- target_key: string
- record_schema: string
- record_payload: object (minimal fields only)
- constraints: array[string]  # e.g. ["NO_WRITE_IN_REPO", "APPEND_ONLY"]
- idempotency_key: string
- status: PLANNED|SKIPPED

---

## [M] HARD RULES
1) REPO NO-WRITE
- Если mode содержит REPO:
  - все LOG_ACTION.kind принудительно становятся NOOP
  - но сохраняется полный record_payload и target_key как “PLAN”
  - constraints обязательно включают "NO_WRITE_IN_REPO"

2) Minimal audit always
- Даже если риск LOW и approval NONE, аудит минимального шага обязателен:
  - RUN_LOG entry (step/module summary)
  - TOKEN_ARCHIVE entry (ROUTE_TOKEN + key outputs summary)

3) Determinism
- Для одинаковых входов (mode, decision_kind, risk_level, change_type, touches_realms)
  log_plan и idempotency_key совпадают 1:1.

4) No new data invention
- Модуль не добавляет “новые факты”.
- Берёт значения только из входных токенов и нормализует поля.

---

## [M] REQUIRED LOG KEYS (canonical set)
required_log_keys:
- LOG.RULES
- LOG.RUN_LOG
- LOG.DECISION_LOG
- LOG.TOKEN_ARCHIVE

Если LOG_CONTEXT не передан, модуль использует эти canonical keys как требования.

---

## [M] AUDIT LEVEL POLICY
- audit_level = MIN если:
  - decision_kind in [AUDIT_ONLY, ALLOW] AND risk_level in [NONE, LOW]
- audit_level = FULL если:
  - decision_kind in [DEFER, DENY] OR risk_level in [MED, HIGH, CRITICAL]
  - OR touches_realms includes NAV or PIPE or REG or LOG

---

## [M] LOG RECORD SCHEMAS
### 1) RUN_LOG_RECORD (minimum)
record_schema: "RUN_LOG_RECORD/v1"
fields:
- run_id
- token_id
- timestamp
- domain
- mode
- step
- module_key (GVN.AUDIT_LOG_BRIDGE)
- change_type
- touches_realms
- risk_level
- approval_level
- decision_kind
- summary
- blocked (bool)
- notes

### 2) DECISION_LOG_RECORD (minimum)
record_schema: "DECISION_LOG_RECORD/v1"
fields:
- decision_id
- token_id
- timestamp
- domain
- mode
- change_type
- touches_realms
- risk_level
- approval_level
- decision_kind
- decision_reason
- required_approvers
- safeguards_required
- status (RECORDED|PENDING|DENIED)

### 3) TOKEN_ARCHIVE_RECORD (minimum)
record_schema: "TOKEN_ARCHIVE_RECORD/v1"
fields:
- archive_id
- token_id
- timestamp
- domain
- mode
- route_token (object)
- input_digest (short)
- output_digest (short)
- pointers (array[string])  # optional “KEY:…”
- notes

---

## [M] ID GENERATION (deterministic)
All ids are deterministic strings (no randomness):
- run_id = "RUN:" + token_id
- decision_id = "DEC:" + token_id
- archive_id = "ARC:" + token_id
- idempotency_key = kind + "|" + target_key + "|" + token_id

timestamp в REPO режиме может быть:
- "0000-00-00T00:00:00Z" как placeholder, если реальное время не доступно в рантайме
(модуль не обязан знать wall-clock)

---

## [M] LOG PLAN CONSTRUCTION
### Step A: Validate log readiness
ready = true only if:
- LOG_CONTEXT.log_keys_available == true
(если поля нет — считаем false)

If not ready:
- ready=false
- defer_reason="log_keys_not_confirmed"
- log_plan still produced (PLANNED) but will include constraints "LOG_NOT_READY"

### Step B: Build planned records (payloads)
Create 3 payloads from inputs:
- run_payload (RUN_LOG_RECORD/v1)
- decision_payload (DECISION_LOG_RECORD/v1) — только если audit_level == FULL
- archive_payload (TOKEN_ARCHIVE_RECORD/v1)

### Step C: Build actions (order is canonical)
Canonical order:
1) RUN_LOG (APPEND)
2) DECISION_LOG (APPEND) if FULL
3) TOKEN_ARCHIVE (ARCHIVE)

Each action:
- kind: APPEND or ARCHIVE
- target_key: LOG.RUN_LOG / LOG.DECISION_LOG / LOG.TOKEN_ARCHIVE
- status: PLANNED
- constraints:
  - always include "APPEND_ONLY"
  - include "NO_WRITE_IN_REPO" if mode contains REPO
  - include "LOG_NOT_READY" if ready == false

### Step D: Apply REPO override
If mode contains REPO:
- set kind=NOOP for all actions
- keep payloads intact
- status remains PLANNED (means: plan exists)

---

## [M] EXAMPLE LOG PLAN (for current governance completion run)
Given:
- mode: REPO
- audit_level: FULL
- decision_kind: AUDIT_ONLY
- risk_level: MED

AUDIT_BRIDGE_TOKEN:
- audit_level: FULL
- ready: (depends on LOG_CONTEXT.log_keys_available)
- log_plan:
  1) kind: NOOP
     target_key: LOG.RUN_LOG
     record_schema: RUN_LOG_RECORD/v1
     constraints: ["APPEND_ONLY","NO_WRITE_IN_REPO"]
     idempotency_key: "NOOP|LOG.RUN_LOG|<token_id>"
  2) kind: NOOP
     target_key: LOG.DECISION_LOG
     record_schema: DECISION_LOG_RECORD/v1
     constraints: ["APPEND_ONLY","NO_WRITE_IN_REPO"]
     idempotency_key: "NOOP|LOG.DECISION_LOG|<token_id>"
  3) kind: NOOP
     target_key: LOG.TOKEN_ARCHIVE
     record_schema: TOKEN_ARCHIVE_RECORD/v1
     constraints: ["APPEND_ONLY","NO_WRITE_IN_REPO"]
     idempotency_key: "NOOP|LOG.TOKEN_ARCHIVE|<token_id>"

---

## [M] FAILURE / DEFER CONDITIONS
This module does not emit GAP.

It can produce:
- ready=false + defer_reason="log_keys_not_confirmed"
- ready=true (normal)

It never blocks the run by itself.
If execution must be blocked, that is handled by GVN.RISK_SAFETY or GVN.RULE_ENFORCER.

---

## [M] CHANGELOG
- 2026-02-03: v1.0.0 created. Deterministic log plan builder + REPO no-write override + minimal/full audit policy.
