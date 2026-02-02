FILE: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/02__COR__DOMAIN_DETECTOR__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 01_CORE_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: COR_ORC_ENT
UID: UE.V2.ENT.ORC.COR.DOMAIN_DETECTOR.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: COR_DOMAIN_DETECTOR
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.COR.DOMAIN_DETECTOR.001

## [M] PURPOSE
Определяет целевой домен/реалм по TASK_TOKEN.
Выдаёт DOMAIN_TARGET + список кандидатов PIPE_KEYS.

## [M] INPUTS / OUTPUTS
- Inputs: [TASK_TOKEN]
- Outputs: [DOMAIN_TARGET, PIPE_CANDIDATES, FAIL_CODE?]

## [M] CORE_RULES
- Если домен не определён — возвращать UE.FAIL.ROUTE_UNRESOLVED и что уточнить.
- Не расширять домен без явных признаков во входе.

## [M] INTERFACES (RAW only)
- Entry points (RAW):
- Dependencies (RAW):

## [M] KB SCOPE
- KB Inputs: [карта доменов UE_V2]
- KB Outputs: [DOMAIN_TARGET]
- KB Boundaries: [без “угадайки”]

## [M] GATES
- PASS: DOMAIN_TARGET выбран, кандидаты есть
- FAIL: ambiguity без входа

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, CTL]
- Handoff: DOMAIN_TARGET -> ROUTE_TOKEN_BUILDER

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
