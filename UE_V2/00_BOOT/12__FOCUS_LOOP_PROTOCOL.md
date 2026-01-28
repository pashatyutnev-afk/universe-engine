# 12__FOCUS_LOOP_PROTOCOL

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: BOOT / PROTOCOL
UID: UE.V2.BOOT.FOCUS_LOOP.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Повторная проработка одного узкого момента несколькими партиями сущностей.

---

## [M] INTENT
Дать системе законный способ делать несколько проходов по одному пункту (хук, микс, текст, канон-узел) без перегруза контекста.

---

## [M] LOOP_STAGES (L0–L5)
L0 SET_FOCUS:
- сформулировать один фокус (1–2 строки)
- выход: FOCUS_TOKEN

L1 PICK_TEAM:
- выбрать партию 3–7 сущностей по совместимости и KB scope
- выход: TEAM_TOKEN

L2 PRODUCE_OPTIONS:
- каждая сущность даёт CONTRIBUTION_TOKEN
- ORC собирает 2–5 вариантов
- выход: OPTIONS_TOKEN

L3 QUESTION_GATE:
- система задаёт 1–3 вопроса или предлагает выбрать A/B/C
- обязательно дефолт-выбор, если пользователь не хочет решать
- выход: DECISION_TOKEN

L4 APPLY + MINI_REVIEW:
- применить выбор
- CTL проверяет бюджет/полноту
- VAL/QA дают короткий мини-репорт
- выход: DELTA_TOKEN + MINI_REPORT_TOKEN

L5 ARCHIVE + NEXT:
- записать токены в TOKEN_ARCHIVE
- спросить “ещё проход” или “го дальше”
- выход: LOOP_NEXT_PROMPT

---

## [M] LOOP_LIMITS
- MAX_PASSES_DEFAULT: 3 (можно увеличивать для “шедевр-режима”)
- ENTITIES_PER_PASS_MAX: 10
- QUESTIONS_MAX: 3
- OPTIONS_MAX: 5

---

## [M] STOP_CONDITIONS
- пользователь сказал “стоп”
- QA/VAL дали PASS по фокусу
- достигнут MAX_PASSES_DEFAULT и нет прогресса (REWORK или смена фокуса)

---

## [M] GATES
PASS если:
- на каждом проходе есть OPTIONS_TOKEN и DECISION_TOKEN
- есть ARCHIVE запись

REWORK если:
- проход сделан без решения пользователя и без дефолта
- нет фиксации токенов

STOP если:
- отсутствует FOCUS (непонятно что улучшаем)
