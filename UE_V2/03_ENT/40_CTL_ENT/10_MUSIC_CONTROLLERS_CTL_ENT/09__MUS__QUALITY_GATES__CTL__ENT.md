FILE: UE_V2/03_ENT/40_CTL_ENT/10_MUSIC_CONTROLLERS_CTL_ENT/09__MUS__QUALITY_GATES__CTL__ENT.md
SCOPE: UE_V2 / 03_ENT / 40_CTL_ENT / 10_MUSIC_CONTROLLERS_CTL_ENT
DOC_TYPE: CTL_ENTITY
DOMAIN: MUS_CTL_ENT
UID: UE.V2.ENT.CTL.MUS.QUALITY_GATES.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: CTL_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_QUALITY_GATES_CTL
- ENTITY_CLASS: CTL
- UID: UE.V2.ENT.CTL.MUS.QUALITY_GATES.001

## [M] PURPOSE
Минимальные гейты качества. Без прохождения нельзя считать релиз готовым.

## [M] SCOPE
- TARGET_DOMAIN: MUS
- APPLIES_TO: [QA_REPORT?, TEST_DOC_TOKEN?, RELEASE_PACK_TOKEN?]
- NON_GOALS: [детальный микс-мастеринг]

## [M] INPUTS / OUTPUTS
- Inputs: [QA_REPORT?, TEST_DOC_TOKEN?]
- Outputs: [CTL_DECISION, CTL_FINDINGS, REQUIRED_FIXES, FAIL_CODE?]

## [M] RULESET
- R1: Должен быть явный статус проверки (PASS/FAIL) или эквивалент.
- R2: Должны быть перечислены блокеры и fixes при FAIL.
- R3: Нельзя выпускать при нерешённых блокерах PD/коллизий.
- R4: Должен быть выбран кандидат релиза (variant chosen) или причина отсутствия.

## [M] DECISION_MATRIX
- IF нет QA_REPORT и нет TEST_DOC_TOKEN -> ASK
- IF есть блокеры -> FAIL (UE.FAIL.GATE_FAIL)
- IF есть WARN без фиксов -> WARN
- ELSE -> PASS

## [M] VIOLATIONS
- V.QA.MISSING_EVIDENCE
- V.QA.BLOCKERS_PRESENT
- V.QA.NO_RELEASE_CANDIDATE

## [M] FAIL_CODES
- UE.FAIL.GATE_FAIL
- UE.FAIL.INPUT_ABSENT

## [M] KB SCOPE
- KB Inputs: [qa tokens, test tokens]
- KB Outputs: [gate decision]
- KB Boundaries: [не подменять проверки предположениями]
- KB RAW refs: []

## [M] GATES
- PASS if: нет блокеров и есть минимальная проверочная база
- FAIL if: блокеры присутствуют

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, QA_ENT, VAL_ENT]
- Handoff rules: FAIL -> stop; PASS -> release packaging
