FILE: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/11__COR__FOCUS_LOOP_CONTROLLER__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 01_CORE_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: COR_ORC_ENT
UID: UE.V2.ENT.ORC.COR.FOCUS_LOOP_CONTROLLER.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: COR_FOCUS_LOOP_CONTROLLER
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.COR.FOCUS_LOOP_CONTROLLER.001

## [M] PURPOSE
Удерживает фокус: не даёт расширять задачу, следит за CONSTRAINTS_LOCK, устраняет дрейф.
Разрешает “повторный цикл” только если есть измеримый прогресс.

## [M] INPUTS / OUTPUTS
- Inputs: [STEP_STATE, ROUTE_TOKEN, DISPATCH_TOKEN]
- Outputs: [FOCUS_REPORT, LOOP_DECISION, FAIL_CODE?]

## [M] CORE_RULES
- Нельзя менять constraints без нового входа.
- Если дрейф — вернуть в scope или FAIL_CODE “route unresolved”.
- Цикл допускается, когда есть явная цель улучшения.

## [M] INTERFACES (RAW only)
- Entry points (RAW):
- Dependencies (RAW):

## [M] KB SCOPE
- KB Inputs: [route token, constraints]
- KB Outputs: [FOCUS_REPORT]
- KB Boundaries: [без расширения]

## [M] GATES
- PASS: фокус соблюдён
- FAIL: drift или бесконечный цикл

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA, CTL]
- Handoff: decision -> STEP_RUN_CONTROLLER / FAIL_HANDLER

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
