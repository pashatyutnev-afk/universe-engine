FILE: UE_V2/03_ENT/30_ORC_ENT/00_GOVERNANCE_ORC_ENT/08__GVN__COMPLIANCE_REPORTER__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 00_GOVERNANCE_ORC_ENT
DOC_TYPE: ORC_MODULE
DOMAIN: GVN_ORC_ENT
MODULE: GVN.COMPLIANCE_REPORTER
UID: UE.V2.ENT.ORC.GVN.COMPLIANCE_REPORTER.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-03
OWNER: ORC_ENT
NAV_RULE: Use KEYS only (RAW resolved via INDEX_MANIFEST)

---

## [M] ROLE
Compliance status reporter for governance runs.

Задача модуля:
- собрать результаты проверок (ENTRY_GUARD / RULE_ENFORCER / DEPENDENCY_RESOLVER / CHANGE_CONTROL / RISK_SAFETY / DECISION_APPROVAL / AUDIT_LOG_BRIDGE)
- сформировать детерминированный COMPLIANCE_REPORT_TOKEN
- вернуть:
  - итоговый статус PASS|FAIL|DEFER
  - список нарушений (violations) с привязкой к fail-codes (если переданы)
  - список обязательных исправлений (required_fixes)
  - список требований к следующему шагу (next_actions)

Этот модуль не “чинит” нарушения и не меняет решение. Он только репортит.

---

## [M] INPUT
### Required
- GOVN_TASK_TOKEN: object
  - token_id
  - domain (must be GVN_ORC_ENT)
  - mode
  - task_text
  - constraints (optional)

- ROUTE_TOKEN: object
  - domain
  - artifact_type
  - mode
  - required_idx[]
  - required_checks[]
  - exec_mode
  - pipe_selected

### Required: module outputs (as tokens)
- ENTRY_GUARD_TOKEN: object
  - ok (bool)
  - missing_inputs[]
  - normalized_mode
  - notes

- RULE_ENFORCER_TOKEN: object
  - ok (bool)
  - violations[]            # list of rule violations (structured)
  - blocked (bool)
  - block_reason
  - required_fixes[]         # list of fix items
  - notes

- DEPENDENCY_TOKEN: object
  - ok (bool)
  - missing_keys[]
  - must_load_plan[]         # ordered KEYS
  - markers_confirmed (bool)
  - notes

- CHANGE_CLASS: object
  - change_type
  - change_level
  - touches_realms[]
  - target_keys_count
  - can_execute_now (bool)

- RISK_TOKEN: object
  - risk_level
  - risk_reasons[]
  - blocked (bool)
  - block_reason
  - required_safeguards[]

- APPROVAL_TOKEN: object
  - approval_level
  - decision_kind            # ALLOW|AUDIT_ONLY|DEFER|DENY
  - decision_reason
  - required_approvers[]
  - required_safeguards_confirm[]
  - blocked (bool)
  - block_reason

- AUDIT_BRIDGE_TOKEN: object
  - audit_level
  - log_plan[]
  - required_log_keys[]
  - ready (bool)
  - defer_reason
  - notes

### Optional
- FAIL_CODE_MAP: object (optional)
  - version
  - codes: map[string] -> object
    - title
    - severity
    - description
    - remedy_hint
  (Если не передан, violations остаются без расширенной расшифровки.)

- REPORT_HINTS: object (optional)
  - verbose: true|false
  - include_payload_digests: true|false

---

## [M] OUTPUT
- COMPLIANCE_REPORT_TOKEN: object
  - status: PASS|FAIL|DEFER
  - decision_kind: (copy from APPROVAL_TOKEN)
  - blocked: bool
  - block_reason: string
  - summary: string
  - violations: array[VIOLATION_ITEM]
  - required_fixes: array[FIX_ITEM]
  - safeguards_required: array[string]
  - dependencies_missing: array[string]
  - log_ready: bool
  - next_actions: array[string]
  - evidence: object
    - tokens_seen: array[string]
    - deterministic_digest: string
  - notes: string

