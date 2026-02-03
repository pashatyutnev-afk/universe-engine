FILE: UE_V2/03_ENT/30_ORC_ENT/00_GOVERNANCE_ORC_ENT/00__PIPELINE_CONTRACT__GVN__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 00_GOVERNANCE_ORC_ENT
DOC_TYPE: PIPELINE_CONTRACT
DOMAIN: GVN_ORC_ENT
UID: UE.V2.ENT.PIPE.GVN_ORC_ENT.001
VERSION: 1.0.1
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-03
OWNER: ORC_ENT
NAV_RULE: Use KEYS only (RAW resolved via INDEX_MANIFEST)

---

## [M] PURPOSE
Контракт пайплайна governance-run для реалма ORC_ENT (GVN_ORC_ENT).
Обеспечивает детерминированный прогон:
- входная валидация
- проверка hard rules
- расчёт зависимостей (минимальная загрузка)
- контроль изменений + риск/безопасность
- решение/аппрув (если нужно)
- план логирования + итоговый compliance-отчёт

Ключевой принцип: **внутри контракта и сущностей используются только KEYS**.
RAW адреса живут в INDEX_MANIFEST данного реалма.

---

## [M] INPUT (minimum)
- TASK_TEXT (required)
- MODE_HINT (optional): FAST|RELEASE_READY|MASTERPIECE
- CONSTRAINTS (optional): platform, duration, style, references
- CONTEXT_TOKEN (optional): prior route token / prior decisions

---

## [M] OUTPUT (minimum)
- GOVN_TASK_TOKEN
- RULE_CHECK_REPORT
- WORK_SET_KEYS
- CHANGE_ENVELOPE
- RISK_REPORT
- DECISION_TOKEN (optional)
- RUN_LOG_PLAN
- DECISION_LOG_PLAN (optional)
- COMPLIANCE_REPORT
- FAIL_CODE? + REQUIRED_FIXES? (if fail)

---

## [M] HARD RULES
1) MODE REPO: **no-edit** — контракт не выполняет запись/изменения в репо.
2) RAW не используется внутри сущностей/контракта:
   - resolve RAW адресов только через KEY -> INDEX_MANIFEST.
3) Никаких обходов навигации:
   - все зависимости и модули вызываются по KEY.
4) Никаких “GAP статусов”:
   - недостача = FAIL_CODE + REQUIRED_FIXES, а не “GAP”.
5) Anti-noise:
   - загружаем минимум: INDEX_MANIFEST -> только нужные модули по pipeline order.

---

## [M] REQUIRED KEYS (realm-local)
These keys MUST exist in realm INDEX_MANIFEST:
- PIPELINE_CONTRACT
- GVN.ENTRY_GUARD
- GVN.RULE_ENFORCER
- GVN.DEPENDENCY_RESOLVER
- GVN.CHANGE_CONTROL
- GVN.RISK_SAFETY
- (optional) GVN.DECISION_APPROVAL
- GVN.AUDIT_LOG_BRIDGE
- GVN.COMPLIANCE_REPORTER

---

## [M] PIPELINE STEPS (S0–S4)

### S0) ENTRY (Input Gate)
Module KEY: GVN.ENTRY_GUARD
Goal:
- validate minimal inputs
- normalize MODE_HINT
- assemble GOVN_TASK_TOKEN
Outputs:
- GOVN_TASK_TOKEN
- or FAIL_CODE + REQUIRED_FIXES

### S1) RULES (Hard Rules Enforcer)
Module KEY: GVN.RULE_ENFORCER
Goal:
- enforce governance hard rules
- block non-compliant operation early
Outputs:
- RULE_CHECK_REPORT
- or FAIL_CODE + REQUIRED_FIXES

### S2) DEPENDENCIES (Minimal Work Set)
Module KEY: GVN.DEPENDENCY_RESOLVER
Goal:
- compute WORK_SET_KEYS (required/optional + load_order)
- verify every required KEY exists in INDEX_MANIFEST
Outputs:
- WORK_SET_KEYS
- or FAIL_CODE UE.FAIL.DEP_MISSING + REQUIRED_FIXES(missing_keys)

### S3) CONTROL + SAFETY (Change Envelope + Risk)
Module KEYs:
- GVN.CHANGE_CONTROL
- GVN.RISK_SAFETY
- (optional) GVN.DECISION_APPROVAL
Goal:
- CHANGE_CONTROL builds CHANGE_ENVELOPE (dry-run intent, required logs, gates)
- RISK_SAFETY builds RISK_REPORT (risk level, flags, safeguards, block/allow)
- DECISION_APPROVAL used if:
  - MODE_HINT != FAST, or
  - risk_level >= medium, or
  - task touches critical registries/index/law/templates, or
  - policy requires approval
Outputs:
- CHANGE_ENVELOPE
- RISK_REPORT
- DECISION_TOKEN (optional)
- or FAIL_CODE (risk block / approval required / gate fail)

### S4) LOG + COMPLIANCE (Plans + Summary)
Module KEYs:
- GVN.AUDIT_LOG_BRIDGE
- GVN.COMPLIANCE_REPORTER
Goal:
- prepare run/decision log plans (without writing anything)
- produce COMPLIANCE_REPORT with PASS/FAIL + next step
Outputs:
- RUN_LOG_PLAN
- DECISION_LOG_PLAN (optional)
- COMPLIANCE_REPORT
- or FAIL_CODE + REQUIRED_FIXES

---

## [M] FAIL CODES (minimum set)
- UE.FAIL.INPUT_ABSENT
- UE.FAIL.MODE_INVALID
- UE.FAIL.RULE_VIOLATION
- UE.FAIL.DEP_MISSING
- UE.FAIL.RISK_BLOCK
- UE.FAIL.APPROVAL_REQUIRED
- UE.FAIL.GATE_FAIL

---

## [M] REQUIRED_FIXES (format)
If FAIL_CODE emitted, REQUIRED_FIXES must be present:
- REQUIRED_FIXES:
  - missing_keys[] (if dep missing)
  - invalid_fields[] (if mode/input invalid)
  - violated_rules[] (if rules violation)
  - required_safeguards[] (if risk-related)
  - required_gates[] (if gate fail)
  - next_step (single action instruction)

---

## [M] DETERMINISM NOTES
- load_order must be deterministic:
  INDEX_MANIFEST -> S0 -> S1 -> S2 -> S3 -> S4
- same input -> same WORK_SET_KEYS and same decision requirements.

---

## [M] CHANGELOG
- 2026-02-02: v1.0.0 created
- 2026-02-03: v1.0.1 normalized contract; “no GAP statuses, only FAIL_CODE + REQUIRED_FIXES”; key-only navigation
