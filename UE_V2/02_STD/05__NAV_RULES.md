# FILE: UE_V2/02_STD/05__NAV_RULES.md
SCOPE: UE_V2
LAYER: 02_STD
DOC_TYPE: STANDARD
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.STD.NAV_RULES.001
OWNER: STANDARDS_OWNER
TITLE: NAVIGATION RULES (RAW-ONLY)

## MARKERS
- [M] INTENT
- [M] ALLOWED
- [M] FORBIDDEN
- [M] RESOURCE_TRACE
- [M] GATES

## [M] INTENT
Навигация должна быть быстрой и не забивать токен-бюджет.

## [M] ALLOWED
- RAW ссылки (внешнее репо) только:
  - присланные пользователем, или
  - уже подтверждённые в текущем рантайме
- Внутри V2 локальной структуры: прямые пути к файлам (без “угадываний новых”)

## [M] FORBIDDEN
- Угадывать пути/файлы/URL
- Ссылаться на “индекс индексов” внутри каждого документа
- Делать большие глобальные индексы как обязательную точку входа

## [M] RESOURCE_TRACE
RESOURCES USED обязателен:
- ссылка/путь
- MARKER FOUND (конкретный [M])

## [M] GATES
- G.NAV.GUESS = FAIL
- G.NAV.RAW_MISSING = STOP если требовалась RAW ссылка, но её нет
- G.NAV.TRACE_MISSING = FAIL если нет Resource Trace