Where:
### VIOLATION_ITEM
- code: string                 # e.g. "FAIL.GVN.RULE.NON_RAW_NAV"
- severity: LOW|MED|HIGH|CRITICAL
- source_module: string        # e.g. "GVN.RULE_ENFORCER"
- message: string
- details: object
- remedy: string               # short instruction
- fail_code_info: object|null  # from FAIL_CODE_MAP if present

### FIX_ITEM
- fix_id: string               # deterministic
- priority: P0|P1|P2
- description: string
- target: string               # KEY or area name
- owner: string                # ORC_ENT|USER|SYS
- gating: array[string]        # what it unblocks
- notes: string

---

## [M] HARD RULES
1) Determinism
- Одинаковые входные токены -> идентичный COMPLIANCE_REPORT_TOKEN (включая order списков).
- Любая сортировка фиксированная:
  - violations: severity desc, then source_module asc, then code asc
  - required_fixes: priority asc (P0 first), then target asc, then fix_id asc

2) No invention
- Не добавлять новые нарушения “из головы”.
- Источник нарушений только:
  - RULE_ENFORCER_TOKEN.violations
  - ENTRY_GUARD_TOKEN.missing_inputs (как нарушения входа)
  - DEPENDENCY_TOKEN.missing_keys (как нарушения зависимостей)
  - RISK_TOKEN.blocked / APPROVAL_TOKEN.blocked / AUDIT_BRIDGE_TOKEN.ready=false (как блокеры/деферы)

3) Status policy
- FAIL если:
  - blocked == true (любой модуль блокирует) OR
  - RULE_ENFORCER_TOKEN.ok == false OR
  - ENTRY_GUARD_TOKEN.ok == false
- DEFER если:
  - APPROVAL_TOKEN.decision_kind == DEFER OR
  - DEPENDENCY_TOKEN.ok == false (missing_keys) OR
  - AUDIT_BRIDGE_TOKEN.ready == false
  (и при этом нет FAIL условий)
- PASS если:
  - нет FAIL и нет DEFER условий

4) REPO mode clarity
- В MODE REPO:
  - status может быть PASS даже если log_plan = NOOP, при условии audit_bridge ready==true (keys confirmed)
  - если audit_bridge ready==false -> DEFER (потому что лог не подтверждён)

---

## [M] COMPLIANCE SIGNALS (what we read)
### Entry signals
- ENTRY_GUARD_TOKEN.ok
- ENTRY_GUARD_TOKEN.missing_inputs[]

### Rule signals
- RULE_ENFORCER_TOKEN.ok
- RULE_ENFORCER_TOKEN.blocked
- RULE_ENFORCER_TOKEN.violations[]
- RULE_ENFORCER_TOKEN.required_fixes[]

### Dependency signals
- DEPENDENCY_TOKEN.ok
- DEPENDENCY_TOKEN.missing_keys[]
- DEPENDENCY_TOKEN.markers_confirmed

### Risk/approval signals
- RISK_TOKEN.blocked, RISK_TOKEN.risk_level, RISK_TOKEN.required_safeguards[]
- APPROVAL_TOKEN.blocked, APPROVAL_TOKEN.decision_kind, APPROVAL_TOKEN.required_approvers[], required_safeguards_confirm[]

### Audit signals
- AUDIT_BRIDGE_TOKEN.ready
- AUDIT_BRIDGE_TOKEN.required_log_keys[]
- AUDIT_BRIDGE_TOKEN.defer_reason

---

## [M] VIOLATION NORMALIZATION
### A) Missing input -> violation
For each missing_inputs item:
- code: "FAIL.GVN.ENTRY.MISSING_INPUT"
- severity: HIGH
- source_module: "GVN.ENTRY_GUARD"
- message: "Required input is missing"
- details: {"missing": "<item>"}
- remedy: "Provide missing input and rerun entry guard"

### B) Missing keys -> violation (defer-class)
For each missing_keys item:
- code: "DEFER.GVN.DEP.MISSING_KEY"
- severity: MED
- source_module: "GVN.DEPENDENCY_RESOLVER"
- message: "Required KEY not confirmed via NAV/IDX"
- details: {"key": "<missing_key>"}
- remedy: "Confirm KEY via INDEX_MANIFEST and load minimal required docs"

