FILE: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/05__COR__REG_SENTINEL__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 01_CORE_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: COR_ORC_ENT
UID: UE.V2.ENT.ORC.COR.REG_SENTINEL.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: COR_REG_SENTINEL
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.COR.REG_SENTINEL.001

## [M] PURPOSE
Проверяет, что прогон сможет отдать RUN_LOG/DECISION_LOG/OUTPUT_PACK (как токены).
Никаких реальных записей в репо, только требования и планы.

## [M] INPUTS / OUTPUTS
- Inputs: [ROUTE_TOKEN, EXEC_MODE]
- Outputs: [REG_CHECK_REPORT, FAIL_CODE?]

## [M] CORE_RULES
- Если логи обязательны по режиму — требовать LOGGER + RELEASE_PACKAGER.
- Если режим запрещает фиксации — маркировать как “token-only”.

## [M] INTERFACES (RAW only)
- Entry points (RAW):
- Dependencies (RAW):

## [M] KB SCOPE
- KB Inputs: [logging requirements]
- KB Outputs: [REG_CHECK_REPORT]
- KB Boundaries: [без “историй”]

## [M] GATES
- PASS: требования логирования обеспечены
- FAIL: отсутствует возможность сформировать минимальные артефакты

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA]
- Handoff: report -> LOGGER / FAIL_HANDLER

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
