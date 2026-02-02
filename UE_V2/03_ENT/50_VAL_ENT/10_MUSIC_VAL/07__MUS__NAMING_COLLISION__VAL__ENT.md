FILE: UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/07__MUS__NAMING_COLLISION__VAL__ENT.md
SCOPE: UE_V2 / 03_ENT / 50_VAL_ENT / 10_MUSIC_VAL
DOC_TYPE: VAL_ENTITY
DOMAIN: MUS_VAL_ENT
UID: UE.V2.ENT.VAL.MUS.NAMING_COLLISION.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: VAL_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_NAMING_COLLISION_VAL
- ENTITY_CLASS: VAL
- UID: UE.V2.ENT.VAL.MUS.NAMING_COLLISION.001

## [M] PURPOSE
Проверяет, что naming (title/version/artist) не конфликтует внутри проекта и с внутренним каталогом, если есть evidence.

## [M] SCOPE
- TARGET_DOMAIN: MUS
- APPLIES_TO: [METADATA_PACK?, CATALOG_NOTES?]
- NON_GOALS: [поиск по интернету]

## [M] INPUTS / OUTPUTS
- Inputs: [METADATA_PACK?, CATALOG_NOTES?]
- Outputs: [VAL_DECISION, REQUIRED_FIXES, VIOLATIONS]

## [M] CHECKS
- C1: Title/Artist/Version присутствуют (Evidence: metadata pack)
- C2: Нет дублирования названий (Evidence: catalog notes / internal list)

## [M] DECISION_MATRIX
- IF metadata отсутствует -> ASK
- IF найден дубль -> FAIL
- IF нет evidence каталога -> WARN
- ELSE -> PASS

## [M] VIOLATIONS
- V.NAME.MISSING
- V.NAME.COLLISION
- V.NAME.NO_CATALOG_EVIDENCE

## [M] FAIL_CODES
- UE.FAIL.GATE_FAIL
- UE.FAIL.INPUT_ABSENT

## [M] KB SCOPE
- KB Inputs: [metadata, internal notes]
- KB Outputs: [naming findings]
- KB Boundaries: [не утверждать уникальность без evidence]
- KB RAW refs: []

## [M] GATES
- PASS if: naming валиден и без дублей
- FAIL if: дубль подтверждён

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, CTL_ENT]
- Handoff rules: FAIL -> rename; ASK -> provide metadata
