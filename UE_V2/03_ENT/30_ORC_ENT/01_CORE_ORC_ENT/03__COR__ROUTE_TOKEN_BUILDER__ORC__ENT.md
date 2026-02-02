FILE: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/03__COR__ROUTE_TOKEN_BUILDER__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 01_CORE_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: COR_ORC_ENT
UID: UE.V2.ENT.ORC.COR.ROUTE_TOKEN_BUILDER.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: COR_ROUTE_TOKEN_BUILDER
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.COR.ROUTE_TOKEN_BUILDER.001

## [M] PURPOSE
Строит ROUTE_TOKEN: TARGET_REALM_KEYS, WORK_SET_KEYS, LOAD_ORDER, PIPE_CANDIDATES, CONSTRAINTS_LOCK.
Это главный “маршрутный билет” прогона.

## [M] INPUTS / OUTPUTS
- Inputs: [TASK_TOKEN, DOMAIN_TARGET, PIPE_CANDIDATES]
- Outputs: [ROUTE_TOKEN, FAIL_CODE?]

## [M] CORE_RULES
- WORK_SET_KEYS минимальный и достаточный.
- CONSTRAINTS_LOCK фиксируется и не меняется без нового входа.
- Любые внешние ссылки не превращать в RAW-обход.

## [M] INTERFACES (RAW only)
- Entry points (RAW):
- Dependencies (RAW):

## [M] KB SCOPE
- KB Inputs: [правила key->resolve]
- KB Outputs: [ROUTE_TOKEN]
- KB Boundaries: [без расширения workset]

## [M] GATES
- PASS: есть target + workset + порядок
- FAIL: missing keys/candidates

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, CTL, QA]
- Handoff: ROUTE_TOKEN -> SENTINELS + PIPE_SELECTOR

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
