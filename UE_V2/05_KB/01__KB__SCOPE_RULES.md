# FILE: UE_V2/05_KB/01__KB_RULES.md
SCOPE: UE_V2
LAYER: 05_KB
DOC_TYPE: RULES
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.KB.RULES.001
OWNER: SYSTEM
TITLE: KB RULES (MIN)

## MARKERS
- [M] LAW
- [M] OBJECT_TYPES
- [M] FORMAT
- [M] UPDATE_POLICY
- [M] GAP_POLICY

## [M] LAW
- KB = “короткая истина”: максимум сигнал, минимум шум
- 1 KB-объект = 1 смысл
- Любая метрика/порог/маппинг должна жить в KB, не в задачах/чатах

## [M] OBJECT_TYPES
- DEF: определение (1–2 строки)
- THR: порог/диапазон (1 строка + смысл)
- MAP: соответствие (X → Y, 1–3 правила)
- CST: ограничение/запрет (1–2 строки)
- EX: пример (короткий)

## [M] FORMAT
Каждая запись обязана иметь:
- ID (короткий код)
- TYPE (DEF/THR/MAP/CST/EX)
- BODY (1–3 строки)
Запрещены: прологи, “почему важно”, эмоциональные вводные.

## [M] UPDATE_POLICY
- Изменение определения = новая версия документа или отдельная запись CHANGE в 14_LOG/CHANGE_LOG
- Не переписывать историю задним числом без фиксации

## [M] GAP_POLICY
Если при выполнении задачи нет нужного DEF/THR/MAP:
- фиксируем GAP
- добавляем запись в релевантный KB_* (минимально)
- продолжаем пайплайн
