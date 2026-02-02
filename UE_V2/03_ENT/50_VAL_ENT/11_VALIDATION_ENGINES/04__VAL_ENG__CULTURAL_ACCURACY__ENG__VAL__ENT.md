FILE: UE_V2/03_ENT/50_VAL_ENT/11_VALIDATION_ENGINES/04__VAL_ENG__CULTURAL_ACCURACY__ENG__VAL__ENT.md
SCOPE: UE_V2 / 03_ENT / 50_VAL_ENT / 11_VALIDATION_ENGINES
DOC_TYPE: VAL_ENTITY
DOMAIN: VAL_ENG_VAL_ENT
UID: UE.V2.ENT.VAL_ENG.CULTURAL_ACCURACY.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: VAL_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: VAL_ENG_CULTURAL_ACCURACY
- ENTITY_CLASS: VAL_ENG
- UID: UE.V2.ENT.VAL_ENG.CULTURAL_ACCURACY.001

## [M] PURPOSE
Проверяет культурную корректность на уровне фактов и контекстной уместности (без “диагнозов” и без стереотипов).

## [M] SCOPE
- TARGET_DOMAIN: MULTI
- APPLIES_TO: [DOC_TEXT, NARRATIVE, WEB_COPY]
- NON_GOALS: [политические оценки, sensitive профилирование]

## [M] INPUTS / OUTPUTS
- Inputs: [ARTIFACT_TEXT?, LOCALE_HINT?]
- Outputs: [VAL_DECISION, VAL_FINDINGS, REQUIRED_FIXES]

## [M] CHECKS
- C1: Локаль/контекст соответствует упоминаниям (например, города/термины).
- C2: Нет явных ошибок названий/категорий.
- C3: Нет неуместных утверждений как фактов без evidence.

## [M] DECISION_MATRIX
- IF text отсутствует -> ASK
- IF обнаружены явные ошибки -> WARN
- IF ошибки критичны и вводят в заблуждение -> FAIL
- ELSE -> PASS

## [M] VIOLATIONS
- V.CULT.NO_INPUT
- V.CULT.MISLABEL
- V.CULT.UNSUPPORTED_FACT

## [M] FAIL_CODES
- UE.FAIL.INPUT_ABSENT
- UE.FAIL.GATE_FAIL

## [M] KB SCOPE
- KB Inputs: [artifact text + locale hint]
- KB Outputs: [cultural findings]
- KB Boundaries: [не использовать внешние источники]
- KB RAW refs: []

## [M] GATES
- PASS if: нет существенных несоответствий
- FAIL if: критические несоответствия подтверждены

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, QA_ENT]
- Handoff rules: WARN -> adjust wording; FAIL -> rewrite facts
