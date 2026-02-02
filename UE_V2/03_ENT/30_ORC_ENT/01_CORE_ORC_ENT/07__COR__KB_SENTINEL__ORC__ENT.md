FILE: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/07__COR__KB_SENTINEL__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 01_CORE_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: COR_ORC_ENT
UID: UE.V2.ENT.ORC.COR.KB_SENTINEL.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: COR_KB_SENTINEL
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.COR.KB_SENTINEL.001

## [M] PURPOSE
Гарантирует KB границы: что можно использовать как знания, что нельзя.
Отсекает “знания вне scope” и запрещает домыслы.

## [M] INPUTS / OUTPUTS
- Inputs: [ROUTE_TOKEN, TASK_TOKEN]
- Outputs: [KB_SCOPE_REPORT, FAIL_CODE?]

## [M] CORE_RULES
- KB только из разрешённых источников (по правилам запуска).
- Если источник отсутствует — FAIL_CODE “input absent”, не заполнять пробел.

## [M] INTERFACES (RAW only)
- Entry points (RAW):
- Dependencies (RAW):

## [M] KB SCOPE
- KB Inputs: [TASK_TOKEN, разрешённые ключи]
- KB Outputs: [KB_SCOPE_REPORT]
- KB Boundaries: [no guessing]

## [M] GATES
- PASS: KB границы соблюдены
- FAIL: требуется знание вне границ без источника

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA, CTL]
- Handoff: report -> PIPE_DISPATCHER / FAIL_HANDLER

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
