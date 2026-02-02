FILE: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/08__COR__PIPE_SELECTOR__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 01_CORE_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: COR_ORC_ENT
UID: UE.V2.ENT.ORC.COR.PIPE_SELECTOR.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: COR_PIPE_SELECTOR
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.COR.PIPE_SELECTOR.001

## [M] PURPOSE
Выбирает лучший PIPE_KEY на основе DOMAIN_TARGET, PIPE_CANDIDATES и ограничений.
Выбор детерминированный: один победитель или FAIL.

## [M] INPUTS / OUTPUTS
- Inputs: [ROUTE_TOKEN, SENTINEL_REPORTS]
- Outputs: [PIPE_KEY, SELECTION_RATIONALE, FAIL_CODE?]

## [M] CORE_RULES
- Если несколько кандидатов и нет признаков — запросить уточнение через FAIL_CODE (route unresolved).
- Предпочитать “специализированный” доменный пайп над legacy.

## [M] INTERFACES (RAW only)
- Entry points (RAW):
- Dependencies (RAW):

## [M] KB SCOPE
- KB Inputs: [карта пайпов, критерии выбора]
- KB Outputs: [PIPE_KEY]
- KB Boundaries: [без выдумывания пайпов]

## [M] GATES
- PASS: PIPE_KEY выбран
- FAIL: неоднозначность без входа

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [CTL, QA]
- Handoff: PIPE_KEY -> PIPE_DISPATCHER

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
