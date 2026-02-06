# FILE: UE_V2/02_STD/06__IDX_RULES.md

SCOPE: UE_V2
LAYER: 02_STD
DOC_TYPE: STANDARD
MODE: REPO
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.1.0
UID: UE.V2.STD.IDX_RULES.001
OWNER: STANDARDS_OWNER
TITLE: INDEX STANDARD (SMALL FAMILY INDEXES)

---

## MARKERS
- [M] INTENT
- [M] INDEX_TYPES
- [M] SIZE_LIMITS
- [M] FORMAT
- [M] LINKING_RULES
- [M] GATES

---

## [M] INTENT
Индексы нужны для маршрутизации, но не должны жрать память
и не должны ломать RAW-навигацию.

---

## [M] INDEX_TYPES
- ROOT NAV (малый): указывает на малые индексы
- FAMILY IDX (малый): 1 семейство / 1 домен / 1 слой
- LIST IDX: список элементов без “эссе”

---

## [M] SIZE_LIMITS
- Индекс ≤ 120 строк
- Описание элемента ≤ 1 строка
- Никаких “портянок” с правилами (правила живут в STD/Law)

---

## [M] FORMAT
- Заголовок + MARKERS
- [M] LIST: список элементов
- [M] RULES: 3–7 коротких правил применения

---

## [M] LINKING_RULES
I1) Разрешены два формата элементов списка:
- RAW: [NAME] RAW_LINK
- PATH_KEY: UE_V2/.../file.md

I2) Если используется PATH_KEY, индекс обязан:
- либо ссылаться на утверждённый LINK_BASE/RESOLVER (где этот PATH_KEY будет CONFIRMED),
- либо сам содержать RAW (предпочтительно для критических entrypoints).

I3) В рантайме открытие выполняется только по RAW (см. NAV_RULES).

---

## [M] GATES
- G.IDX.BIG = REWORK_REQUIRED если превышены SIZE_LIMITS
- G.IDX.RULES_IN_BODY = REWORK_REQUIRED если индекс содержит “воду” вместо списка
- G.IDX.UNRESOLVABLE_PATH = STOP если PATH_KEY встречается, но нет утверждённого RESOLVER
