# ENG FAMILY README — DOMAIN_CHARACTER_ENGINES (TEMPLATE v2)
FILE: 00__TEMPLATE__README__DOMAIN_CHARACTER_ENGINES.md

SCOPE: Universe Engine
LAYER: ENG
DOC_TYPE: TEMPLATE
ENTITY_KIND: CHR
PROJECT_SCOPE: GLOBAL
OUTPUT_LEVEL: N/A
ID: ENG.TPL.FAMILY.DOMAIN_CHARACTER.README
STATUS: ACTIVE
VERSION: 2.0
ROLE: Realm law + role map + interfaces + required REG/XREF + canon order for DOMAIN_CHARACTER family.

---

## 0) PURPOSE (REALM LAW)

Этот README — закон семейства **DOMAIN_CHARACTER_ENGINES**.
Семейство отвечает за:
- core персонажа как личности (характерный каркас, ценности)
- мотивацию, желания, цели
- мораль/ценностный компас
- психологию (модели поведения, травма, рост)
- поведение и выбор
- отношения (сетевые связи)
- диалог и естественность речи
- развитие персонажа (эволюция)

### EXISTENCE RULE (CHARACTER)
> Персонаж не считается “живым” в каноне без: core + мотивации + поведения + отношений (хотя бы минимально).

---

## 1) FAMILY IDENTITY (MANDATORY)

FAMILY_NAME: DOMAIN_CHARACTER_ENGINES  
FAMILY_CODE: CHR  
FAMILY_CLASS: DOMAIN  
FAMILY_LEVEL: L2  

FAMILY_PATH: `10_ENG__ENGINES/03_DOMAIN_CHARACTER_ENGINES/`  
README_FILE: `00__README__DOMAIN_CHARACTER_ENGINES.md`

---

## 2) OWNERSHIP BOUNDARIES (ANTI-DUPLICATION)

### 2.1 OWNS
- Character core: идентичность личности (не системная, а “персонажная”)
- Motivation & desire: желания/цели/страхи/потребности
- Moral & value: ценностный код, границы, табу
- Character psychology: модели психики, реакции, паттерны
- Behavior: поведенческие стратегии, выборы
- Relationship: связи, динамики, узлы отношений
- Dialogue: смысл/подтекст/ритм речи (в смысле содержания, не монтажа)
- Speech naturalization: “как это звучит естественно” (лексика, регистр, привычки)
- Growth & trauma: травма/рост/переломы
- Character evolution: дуга развития персонажа

### 2.2 DOES NOT OWN (hard boundaries)
- Story structure / scene construction (как сцены стоят в истории) → Narrative
- Event atoms (событие/конфликт/кульминация как формальные блоки) → Expression
- World law / economy / geopolitics → World
- Genre tone/atmosphere (как “ощущается” проект) → Genre/Style
- Production timing (тайминг реплик, монтаж, паузы в секундах) → Editing/Montage (08)
- “Актёрская” постановка и продакшн звук (placement/clarity) → 08 Sound (Production)
- Deep music (композиция/гармония) → 09

Boundary rule:
> Character family отвечает за “почему персонаж так говорит/делает” и “кто он внутри”, но не за монтаж/тайминг и не за построение истории.

---

## 3) ROLE MAP (MANDATORY)

- FOUNDATION — core/ценности/психологический базис
- BUILDER — поведение/отношения/диалог как сборка
- VALIDATOR — естественность речи, непротиворечивость мотивации, целостность роста
- BRIDGE — стык персонажа с narrative/world constraints (что допустимо)
- OUTPUT — character bible / character card / relationship map / dialogue packs

### 3.1 Canonical role map table
| Engine NN | Engine Name | ROLE_IN_FAMILY | PIPELINE_STAGE |
|---|---|---|---|
| 01 | Character Core Engine | FOUNDATION | DEFINE |
| 02 | Motivation & Desire Engine | FOUNDATION | DEFINE |
| 03 | Moral & Value Engine | FOUNDATION | DEFINE |
| 04 | Character Psychology Engine | FOUNDATION | DEFINE |
| 05 | Character Behavior Engine | BUILDER | BUILD |
| 06 | Relationship Engine | BUILDER | BUILD |
| 07 | Dialogue Engine | BUILDER | BUILD |
| 08 | Speech Naturalization Engine | VALIDATOR | CHECK |
| 09 | Growth & Trauma Engine | BUILDER | BUILD |
| 10 | Character Evolution Engine | BRIDGE | PACKAGE |

OUTPUT в практике:
- character bible (L2)
- dialogue pack (L3) — как текст/подтекст, без тайминга монтажа

---

## 4) FAMILY OUTPUT POLICY (WORKSHOP L0–L3) — MANDATORY

DEFAULT_PROJECT_OUTPUT_ROOT:
- `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/`

