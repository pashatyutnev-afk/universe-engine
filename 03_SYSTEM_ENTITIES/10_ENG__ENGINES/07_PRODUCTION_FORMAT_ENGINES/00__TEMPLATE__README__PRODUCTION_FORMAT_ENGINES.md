# ENG FAMILY README — PRODUCTION_FORMAT_ENGINES (TEMPLATE v2)
FILE: 00__TEMPLATE__README__PRODUCTION_FORMAT_ENGINES.md

SCOPE: Universe Engine
LAYER: ENG
DOC_TYPE: TEMPLATE
ENTITY_KIND: FMT
PROJECT_SCOPE: GLOBAL
OUTPUT_LEVEL: N/A
ID: ENG.TPL.FAMILY.PRODUCTION_FORMAT.README
STATUS: ACTIVE
VERSION: 2.0
ROLE: Realm law + role map + interfaces + required REG/XREF + canon order for PRODUCTION_FORMAT family.

---

## 0) PURPOSE (REALM LAW)

Этот README — закон семейства **PRODUCTION_FORMAT_ENGINES**.
Семейство отвечает за форматную упаковку проекта:
- жанр как категория выпуска (Genre Engine) — именно “формат жанра” как упаковка/market label, не стиль атмосферы
- смешение жанров как правило упаковки
- адаптацию истории под формат
- правила книги
- правила сериала/эпизодов
- правила короткого контента
- правила YouTube longform
- правила игры (нарративные ограничения формата игры)

### EXISTENCE RULE (FORMAT)
> Любой проект обязан выбрать формат и иметь форматный constraints pack.  
> Без формата нельзя валидировать deliverables и структуру выпуска.

---

## 1) FAMILY IDENTITY (MANDATORY)

FAMILY_NAME: PRODUCTION_FORMAT_ENGINES  
FAMILY_CODE: FMT  
FAMILY_CLASS: PRODUCTION  
FAMILY_LEVEL: L3  

FAMILY_PATH: `10_ENG__ENGINES/07_PRODUCTION_FORMAT_ENGINES/`  
README_FILE: `00__README__PRODUCTION_FORMAT_ENGINES.md`

---

## 2) OWNERSHIP BOUNDARIES (ANTI-DUPLICATION)

### 2.1 OWNS
- Форматные правила: единицы выпуска, deliverables, структура пакетов
- Требования к длительности/объёму на уровне “диапазонов” (не секунды монтажа)
- Правила сериализации: сезоны/эпизоды, cliffhangers как форматный паттерн
- Адаптация структуры под формат (через интерфейсы к Narrative)

### 2.2 DOES NOT OWN (hard boundaries)
- Story logic/scene ordering/arc design → Narrative
- Event atoms → Expression
- Style/атмосфера/символизм → Genre/Style (06)
- Монтаж/секунды/тайминг кадра → 08 Editing
- Визуальный арт-дирекшн и камера/свет → 08
- Глубокая музыка → 09
- Законы мира/экономика → 04
- Психология персонажа/диалог → 03

Boundary rule:
> Format говорит “каким пакетом и в каких единицах выпускать”, но не пишет историю и не монтирует.

---

## 3) ROLE MAP (MANDATORY)

- FOUNDATION — жанр/жанровое смешение (как упаковка)
- BUILDER — адаптация под формат (mapping narrative → format)
- VALIDATOR — проверка deliverables/структуры выпуска
- BRIDGE — интерфейс между narrative canon (L2) и production outputs (08)
- OUTPUT — format constraints pack + delivery spec

### 3.1 Canonical role map table
| Engine NN | Engine Name | ROLE_IN_FAMILY | PIPELINE_STAGE |
|---|---|---|---|
| 01 | Genre Engine | FOUNDATION | DEFINE |
| 02 | Genre Blending Engine | FOUNDATION | DEFINE |
| 03 | Format Adaptation Engine | BRIDGE | PACKAGE |
| 04 | Book Format Engine | BUILDER | BUILD |
| 05 | Series & Episode Engine | BUILDER | BUILD |
| 06 | Short Content Engine | BUILDER | BUILD |
| 07 | YouTube Longform Engine | BUILDER | BUILD |
| 08 | Game Narrative Engine | BUILDER | BUILD |

