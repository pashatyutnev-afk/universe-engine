FILE: UE_V2/03_ENT/50_VAL_ENT/11_VALIDATION_ENGINES/05__VAL_ENG__HISTORICAL_ACCURACY__ENG__VAL__ENT.md
SCOPE: UE_V2 / 03_ENT / 50_VAL_ENT / 11_VALIDATION_ENGINES
DOC_TYPE: VAL_ENTITY
DOMAIN: VAL_ENG_VAL_ENT
UID: UE.V2.ENT.VAL_ENG.HISTORICAL_ACCURACY.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: VAL_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: VAL_ENG_HISTORICAL_ACCURACY
- ENTITY_CLASS: VAL_ENG
- UID: UE.V2.ENT.VAL_ENG.HISTORICAL_ACCURACY.001

## [M] PURPOSE
Проверяет историческую точность и правдоподобие таймлайна (внутренняя согласованность + базовые признаки ошибок).

## [M] SCOPE
- TARGET_DOMAIN: MULTI
- APPLIES_TO: [HISTORICAL_TEXT, TIMELINE, WORLD_NOTES]
- NON_GOALS: [веб-верификация]

## [M] INPUTS / OUTPUTS
- Inputs: [ARTIFACT_TEXT?, TIMELINE_NOTES?]
- Outputs: [VAL_DECISION, VAL_FINDINGS, REQUIRED_FIXES]

## [M] CHECKS
- C1: Внутренняя согласованность дат/эпох.
- C2: Нет взаимоисключающих исторических утверждений в одном документе.
- C3: Термины эпох не конфликтуют с контекстом.

## [M] DECISION_MATRIX
- IF inputs отсутствуют -> ASK
- IF противоречия в таймлайне -> FAIL
- IF сомнительные места -> WARN
- ELSE -> PASS

## [M] VIOLATIONS
- V.HIST.NO_INPUT
- V.HIST.CONTRADICTION
- V.HIST.TIMELINE_DRIFT

## [M] FAIL_CODES
- UE.FAIL.INPUT_ABSENT
- UE.FAIL.GATE_FAIL

## [M] KB SCOPE
- KB Inputs: [artifact text]
- KB Outputs: [timeline findings]
- KB Boundaries: [без внешних источников]
- KB RAW refs: []

## [M] GATES
- PASS if: таймлайн согласован
- FAIL if: противоречия подтверждены

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, QA_ENT]
- Handoff rules: FAIL -> fix timeline; WARN -> clarify dates
