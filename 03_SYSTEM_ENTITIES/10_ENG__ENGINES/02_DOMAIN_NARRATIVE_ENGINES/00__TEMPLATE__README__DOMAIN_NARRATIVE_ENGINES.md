# ENG FAMILY README — DOMAIN_NARRATIVE_ENGINES (TEMPLATE v2)
FILE: 00__TEMPLATE__README__DOMAIN_NARRATIVE_ENGINES.md

SCOPE: Universe Engine
LAYER: ENG
DOC_TYPE: TEMPLATE
ENTITY_KIND: GENERIC
PROJECT_SCOPE: GLOBAL
OUTPUT_LEVEL: N/A
ID: ENG.TPL.FAMILY.DOMAIN_NARRATIVE.README
STATUS: ACTIVE
VERSION: 2.0
ROLE: Realm law + role map + interfaces + required REG/XREF + canon order for DOMAIN_NARRATIVE family.

---

## 0) PURPOSE (REALM LAW)

Этот README — закон семейства **DOMAIN_NARRATIVE_ENGINES**.
Семейство отвечает за:
- логику истории (story logic)
- структуру (story structure)
- драматургию (arc)
- построение сцен (scene construction)
- story-time pacing/rhythm (ритм истории, а не монтажа)
- напряжение/ставки, предвосхищения, твисты, непрерывность, тема/смысл

### EXISTENCE RULE (NARRATIVE)
> Любая история в проекте обязана иметь структурный “скелет” Narrative: логика → структура → арка → сцены → непрерывность.

---

## 1) FAMILY IDENTITY (MANDATORY)

FAMILY_NAME: DOMAIN_NARRATIVE_ENGINES  
FAMILY_CODE: NAR  
FAMILY_CLASS: DOMAIN  
FAMILY_LEVEL: L2  

FAMILY_PATH: `10_ENG__ENGINES/02_DOMAIN_NARRATIVE_ENGINES/`  
README_FILE: `00__README__DOMAIN_NARRATIVE_ENGINES.md`

---

## 2) OWNERSHIP BOUNDARIES (ANTI-DUPLICATION)

### 2.1 OWNS
- Story logic: причинность, правила правдоподобия истории
- Story structure: акты/фазы/узлы
- Dramatic arc: рост/повороты/разрядка (как каркас)
- Scene construction: сцена как unit истории (цель/конфликт/изменение)
- Pacing & rhythm (story-time): темп развёртывания событий в истории
- Tension & stakes: что на кону и как растёт давление
- Foreshadowing: предвосхищения
- Twist & reveal: раскрытия и перевороты
- Continuity: непрерывность истории, логические стыки
- Theme & meaning: смысловой каркас

### 2.2 DOES NOT OWN (hard boundaries)
- Expression units (Event/Cause-Effect/Conflict/Climax/Resolution) → `05_EXPRESSION_ENGINES`
- Screen-time rhythm (монтаж/тайминг кадра) → `08_KNOWLEDGE_PRODUCTION_ENGINES/07__EDITING_MONTAGE_ENG.md`
- Dialogue craft/речь/психология → `03_DOMAIN_CHARACTER_ENGINES`
- World laws/timeline epochs/civilization → `04_DOMAIN_WORLD_ENGINES` (Narrative only consumes them)
- Genre tone/atmosphere/symbolism → `06_GENRE_STYLE_ENGINES` (Narrative uses as constraints)
- Format constraints (book/series/shorts/game) → `07_PRODUCTION_FORMAT_ENGINES` (Narrative adapts to them via interfaces)

Boundary rule:
> Narrative проектирует каркас и логику, но “атомы событий” формализует EXPRESSION, а “экранный тайминг” делает PRODUCTION/EDITING.

---

## 3) ROLE MAP (MANDATORY)

- FOUNDATION — логика/структура как базовые законы истории
- BUILDER — сбор арки/сцен в черновик
- VALIDATOR — continuity, stakes coherence, foreshadowing integrity
- BRIDGE — стыки с FORMAT (книга/сериал/короткие) и WORLD timeline
- OUTPUT — сюжетный blueprint/outline/scene list

### 3.1 Canonical role map table
| Engine NN | Engine Name | ROLE_IN_FAMILY | PIPELINE_STAGE |
|---|---|---|---|
| 01 | Narrative Logic Engine | FOUNDATION | DEFINE |
| 02 | Story Structure Engine | FOUNDATION | DEFINE |
| 03 | Dramatic Arc Engine | BUILDER | BUILD |
| 04 | Scene Construction Engine | BUILDER | BUILD |
| 05 | Pacing & Rhythm Engine | VALIDATOR | CHECK |
| 06 | Tension & Stakes Engine | VALIDATOR | CHECK |
| 07 | Foreshadowing Engine | VALIDATOR | CHECK |
| 08 | Twist & Reveal Engine | BUILDER | BUILD |
| 09 | Narrative Continuity Engine | VALIDATOR | CHECK |
| 10 | Theme & Meaning Engine | BRIDGE | PACKAGE |

