FILE: UE_V2/03_ENT/30_ORC_ENT/00_GOVERNANCE_ORC_ENT/06__GVN__DECISION_APPROVAL__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 00_GOVERNANCE_ORC_ENT
DOC_TYPE: ORC_MODULE
DOMAIN: GVN_ORC_ENT
MODULE: GVN.DECISION_APPROVAL
UID: UE.V2.ENT.ORC.GVN.DECISION_APPROVAL.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-03
OWNER: ORC_ENT
NAV_RULE: Use KEYS only (RAW resolved via INDEX_MANIFEST)

---

## [M] ROLE
Decision approval and escalation module for governance actions.

Задача модуля:
- на основе RISK_TOKEN и CHANGE_CLASS детерминированно решить:
  - нужно ли approval
  - какой тип approval (REQUIRED | ESCALATE | BLOCKED_IN_REPO | NONE)
  - кто считается “owner” для принятия решения
  - какие записи обязательно должны попасть в DECISION_LOG / RUN_LOG
- вернуть APPROVAL_TOKEN, который читает CHANGE_CONTROL и AUDIT_LOG_BRIDGE

В MODE REPO модуль всегда:
- запрещает “утверждать выполнение”
- разрешает только “фиксировать решение” (AUDIT-ONLY), если LOG доступен по KEY

---

## [M] INPUT
- GOVN_TASK_TOKEN (required): object
  - token_id
  - domain (must be GVN_ORC_ENT)
  - mode (REPO|EDIT|…)
  - task_text
  - constraints (optional)

- RISK_TOKEN (required): object
  - risk_level
  - risk_reasons[]
  - blocked
  - block_reason
  - required_safeguards[]
  - required_approvals (optional)
  - exec_constraints

- CHANGE_CLASS (required): object
  - change_type
  - change_level
  - touches_realms: array[string]
  - target_keys_count: integer
  - can_execute_now
  - reason_if_blocked (optional)

- OWNER_HINT (optional): object
  - owner_primary (string)
  - owners_secondary: array[string]

- CONTEXT_FLAGS (optional): object
  - log_keys_available (bool)
  - decision_log_ready (bool)
  - requires_multi_owner (bool)

---

## [M] OUTPUT
- APPROVAL_TOKEN: object
  - approval_level: NONE|REQUIRED|ESCALATE|BLOCKED_IN_REPO
  - decision_kind: ALLOW|DENY|AUDIT_ONLY|DEFER
  - decision_reason: string
  - required_approvers: array[string]
  - escalation_path: array[string]
  - required_decision_log_fields: array[string]
  - required_run_log_fields: array[string]
  - required_safeguards_confirm: array[string]
  - blocked: true|false
  - block_reason: string (if blocked)
  - notes: short string

---

## [M] HARD RULES
1) REPO = no approval to execute
- Если mode содержит REPO, decision_kind не может быть ALLOW.
- Допустимы только: AUDIT_ONLY, DEFER, DENY.

2) If RISK_TOKEN.blocked == true -> always blocked
- approval_level = BLOCKED_IN_REPO (если причина unsafe_exec_in_repo)
  иначе approval_level = ESCALATE
- decision_kind = DENY (или DEFER, если блок устраним safeguards и это не REPO)

3) Logs are mandatory for governance decisions
- Если decision_log_ready == false или log_keys_available == false:
  - decision_kind = DEFER
  - blocked=false
  - decision_reason = "log_not_ready"
  - required_approvers includes "SYS/LOG_OWNER"

4) Determinism
- При одинаковом (risk_level, mode, change_type, touches_realms) выход всегда одинаковый.
- Любые “мнения” формулируются как notes, не меняя решение.

---

## [M] APPROVAL MATRIX (deterministic)
### Step A: Base approval_level by risk
- NONE: risk_level in [NONE, LOW]
- REQUIRED: risk_level == MED
- ESCALATE: risk_level in [HIGH, CRITICAL]

### Step B: Override by realms
If touches_realms includes NAV or PIPE:
- min approval_level = ESCALATE

If touches_realms includes REG and change_type != AUDIT_ONLY:
- min approval_level = REQUIRED

If touches_realms includes LOG and change_type in [LOG_POLICY_CHANGE]:
- min approval_level = ESCALATE

### Step C: Override by mode
If mode contains REPO:
- approval_level = BLOCKED_IN_REPO
- decision_kind = AUDIT_ONLY or DEFER (see decision rules)