---

## 4) FORMAT CONSTRAINTS STANDARD (MANDATORY)

Каждый форматный pack обязан иметь:
- FORMAT_ID
- FORMAT_TYPE (BOOK|SERIES|SHORT|YTLONG|GAME)
- UNIT_DEFINITION (chapter/episode/short/quest)
- DELIVERABLES (что сдаём)
- STRUCTURE_RULES (например “эпизод: intro→push→turn→cliff” как pattern, не как сюжет)
- LENGTH_RANGE (диапазон, не монтажные секунды)
- CADENCE (release cadence optional)
- HANDOFFS:
  - to Narrative (что требовать от outline)
  - to Production (что производить)

Rule:
> Format pack обязан быть “машиночитаемым” constraints документом, не эссе.

---

## 5) FAMILY OUTPUT POLICY (WORKSHOP L0–L3) — MANDATORY

DEFAULT_PROJECT_OUTPUT_ROOT:
- `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/`

Primary categories:
- `11_FORMAT/`
- `05_PROJECT__L3/` (delivery specs)

Recommended:
- L0: идеи формата
- L1: черновые constraints
- L2: format canon pack
- L3: delivery spec для production

File examples:
- L2: `03_CANON_L2/00__FORMAT_CONSTRAINTS_CANON.md`
- L3: `04_OUTPUT_L3/00__DELIVERY_SPEC.md`

---

## 6) REQUIRED REGISTRIES (MANDATORY)

REQUIRED_REGISTRIES (project-scoped):
- `REG.PRJ.<PROJECT_ID>.CANON_L2` (format canon)
- `REG.PRJ.<PROJECT_ID>.OUTPUT_L3` (delivery spec)

---

## 7) REQUIRED XREF INDEXES (MANDATORY)

REQUIRED_XREF (project-scoped):
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__DEPENDENCIES.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CANON_REFS.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__PROVENANCE.md`

Hard rule:
> Любой narrative output pack (L3) должен ссылаться на FORMAT_CONSTRAINTS_PACK, и любой production plan (08) тоже.

---

## 8) INTERFACES (INPUT / OUTPUT ARTIFACT TYPES)

### 8.1 INPUT TYPES
- NARRATIVE_CANON_OUTLINE (L2)
- STYLE_CONSTRAINTS_PACK (06)
- WORLD_CONSTRAINTS_PACK (04)
- PRODUCTION_CAPABILITIES (optional)
- target platform constraints (optional)

### 8.2 OUTPUT TYPES
- FORMAT_CONSTRAINTS_PACK
- DELIVERY_SPEC
- UNIT_TEMPLATE (chapter/episode/short skeleton)
- ADAPTATION_MAP (narrative→format)
- RELEASE_CADENCE (optional)

---

## 9) TEMPLATES (MANDATORY BLOCK)

Base templates:
- FAMILY README TEMPLATE (base) — `10_ENG__ENGINES/00__TEMPLATE__README__FAMILY__ENG.md`
- ENGINE TEMPLATE (base) — `10_ENG__ENGINES/00__TEMPLATE__ENGINE__ENG.md`

Family overlays:
- README TEMPLATE (this file) — `10_ENG__ENGINES/07_PRODUCTION_FORMAT_ENGINES/00__TEMPLATE__README__PRODUCTION_FORMAT_ENGINES.md`
- ENGINE TEMPLATE (family) — `10_ENG__ENGINES/07_PRODUCTION_FORMAT_ENGINES/00__TEMPLATE__ENGINE__PRODUCTION_FORMAT_ENGINES.md`

---

## 10) CANON ORDER (MANDATORY)

00 — README (Realm)  
01 — Genre Engine  
02 — Genre Blending Engine  
03 — Format Adaptation Engine  
04 — Book Format Engine  
05 — Series & Episode Engine  
06 — Short Content Engine  
07 — YouTube Longform Engine  
08 — Game Narrative Engine  

---

## FINAL RULE (LOCK)

> Format family задаёт упаковку и deliverables.  
> Он должен быть dependency для Narrative outputs и Production plans.

OWNER: Universe Engine  
LOCK: FIXED
