FILE: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/14__COR__FAIL_HANDLER__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 01_CORE_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: COR_ORC_ENT
UID: UE.V2.ENT.ORC.COR.FAIL_HANDLER.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: COR_FAIL_HANDLER
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.COR.FAIL_HANDLER.001

## [M] PURPOSE
Нормализует FAIL_CODE и превращает в понятный “что нужно дать/исправить”.
Делает минимальный NEXT_PROMPT: "го" только когда вход исправлен.

## [M] INPUTS / OUTPUTS
- Inputs: [FAIL_CODE, CONTEXT_TOKEN?]
- Outputs: [FAIL_RESPONSE, REQUIRED_INPUTS, NEXT_PROMPT]

## [M] CORE_RULES
- Никаких лишних вопросов: только минимальный required input list.
- Не скрывать причину fail.

## [M] INTERFACES (RAW only)
- Entry points (RAW):
- Dependencies (RAW):

## [M] KB SCOPE
- KB Inputs: [fail code taxonomy]
- KB Outputs: [fail response]
- KB Boundaries: [no scope expansion]

## [M] GATES
- PASS: fail объяснён и требование чёткое

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA, CTL]
- Handoff: required inputs -> TASK_INTAKE

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
