FILE: UE_V2/03_ENT/30_ORC_ENT/00_GOVERNANCE_ORC_ENT/05__GVN__RISK_SAFETY__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 00_GOVERNANCE_ORC_ENT
DOC_TYPE: ORC_MODULE
DOMAIN: GVN_ORC_ENT
MODULE: GVN.RISK_SAFETY
UID: UE.V2.ENT.ORC.GVN.RISK_SAFETY.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-03
OWNER: ORC_ENT
NAV_RULE: Use KEYS only (RAW resolved via INDEX_MANIFEST)

---

## [M] ROLE
Risk and safety evaluator for governance actions.

Задача модуля:
- обнаружить рискованные классы операций (NAV/PIPE/LOG/REG/KB/XREF/массовые правки)
- назначить обязательные safeguards (ограничители, режимы, требования к проверкам)
- заблокировать выполнение при нарушении HARD_RULES или при отсутствии safeguards
- вернуть детерминированный RISK_TOKEN, который читают DECISION_APPROVAL и RULE_ENFORCER

В MODE REPO модуль никогда не запускает «опасное выполнение», а только:
- классифицирует риск
- требует гейты/апрув
- отдаёт план мер безопасности

---

## [M] INPUT
- GOVN_TASK_TOKEN (required): object
  - token_id
  - domain (must be GVN_ORC_ENT)
  - mode (REPO|EDIT|…)
  - task_text
  - constraints (optional)
  - exec_policy (optional)
  - run_intent (optional)

- CHANGE_CLASS (required): object
  - change_type
  - change_level
  - touches_realms: array[string]
  - can_execute_now
  - reason_if_blocked

- CHANGE_PLAN (optional): object
  - target_keys: array[string]
  - operations: array[object]
    - op_kind
    - target_key
    - required_checks
    - required_logs

- CONTEXT_FLAGS (optional): object
  - user_requested_bypass (bool)
  - mass_load_detected (bool)
  - raw_missing_detected (bool)
  - marker_missing_detected (bool)
  - external_dependency_required (bool)

---

## [M] OUTPUT
- RISK_TOKEN: object
  - risk_level: NONE|LOW|MED|HIGH|CRITICAL
  - risk_reasons: array[string]
  - blocked: true|false
  - block_reason: string (if blocked)
  - required_safeguards: array[string]
  - required_approvals: array[string]
  - required_checks_additional: array[string]
  - exec_constraints: object
    - max_targets: integer
    - allowed_realms: array[string]
    - nav_policy: "KEY_ONLY"
    - load_policy: "ANTI_NOISE_MIN"
    - write_policy: "NO_WRITE_IN_REPO" | "ALLOW_WRITE"
  - notes: short string

---

## [M] HARD RULES (safety invariants)
1) KEY_ONLY NAV
- Любые действия и ссылки на цели только по KEY.

2) NO MASS LOAD
- Запрещена массовая загрузка деревьев/реалмов.
- Разрешено: START + MANIFEST + ROUTER + NAV_ROOT + 1 доменный IDX + 1–3 target docs.

3) REPO = NO WRITE
- Если mode содержит REPO: write_policy = NO_WRITE_IN_REPO.
- Любая попытка “внести изменения” помечается как blocked=true (кроме AUDIT_ONLY).

4) RAW / MARKER missing = STOP condition (propagate)
- Если raw_missing_detected или marker_missing_detected: blocked=true.
- block_reason = "missing_raw_or_marker"

---

## [M] RISK TAXONOMY (deterministic)
### Risk Reasons (canonical codes)
- RISK.NAV_BYPASS_ATTEMPT
- RISK.MASS_LOAD
- RISK.RAW_MISSING
- RISK.MARKER_MISSING
- RISK.PIPE_BREAKAGE
- RISK.NAV_RULE_MUTATION
- RISK.LOG_POLICY_IMPACT
- RISK.REG_CONFLICT
- RISK.KB_SCOPE_DRIFT
- RISK.XREF_CYCLE
- RISK.HIGH_BLAST_RADIUS
- RISK.UNSAFE_EXEC_IN_REPO

