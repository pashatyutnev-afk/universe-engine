# 03__TOKEN_ARCHIVE

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: LOG / TOKENS
UID: UE.V2.LOG.TOKEN_ARCHIVE.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Архив токенов по шагам (STEP-RUN и FOCUS-LOOP), чтобы не держать всё в контексте.

---

## [M] INTENT
Сохранить "память процесса" компактно: каждый шаг оставляет токены, которые можно перечитать выборочно, не таща весь контент.

---

## [M] RULES
1) Каждый STEP обязан оставить минимум:
   - ROUTE_TOKEN
   - один из: BRIEF/PLAN/OPTIONS/REPORT/DELTA/PACK (по смыслу шага)
2) Для FOCUS-LOOP каждый pass обязан оставить:
   - FOCUS_TOKEN (на первый pass)
   - OPTIONS_TOKEN
   - DECISION_TOKEN
   - MINI_REPORT_TOKEN
   - DELTA_TOKEN (если применялось)
3) Архив append-only: добавляем записи, не переписываем прошлые.
4) В активном контексте держим только:
   - текущий STEP
   - BRIEF_TOKEN
   - последний DECISION/REPORT
   Остальное — ссылки на архивные TOKEN_ID.
5) Если токены не записаны — шаг считается незавершённым (REWORK).

---

## [M] ARCHIVE_ENTRY_TEMPLATE
TOKEN_ARCHIVE_ENTRY:
- RUN_ID:
- STEP_ID:
- FOCUS_ID: (optional)
- DOMAIN:
- ARTIFACT:
- TOKENS:
  - TOKEN_ID: TYPE: SUMMARY (1–3 строки)
  - ...
- LINKS (optional): ссылки на артефакты/файлы/пакеты
- STATUS: (DONE|REWORK|STOP|GAP)

---

## [M] ARCHIVE (APPEND ONLY)
| RUN_ID | STEP_ID | DOMAIN | ARTIFACT | TOKENS (IDs) | STATUS |
|---|---|---|---|---|---|

---

## [M] GATES
PASS если:
- для шага есть запись в архиве
REWORK если:
- шаг завершён без токенов
STOP если:
- систематически теряются токены (нарушение протокола)
