FILE: UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/11__MUS__CHAIN_COMPLETENESS__VAL__ENT.md
SCOPE: UE_V2 / 03_ENT / 50_VAL_ENT / 10_MUSIC_VAL
DOC_TYPE: VAL_ENTITY
DOMAIN: MUS_VAL_ENT
UID: UE.V2.ENT.VAL.MUS.CHAIN_COMPLETENESS.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: VAL_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_CHAIN_COMPLETENESS_VAL
- ENTITY_CLASS: VAL
- UID: UE.V2.ENT.VAL.MUS.CHAIN_COMPLETENESS.001

## [M] PURPOSE
Проверяет, что цепочка артефактов не дырявая: есть brief, prompt pack, выбранный вариант, QA/VAL статусы (для релиза).

## [M] SCOPE
- TARGET_DOMAIN: MUS
- APPLIES_TO: [MUS_BRIEF, PROMPT_PACK, VARIANT_NOTES?, QA_REPORT?, RELEASE_PACK_TOKEN?]
- NON_GOALS: [оценка содержания]

## [M] INPUTS / OUTPUTS
- Inputs: [MUS_BRIEF?, PROMPT_PACK?, SELECTED_VARIANT_TOKEN?, QA_REPORT?]
- Outputs: [VAL_DECISION, REQUIRED_FIXES, VIOLATIONS]

## [M] CHECKS
- C1: MUS_BRIEF присутствует (Evidence: token)
- C2: PROMPT_PACK присутствует (Evidence: token)
- C3: Для релиза выбран вариант (Evidence: selected variant token)
- C4: Есть QA статус (Evidence: qa report)

## [M] DECISION_MATRIX
- IF отсутствует brief или prompt -> FAIL
- IF релиз заявлен и нет selected variant -> ASK
- IF релиз заявлен и нет QA -> ASK
- ELSE -> PASS

## [M] VIOLATIONS
- V.CHAIN.MISSING_BRIEF
- V.CHAIN.MISSING_PROMPT
- V.CHAIN.MISSING_SELECTED_VARIANT
- V.CHAIN.MISSING_QA

## [M] FAIL_CODES
- UE.FAIL.GATE_FAIL
- UE.FAIL.INPUT_ABSENT

## [M] KB SCOPE
- KB Inputs: [artifact tokens]
- KB Outputs: [missing list]
- KB Boundaries: [не придумывать отсутствующие токены]
- KB RAW refs: []

## [M] GATES
- PASS if: цепочка достаточна под режим
- FAIL if: базовые токены отсутствуют

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, CTL_ENT, QA_ENT]
- Handoff rules: FAIL/ASK -> request missing tokens
