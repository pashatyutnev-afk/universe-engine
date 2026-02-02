FILE: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/04__COR__NAV_SENTINEL__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 01_CORE_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: COR_ORC_ENT
UID: UE.V2.ENT.ORC.COR.NAV_SENTINEL.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: COR_NAV_SENTINEL
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.COR.NAV_SENTINEL.001

## [M] PURPOSE
Гарантирует навигацию только через KEY->INDEX_MANIFEST->open.
Блокирует PATH-обходы и “RAW вне индекса”.

## [M] INPUTS / OUTPUTS
- Inputs: [ROUTE_TOKEN]
- Outputs: [NAV_CHECK_REPORT, FAIL_CODE?]

## [M] CORE_RULES
- Если обнаружен обход — UE.FAIL.RULE_VIOLATION.
- Разрешены только KEYS как ссылки внутри контрактов и сущностей.

## [M] INTERFACES (RAW only)
- Entry points (RAW):
- Dependencies (RAW):

## [M] KB SCOPE
- KB Inputs: [NAV_RULES]
- KB Outputs: [NAV_CHECK_REPORT]
- KB Boundaries: [без новых правил]

## [M] GATES
- PASS: nav чистый
- FAIL: обход найден

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA, CTL]
- Handoff: report -> PIPE_DISPATCHER / FAIL_HANDLER

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