OUTPUT в практике:
- outline / beat sheet / scene list / arc map (L2)
- production-ready story blueprint (L3) — но без монтажа

---

## 4) FAMILY OUTPUT POLICY (WORKSHOP L0–L3) — MANDATORY

Narrative работает как по сущностям (ARC/EVT), так и по project-level “сюжетным пакетам”.

DEFAULT_PROJECT_OUTPUT_ROOT:
- `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/`

Primary categories:
- `09_ARCS/` (для арок)
- `06_EVENTS/` (если храните narrative-представление событий как сущность, но event-атомы всё равно выражаются EXPRESSION)
- Project-level narrative packs:
  - `05_PROJECT__L3/` (когда выход — “outline сезона/книги”)

Recommended routing:
- L0: зерно идеи/синопсис/сырьё
- L1: черновые структуры/варианты арки/сцены
- L2: canon outline + canon scene list + continuity map
- L3: output pack под формат (book/series/shorts/game) — без монтажа

---

## 5) REQUIRED REGISTRIES (MANDATORY)

REQUIRED_REGISTRIES (project-scoped):
- `REG.PRJ.<PROJECT_ID>.ENTITIES` (если арки/сцены/темы заведены как сущности)
- `REG.PRJ.<PROJECT_ID>.CANON_L2` (для канон-outline/arc canon)
- `REG.PRJ.<PROJECT_ID>.OUTPUT_L3` (для narrative output packs)

Rule:
> Любой L2 narrative-pack и L3 narrative output обязаны быть в REG.

---

## 6) REQUIRED XREF INDEXES (MANDATORY)

REQUIRED_XREF (project-scoped):
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__PROVENANCE.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CANON_REFS.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__DEPENDENCIES.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__ENTITY_GRAPH.md`

Narrative-specific recommended:
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__NARRATIVE_CONTINUITY.md` (optional)

Hard rule:
> Любой narrative pack обязан ссылаться на world/character/style constraints через DEPENDS_ON (в XREF).

---

## 7) INTERFACES (INPUT / OUTPUT ARTIFACT TYPES)

### 7.1 INPUT TYPES
- CORE_CARD / ENTITY_CORE (from CORE)
- WORLD_CONSTRAINTS (from WORLD)
- CHARACTER_MOTIVATION/ARC (from CHARACTER)
- FORMAT_CONSTRAINTS (from PRODUCTION_FORMAT)
- STYLE_CONSTRAINTS (from GENRE_STYLE)
- EXPRESSION_ATOMS (events/conflicts/resolutions as units) (from EXPRESSION)

### 7.2 OUTPUT TYPES
- STORY_BLUEPRINT (outline)
- BEAT_SHEET
- ARC_MAP
- SCENE_LIST
- CONTINUITY_MAP
- THEME_MAP
- FORMAT_ADAPTED_OUTLINE (for book/series/shorts/game) — still story-time

---

## 8) TEMPLATES (MANDATORY BLOCK)

Base templates:
- FAMILY README TEMPLATE (base) — `10_ENG__ENGINES/00__TEMPLATE__README__FAMILY__ENG.md`
- ENGINE TEMPLATE (base) — `10_ENG__ENGINES/00__TEMPLATE__ENGINE__ENG.md`

Family overlays:
- README TEMPLATE (this file) — `10_ENG__ENGINES/02_DOMAIN_NARRATIVE_ENGINES/00__TEMPLATE__README__DOMAIN_NARRATIVE_ENGINES.md`
- ENGINE TEMPLATE (family) — `10_ENG__ENGINES/02_DOMAIN_NARRATIVE_ENGINES/00__TEMPLATE__ENGINE__DOMAIN_NARRATIVE_ENGINES.md`

---

## 9) CANON ORDER (MANDATORY)

00 — README (Realm)  
01 — Narrative Logic Engine  
02 — Story Structure Engine  
03 — Dramatic Arc Engine  
04 — Scene Construction Engine  
05 — Pacing & Rhythm Engine  
06 — Tension & Stakes Engine  
07 — Foreshadowing Engine  
08 — Twist & Reveal Engine  
09 — Narrative Continuity Engine  
10 — Theme & Meaning Engine  

---

## 10) GOVERNANCE COMPATIBILITY (MANDATORY)

Narrative canon changes:
- требуют фиксации WHY (audit log)
- требуют обновления continuity/xref links
- не должны ломать boundary rules (event atoms остаются в EXPRESSION)

---

## FINAL RULE (LOCK)

> Narrative family задаёт каркас истории.  
> Любой narrative output обязан быть traceable (REG/XREF) и совместим с format/style/world/character constraints.

OWNER: Universe Engine  
LOCK: FIXED
