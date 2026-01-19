# KNOWLEDGE BASE — MASTER INDEX (CANON / ONE-INDEX MODE)
FILE: 04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: INDEX
INDEX_TYPE: LAYER_MASTER_REGISTRY (KB)
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.1
UID: UE.KB.IDX.MASTER.001
OWNER: SYSTEM
ROLE: Single SoT for KB NAV/EXISTENCE + one-file operational navigation rules + source-lock/no-fantasy enforcement

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Rebuilt KB as strict ONE-INDEX operational system: RAW-only canon map + existence rule + no-fantasy/source-lock + KB usage gate."
- REASON: "KB must be universal quality library; deterministic navigation; no drift; no invented knowledge."
- IMPACT: "Any KB file not registered here is non-canon for KB operations."
- CHANGE_ID: UE.CHG.2026-01-14.KB.IDX.001


CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Clarified linkage to ROOT snapshot + ensured canon map is never truncated in runtime exports; no link removals."
- REASON: "Prevent confusion: KB master index is large; assistant must not summarize it as if links are missing."
- IMPACT: "Users can rely on this file as the full KB navigation surface; assistant outputs provide full-file artifact when requested."
- CHANGE_ID: UE.CHG.2026-01-20.KB.IDX.002

---

## 0) PURPOSE (LAW)
Этот INDEX — единственная точка истины (SoT) для слоя `04_KNOWLEDGE_BASE` по двум функциям:
1) NAV/EXISTENCE: какие KB файлы существуют и как их открывать (RAW-only).
2) OPERATIONAL MODE: как ассистент/сущности обязаны использовать KB без фантазии и без искажения.

---


## 0.1) RELATION TO ROOT + START (CLARIFICATION)
Этот KB master-index не заменяет ROOT-INDEX и не является рантайм-энтрипоинтом.
- ROOT-INDEX: snapshot базы RAW ссылок для всего тома.
- START_UNIVERSE_ENGINE: единственный запуск задач и маршрутизация.
- Этот файл: ONLY KB NAV/EXISTENCE + KB operational laws.

Если пользователь просит "покажи все ссылки" — ассистент обязан отдавать ПОЛНЫЙ файл-артефакт (без урезаний) либо готовый downloadable файл.
## 1) OPERATIONAL MODE (ONE FILE / ABSOLUTE)
### 1.1 One-index rule (ABSOLUTE)
Оперативная работа по KB выполняется ТОЛЬКО через этот файл:
`04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md`

### 1.2 Strict single-index model (NO SUB-INDEX)
Запрещено создавать “вторые индексы” в подпапках KB (любые попытки второго entrypoint).
В подпапках допускаются:
- README (локальная ориентация / карта действий)
- CATALOG / REGISTRY / TAXONOMY (справочники; не SoT)
Но NAV/EXISTENCE определяет ТОЛЬКО этот master-index.

### 1.3 Existence rule (ABSOLUTE)
- Если KB файла нет в CANON MAP ниже — он не существует оперативно для KB.
- Если файл есть в репо, но не зарегистрирован здесь — NON-CANON / ignored.
- NAV работает только по RAW ссылкам (PATH — метка для человека, не механизм).

---

## 2) SOURCE-LOCK / NO FANTASY (ABSOLUTE)
### 2.1 No invention (ABSOLUTE)
Запрещено:
- додумывать знания,
- “улучшать” смысл,
- компилировать как факт то, чего нет в источнике.

Любое утверждение/правило/процедура для сущностей допускается только:
A) из открытого KB-источника (RAW/PATH), или
B) из памяти (Memory-OK), если модуль уже открывали раньше и воспроизводим без искажения смысла.

### 2.2 Memory policy (allowed vs forbidden)
Memory-OK (разрешено):
- модуль ранее открывался,
- смысл воспроизводится без изменений,
- при сомнении — обязателен повторный просмотр по RAW.

Memory-NO (запрещено):
- добавлять детали “по логике”,
- менять формулировки так, что меняется смысл,
- выдавать предположения как данные.

