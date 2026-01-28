# 11__IDX_KB_MODULES_BY_DOMAIN

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: KB / INDEX
UID: UE.V2.KB.IDX.MODULES_BY_DOMAIN.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Индекс KB модулей по доменам. Главный вход для выбора модулей без блуждания.

---

## [M] INTENT
Быстро найти нужные KB-модули по домену задачи (MUSIC/VIS/LOR/REL/CORE), выбрать 3–7 и собрать KB_TOKEN.

---

## [M] RULES
1) Источник истины по scope: KB_SCOPE_PROFILES.
2) Выбор модулей строго в рамках DOMAIN_ALLOWED + SOURCES_ALLOWED.
3) Модулей в PICKSET: максимум 7.
4) Любой модуль должен быть "карточкой" (короткий extract), не полотном.

---

## [M] INDEX (STARTER)
CORE:
- UE_V2/02_STD/* (формат/гейты/токены)  [если ты держишь как KB-модули — иначе убрать]
- UE_V2/01_LAW/* (законы)               [если ты держишь как KB-модули — иначе убрать]
- UE_V2/08_XREF/* (карты)              [если ты держишь как KB-модули — иначе убрать]

MUSIC:
- UE_V2/10_TOPICS/03_SOUND_MUSIC/00__INDEX_SOUND_MUSIC_TOPICS.md
  (далее выбирать конкретные модули по темам: hook/structure/palette/prompt/qa)

VIS:
- UE_V2/10_TOPICS/01_VISUAL/00__INDEX_VISUAL_TOPICS.md

LOR:
- UE_V2/10_TOPICS/02_LORE/00__INDEX_LORE_TOPICS.md

REL:
- UE_V2/10_TOPICS/04_RELEASE/00__INDEX_RELEASE_TOPICS.md

---

## [M] NOTE (IMPORTANT)
Если у тебя TOPICS лежат не в UE_V2 или индекс называется иначе:
- замени пути на твои реальные.
Главное правило: IDX ведёт в "малый индекс тем", а не в сотню файлов.

---

## [M] GATES
PASS если:
- по домену найден малый индекс тем/модулей
GAP если:
- отсутствуют доменные индексы TOPICS (нужно создать)
REWORK если:
- индекс превращён в огромный список всех файлов
