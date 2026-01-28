# 04__IDX_KB

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: NAV / INDEX
UID: UE.V2.NAV.IDX_KB.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Вход в KB слой. Единственная правильная навигация: через KB_NAV_ROOT + KB_SCOPE.

---

## [M] INTENT
Сделать KB библиотекой:
- вход через KB_NAV_ROOT
- выбор модулей через малые индексы
- использование только через KB_TOKEN

---

## [M] ENTRYPOINT
- UE_V2/05_KB/10__KB_NAV_ROOT.md

---

## [M] CORE KB DOCS
- UE_V2/05_KB/00__KB_START.md
- UE_V2/05_KB/01__KB_RULES.md
- UE_V2/05_KB/02__KB_INPUTS.md
- UE_V2/05_KB/03__KB_OUTPUTS.md
- UE_V2/05_KB/04__KB_BOUNDARIES.md
- UE_V2/05_KB/08__KB_SOURCES.md
- UE_V2/05_KB/09__KB_SCOPE_PROFILES.md

---

## [M] KB NAV (SMALL INDEXES)
- UE_V2/05_KB/11__IDX_KB_MODULES_BY_DOMAIN.md
- UE_V2/05_KB/12__IDX_KB_MODULES_BY_TOPIC.md

OPTIONAL:
- UE_V2/05_KB/13__IDX_KB_SCOPES.md
- UE_V2/05_KB/14__KB_MODULE_FMT.md

---

## [M] RULES
1) Любая сущность использует KB только через SCOPE-GATE:
   KB_SCOPE -> IDX -> PICKSET -> KB_TOKEN.
2) Запрещено открывать пачку KB файлов “на всякий случай”.
3) Если модулей не хватает — добавлять модули и индексы, а не тащить контент в контекст.

---

## [M] GATES
PASS если:
- KB используется через KB_NAV_ROOT и KB_TOKEN
REWORK если:
- KB читается напрямую пачкой файлов
GAP если:
- отсутствуют 10/11/12 KB NAV файлы
STOP если:
- KB недоступна при задаче, где она обязательна
