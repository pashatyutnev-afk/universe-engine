FILE: UE_V2/03_ENT/30_ORC_ENT/00_GOVERNANCE_ORC_ENT/07__GVN__AUDIT_LOG_BRIDGE__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 00_GOVERNANCE_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: GVN_ORC_ENT
UID: UE.V2.ENT.ORC.GVN.AUDIT_LOG_BRIDGE.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: GVN_AUDIT_LOG_BRIDGE
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.GVN.AUDIT_LOG_BRIDGE.001
- STATUS: ACTIVE
- OWNER: ORC_ENT
- VERSION: 1.0.0
- CREATED: 2026-02-02
- UPDATED: 2026-02-02

## [M] PURPOSE
Мост между governance-прогоном и аудит-логированием.
Готовит run/decision лог-артефакты и правила фиксации маршрутов.

## [M] CAPABILITIES (what it can produce)
- Produces: [RUN_LOG_PLAN, DECISION_LOG_PLAN, AUDIT_HOOKS]
- Edits: [] (MODE REPO)
- Never:
  - не пишет в регистры напрямую, если это запрещено режимом
  - не пропускает прогон без минимального лог-плана

## [M] INPUTS / OUTPUTS
- Inputs:
  - GOVN_RESULT_TOKEN (предварительный)
  - DECISION_TOKEN?
  - REQUIRED_LOGS (из CHANGE_CONTROL)
- Outputs:
  - RUN_LOG_PLAN: что и как зафиксировать
  - DECISION_LOG_PLAN: когда писать decision entry
  - AUDIT_HOOKS: ссылки на токены/ключи (без RAW)

## [M] INTERFACES (RAW only)
- Entry points (RAW):
- Dependencies (RAW):

## [M] KB SCOPE
- KB Inputs: [logging policy, минимальные требования audit]
- KB Outputs: [лог-планы и хуки]
- KB Boundaries: [никаких “историй”, только факты прогона и токены]
- KB RAW refs: []

## [M] GATES (pass/fail)
- PASS if:
  - есть план RUN_LOG и условия DECISION_LOG
- FAIL if:
  - логирование требуется, но не может быть обеспечено

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, QA]
- Handoff rules:
  - Передаёт планы в COMPLIANCE_REPORTER и назад в PIPELINE_CONTRACT S3

## [M] CHANGELOG (minimal)
- 2026-02-02: v1.0.0 init