---

## [M] DECISION KIND RULES
### 1) If mode contains REPO
- If RISK_TOKEN.blocked == true and block_reason == "unsafe_exec_in_repo":
  - decision_kind = AUDIT_ONLY
  - decision_reason = "repo_mode_no_write"
- Else:
  - decision_kind = DEFER
  - decision_reason = "repo_mode_requires_edit_session"

### 2) If not REPO
- If RISK_TOKEN.blocked == true:
  - decision_kind = DENY
  - decision_reason = RISK_TOKEN.block_reason
- Else:
  - If approval_level == NONE:
    - decision_kind = ALLOW
    - decision_reason = "low_risk"
  - If approval_level == REQUIRED:
    - decision_kind = DEFER
    - decision_reason = "approval_required"
  - If approval_level == ESCALATE:
    - decision_kind = DEFER
    - decision_reason = "escalation_required"

---

## [M] APPROVER RESOLUTION (who must approve)
### Canonical approver tags
- SYS/NAV_OWNER
- SYS/PIPE_OWNER
- SYS/REG_OWNER
- SYS/LOG_OWNER
- SYS/KB_OWNER
- SYS/XREF_OWNER
- SYS/RUNTIME_OWNER
- USER/REQUESTOR

### Deterministic mapping by touched realms
required_approvers always includes:
- USER/REQUESTOR

Then add:
- if touches NAV -> SYS/NAV_OWNER
- if touches PIPE -> SYS/PIPE_OWNER
- if touches REG -> SYS/REG_OWNER
- if touches LOG -> SYS/LOG_OWNER
- if touches KB -> SYS/KB_OWNER
- if touches XREF -> SYS/XREF_OWNER

If approval_level == ESCALATE:
- add SYS/RUNTIME_OWNER

OWNER_HINT может сузить список, но не может удалить обязательные realm owners.

---

## [M] ESCALATION PATH (deterministic)
- If approval_level != ESCALATE: escalation_path = []
- Else:
  - escalation_path = [
      "USER/REQUESTOR",
      "SYS/<PRIMARY_REALM_OWNER>",
      "SYS/RUNTIME_OWNER"
    ]

PRIMARY_REALM_OWNER определяется приоритетом:
NAV > PIPE > LOG > REG > XREF > KB > ENT

---

## [M] REQUIRED LOG FIELDS
### DECISION_LOG fields (minimum)
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

### RUN_LOG fields (minimum)
- run_id
- token_id
- step
- module_key (GVN.DECISION_APPROVAL)
- inputs_hash (optional)
- output_summary
- blocked
- notes

---

## [M] REQUIRED SAFEGUARDS CONFIRM (pass-through)
required_safeguards_confirm = RISK_TOKEN.required_safeguards
(модуль не придумывает новые safeguards, только подтверждает список)

---

## [M] FAILURE / DEFER CONDITIONS
This module never emits GAP.

It can produce:
- blocked=true, decision_kind=DENY (hard stop)
- decision_kind=DEFER (waiting for approvals/log readiness)
- decision_kind=AUDIT_ONLY (REPO mode, record-only)

block_reason values:
- "unsafe_exec_in_repo"
- "missing_raw_or_marker"
- "mass_load_detected"
- "hard_rule_violation"
- "risk_blocked"

defer reasons:
- "approval_required"
- "escalation_required"
- "log_not_ready"
- "repo_mode_requires_edit_session"

---

## [M] EXAMPLE OUTPUT (for current governance completion run)
Input:
- mode: REPO (USAGE-ONLY, NO-EDIT)
- risk_level: MED
- blocked: true (unsafe_exec_in_repo)
- touches_realms: [ENT, LOG] (multi-doc governance)

Output:
- approval_level: BLOCKED_IN_REPO
- decision_kind: AUDIT_ONLY
- decision_reason: "repo_mode_no_write"
- required_approvers: ["USER/REQUESTOR", "SYS/LOG_OWNER"]
- escalation_path: []
- required_decision_log_fields: (minimum set)
- required_run_log_fields: (minimum set)
- required_safeguards_confirm: includes SAFE.NO_WRITE_IN_REPO

---

## [M] CHANGELOG
- 2026-02-03: v1.0.0 created. Deterministic approval matrix + REPO constraints + log requirements.
