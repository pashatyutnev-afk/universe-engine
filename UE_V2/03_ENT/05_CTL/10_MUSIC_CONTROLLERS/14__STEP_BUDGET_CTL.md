# 14__STEP_BUDGET_CTL

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: CTL
UID: UE.V2.CTL.MUSIC.STEP_BUDGET.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Лимиты на шаг/варианты/вопросы/проходы для MUSIC задач в режиме STEP-RUN + FOCUS-LOOP.

---

## [M] INTENT
Не дать музыке “взорвать” контекст: всё делается партиями, каждый шаг короткий, все решения фиксируются токенами, “лишние” сущности не допускаются.

---

## [M] INPUTS
- MODE: FAST | RELEASE_READY | MASTERPIECE
- ARTIFACT_TYPE: TRACK | HOOK | LYRICS | MIX | MASTER | RELEASE_PACK
- PLAN_TOKEN (если есть)

---

## [M] OUTPUTS
- REPORT_TOKEN (CTL): PASS/REWORK + рекомендации по сокращению/переразбиению

---

## [M] BUDGETS (DEFAULT)
### MODE=FAST
- ENTITIES_ACTIVE_PER_STEP_MAX: 7
- CONTRIBUTORS_PER_STEP_MAX: 3
- OPTIONS_MAX: 3
- QUESTIONS_MAX: 2
- FOCUS_LOOP_MAX_PASSES: 2
- STEPS_MAX_TARGET: 10

### MODE=RELEASE_READY
- ENTITIES_ACTIVE_PER_STEP_MAX: 9
- CONTRIBUTORS_PER_STEP_MAX: 5
- OPTIONS_MAX: 5
- QUESTIONS_MAX: 3
- FOCUS_LOOP_MAX_PASSES: 3
- STEPS_MAX_TARGET: 16

### MODE=MASTERPIECE
- ENTITIES_ACTIVE_PER_STEP_MAX: 10
- CONTRIBUTORS_PER_STEP_MAX: 6
- OPTIONS_MAX: 5
- QUESTIONS_MAX: 3
- FOCUS_LOOP_MAX_PASSES: 5
- STEPS_MAX_TARGET: 25

---

## [M] HARD RULES
1) Один STEP = один основной OUTPUT_TOKEN.
2) Если нужно больше участия — разбить на несколько STEP или FOCUS-LOOP passes.
3) Любая сущность без CONTRIBUTION_TOKEN в шаге = шум → исключить (REWORK).
4) Вопросы только через QUESTIONS_GATE (макс 3, с дефолтом).
5) “Сделай всё сразу” запрещено: обязательно разбиение.

---

## [M] TRIGGERS (WHEN TO FORCE FOCUS-LOOP)
FOCUS-LOOP обязателен, если:
- HOOK не проходит 06__HOOK_PANEL_QA или 03__RECOGNITION_10S_QA
- MIX не проходит 05__MIX_TRANSLATION_QA
- UNIQUENESS не проходит 07__CATALOG_DIFFERENTIATION_QA
- REGRESSION_GUARD даёт FAIL/REWORK

---

## [M] GATES
PASS если:
- лимиты соблюдены
REWORK если:
- превышены лимиты без причины или шаг “комком”
STOP если:
- систематическое нарушение бюджета (игнор протоколов)
