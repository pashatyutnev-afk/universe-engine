FILE: UE_V2/03_ENT/40_CTL_ENT/10_MUSIC_CONTROLLERS_CTL_ENT/15__MUS__VARIANT_POLICY__CTL__ENT.md
SCOPE: UE_V2 / 03_ENT / 40_CTL_ENT / 10_MUSIC_CONTROLLERS_CTL_ENT
DOC_TYPE: CTL_ENTITY
DOMAIN: MUS_CTL_ENT
UID: UE.V2.ENT.CTL.MUS.VARIANT_POLICY.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: CTL_ENT
NAV_RULE: No RAW in entity docs
---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_VARIANT_POLICY_CTL
- ENTITY_CLASS: CTL
- UID: UE.V2.ENT.CTL.MUS.VARIANT_POLICY.001

## [M] PURPOSE
Правила вариативности: как называть, чем отличать, как хранить заметки и не плодить дубликаты.

## [M] SCOPE
- TARGET_DOMAIN: MUS
- APPLIES_TO: [VARIANT_NOTES, RELEASE_PACK_TOKEN?]
- NON_GOALS: [merge стратегия]

## [M] INPUTS / OUTPUTS
- Inputs: [VARIANT_SET?, VARIANT_NOTES?]
- Outputs: [CTL_DECISION, CTL_FINDINGS, REQUIRED_FIXES]

## [M] RULESET
- R1: У каждого варианта должна быть метка отличия (hook, energy, arrangement).
- R2: Нельзя делать варианты полностью одинаковыми, различие должно быть измеримым.
- R3: Названия вариантов должны быть детерминированными.

## [M] DECISION_MATRIX
- IF variants отсутствуют -> PASS
- IF notes отсутствуют -> WARN
- IF variants дубли -> WARN
- ELSE -> PASS

## [M] VIOLATIONS
- V.VAR.NO_NOTES
- V.VAR.DUPLICATES

## [M] FAIL_CODES
- UE.FAIL.GATE_FAIL

## [M] KB SCOPE
- KB Inputs: [variant notes]
- KB Outputs: [variant fixes]
- KB Boundaries: [не выдумывать отличия]
- KB RAW refs: []

## [M] GATES
- PASS if: вариативность описана и контролируема
- FAIL if: релиз требует выбор, но вариантов нельзя различить

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT]
- Handoff rules: WARN -> add notes; PASS -> continue