### Realm-based sensitivity map
- NAV: HIGH
- PIPE: HIGH
- LOG: MED
- REG: MED
- KB: MED
- XREF: MED
- ENT (leaf docs): LOW–MED

---

## [M] RISK LEVEL RULES (top-down, first match wins)
### CRITICAL
- CONTEXT_FLAGS.user_requested_bypass == true
- CHANGE_CLASS.change_type in [NAV_RULE_CHANGE, PIPE_CONTRACT_CHANGE, SAFETY_POLICY_CHANGE]
- CONTEXT_FLAGS.mass_load_detected == true
- operations count > 10 OR target_keys count > 10

### HIGH
- touches_realms includes NAV or PIPE
- CHANGE_CLASS.change_level == CRITICAL
- CHANGE_CLASS.change_type == DOC_MOVE_RENAME
- REG_ENTRY_CHANGE with unknown conflict state

### MED
- touches_realms includes LOG or REG or KB or XREF
- INDEX_UPDATE (single realm) with target_keys count between 6..10
- XREF_LINK_CHANGE (non-trivial)

### LOW
- DOC_CREATE / DOC_UPDATE with <= 5 targets
- INDEX_UPDATE with <= 5 entries

### NONE
- AUDIT_ONLY with no external dependency and within anti-noise limits

---

## [M] SAFEGUARDS (canonical)
- SAFE.KEY_ONLY_NAV_ENFORCED
- SAFE.ANTI_NOISE_MINLOAD
- SAFE.TARGET_LIMIT_5
- SAFE.TARGET_LIMIT_10
- SAFE.NO_WRITE_IN_REPO
- SAFE.REQUIRE_ROLLBACK_PLAN
- SAFE.REQUIRE_APPROVAL_GATE
- SAFE.REQUIRE_DOUBLE_CHECKS
- SAFE.REQUIRE_XREF_CYCLE_SCAN
- SAFE.REQUIRE_REG_CONFLICT_SCAN
- SAFE.REQUIRE_PIPE_DEFAULT_COMPAT
- SAFE.REQUIRE_NAV_ROOT_COMPAT
- SAFE.REQUIRE_LOG_KEYS_AVAILABLE

---

## [M] APPROVALS (canonical)
- APPROVAL.NONE
- APPROVAL.REQUIRED (single owner)
- APPROVAL.ESCALATE (multi-owner / critical realms)
- APPROVAL.BLOCKED_IN_REPO

---

## [M] REQUIRED CHECKS ADDITIONS (by risk)
### Always add
- CHECK.KEY_ONLY_NAV
- CHECK.ANTI_NOISE_MAXLOAD

### If risk >= MED
- CHECK.LOG_KEYS_AVAILABLE
- CHECK.DECISION_LOG_READY

### If touches XREF
- CHECK.XREF_EDGE_VALID
- CHECK.XREF_CYCLE_RISK_EVAL

### If touches REG
- CHECK.REG_KEY_VALID
- CHECK.REG_NON_CONFLICT

### If touches PIPE
- CHECK.PIPE_DEFAULT_ROUTING
- CHECK.PIPE_COMPAT_NOTES

### If touches NAV
- CHECK.NAV_ROOT_COMPAT
- CHECK.NO_BYPASS_PATH

---

## [M] EXEC CONSTRAINTS (deterministic defaults)
- max_targets:
  - NONE/LOW: 5
  - MED: 10
  - HIGH/CRITICAL: 3 (force minimal blast radius)
- allowed_realms:
  - default: touches_realms (from CHANGE_CLASS), but clamped:
    - if HIGH/CRITICAL: must be subset without expanding
- load_policy:
  - always "ANTI_NOISE_MIN"
- nav_policy:
  - always "KEY_ONLY"
- write_policy:
  - if mode contains REPO -> "NO_WRITE_IN_REPO"
  - else -> "ALLOW_WRITE" (subject to DECISION_APPROVAL)

---

