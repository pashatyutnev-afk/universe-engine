FILE: UE_V2/03_ENT/50_VAL_ENT/11_VALIDATION_ENGINES/02__VAL_ENG__FACT_CONSISTENCY__ENG__VAL__ENT.md
SCOPE: UE_V2 / 03_ENT / 50_VAL_ENT / 11_VALIDATION_ENGINES
DOC_TYPE: VAL_ENTITY
DOMAIN: VAL_ENG_VAL_ENT
UID: UE.V2.ENT.VAL_ENG.FACT_CONSISTENCY.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: VAL_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: VAL_ENG_FACT_CONSISTENCY
- ENTITY_CLASS: VAL_ENG
- UID: UE.V2.ENT.VAL_ENG.FACT_CONSISTENCY.001

## [M] PURPOSE
Проверяет внутреннюю логическую и фактическую согласованность текста: противоречия, несовместимые числа, взаимоисключающие утверждения.

## [M] SCOPE
- TARGET_DOMAIN: MULTI
- APPLIES_TO: [DOC_TEXT, SPEC_TEXT, CLAIM_LIST, NARRATIVE_SUMMARY]
- NON_GOALS: [веб-поиск фактов, внешняя верификация]

## [M] INPUTS / OUTPUTS
- Inputs: [ARTIFACT_TEXT?]
- Outputs: [VAL_DECISION, VAL_FINDINGS, REQUIRED_FIXES, VIOLATIONS]

## [M] CHECKS
- C1: Нет противоречий внутри одного документа (A и not-A).
- C2: Числа и диапазоны не конфликтуют (например, duration 8s и 30s одновременно).
- C3: Термины используются стабильно (одно понятие не меняет смысл).
- C4: Таймлайн/порядок шагов не конфликтует сам с собой.

## [M] DECISION_MATRIX
- IF ARTIFACT_TEXT отсутствует -> ASK
- IF найдены явные противоречия -> FAIL (UE.FAIL.GATE_FAIL)
- IF найдены сомнительные места -> WARN
- ELSE -> PASS

## [M] VIOLATIONS
- V.FACT.NO_INPUT
- V.FACT.CONTRADICTION
- V.FACT.NUMERIC_MISMATCH
- V.FACT.TERM_DRIFT

## [M] FAIL_CODES
- UE.FAIL.INPUT_ABSENT
- UE.FAIL.GATE_FAIL

## [M] KB SCOPE
- KB Inputs: [artifact text]
- KB Outputs: [contradiction list + fixes]
- KB Boundaries: [не использовать внешние источники]
- KB RAW refs: []

## [M] GA