Primary category:
- `01_CHARACTERS/CHR_<NAME>/`

Recommended routing:
- L0: наблюдения, наброски, референсы речи
- L1: структурные черновики (мотивация/ценности/отношения)
- L2: canon character bible (`03_CANON_L2/00__CANON.md` + секции)
- L3: output packs (dialogue lines, acting notes as text, relationship snapshots)

File examples:
- L0: `01_INTAKE_L0/00__VOICE_NOTES.md`
- L1: `02_DRAFT_L1/00__CHARACTER_BIBLE_DRAFT.md`
- L2: `03_CANON_L2/00__CANON.md` (единый канон) + optional appendices
- L3: `04_OUTPUT_L3/00__DIALOGUE_PACK.md`

Hard rule:
> Тайминг/секунды/монтаж в character outputs запрещены → это 08 editing.

---

## 5) REQUIRED REGISTRIES (MANDATORY)

REQUIRED_REGISTRIES (project-scoped):
- `REG.PRJ.<PROJECT_ID>.ENTITIES` (characters must exist)
- `REG.PRJ.<PROJECT_ID>.CANON_L2` (если L2 канон хранится отдельным артефактом)
- `REG.PRJ.<PROJECT_ID>.OUTPUT_L3` (если есть L3 packs)

Rule:
> Каждый CHR root folder должен быть зарегистрирован как entity.

---

## 6) REQUIRED XREF INDEXES (MANDATORY)

REQUIRED_XREF (project-scoped):
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__ENTITY_GRAPH.md` (character ↔ others)
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__PROVENANCE.md` (draft→canon)
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CANON_REFS.md` (output→canon)
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__DEPENDENCIES.md` (constraints)
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CHANGES.md` (replaced/merged/split)

Optional:
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__RELATIONSHIPS.md` (если нужен отдельный индекс отношений)

Hard rule:
> Relationships обязаны быть либо в entity graph xref, либо в отдельном relationships xref, но не “внутри текста без ссылок”.

---

## 7) INTERFACES (INPUT / OUTPUT ARTIFACT TYPES)

### 7.1 INPUT TYPES
- CORE_CARD (system existence)
- WORLD_CONSTRAINTS (laws, culture, tech level)
- NARRATIVE_CONSTRAINTS (role in arc, scene requirements)
- STYLE_CONSTRAINTS (tone, genre, register)
- RELATION_CONTEXT (links to other chars)
- EXPRESSION_ATOMS (conflict types, event triggers) — as constraints

### 7.2 OUTPUT TYPES
- CHARACTER_BIBLE (canon)
- MOTIVATION_MAP
- VALUE_COMPASS
- PSYCH_PROFILE
- BEHAVIOR_RULES
- RELATIONSHIP_MAP
- DIALOGUE_PACK (no timing)
- SPEECH_PROFILE (idiolect)
- GROWTH_TRAUMA_MAP
- EVOLUTION_ARC (character arc)

---

## 8) TEMPLATES (MANDATORY BLOCK)

Base templates:
- FAMILY README TEMPLATE (base) — `10_ENG__ENGINES/00__TEMPLATE__README__FAMILY__ENG.md`
- ENGINE TEMPLATE (base) — `10_ENG__ENGINES/00__TEMPLATE__ENGINE__ENG.md`

Family overlays:
- README TEMPLATE (this file) — `10_ENG__ENGINES/03_DOMAIN_CHARACTER_ENGINES/00__TEMPLATE__README__DOMAIN_CHARACTER_ENGINES.md`
- ENGINE TEMPLATE (family) — `10_ENG__ENGINES/03_DOMAIN_CHARACTER_ENGINES/00__TEMPLATE__ENGINE__DOMAIN_CHARACTER_ENGINES.md`

---

## 9) CANON ORDER (MANDATORY)

00 — README (Realm)  
01 — Character Core Engine  
02 — Motivation & Desire Engine  
03 — Moral & Value Engine  
04 — Character Psychology Engine  
05 — Character Behavior Engine  
06 — Relationship Engine  
07 — Dialogue Engine  
08 — Speech Naturalization Engine  
09 — Growth & Trauma Engine  
10 — Character Evolution Engine  

---

## 10) GOVERNANCE COMPATIBILITY (MANDATORY)

Изменения character canon:
- фиксируются как change (WHY)
- отражаются в XREF__CHANGES (REPLACED_BY / MERGED_INTO / SPLIT_INTO)
- output packs должны ссылаться на актуальный canon (CANON_REF)

---

## FINAL RULE (LOCK)

> Character family создаёт “живого человека”: мотивация → поведение → отношения → речь → рост.  
> Всё должно быть traceable (REG/XREF) и boundary-safe (без монтажа и без event-atoms внутри).

OWNER: Universe Engine  
LOCK: FIXED
