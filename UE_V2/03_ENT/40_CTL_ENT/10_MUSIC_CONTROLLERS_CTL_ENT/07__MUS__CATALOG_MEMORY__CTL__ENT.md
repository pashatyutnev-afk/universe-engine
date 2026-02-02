FILE: UE_V2/03_ENT/40_CTL_ENT/10_MUSIC_CONTROLLERS_CTL_ENT/07__MUS__CATALOG_MEMORY__CTL__ENT.md
SCOPE: UE_V2 / 03_ENT / 40_CTL_ENT / 10_MUSIC_CONTROLLERS_CTL_ENT
DOC_TYPE: CTL_ENTITY
DOMAIN: MUS_CTL_ENT
UID: UE.V2.ENT.CTL.MUS.CATALOG_MEMORY.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: CTL_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_CATALOG_MEMORY_CTL
- ENTITY_CLASS: CTL
- UID: UE.V2.ENT.CTL.MUS.CATALOG_MEMORY.001

## [M] PURPOSE
Правила памяти каталога: как фиксировать отличия, не повторять названия/хуки/образы.

## [M] SCOPE
- TARGET_DOMAIN: MUS
- APPLIES_TO: [TRACK_PLAN, METADATA_PACK, HOOK_NOTES?]
- NON_GOALS: [внешние источники]

## [M] INPUTS / OUTPUTS
- Inputs: [PAST_RELEASES_HINT?, CATALOG_NOTES?]
- Outputs: [CTL_DECISION, CTL_FINDINGS, REQUIRED_FIXES]

## [M] RULESET
- R1: Новое название не должно совпадать с уже используемым в каталоге.
- R2: Хук-фраза должна быть уникальна относительно каталога.
- R3: Для релиза добавлять короткий “differentiation note”.

## [M] DECISION_MATRIX
- IF нет каталога и проект новый -> PASS
- IF нет notes и релиз готовится -> WARN
- IF найдено совпадение -> FAIL (UE.FAIL.GATE_FAIL)
- ELSE -> PASS

## [M] VIOLATIONS
- V.CAT.NO_NOTES
- V.CAT.NAME_COLLISION
- V.CAT.HOOK_REPEAT

## [M] FAIL_CODES
- UE.FAIL.GATE_FAIL

## [M] KB SCOPE
- KB Inputs: [внутренние заметки каталога]
- KB Outputs: [required fixes]
- KB Boundaries: [не придумывать каталог, если его нет]
- KB RAW refs: []

## [M] GATES
- PASS if: есть differentiation note или не требуется
- FAIL if: коллизия названия или повтора хука

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, VAL_ENT]
- Handoff rules: WARN -> add notes; FAIL -> rename/rework hook
