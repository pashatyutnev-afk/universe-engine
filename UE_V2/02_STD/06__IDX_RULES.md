# FILE: UE_V2/02_STD/06__IDX_RULES.md
SCOPE: UE_V2
LAYER: 02_STD
DOC_TYPE: STANDARD
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.STD.IDX_RULES.001
OWNER: STANDARDS_OWNER
TITLE: INDEX STANDARD (SMALL FAMILY INDEXES)

## MARKERS
- [M] INTENT
- [M] INDEX_TYPES
- [M] SIZE_LIMITS
- [M] FORMAT
- [M] GATES

## [M] INTENT
Индексы нужны для маршрутизации, но не должны жрать память.

## [M] INDEX_TYPES
- ROOT NAV (малый): указывает на малые индексы
- FAMILY IDX (малый): 1 семейство / 1 домен / 1 слой
- LIST IDX: список элементов без описаний-эссе

## [M] SIZE_LIMITS
- Индекс ≤ 120 строк
- Описание элемента ≤ 1 строка
- Никаких “портянок” с правилами (правила живут в STD/Law)

## [M] FORMAT
- Заголовок + MARKERS
- [M] LIST: список элементов
- [M] RULES: 3–7 коротких правил применения

## [M] GATES
- G.IDX.BIG = REWORK_REQUIRED если превышены SIZE_LIMITS
- G.IDX.RULES_IN_BODY = REWORK_REQUIRED если индекс содержит “воду” вместо списка
