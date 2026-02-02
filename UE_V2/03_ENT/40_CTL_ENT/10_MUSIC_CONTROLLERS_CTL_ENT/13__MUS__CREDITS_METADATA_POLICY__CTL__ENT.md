FILE: UE_V2/03_ENT/40_CTL_ENT/10_MUSIC_CONTROLLERS_CTL_ENT/13__MUS__CREDITS_METADATA_POLICY__CTL__ENT.md
SCOPE: UE_V2 / 03_ENT / 40_CTL_ENT / 10_MUSIC_CONTROLLERS_CTL_ENT
DOC_TYPE: CTL_ENTITY
DOMAIN: MUS_CTL_ENT
UID: UE.V2.ENT.CTL.MUS.CREDITS_METADATA_POLICY.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: CTL_ENT
NAV_RULE: No RAW in entity docs
---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_CREDITS_METADATA_POLICY_CTL
- ENTITY_CLASS: CTL
- UID: UE.V2.ENT.CTL.MUS.CREDITS_METADATA_POLICY.001

## [M] PURPOSE
Политика метаданных и кредитов: консистентность артиста, названия, версии, теги, язык.

## [M] SCOPE
- TARGET_DOMAIN: MUS
- APPLIES_TO: [METADATA_PACK, RELEASE_PACK_TOKEN]
- NON_GOALS: [права/PD как юридический вывод]

## [M] INPUTS / OUTPUTS
- Inputs: [METADATA_PACK?]
- Outputs: [CTL_DECISION, CTL_FINDINGS, REQUIRED_FIXES]

## [M] RULESET
- R1: Artist name должен быть стабильным.
- R2: Title/Version должны быть детерминированными и без дублей.
- R3: Language и explicit flags должны быть согласованы с текстом.
- R4: Credits не должны содержать утверждений без источника.

## [M] DECISION_MATRIX
- IF METADATA_PACK отсутствует -> ASK
- IF найден конфликт именования -> FAIL
- IF поля неполные -> WARN
- ELSE -> PASS

## [M] VIOLATIONS
- V.META.MISSING
- V.META.NAME_CONFLICT
- V.META.UNSUPPORTED_CLAIM

## [M] FAIL_CODES
- UE.FAIL.GATE_FAIL
- UE.FAIL.INPUT_ABSENT

## [M] KB SCOPE
- KB Inputs: [metadata pack]
- KB Outputs: [metadata fixes]
- KB Boundaries: [не выдумывать кредиты]
- KB RAW refs: []

## [M] GATES
- PASS if: метаданные полные и консистентны
- FAIL if: конфликты имени/версии

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT]
- Handoff rules: FAIL -> fix metadata; PASS -> continue
