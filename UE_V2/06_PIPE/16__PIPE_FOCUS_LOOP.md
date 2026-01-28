# 16__PIPE_FOCUS_LOOP

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: PIPE / PROTOCOL
UID: UE.V2.PIPE.FOCUS_LOOP.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Встраивание FOCUS-LOOP в любой PIPE (итерации одного момента).

---

## [M] INTENT
Дать пайпам встроенную итеративность: один узкий фокус можно прокачивать несколькими партиями сущностей с вопросами/вариантами и мини-проверками.

---

## [M] WHEN_TO_INJECT
FOCUS-LOOP вставляется если:
- нужно улучшить один компонент (хук/микс/текст/обложка/канон-узел)
- есть 2+ конкурентных варианта
- QA/VAL требуют итераций
- пользователь сказал "ещё проход" или "варианты" или "уточни"

---

## [M] LOOP_CONTRACT
- FOCUS_TOKEN обязателен на первом pass
- Каждый pass обязан: OPTIONS_TOKEN -> DECISION_TOKEN -> MINI_REPORT_TOKEN -> ARCHIVE запись
- PASS завершается либо QA/VAL PASS, либо "стоп" пользователя

---

## [M] LIMITS
- MAX_PASSES_DEFAULT = 3
- ENTITIES_PER_PASS_MAX = 10
- OPTIONS_MAX = 5
- QUESTIONS_MAX = 3
(расширение только в режиме "шедевр")

---

## [M] GATES
PASS если:
- каждый pass фиксируется токенами и архивом
REWORK если:
- итерации идут без решений/архива
STOP если:
- фокус не определён
