FILE: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/13__COR__LOGGER__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 01_CORE_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: COR_ORC_ENT
UID: UE.V2.ENT.ORC.COR.LOGGER.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: COR_LOGGER
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.COR.LOGGER.001

## [M] PURPOSE
Формирует RUN_LOG и DECISION_LOG как токены/артефакты вывода (без записи в репо).
Пишет только факты: какие KEYS трогали, какие решения приняли, какой итог.

## [M] INPUTS / OUTPUTS
- Inputs: [ROUTE_TOKEN, STEP_STATE, FINAL_STATUS, DECISION_TOKEN?]
- Outputs: [RUN_LOG, DECISION_LOG?]

## [M] CORE_RULES
- Никаких “историй” и длинных лирических описаний.
- Вся навигация в логах через KEYS, без RAW.

## [M] INTERFACES (RAW only)
- Entry points (RAW):
- Dependencies (RAW):

## [M] KB SCOPE
- KB Inputs: [log templates]
- KB Outputs: [RUN_LOG, DECISION_LOG]
- KB Boundaries: [facts only]

## [M] GATES
- PASS: RUN_LOG сформирован
- FAIL: UE.FAIL.LOG_MISSING

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA]
- Handoff: logs -> RELEASE_PACKAGER

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