### 2.3 Hard stop conditions
Run обязан остановиться (HARD FAIL), если:
- RAW недоступен/битый,
- нужный модуль не открыт и нет Memory-OK уверенности,
- обнаружена попытка “додумать” вместо чтения источника.

---

## 3) KB QUALITY & KB USAGE GATE (ABSOLUTE)
### 3.1 KB is quality control plane
KB — универсальная библиотека качества. Сущности обязаны пользоваться KB, иначе качество не контролируется.

### 3.2 KB Usage Gate (ABSOLUTE)
Любой результат (решение/контент/док/пакет) считается FAIL, если:
- не указаны KB_SOURCES (какие KB модули реально использованы),
- не указаны KB_GATES (какие проверки/рубрики применены),
- результат противоречит KB-политикам/правилам.

---

## 4) KB REALMS (MAP / ORIENTATION TOMES)
Ниже — “карта действий” (внутри KB) без второго индекса:

- 00_KB_GOVERNANCE — правила KB, шаблоны, контроль качества, source-lock, gate, именование, связи.
- 01_PILLARS — фундаментальные “тома” знаний (база домена).
- 10_TOPICS — атомарные модули знаний (маленькие темы).
- 20_ENTITIES_KB — стандарты подключения KB к сущностям + PRO PACK для SPC.
- 30_SHARED_LIBRARIES — переиспользуемые активы качества: чеклисты/рубрики/шаблоны/паттерны/примеры/промпт-либа.
- 40_RELATION_XREF — карты связей, маршруты, task→scope.

---

## 5) KB MODULE STATES (OPERATIONAL)
Состояния модулей (для контроля “память можно/нельзя”):
- UNREAD
- READ_ONCE
- VERIFIED
- DEPRECATED

Правило: использовать “из памяти” можно только VERIFIED (без искажений). При сомнении — переоткрыть модуль.

---

## 6) ENTITIES MUST USE KB (UNIVERSAL CONNECTOR RULE)
Каждая сущность (SPC/ENG/ORC/CTL/VAL/QA/XREF) обязана иметь KB-коннектор, где прописано:
- KB_SOURCES (REQUIRED/OPTIONAL, PATH/RAW)
- KB_GATES (что обязано проверяться)
- OUTPUT CONTRACT (каким шаблоном отдаётся результат)
- STOP CONDITIONS

---

## 7) CANON MAP — KB FILES (RAW-ONLY NAV)

### 7.0 Base RAW Prefix (used for all entries)
BASE_RAW_PREFIX:
https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/

---

### 7.1 ROOT — KB MASTER INDEX
00 — KB MASTER INDEX (THIS FILE)
PATH: `04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md

---

### 7.2 00_KB_GOVERNANCE (ORIENTATION + RULE TOMES + TEMPLATES)
00 — README KB REALM
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/00__README__KB_REALM.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/00__README__KB_REALM.md

01 — RULES KB
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB.md

02 — KB STORAGE MAP
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/02__KB_STORAGE_MAP.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/02__KB_STORAGE_MAP.md

03 — KB ENTITY TYPES
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/03__KB_ENTITY_TYPES.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/03__KB_ENTITY_TYPES.md

04 — KB NAMING RULES
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/04__KB_NAMING_RULES.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/04__KB_NAMING_RULES.md

05 — KB TAGS
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/05__KB_TAGS.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/05__KB_TAGS.md

06 — KB REL TYPES
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/06__KB_REL_TYPES.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/06__KB_REL_TYPES.md

07 — KB XREF RULES
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/07__KB_XREF_RULES.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/07__KB_XREF_RULES.md

08 — KB DOC CONTROL
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/08__KB_DOC_CONTROL.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/08__KB_DOC_CONTROL.md

09 — KB CHANGELOG
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/09__KB_CHANGELOG.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/09__KB_CHANGELOG.md

10 — KB QUALITY LAWS
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/10__KB_QUALITY_LAWS.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/10__KB_QUALITY_LAWS.md

11 — KB USAGE GATE
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/11__KB_USAGE_GATE.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/11__KB_USAGE_GATE.md

12 — KB SOURCE-LOCK / NO FANTASY
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/12__KB_SOURCE_LOCK_NO_FANTASY.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/12__KB_SOURCE_LOCK_NO_FANTASY.md

13 — KB MEMORY POLICY
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/13__KB_MEMORY_POLICY.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/13__KB_MEMORY_POLICY.md

14 — KB MODULE STATE SYSTEM
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/14__KB_MODULE_STATE_SYSTEM.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/14__KB_MODULE_STATE_SYSTEM.md

20 — TEMPLATE KB MODULE
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/20__TEMPLATE__KB_MODULE.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/20__TEMPLATE__KB_MODULE.md

21 — TEMPLATE KB LIBRARY ITEM
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/21__TEMPLATE__KB_LIBRARY_ITEM.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/21__TEMPLATE__KB_LIBRARY_ITEM.md

22 — TEMPLATE SPC PRO PACK
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/22__TEMPLATE__SPC_PRO_PACK.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/22__TEMPLATE__SPC_PRO_PACK.md

23 — TEMPLATE ENTITY KB CONNECTOR
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/23__TEMPLATE__ENTITY_KB_CONNECTOR.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/23__TEMPLATE__ENTITY_KB_CONNECTOR.md

---

### 7.3 01_PILLARS (FOUNDATION TOMES)
00 — README PILLARS REALM
PATH: `04_KNOWLEDGE_BASE/01_PILLARS/00__README__PILLARS_REALM.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/01_PILLARS/00__README__PILLARS_REALM.md