## [M] BLOCKING LOGIC
blocked=true if any:
- CONTEXT_FLAGS.raw_missing_detected == true
- CONTEXT_FLAGS.marker_missing_detected == true
- CONTEXT_FLAGS.mass_load_detected == true
- (mode contains REPO) AND (CHANGE_CLASS.change_type != AUDIT_ONLY)

block_reason values:
- "missing_raw_or_marker"
- "mass_load_detected"
- "unsafe_exec_in_repo"

---

## [M] BUILD RISK_TOKEN (algorithm)
1) Init:
- risk_level = NONE
- reasons = []

2) Add reasons from flags:
- if user_requested_bypass -> add RISK.NAV_BYPASS_ATTEMPT
- if mass_load_detected -> add RISK.MASS_LOAD
- if raw_missing_detected -> add RISK.RAW_MISSING
- if marker_missing_detected -> add RISK.MARKER_MISSING

3) Add reasons from CHANGE_CLASS:
- if touches_realms includes PIPE -> add RISK.PIPE_BREAKAGE
- if change_type == NAV_RULE_CHANGE -> add RISK.NAV_RULE_MUTATION
- if touches_realms includes LOG and change_type == LOG_POLICY_CHANGE -> add RISK.LOG_POLICY_IMPACT
- if touches_realms includes REG -> add RISK.REG_CONFLICT
- if change_type == KB_SCOPE_CHANGE -> add RISK.KB_SCOPE_DRIFT
- if touches_realms includes XREF -> add RISK.XREF_CYCLE
- if target_keys count > 10 -> add RISK.HIGH_BLAST_RADIUS

4) Compute risk_level using section “RISK LEVEL RULES”.

5) Determine safeguards:
- always include:
  - SAFE.KEY_ONLY_NAV_ENFORCED
  - SAFE.ANTI_NOISE_MINLOAD
  - SAFE.REQUIRE_LOG_KEYS_AVAILABLE
- include target limits:
  - NONE/LOW -> SAFE.TARGET_LIMIT_5
  - MED -> SAFE.TARGET_LIMIT_10
  - HIGH/CRITICAL -> SAFE.TARGET_LIMIT_5 (and exec_constraints max_targets=3)
- if risk >= MED -> SAFE.REQUIRE_DOUBLE_CHECKS
- if touches XREF -> SAFE.REQUIRE_XREF_CYCLE_SCAN
- if touches REG -> SAFE.REQUIRE_REG_CONFLICT_SCAN
- if touches PIPE -> SAFE.REQUIRE_PIPE_DEFAULT_COMPAT
- if touches NAV -> SAFE.REQUIRE_NAV_ROOT_COMPAT
- if risk >= HIGH -> SAFE.REQUIRE_ROLLBACK_PLAN
- if mode contains REPO -> SAFE.NO_WRITE_IN_REPO

6) Determine approvals:
- if blocked because REPO -> APPROVAL.BLOCKED_IN_REPO
- else if risk_level in [HIGH, CRITICAL] -> APPROVAL.ESCALATE
- else if risk_level == MED -> APPROVAL.REQUIRED
- else -> APPROVAL.NONE

7) Return RISK_TOKEN.

---

## [M] NOTES ON “GAP”
Модуль не вводит отдельный статус GAP.
Он работает так:
- если не хватает RAW/markers/keys -> blocked=true с конкретной причиной
- если чего-то “нет для выполнения” (например approval path) -> required_approvals выставляет необходимость, а CHANGE_CONTROL/DECISION_APPROVAL решают дальше

---

## [M] EXAMPLE OUTPUT (for current governance completion run)
Input:
- mode: REPO (USAGE-ONLY, NO-EDIT)
- change_type inferred: DOC_UPDATE (governance modules)
- target_keys count: ~8

Result:
- risk_level: MED (touches ENT+LOG, multi-target)
- blocked: true
- block_reason: "unsafe_exec_in_repo"
- required_safeguards: includes SAFE.NO_WRITE_IN_REPO + SAFE.TARGET_LIMIT_10 + SAFE.REQUIRE_DOUBLE_CHECKS

---

## [M] CHANGELOG
- 2026-02-03: v1.0.0 created. Deterministic risk taxonomy + safeguards + REPO block rules.
