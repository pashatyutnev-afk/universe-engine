FILE: UE_V2/03_ENT/50_VAL_ENT/11_VALIDATION_ENGINES/03__VAL_ENG__LANGUAGE_LINGUISTICS__ENG__VAL__ENT.md
SCOPE: UE_V2 / 03_ENT / 50_VAL_ENT / 11_VALIDATION_ENGINES
DOC_TYPE: VAL_ENTITY
DOMAIN: VAL_ENG_VAL_ENT
UID: UE.V2.ENT.VAL_ENG.LANGUAGE_LINGUISTICS.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: VAL_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: VAL_ENG_LANGUAGE_LINGUISTICS
- ENTITY_CLASS: VAL_ENG
- UID: UE.V2.ENT.VAL_ENG.LANGUAGE_LINGUISTICS.001

## [M] PURPOSE
Лингвистические проверки: ясность, грамматика, двусмысленность, несогласованность регистра, паразитные слова.

## [M] SCOPE
- TARGET_DOMAIN: MULTI
- APPLIES_TO: [DOC_TEXT, PROMPTS, LYRICS]
- NON_GOALS: [стилизация как “вкус”, переписывание смысла]

## [M] INPUTS / OUTPUTS
- Inputs: [ARTIFACT_TEXT?]
- Outputs: [VAL_DECISION, VAL_FINDINGS, REQUIRED_FIXES]

## [M] CHECKS
- C1: Ясность: нет двусмысленных инструкций.
- C2: Минимум грамматических ошибок, мешающих пониманию.
- C3: Термины не прыгают по написанию (consistency).
- C4: Нет запрещённых паттернов (например, “!” в SUNO контексте).

## [M] DECISION_MATRIX
- IF ARTIFACT_TEXT отсутствует -> ASK
- IF двусмысленность ломает выполнение -> FAIL
- IF ошибки умеренные -> WARN
- ELSE -> PASS

## [M] VIOLATIONS
- V.LANG.NO_INPUT
- V.LANG.AMBIGUOUS
- V.LANG.ERRORS
- V.LANG.BANNED_PUNCT

## [M] FAIL_CODES
- UE.FAIL.INPUT_ABSENT
- UE.FAIL.GATE_FAIL
- UE.FAIL.RULE_VIOLATION

## [M] KB SCOPE
- KB Inputs: [artifact text]
- KB Outputs: [language findings + fixes]
- KB Boundaries: [не менять смысл без запроса]
- KB RAW refs: []

## [M] GATES
- PASS if: текст исполним и ясен
- FAIL if: двусмысленность или запретные паттерны критичны

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, CTL_ENT]
- Handoff rules: WARN -> edit wording; FAIL -> clarify intent