01 — PILLAR NARRATIVE CRAFT
PATH: `04_KNOWLEDGE_BASE/01_PILLARS/01__PILLAR__NARRATIVE_CRAFT.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/01_PILLARS/01__PILLAR__NARRATIVE_CRAFT.md

02 — PILLAR CHARACTER CRAFT
PATH: `04_KNOWLEDGE_BASE/01_PILLARS/02__PILLAR__CHARACTER_CRAFT.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/01_PILLARS/02__PILLAR__CHARACTER_CRAFT.md

03 — PILLAR WORLD CRAFT
PATH: `04_KNOWLEDGE_BASE/01_PILLARS/03__PILLAR__WORLD_CRAFT.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/01_PILLARS/03__PILLAR__WORLD_CRAFT.md

04 — PILLAR VISUAL CINEMA
PATH: `04_KNOWLEDGE_BASE/01_PILLARS/04__PILLAR__VISUAL_CINEMA.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/01_PILLARS/04__PILLAR__VISUAL_CINEMA.md

05 — PILLAR SOUND MUSIC
PATH: `04_KNOWLEDGE_BASE/01_PILLARS/05__PILLAR__SOUND_MUSIC.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/01_PILLARS/05__PILLAR__SOUND_MUSIC.md

06 — PILLAR PRODUCTION PIPELINE
PATH: `04_KNOWLEDGE_BASE/01_PILLARS/06__PILLAR__PRODUCTION_PIPELINE.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/01_PILLARS/06__PILLAR__PRODUCTION_PIPELINE.md

07 — PILLAR MARKETING DISTRIBUTION
PATH: `04_KNOWLEDGE_BASE/01_PILLARS/07__PILLAR__MARKETING_DISTRIBUTION.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/01_PILLARS/07__PILLAR__MARKETING_DISTRIBUTION.md

08 — PILLAR RESEARCH FACT CHECKING
PATH: `04_KNOWLEDGE_BASE/01_PILLARS/08__PILLAR__RESEARCH_FACT_CHECKING.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/01_PILLARS/08__PILLAR__RESEARCH_FACT_CHECKING.md

09 — PILLAR REFERENCE GLOSSARY
PATH: `04_KNOWLEDGE_BASE/01_PILLARS/09__PILLAR__REFERENCE_GLOSSARY.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/01_PILLARS/09__PILLAR__REFERENCE_GLOSSARY.md

---

### 7.4 10_TOPICS (ATOMIC KNOWLEDGE MODULES)
00 — README TOPICS REALM
PATH: `04_KNOWLEDGE_BASE/10_TOPICS/00__README__TOPICS_REALM.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/10_TOPICS/00__README__TOPICS_REALM.md

