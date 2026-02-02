FILE: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/10__COR__STEP_RUN_CONTROLLER__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 01_CORE_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: COR_ORC_ENT
UID: UE.V2.ENT.ORC.COR.STEP_RUN_CONTROLLER.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: COR_STEP_RUN_CONTROLLER
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.COR.STEP_RUN_CONTROLLER.001

## [M] PURPOSE
Контролирует каденс STEP-RUN: что выполняем сейчас, что дальше, когда остановиться.
Следит за формой шага и за обязательным NEXT_PROMPT.

## [M] INPUTS / OUTPUTS
- Inputs: [DISPATCH_TOKEN, EXEC_MODE]
- Outputs: [STEP_STATE, NEXT_PROMPT, FAIL_CODE?]

## [M] CORE_RULES
- Один шаг = один пакет действий.
- После шага: NEXT_PROMPT "го" или FAIL_CODE.
- Не допускать бесконечных циклов без прогресса (delegate to FOCUS_LOOP_CONTROLLER).

## [M] INTERFACES (RAW only)
- Entry points (RAW):
- Dependencies (RAW):

## [M] KB SCOPE
- KB Inputs: [step-run contract rules]
- KB Outputs: [STEP_STATE]
- KB Boundaries: [без увеличения scope]

## [M] GATES
- PASS: шаг корректен, progress есть
- FAIL: нет прогресса или нарушена форма шага

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA, CTL]
- Handoff: STEP_STATE -> FOCUS_LOOP_CONTROLLER / GATEKEEPER

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
