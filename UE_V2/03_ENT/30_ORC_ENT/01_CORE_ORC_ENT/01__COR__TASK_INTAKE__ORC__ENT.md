FILE: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/01__COR__TASK_INTAKE__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 01_CORE_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: COR_ORC_ENT
UID: UE.V2.ENT.ORC.COR.TASK_INTAKE.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: COR_TASK_INTAKE
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.COR.TASK_INTAKE.001

## [M] PURPOSE
Принимает TASK_TEXT и превращает в TASK_TOKEN: intent, constraints, output_goal, domain_hints.
Ничего не “угадывает”, если входа нет.

## [M] INPUTS / OUTPUTS
- Inputs: [TASK_TEXT, MODE_HINT?]
- Outputs: [TASK_TOKEN, EXEC_MODE, FAIL_CODE?]

## [M] CORE_RULES
- В MODE REPO любые запросы “отредактируй репо” помечать как запрещённые intent.
- Если не хватает входа — FAIL_CODE + минимальный список требуемых данных.

## [M] INTERFACES (RAW only)
- Entry points (RAW):
- Dependencies (RAW):

## [M] KB SCOPE
- KB Inputs: [формат токенов, режимы исполнения]
- KB Outputs: [TASK_TOKEN]
- KB Boundaries: [без расширения scope]

## [M] GATES
- PASS: TASK_TEXT есть, intent определён
- FAIL: TASK_TEXT пуст, или требуется запрещённое действие

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, CTL, QA]
- Handoff: TASK_TOKEN -> DOMAIN_DETECTOR

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