01 — TOPIC TAXONOMY
PATH: `04_KNOWLEDGE_BASE/10_TOPICS/01__TOPIC_TAXONOMY.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/10_TOPICS/01__TOPIC_TAXONOMY.md

10 — README TOPICS NARRATIVE
PATH: `04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/00__README__TOPICS_NARRATIVE.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/00__README__TOPICS_NARRATIVE.md

20 — README TOPICS CHARACTER
PATH: `04_KNOWLEDGE_BASE/10_TOPICS/20_CHARACTER/00__README__TOPICS_CHARACTER.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/10_TOPICS/20_CHARACTER/00__README__TOPICS_CHARACTER.md

30 — README TOPICS WORLD
PATH: `04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD/00__README__TOPICS_WORLD.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD/00__README__TOPICS_WORLD.md

40 — README TOPICS VISUAL
PATH: `04_KNOWLEDGE_BASE/10_TOPICS/40_VISUAL/00__README__TOPICS_VISUAL.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/10_TOPICS/40_VISUAL/00__README__TOPICS_VISUAL.md

50 — README TOPICS SOUND MUSIC
PATH: `04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/00__README__TOPICS_SOUND_MUSIC.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/00__README__TOPICS_SOUND_MUSIC.md

60 — README TOPICS PRODUCTION
PATH: `04_KNOWLEDGE_BASE/10_TOPICS/60_PRODUCTION/00__README__TOPICS_PRODUCTION.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/10_TOPICS/60_PRODUCTION/00__README__TOPICS_PRODUCTION.md

70 — README TOPICS MARKETING
PATH: `04_KNOWLEDGE_BASE/10_TOPICS/70_MARKETING/00__README__TOPICS_MARKETING.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/10_TOPICS/70_MARKETING/00__README__TOPICS_MARKETING.md