### C) Rule enforcer violations pass-through
Each violation from RULE_ENFORCER_TOKEN.violations is included as-is, then optionally enriched by FAIL_CODE_MAP.

### D) Audit not ready -> violation (defer-class)
If AUDIT_BRIDGE_TOKEN.ready == false:
- code: "DEFER.GVN.LOG.NOT_READY"
- severity: MED
- source_module: "GVN.AUDIT_LOG_BRIDGE"
- message: "Log keys not confirmed"
- details: {"defer_reason": "<AUDIT_BRIDGE_TOKEN.defer_reason>"}
- remedy: "Confirm LOG realm availability via NAV / IDX and rerun"

### E) Risk/approval blocks -> violation (fail-class)
If RISK_TOKEN.blocked == true:
- code: "FAIL.GVN.RISK.BLOCKED"
- severity: CRITICAL
- source_module: "GVN.RISK_SAFETY"
- message: "Action blocked by risk safety"
- details: {"block_reason": "<RISK_TOKEN.block_reason>", "risk_level": "<risk_level>"}
- remedy: "Apply required safeguards or narrow scope"

If APPROVAL_TOKEN.blocked == true OR APPROVAL_TOKEN.decision_kind == DENY:
- code: "FAIL.GVN.APPROVAL.DENIED"
- severity: CRITICAL
- source_module: "GVN.DECISION_APPROVAL"
- message: "Action denied or approval block"
- details: {"block_reason": "<APPROVAL_TOKEN.block_reason>", "approval_level": "<approval_level>"}
- remedy: "Provide required approval inputs or change request"

---

## [M] REQUIRED FIXES MERGE
required_fixes = RULE_ENFORCER_TOKEN.required_fixes (pass-through)
plus synthesized fixes for:
- missing_inputs (P0)
- missing_keys (P1)
- audit not ready (P1)

### Synthesized FIX format
- fix_id deterministic:
  - "FIX|<code>|<target>"
- priority:
  - missing_inputs -> P0
  - risk/approval blocked -> P0
  - missing_keys -> P1
  - audit not ready -> P1
- owner:
  - missing_inputs -> USER
  - missing_keys -> ORC_ENT
  - audit not ready -> ORC_ENT
  - risk safeguards -> USER (or SYS depending on policy; default USER)

---

## [M] NEXT ACTIONS GENERATION (deterministic)
next_actions is a canonical list of short instructions, in this order if applicable:
1) "Provide missing inputs"
2) "Resolve required KEYS via INDEX_MANIFEST"
3) "Confirm LOG keys availability"
4) "Apply required safeguards"
5) "Request required approvals"
6) "Proceed to next pipeline step"

Rules:
- If status == FAIL: exclude "Proceed to next pipeline step"
- If status == DEFER: include steps 1–5 as needed, exclude "Proceed" until all defer reasons cleared
- If status == PASS: include "Proceed to next pipeline step"

---

## [M] REPORT SUMMARY TEMPLATE
summary is a single line:
"COMPLIANCE=<status> | DECISION=<decision_kind> | BLOCKED=<true/false> | V=<count> | FIX=<count> | RISK=<risk_level> | LOG_READY=<true/false>"

---

## [M] EVIDENCE DIGEST (deterministic)
deterministic_digest is a short stable string built from:
- token_id
- status
- decision_kind
- risk_level
- counts (violations, fixes)
- sorted list of violation codes (joined)

Format:
"DIGEST:v1|" + token_id + "|" + status + "|" + decision_kind + "|" + risk_level + "|V" + v_count + "|F" + f_count + "|" + codes_joined

---

## [M] REPO MODE NOTE
В MODE REPO модуль всегда выдаёт полный отчёт как данные.
Никаких записей в LOG не делает. Если нужно “зафиксировать” отчёт, это делает внешний слой при выходе из REPO.

---

## [M] CHANGELOG
- 2026-02-03: v1.0.0 created. Deterministic compliance reporter with PASS/FAIL/DEFER policy, violation normalization, required fixes merge, and next-actions generator.
