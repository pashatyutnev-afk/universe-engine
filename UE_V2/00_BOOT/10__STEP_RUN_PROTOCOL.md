# 10__STEP_RUN_PROTOCOL

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: BOOT / PROTOCOL
UID: UE.V2.BOOT.STEP_RUN.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Универсальный режим пошагового исполнения задач через “го”, с обязательной фиксацией токенов/решений в LOG.

---

## [M] INTENT
Обеспечить выполнение сложных задач серией коротких прогонов:
один шаг → один мини-результат → фиксация токенов → "го" → следующий шаг.

---

## [M] CORE_RULES
1) Один прогон = один STEP.
2) В конце каждого STEP система обязана спросить: "го".
3) Без "го" следующий STEP не выполняется.
4) В каждом STEP активны максимум:
   - 1 Lead SPC
   - 1 ORC
   - 1 CTL
   - 1 VAL или 1 QA (по необходимости)
   - 0–5 узких вкладчиков
5) Каждый вкладчик обязан оставить CONTRIBUTION_TOKEN (STD/14).
6) Любой STEP обязан оставить STEP_TOKEN (STD/15).

---

## [M] REQUIRED LOG WRITES (MANDATORY)
После каждого STEP обязательно:
A) RUN_LOG: краткая запись (STEP_ID, DOMAIN, STATUS)
B) TOKEN_ARCHIVE: запись TOKEN_ID(ов) шага
C) Если были варианты (OPTIONS_TOKEN) → DECISION_LOG обязателен

Если эти записи не сделаны — STEP считается незавершённым (REWORK).

---

## [M] STEP_OUTPUT_FORMAT (TOKEN SET MIN)
Каждый STEP обязан выдать:
- STEP_ID
- STAGE (STD stage model)
- INPUT_SUMMARY (3–8 строк)
- CONTRIBUTIONS (список TOKEN_ID вкладов)
- OUTPUT_TOKEN (главный токен шага)
- NEXT_STEP (что дальше)
- USER_PROMPT ("го")

---

## [M] CONTEXT_BUDGET
В активном контексте держать только:
- текущий STEP
- BRIEF_TOKEN
- последний DECISION_TOKEN или REPORT_TOKEN
Остальное — ссылки на TOKEN_ARCHIVE.

---

## [M] FAILURE HANDLING
- REWORK: если нарушен формат шага, нет токенов, нет логов, слишком много сущностей
- GAP: если нужно создать отсутствующий пайп/индекс/сущность/шаблон
- STOP: только по 3 причинам из STOP_GAP

---

## [M] GATES
PASS если:
- STEP_OUTPUT_FORMAT соблюдён
- логирование выполнено (RUN_LOG + TOKEN_ARCHIVE + DECISION_LOG при необходимости)
REWORK если:
- нет токена шага или нет логов
STOP если:
- отсутствует задача
