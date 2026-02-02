FILE: UE_V2/03_ENT/30_ORC_ENT/00_GOVERNANCE_ORC_ENT/08__GVN__COMPLIANCE_REPORTER__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 00_GOVERNANCE_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: GVN_ORC_ENT
UID: UE.V2.ENT.ORC.GVN.COMPLIANCE_REPORTER.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: GVN_COMPLIANCE_REPORTER
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.GVN.COMPLIANCE_REPORTER.001
- STATUS: ACTIVE
- OWNER: ORC_ENT
- VERSION: 1.0.0
- CREATED: 2026-02-02
- UPDATED: 2026-02-02

## [M] PURPOSE
Сборщик итогового compliance-отчёта governance-прогона.
Фиксирует PASS/FAIL, нарушения, условия продолжения и минимальные действия на исправление.

## [M] CAPABILITIES (what it can produce)
- Produces: [COMPLIANCE_REPORT, VIOLATIONS, REQUIRED_FIXES, FAIL_CODE?]
- Edits: [] (MODE REPO)
- Never:
  - не делает “монтажных решений”, только ограничения/риски и факты
  - не добавляет внешние ссылки/RAW в отчёт

## [M] INPUTS / OUTPUTS
- Inputs:
  - RULE_CHECK_REPORT
  - LOAD_ORDER / WORK_SET_KEYS
  - CHANGE_ENVELOPE
  - RISK_REPORT
  - DECISION_TOKEN?
  - RUN_LOG_PLAN / DECISION_LOG_PLAN
- Outputs:
  - COMPLIANCE_REPORT: status + evidence tokens + violations + next
  - REQUIRED_FIXES: короткий список обязательных правок входа/маршрута
  - FAIL_CODE?: UE.FAIL.RULE_VIOLATION | UE.FAIL.GATE_FAIL | UE.FAIL.APPROVAL_REQUIRED

## [M] INTERFACES (RAW only)
- Entry points (RAW):
- Dependencies (RAW):

## [M] KB SCOPE
- KB Inputs: [политики compliance, правила гейтов]
- KB Outputs: [только отчёт и токены]
- KB Boundaries: [без предположений; без расширения scope]
- KB RAW refs: []

## [M] GATES (pass/fail)
- PASS if:
  - violations пусто или полностью покрыто safeguards/условиями
  - required logs and gates удовлетворены
- FAIL if:
  - есть нарушения hard rules
  - approval требуется и не подтверждён
  - gate fail по риску/логированию/ключам

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, QA, CTL]
- Handoff rules:
  - PASS -> вернуть отчёт как итог S2/S3
  - FAIL -> вернуть FAIL_CODE + REQUIRED_FIXES

## [M] CHANGELOG (minimal)
- 2026-02-02: v1.0.0 init
