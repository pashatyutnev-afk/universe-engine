FILE: UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/12__MUS__COVERAGE_PASS__VAL__ENT.md
SCOPE: UE_V2 / 03_ENT / 50_VAL_ENT / 10_MUSIC_VAL
DOC_TYPE: VAL_ENTITY
DOMAIN: MUS_VAL_ENT
UID: UE.V2.ENT.VAL.MUS.COVERAGE_PASS.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: VAL_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_COVERAGE_PASS_VAL
- ENTITY_CLASS: VAL
- UID: UE.V2.ENT.VAL.MUS.COVERAGE_PASS.001

## [M] PURPOSE
Проверяет, что заявленный scope выполнен: есть все части (куплет/припев/бридж или другой заявленный формат).

## [M] SCOPE
- TARGET_DOMAIN: MUS
- APPLIES_TO: [MUS_BRIEF, LYRICS_FINAL?, STRUCTURE_NOTES?]
- NON_GOALS: [субъективная оценка]

## [M] INPUTS / OUTPUTS
- Inputs: [MUS_BRIEF, LYRICS_FINAL?, STRUCTURE_NOTES?]
- Outputs: [VAL_DECISION, REQUIRED_FIXES, VIOLATIONS]

## [M] CHECKS
- C1: brief описывает структуру (Evidence: brief)
- C2: выход содержит все части (Evidence: lyrics/structure notes)

## [M] DECISION_MATRIX
- IF нет brief -> ASK
- IF нет текста/структуры -> ASK
- IF часть отсутствует -> WARN
- ELSE -> PASS

## [M] VIOLATIONS
- V.COV.NO_EVIDENCE
- V.COV.MISSING_SECTION

## [M] FAIL_CODES
- UE.FAIL.INPUT_ABSENT

## [M] KB SCOPE
- KB Inputs: [brief + draft]
- KB Outputs: [coverage report]
- KB Boundaries: [не дописывать контент без запроса]
- KB RAW refs: []

## [M] GATES
- PASS if: coverage соответствует brief
- FAIL if: coverage критично неполный и нельзя продолжать

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT]
- Handoff rules: WARN -> add missing sections; ASK -> provide draft
