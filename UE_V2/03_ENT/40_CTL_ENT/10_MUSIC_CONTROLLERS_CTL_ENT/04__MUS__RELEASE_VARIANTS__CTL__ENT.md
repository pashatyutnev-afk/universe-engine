FILE: UE_V2/03_ENT/40_CTL_ENT/10_MUSIC_CONTROLLERS_CTL_ENT/04__MUS__RELEASE_VARIANTS__CTL__ENT.md
SCOPE: UE_V2 / 03_ENT / 40_CTL_ENT / 10_MUSIC_CONTROLLERS_CTL_ENT
DOC_TYPE: CTL_ENTITY
DOMAIN: MUS_CTL_ENT
UID: UE.V2.ENT.CTL.MUS.RELEASE_VARIANTS.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: CTL_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_RELEASE_VARIANTS_CTL
- ENTITY_CLASS: CTL
- UID: UE.V2.ENT.CTL.MUS.RELEASE_VARIANTS.001

## [M] PURPOSE
Определяет, какие варианты нужны для выбора финала (минимальный набор) и как их сравнивать.

## [M] SCOPE
- TARGET_DOMAIN: MUS
- APPLIES_TO: [TRACK_PLAN, VARIANT_NOTES, RELEASE_PACK_TOKEN?]
- NON_GOALS: [метаданные, права]

## [M] INPUTS / OUTPUTS
- Inputs: [MUS_BRIEF, TRACK_PLAN?]
- Outputs: [CTL_DECISION, CTL_FINDINGS, REQUIRED_FIXES]

## [M] RULESET
- R1: Если цель release-ready, должен быть минимум 2 варианта на выбор (если не запрещено brief).
- R2: Варианты должны отличаться по одному измерению (hook, energy, arrangement), а не случайно.
- R3: Каждый вариант должен иметь короткую заметку отличий.

## [M] DECISION_MATRIX
- IF brief=single take only -> PASS
- IF нет TRACK_PLAN -> ASK
- IF вариантов нет/один -> WARN
- ELSE -> PASS

## [M] VIOLATIONS
- V.VAR.MISSING
- V.VAR.NO_DIFF_NOTES

## [M] FAIL_CODES
- UE.FAIL.INPUT_ABSENT

## [M] KB SCOPE
- KB Inputs: [brief/plan/variant notes]
- KB Outputs: [variant requirements]
- KB Boundaries: [не требовать варианты, если brief запретил]
- KB RAW refs: []

## [M] GATES
- PASS if: policy соблюдена или не применима
- FAIL if: требуется релиз, а вариантов нет и нельзя продолжать

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, QA_ENT]
- Handoff rules: WARN -> variant loop; PASS -> continue
