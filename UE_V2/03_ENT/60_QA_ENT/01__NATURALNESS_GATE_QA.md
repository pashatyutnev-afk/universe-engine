FILE: UE_V2/03_ENT/60_QA_ENT/01__NATURALNESS_GATE__QA__ENT.md
SCOPE: UE_V2 / 03_ENT / 60_QA_ENT
DOC_TYPE: QA_ENTITY
DOMAIN: QA_ENT
UID: UE.V2.ENT.QA.NATURALNESS_GATE.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: QA_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: NATURALNESS_GATE_QA_ROOT
- ENTITY_CLASS: QA
- UID: UE.V2.ENT.QA.NATURALNESS_GATE.001

## [M] PURPOSE
Root гейт “естественности” для любых текстовых артефактов.
Ловит роботизированный тон, мусор/повторы, пустые формулировки и сломанный формат.

## [M] SCOPE
- TARGET_DOMAIN: MULTI
- APPLIES_TO: [ANSWER_TEXT, DOC_TEXT, PROMPT_TEXT, README_TEXT]
- NON_GOALS: [факт-чекинг через интернет, художественный вкус]

## [M] INPUTS / OUTPUTS
- Inputs: [ARTIFACT_TEXT?]
- Outputs:
  - QA_DECISION: PASS|WARN|ASK|FAIL
  - QA_FINDINGS: [findings]
  - REQUIRED_FIXES: [fixes]
  - FAIL_CODE?: UE.FAIL.INPUT_ABSENT|UE.FAIL.GATE_FAIL

## [M] CHECKS
- C1: Вход присутствует (не пусто).
- C2: Нет спам-повторов (одни и те же фразы/абзацы).
- C3: Текст исполним: есть конкретика, нет “воды” вместо действий.
- C4: Формат не сломан (заголовки/списки/код-блоки согласованы).
- C5: Нет запретных паттернов по политике контекста (например, лишняя пунктуация в строгих промптах).

## [M] DECISION_MATRIX
- IF ARTIFACT_TEXT отсутствует -> ASK (UE.FAIL.INPUT_ABSENT)
- IF формат критично сломан -> FAIL (UE.FAIL.GATE_FAIL)
- IF много мусора/повторов -> WARN
- IF тон мешает исполнению -> WARN
- ELSE -> PASS

## [M] REQUIRED_FIXES (style)
- 1–7 пунктов, каждый “что исправить” + “как проверить”.
- Без лирики, только действия.

## [M] KB SCOPE
- KB Inputs: [artifact text]
- KB Outputs: [naturalness findings + fixes]
- KB Boundaries: [не добавлять новые требования вне входа]
- KB RAW refs: []

## [M] GATES
- PASS if: текст понятный, чистый, исполнимый
- FAIL if: формат ломает исполнение
