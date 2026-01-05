# ENG FAMILY README — DOMAIN_WORLD_ENGINES (TEMPLATE v2)
FILE: 00__TEMPLATE__README__DOMAIN_WORLD_ENGINES.md

SCOPE: Universe Engine
LAYER: ENG
DOC_TYPE: TEMPLATE
ENTITY_KIND: WORLD
PROJECT_SCOPE: GLOBAL
OUTPUT_LEVEL: N/A
ID: ENG.TPL.FAMILY.DOMAIN_WORLD.README
STATUS: ACTIVE
VERSION: 2.0
ROLE: Realm law + role map + interfaces + required REG/XREF + canon order for DOMAIN_WORLD family.

---

## 0) PURPOSE (REALM LAW)

Этот README — закон семейства **DOMAIN_WORLD_ENGINES**.
Семейство отвечает за мир как систему:
- структура мира (слои, карты, регионы, масштабы)
- законы мира (физика/соц правила/ограничения)
- таймлайн и эпохи
- цивилизации и их устройство
- конфликты и власть на уровне мира (не сюжетный конфликт сцены)
- геополитика
- экономика/ресурсы (как устройство обмена/распределения)
- технологии/магия
- мифология/вера
- среда/экология

### EXISTENCE RULE (WORLD)
> Любой проект обязан иметь World canon minimum: структура + законы + эпохи (хотя бы базово).

---

## 1) FAMILY IDENTITY (MANDATORY)

FAMILY_NAME: DOMAIN_WORLD_ENGINES  
FAMILY_CODE: WLD  
FAMILY_CLASS: DOMAIN  
FAMILY_LEVEL: L2  

FAMILY_PATH: `10_ENG__ENGINES/04_DOMAIN_WORLD_ENGINES/`  
README_FILE: `00__README__DOMAIN_WORLD_ENGINES.md`

---

## 2) OWNERSHIP BOUNDARIES (ANTI-DUPLICATION)

### 2.1 OWNS
- World structure: карта понятий/регионов/уровней
- World law: правила, ограничения, “что возможно/невозможно”
- Timeline & epoch: хронология, эпохи, переходы эпох
- Civilization: социальные системы, институты, уровни развития
- Conflict & power (world-level): силы, полюса, долгие напряжения
- Geopolitics: территории, блоки, динамики
- Economy & resource: ресурсы, логистика, распределение, scarcity/abundance
- Technology & magic: технологические стеки/магсистемы
- Mythology & belief: пантеоны/верования/культовые структуры
- Environment & ecology: климат, биомы, циклы, экология

### 2.2 DOES NOT OWN (hard boundaries)
- Сюжетное построение (структура истории/сцены/темп) → Narrative
- Персонажная психология/мотивация/диалог → Character
- Genre tone/atmosphere/symbolism → Genre/Style
- Production outputs (арт/монтаж/звук) → Knowledge Production
- Deep music → Sound Music
- Governance: изменения канона и правила → Governance
- “Атомы событий” (event/cause-effect/conflict/climax/resolution как формальные блоки) → Expression

Boundary rule:
> World defines constraints. Narrative/Character “играют внутри” этих границ.

---

## 3) WORLD AXIOMS (MANDATORY FAMILY RULES)

### 3.1 No currency in great civilizations (canon rule)
CANON_RULE:
- Great civilizations do not use currency.
- Economic organization must be modeled as:
  - allocation / access rights / resource governance / energy quotas / reputation / duty / distribution protocols
- Currency may exist only in:
  - low-tier периферии
  - transitional societies
  - black markets / collapse zones
- Any appearance of currency must be flagged as:
  - WORLD_EXCEPTION and linked via XREF__CHANGES / XREF__CONFLICTS if it contradicts canon.

Rule:
> Если “великая цивилизация” и “валюта” встречаются вместе — это либо ошибка, либо отдельный эксепшн с объяснением.

---

## 4) ROLE MAP (MANDATORY)

- FOUNDATION — структура мира + законы
- BUILDER — эпохи/цивилизации/геополитика/тех
- VALIDATOR — согласованность: экономика↔тех↔экология↔таймлайн
- BRIDGE — стык мира с narrative constraints (что возможно в сюжетах)
- OUTPUT — world bible / world canon pack / timeline pack

### 4.1 Canonical role map table
| Engine NN | Engine Name | ROLE_IN_FAMILY | PIPELINE_STAGE |
|---|---|---|---|
| 01 | World Structure Engine | FOUNDATION | DEFINE |
| 02 | World Law Engine | FOUNDATION | DEFINE |
| 03 | Timeline & Epoch Engine | BUILDER | BUILD |
| 04 | Civilization Engine | BUILDER | BUILD |
| 05 | Conflict & Power Engine | BUILDER | BUILD |
| 06 | Geopolitics Engine | BUILDER | BUILD |
| 07 | Economy & Resource Engine | VALIDATOR | CHECK |
| 08 | Technology & Magic Engine | BUILDER | BUILD |
| 09 | Mythology & Belief Engine | BUILDER | BUILD |
| 10 | Environment & Ecology Engine | VALIDATOR | CHECK |

---

## 5) FAMILY OUTPUT POLICY (WORKSHOP L0–L3) — MANDATORY

DEFAULT_PROJECT_OUTPUT_ROOT:
- `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/`

Primary categories:
- `04_SYSTEMS/` (если мир как система)
- `02_LOCATIONS/` (если регионы как сущности)
- `05_FACTIONS/` (если блоки/державы как сущности)
- `07_CONCEPTS/` (если законы/магсистема/экономика как концепты)
- Project-level world packs:
  - `05_PROJECT__L3/`

Recommended:
- L0: мировые заметки/референсы
- L1: черновые карты/таблицы/правила
- L2: world bible canon + timeline canon + rulesets
- L3: output pack для продакшна (справочник, bible condensed)

---

## 6) REQUIRED REGISTRIES (MANDATORY)

REQUIRED_REGISTRIES (project-scoped):
- `REG.PRJ.<PROJECT_ID>.ENTITIES` (locations/factions/systems/concepts)
- `REG.PRJ.<PROJECT_ID>.CANON_L2` (world canon packs)
- `REG.PRJ.<PROJECT_ID>.OUTPUT_L3` (world output packs)

---

## 7) REQUIRED XREF INDEXES (MANDATORY)

REQUIRED_XREF (project-scoped):
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__ENTITY_GRAPH.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__DEPENDENCIES.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__PROVENANCE.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CANON_REFS.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CONFLICTS.md` (world contradictions)

Hard rule:
> Любое правило мира, на которое опирается narrative/character, обязано быть DEPENDS_ON link.

---

## 8) INTERFACES (INPUT / OUTPUT ARTIFACT TYPES)

### 8.1 INPUT TYPES
- CORE_CARD (existence)
- NARRATIVE_REQUIREMENTS (what story needs)
- CHARACTER_REQUIREMENTS (background constraints)
- STYLE_CONSTRAINTS (tone may constrain world presentation)
- EXPRESSION_ATOMS (event types as stress-tests; optional)

### 8.2 OUTPUT TYPES
- WORLD_BIBLE
- WORLD_LAWSET
- TIMELINE_PACK
- EPOCH_MAP
- CIVILIZATION_PROFILE_SET
- GEOPOLITICS_MAP
- ECON_RESOURCE_MODEL (non-currency for great civilizations)
- TECH_MAGIC_STACK
- MYTH_BELIEF_SYSTEM
- ECOLOGY_PROFILE
- WORLD_CONSTRAINTS_PACK (condensed constraints to be consumed by other families)

---

## 9) TEMPLATES (MANDATORY BLOCK)

Base
