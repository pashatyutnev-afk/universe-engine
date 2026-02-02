FILE: UE_V2/03_ENT/40_CTL_ENT/10_MUSIC_CONTROLLERS_CTL_ENT/08__MUS__AUDIENCE_SEGMENTS__CTL__ENT.md
SCOPE: UE_V2 / 03_ENT / 40_CTL_ENT / 10_MUSIC_CONTROLLERS_CTL_ENT
DOC_TYPE: CTL_ENTITY
DOMAIN: MUS_CTL_ENT
UID: UE.V2.ENT.CTL.MUS.AUDIENCE_SEGMENTS.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: CTL_ENT
NAV_RULE: No RAW in entity docs
---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_AUDIENCE_SEGMENTS_CTL
- ENTITY_CLASS: CTL
- UID: UE.V2.ENT.CTL.MUS.AUDIENCE_SEGMENTS.001

## [M] PURPOSE
Сегментация аудитории как ограничения: плотность текста, энергия, структура хука, длина интро.

## [M] SCOPE
- TARGET_DOMAIN: MUS
- APPLIES_TO: [MUS_BRIEF, STYLE_ROUTE_TOKEN, TRACK_PLAN]
- NON_GOALS: [маркетинговые обещания]

## [M] INPUTS / OUTPUTS
- Inputs: [MUS_BRIEF]
- Outputs: [CTL_DECISION, CTL_FINDINGS, REQUIRED_FIXES]

## [M] RULESET
- R1: Если audience=спорт -> energy high, hook early, lyrics density low-medium.
- R2: Если audience=релакс -> energy low-medium, intro допускается длиннее.
- R3: Если audience=путешествия -> cinematic arc, ясный мотив, умеренная плотность.
- R4: Если audience не задана -> не применять.

## [M] DECISION_MATRIX
- IF audience не задана -> PASS
- IF plan противоречит сегменту -> WARN
- ELSE -> PASS

## [M] VIOLATIONS
- V.AUD.MISMATCH

## [M] FAIL_CODES
- UE.FAIL.GATE_FAIL

## [M] KB SCOPE
- KB Inputs: [brief]
- KB Outputs: [segment guidance]
- KB Boundaries: [не придумывать сегмент]
- KB RAW refs: []

## [M] GATES
- PASS if: нет конфликтов с сегментом
- FAIL if: сегмент обязателен и конфликт неустраним

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT]
- Handoff rules: WARN -> adjust plan; PASS -> continue