90 — README TOPICS REFERENCE
PATH: `04_KNOWLEDGE_BASE/10_TOPICS/90_REFERENCE/00__README__TOPICS_REFERENCE.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/10_TOPICS/90_REFERENCE/00__README__TOPICS_REFERENCE.md

---

### 7.5 20_ENTITIES_KB (CONNECTORS + SPC PRO PACK)
00 — README ENTITIES KB REALM
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/00__README__ENTITIES_KB_REALM.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/00__README__ENTITIES_KB_REALM.md

01 — ENTITY KB RULES
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/01__ENTITY_KB_RULES.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/01__ENTITY_KB_RULES.md

02 — ENTITY TO KB SCOPE MAP
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/02__ENTITY_TO_KB_SCOPE_MAP.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/02__ENTITY_TO_KB_SCOPE_MAP.md

03 — COVERAGE ENTITY KB STATUS
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/03__COVERAGE__ENTITY_KB_STATUS.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/03__COVERAGE__ENTITY_KB_STATUS.md

04 — COVERAGE SPC PROFICIENCY MATRIX
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/04__COVERAGE__SPC_PROFICIENCY_MATRIX.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/04__COVERAGE__SPC_PROFICIENCY_MATRIX.md

10 — README SPC PRO PACK STANDARD
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/00__README__SPC_PRO_PACK_STANDARD.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/00__README__SPC_PRO_PACK_STANDARD.md

10A — SPC TEMPLATE / 00 KB PASSPORT
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/SPC__TEMPLATE/00__KB_PASSPORT.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/SPC__TEMPLATE/00__KB_PASSPORT.md
10B — SPC TEMPLATE / 01 SKILL TREE
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/SPC__TEMPLATE/01__SKILL_TREE.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/SPC__TEMPLATE/01__SKILL_TREE.md
10C — SPC TEMPLATE / 02 GOLDEN PRINCIPLES
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/SPC__TEMPLATE/02__GOLDEN_PRINCIPLES.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/SPC__TEMPLATE/02__GOLDEN_PRINCIPLES.md
10D — SPC TEMPLATE / 03 PLAYBOOKS
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/SPC__TEMPLATE/03__PLAYBOOKS.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/SPC__TEMPLATE/03__PLAYBOOKS.md
10E — SPC TEMPLATE / 04 CHECKLISTS
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/SPC__TEMPLATE/04__CHECKLISTS.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/SPC__TEMPLATE/04__CHECKLISTS.md
10F — SPC TEMPLATE / 05 PATTERNS ANTI PATTERNS
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/SPC__TEMPLATE/05__PATTERNS_ANTI_PATTERNS.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/SPC__TEMPLATE/05__PATTERNS_ANTI_PATTERNS.md
10G — SPC TEMPLATE / 06 CASE LIBRARY
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/SPC__TEMPLATE/06__CASE_LIBRARY.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/SPC__TEMPLATE/06__CASE_LIBRARY.md
10H — SPC TEMPLATE / 07 EVALUATION RUBRIC
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/SPC__TEMPLATE/07__EVALUATION_RUBRIC.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/SPC__TEMPLATE/07__EVALUATION_RUBRIC.md
10I — SPC TEMPLATE / 90 KB SOURCES
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/SPC__TEMPLATE/90__KB_SOURCES.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/SPC__TEMPLATE/90__KB_SOURCES.md
10J — SPC TEMPLATE / 91 KB GATES
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/SPC__TEMPLATE/91__KB_GATES.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/SPC__TEMPLATE/91__KB_GATES.md

20 — README ENG KB CONNECTOR STANDARD
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/20_ENG/00__README__ENG_KB_CONNECTOR_STANDARD.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/20_ENG/00__README__ENG_KB_CONNECTOR_STANDARD.md

(ENG__TEMPLATE files registered below)
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/20_ENG/ENG__TEMPLATE/00__KB_PASSPORT.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/20_ENG/ENG__TEMPLATE/00__KB_PASSPORT.md
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/20_ENG/ENG__TEMPLATE/01__METHOD.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/20_ENG/ENG__TEMPLATE/01__METHOD.md
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/20_ENG/ENG__TEMPLATE/02__PARAMETERS.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/20_ENG/ENG__TEMPLATE/02__PARAMETERS.md
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/20_ENG/ENG__TEMPLATE/03__EDGE_CASES.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/20_ENG/ENG__TEMPLATE/03__EDGE_CASES.md
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/20_ENG/ENG__TEMPLATE/04__EXAMPLES.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/20_ENG/ENG__TEMPLATE/04__EXAMPLES.md
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/20_ENG/ENG__TEMPLATE/90__KB_SOURCES.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/20_ENG/ENG__TEMPLATE/90__KB_SOURCES.md
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/20_ENG/ENG__TEMPLATE/91__KB_GATES.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/20_ENG/ENG__TEMPLATE/91__KB_GATES.md

30 — README ORC KB CONNECTOR STANDARD
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/30_ORC/00__README__ORC_KB_CONNECTOR_STANDARD.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/30_ORC/00__README__ORC_KB_CONNECTOR_STANDARD.md

(ORC__TEMPLATE files registered below)
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/30_ORC/ORC__TEMPLATE/00__KB_PASSPORT.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/30_ORC/ORC__TEMPLATE/00__KB_PASSPORT.md
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/30_ORC/ORC__TEMPLATE/01__PIPELINE_STEPS.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/30_ORC/ORC__TEMPLATE/01__PIPELINE_STEPS.md
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/30_ORC/ORC__TEMPLATE/02__HANDOFFS.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/30_ORC/ORC__TEMPLATE/02__HANDOFFS.md
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/30_ORC/ORC__TEMPLATE/03__GATES_PLACEMENT.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/30_ORC/ORC__TEMPLATE/03__GATES_PLACEMENT.md
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/30_ORC/ORC__TEMPLATE/04__FAILOVER.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/30_ORC/ORC__TEMPLATE/04__FAILOVER.md
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/30_ORC/ORC__TEMPLATE/90__KB_SOURCES.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/30_ORC/ORC__TEMPLATE/90__KB_SOURCES.md

40 — README CTL KB CONNECTOR STANDARD
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/40_CTL/00__README__CTL_KB_CONNECTOR_STANDARD.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/40_CTL/00__README__CTL_KB_CONNECTOR_STANDARD.md

(CTL__TEMPLATE files registered below)
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/40_CTL/CTL__TEMPLATE/00__KB_PASSPORT.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/40_CTL/CTL__TEMPLATE/00__KB_PASSPORT.md
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/40_CTL/CTL__TEMPLATE/01__POLICY.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/40_CTL/CTL__TEMPLATE/01__POLICY.md
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/40_CTL/CTL__TEMPLATE/02__LIMITS_THRESHOLDS.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/40_CTL/CTL__TEMPLATE/02__LIMITS_THRESHOLDS.md
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/40_CTL/CTL__TEMPLATE/03__EXAMPLES.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/40_CTL/CTL__TEMPLATE/03__EXAMPLES.md
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/40_CTL/CTL__TEMPLATE/90__KB_SOURCES.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/40_CTL/CTL__TEMPLATE/90__KB_SOURCES.md

50 — README VAL KB CONNECTOR STANDARD
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/50_VAL/00__README__VAL_KB_CONNECTOR_STANDARD.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/50_VAL/00__README__VAL_KB_CONNECTOR_STANDARD.md

(VAL__TEMPLATE files registered below)
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/50_VAL/VAL__TEMPLATE/00__KB_PASSPORT.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/50_VAL/VAL__TEMPLATE/00__KB_PASSPORT.md
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/50_VAL/VAL__TEMPLATE/01__CHECK_RULE.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/50_VAL/VAL__TEMPLATE/01__CHECK_RULE.md
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/50_VAL/VAL__TEMPLATE/02__VIOLATION_FORMAT.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/50_VAL/VAL__TEMPLATE/02__VIOLATION_FORMAT.md
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/50_VAL/VAL__TEMPLATE/03__FIX_GUIDE.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/50_VAL/VAL__TEMPLATE/03__FIX_GUIDE.md
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/50_VAL/VAL__TEMPLATE/04__TEST_CASES.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/50_VAL/VAL__TEMPLATE/04__TEST_CASES.md
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/50_VAL/VAL__TEMPLATE/90__KB_SOURCES.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/50_VAL/VAL__TEMPLATE/90__KB_SOURCES.md

60 — README QA KB CONNECTOR STANDARD
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/60_QA/00__README__QA_KB_CONNECTOR_STANDARD.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/60_QA/00__README__QA_KB_CONNECTOR_STANDARD.md

(QA__TEMPLATE files registered below)
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/60_QA/QA__TEMPLATE/00__KB_PASSPORT.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/60_QA/QA__TEMPLATE/00__KB_PASSPORT.md
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/60_QA/QA__TEMPLATE/01__RUBRIC.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/60_QA/QA__TEMPLATE/01__RUBRIC.md
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/60_QA/QA__TEMPLATE/02__PROTOCOL.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/60_QA/QA__TEMPLATE/02__PROTOCOL.md
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/60_QA/QA__TEMPLATE/03__EXAMPLES.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/60_QA/QA__TEMPLATE/03__EXAMPLES.md
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/60_QA/QA__TEMPLATE/90__KB_SOURCES.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/60_QA/QA__TEMPLATE/90__KB_SOURCES.md

90 — README XREF KB CONNECTOR STANDARD
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/90_XREF/00__README__XREF_KB_CONNECTOR_STANDARD.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/90_XREF/00__README__XREF_KB_CONNECTOR_STANDARD.md

(XREF__TEMPLATE files registered below)
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/90_XREF/XREF__TEMPLATE/00__KB_PASSPORT.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/90_XREF/XREF__TEMPLATE/00__KB_PASSPORT.md
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/90_XREF/XREF__TEMPLATE/01__USAGE.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/90_XREF/XREF__TEMPLATE/01__USAGE.md
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/90_XREF/XREF__TEMPLATE/02__EXAMPLES.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/90_XREF/XREF__TEMPLATE/02__EXAMPLES.md
PATH: `04_KNOWLEDGE_BASE/20_ENTITIES_KB/90_XREF/XREF__TEMPLATE/90__KB_SOURCES.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/20_ENTITIES_KB/90_XREF/XREF__TEMPLATE/90__KB_SOURCES.md

