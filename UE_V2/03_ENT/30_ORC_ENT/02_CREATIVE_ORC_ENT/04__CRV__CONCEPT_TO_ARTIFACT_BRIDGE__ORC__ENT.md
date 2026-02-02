FILE: UE_V2/03_ENT/30_ORC_ENT/02_CREATIVE_ORC_ENT/04__CRV__CONCEPT_TO_ARTIFACT_BRIDGE__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 02_CREATIVE_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: CRV_ORC_ENT
UID: UE.V2.ENT.ORC.CRV.CONCEPT_TO_ARTIFACT_BRIDGE.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: CRV_CONCEPT_TO_ARTIFACT_BRIDGE
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.CRV.CONCEPT_TO_ARTIFACT_BRIDGE.001

## [M] PURPOSE
Переводит концепт в ARTIFACT_SPEC под целевой домен (music/video/web/docs/brand).
Собирает “упаковку” для генерации/публикации: структура, ограничения, чеклист.

## [M] INPUTS / OUTPUTS
- Inputs: [CREATIVE_BRIEF, IDENTITY_TOKEN, STYLE_TOKEN, TREND_TOKEN]
- Outputs: [ARTIFACT_SPEC, OUTPUT_PACK_TOKEN, FAIL_CODE?]

## [M] ARTIFACT_SPEC (canonical sections)
- TARGET_DOMAIN
- GOAL
- CONSTRAINTS (hard)
- STYLE_PRINCIPLES
- VARIATIONS (slots)
- DELIVERABLE_FORMAT
- QA_CHECKS (what must be verified)
- NEXT_ACTION (what to do after generation)

## [M] INTERFACES (RAW only)
- Entry points (RAW):
- Dependencies (RAW):

## [M] KB SCOPE
- KB Inputs: [tokens from previous steps]
- KB Outputs: [artifact spec]
- KB Boundaries: [не добавлять факты, которых не было во входе]

## [M] GATES
- PASS: spec полный и непротиворечивый
- FAIL: неясен target domain или конфликт ограничений

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA, CTL]
- Handoff: ARTIFACT_SPEC -> domain pipe (MUS/VID/WEB/DOC)

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
