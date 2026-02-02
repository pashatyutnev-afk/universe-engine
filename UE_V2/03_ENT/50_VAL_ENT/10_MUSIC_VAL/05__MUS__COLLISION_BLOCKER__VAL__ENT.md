FILE: UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/05__MUS__COLLISION_BLOCKER__VAL__ENT.md
SCOPE: UE_V2 / 03_ENT / 50_VAL_ENT / 10_MUSIC_VAL
DOC_TYPE: VAL_ENTITY
DOMAIN: MUS_VAL_ENT
UID: UE.V2.ENT.VAL.MUS.COLLISION_BLOCKER.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: VAL_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_COLLISION_BLOCKER_VAL
- ENTITY_CLASS: VAL
- UID: UE.V2.ENT.VAL.MUS.COLLISION_BLOCKER.001

## [M] PURPOSE
Блокирует коллизии с внутренним каталогом: имя/хук/концепт при наличии evidence.

## [M] SCOPE
- TARGET_DOMAIN: MUS
- APPLIES_TO: [CATALOG_NOTES?, METADATA_PACK?, HOOK_NOTES?]
- NON_GOALS: [внешние проверки по интернету]

## [M] INPUTS / OUTPUTS
- Inputs: [CATALOG_NOTES?, METADATA_PACK?, HOOK_NOTES?]
- Outputs: [VAL_DECISION, VAL_FINDINGS, REQUIRED_FIXES, VIOLATIONS]

## [M] CHECKS
- C1: Есть evidence сравнения с каталогом? (Evidence: catalog notes)
- C2: Найдена коллизия имени? (Evidence: metadata + catalog)
- C3: Найден повтор хук-фразы/мотива? (Evidence: hook notes)

## [M] DECISION_MATRIX
- IF релиз готовится и нет catalog notes -> ASK
- IF коллизия подтверждена -> FAIL (UE.FAIL.GATE_FAIL)
- IF есть риск, но не подтверждено -> WARN
- ELSE -> PASS

## [M] VIOLATIONS
- V.COL.NO_EVIDENCE
- V.COL.NAME_COLLISION
- V.COL.HOOK_REPEAT

## [M] FAIL_CODES
- UE.FAIL.GATE_FAIL
- UE.FAIL.INPUT_ABSENT

## [M] KB SCOPE
- KB Inputs: [internal catalog notes]
- KB Outputs: [collision findings]
- KB Boundaries: [не утверждать “коллизии нет” без evidence]
- KB RAW refs: []

## [M] GATES
- PASS if: нет подтверждённых коллизий
- FAIL if: коллизия подтверждена

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, CTL_ENT]
- Handoff rules: ASK -> provide notes; FAIL -> rename/rework hook
