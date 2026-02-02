FILE: UE_V2/03_ENT/30_ORC_ENT/08_META_ORC_ENT/01__MET__SELF_CHECK__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 08_META_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: MET_ORC_ENT
UID: UE.V2.ENT.ORC.MET.SELF_CHECK.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MET_SELF_CHECK
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.MET.SELF_CHECK.001

## [M] PURPOSE
Выполняет self-check: проверяет входы, непротиворечивость, соответствие режиму (no-edit), наличие обязательных секций и токенов.
Возвращает SELF_CHECK_REPORT и список REQUIRED_FIXES.

## [M] INPUTS / OUTPUTS
- Inputs: [TASK_TEXT, DRAFT_OUTPUT?]
- Outputs: [SELF_CHECK_REPORT, REQUIRED_FIXES, FAIL_CODE?]

## [M] SELF_CHECK_REPORT (minimum)
- MISSING_INPUTS
- CONTRADICTIONS
- POLICY_VIOLATIONS
- TEMPLATE_MISSING_SECTIONS
- NEXT_REQUIRED_ACTION

## [M] KB SCOPE
- KB Inputs: [task + draft]
- KB Outputs: [self-check tokens]
- KB Boundaries: [без расширения scope]
- KB RAW refs: []

## [M] GATES
- PASS: нет блокирующих нарушений
- FAIL: есть policy violations или критические пропуски входа

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA, CTL]
- Handoff: SELF_CHECK_REPORT -> TEMPLATE_APPLIER / FAIL_HANDLER (caller)

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