---

### 7.6 30_SHARED_LIBRARIES (QUALITY ASSETS)
00 — README SHARED LIBRARIES REALM
PATH: `04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/00__README__SHARED_LIBRARIES_REALM.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/00__README__SHARED_LIBRARIES_REALM.md

01 — LIB TAXONOMY
PATH: `04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/01__LIB_TAXONOMY.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/01__LIB_TAXONOMY.md

10 — README CHECKLISTS
PATH: `04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/10_CHECKLISTS/00__README__CHECKLISTS.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/10_CHECKLISTS/00__README__CHECKLISTS.md

20 — README RUBRICS
PATH: `04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/20_RUBRICS/00__README__RUBRICS.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/20_RUBRICS/00__README__RUBRICS.md

30 — README TEMPLATES
PATH: `04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/30_TEMPLATES/00__README__TEMPLATES.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/30_TEMPLATES/00__README__TEMPLATES.md

40 — README PATTERNS
PATH: `04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/40_PATTERNS/00__README__PATTERNS.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/40_PATTERNS/00__README__PATTERNS.md

50 — README EXAMPLES
PATH: `04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/50_EXAMPLES/00__README__EXAMPLES.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/50_EXAMPLES/00__README__EXAMPLES.md

60 — README PROMPT LIB
PATH: `04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/60_PROMPT_LIB/00__README__PROMPT_LIB.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/60_PROMPT_LIB/00__README__PROMPT_LIB.md

