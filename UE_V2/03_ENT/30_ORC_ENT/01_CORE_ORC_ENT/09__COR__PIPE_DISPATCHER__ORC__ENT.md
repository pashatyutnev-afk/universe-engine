FILE: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/09__COR__PIPE_DISPATCHER__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 01_CORE_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: COR_ORC_ENT
UID: UE.V2.ENT.ORC.COR.PIPE_DISPATCHER.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: COR_PIPE_DISPATCHER
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.COR.PIPE_DISPATCHER.001

## [M] PURPOSE
Диспетчеризует выполнение в выбранный PIPE_KEY.
Готовит DISPATCH_TOKEN: что запустить, какие ключи открыть, какие outputs ожидать.

## [M] INPUTS / OUTPUTS
- Inputs: [PIPE_KEY, ROUTE_TOKEN, EXEC_MODE]
- Outputs: [DISPATCH_TOKEN, FAIL_CODE?]

## [M] CORE_RULES
- Dispatch только через KEY-resolve, без прямых ссылок.
- DISPATCH_TOKEN фиксирует expected artifacts и минимальный план шагов.

## [M] INTERFACES (RAW only)
- Entry points (RAW):
- Dependencies (RAW):

## [M] KB SCOPE
- KB Inputs: [контракты пайпов как ключи]
- KB Outputs: [DISPATCH_TOKEN]
- KB Boundaries: [без расширения workset]

## [M] GATES
- PASS: dispatch план сформирован
- FAIL: отсутствуют ключи/контракт

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [CTL]
- Handoff: DISPATCH_TOKEN -> STEP_RUN_CONTROLLER

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