---

### 7.7 40_RELATION_XREF (ROUTES / MAPS)
00 — README RELATION XREF REALM
PATH: `04_KNOWLEDGE_BASE/40_RELATION_XREF/00__README__RELATION_XREF_REALM.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/40_RELATION_XREF/00__README__RELATION_XREF_REALM.md

01 — TASK TO KB SCOPE MAP
PATH: `04_KNOWLEDGE_BASE/40_RELATION_XREF/01__TASK_TO_KB_SCOPE_MAP.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/40_RELATION_XREF/01__TASK_TO_KB_SCOPE_MAP.md

02 — KB REL GRAPH
PATH: `04_KNOWLEDGE_BASE/40_RELATION_XREF/02__KB_REL_GRAPH.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/40_RELATION_XREF/02__KB_REL_GRAPH.md

03 — KB XREF MAPS
PATH: `04_KNOWLEDGE_BASE/40_RELATION_XREF/03__KB_XREF_MAPS.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/40_RELATION_XREF/03__KB_XREF_MAPS.md

04 — GLOSSARY CANON TERMS
PATH: `04_KNOWLEDGE_BASE/40_RELATION_XREF/04__GLOSSARY_CANON_TERMS.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/40_RELATION_XREF/04__GLOSSARY_CANON_TERMS.md

---

## 8) ENFORCEMENT (MANDATORY)
### 8.1 Mandatory checks
- Любой новый KB файл обязан быть зарегистрирован в CANON MAP этого master-index.
- Любая попытка создать sub-index в подпапке — нарушение strict single-index model.
- Любой контент/решение без KB_SOURCES/KB_GATES — FAIL.

### 8.2 Fail conditions
- Появился KB файл, которого нет в CANON MAP.
- Появился второй индекс-entrypoint в подпапке.
- Использована “фантазия” вместо source-lock.

---

## 9) REFERENCES (RAW ONLY)
- DOC CONTROL STANDARD (STD):
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md
- INDEX STRUCTURE SPEC (STD):
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/09__INDEX_STRUCTURE_SPEC.md
- SYSTEM LAW — UID RULES:
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/02__UID_RULES.md
- SYSTEM LAW — NAMING RULES:
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/01__NAMING_RULES.md

--- END.