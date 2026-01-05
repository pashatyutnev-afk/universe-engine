# ENG FAMILY README — EXPRESSION_ENGINES (TEMPLATE v2)
FILE: 00__TEMPLATE__README__EXPRESSION_ENGINES.md

SCOPE: Universe Engine
LAYER: ENG
DOC_TYPE: TEMPLATE
ENTITY_KIND: EXP
PROJECT_SCOPE: GLOBAL
OUTPUT_LEVEL: N/A
ID: ENG.TPL.FAMILY.EXPRESSION.README
STATUS: ACTIVE
VERSION: 2.0
ROLE: Realm law + role map + interfaces + required REG/XREF + canon order for EXPRESSION family.

---

## 0) PURPOSE (REALM LAW)

Этот README — закон семейства **EXPRESSION_ENGINES**.
Семейство отвечает за “атомы выражения” — минимальные блоки из которых строится история:
- событие (Event)
- причина–следствие (Cause–Effect)
- конфликт (Conflict)
- поворот (Turning Point)
- кульминация (Climax)
- развязка (Resolution)
- системный шок (System Shock)
- расписание/тайминг событий как логика мира (не монтаж)
- случайность/хаос как управляемый фактор

### EXISTENCE RULE (EXPRESSION)
> Любая сцена/арка/история обязана быть выражаемой через атомы Expression.  
> Если нельзя выразить через Event/Cause-Effect/Conflict/TP/Climax/Resolution — структура невалидна.

---

## 1) FAMILY IDENTITY (MANDATORY)

FAMILY_NAME: EXPRESSION_ENGINES  
FAMILY_CODE: EXP  
FAMILY_CLASS: EXPRESSION  
FAMILY_LEVEL: L3  

FAMILY_PATH: `10_ENG__ENGINES/05_EXPRESSION_ENGINES/`  
README_FILE: `00__README__EXPRESSION_ENGINES.md`

---

## 2) OWNERSHIP BOUNDARIES (ANTI-DUPLICATION)

### 2.1 OWNS
- Формализация атомов истории:
  - Event unit (что произошло)
  - Cause–Effect links (почему и что вызвало)
  - Conflict unit (столкновение сил/интересов)
  - Turning point (перелом)
  - Climax (пиковая точка)
  - Resolution (разрядка/итог)
  - System shock (внешний удар по системе)
  - Event scheduling (когда/в каком порядке это должно наступать по логике мира/сюжета)
  - Randomness & chaos (контролируемая неопределённость)

### 2.2 DOES NOT OWN (hard boundaries)
- Каркас истории (акты/арки/сцены как последовательность) → Narrative
- Ритм истории как темп развёртывания (story-time pacing) → Narrative (05 engine там)
- Экранный тайминг/секунды/монтаж/паузы → 08 Editing & Montage
- Диалог/психология персонажей → Character
- Законы мира/эпохи → World (Expression может только стресс-тестить)
- Стиль/атмосфера/символизм → Genre/Style
- Governance change control → Governance

Boundary rule:
> Expression “даёт кирпичи”, Narrative “строит дом”, Production “снимает и монтирует”.

---

## 3) ROLE MAP (MANDATORY)

- FOUNDATION — Event + Cause-Effect (основа выразимости)
- BUILDER — Conflict/Turning point/Climax/Resolution как сборка динамики
- VALIDATOR — проверка причинности/согласованности/схемы атомов
- BRIDGE — event scheduling и системный шок как мост к world timeline
- OUTPUT — atom packs (наборы атомов под арку/сцену)

### 3.1 Canonical role map table
| Engine NN | Engine Name | ROLE_IN_FAMILY | PIPELINE_STAGE |
|---|---|---|---|
| 01 | Event Engine | FOUNDATION | DEFINE |
| 02 | Cause–Effect Engine | FOUNDATION | DEFINE |
| 03 | Conflict Engine | BUILDER | BUILD |
| 04 | Turning Point Engine | BUILDER | BUILD |
| 05 | Climax Engine | BUILDER | BUILD |
| 06 | Resolution Engine | BUILDER | BUILD |
| 07 | System Shock Engine | BRIDGE | PACKAGE |
| 08 | Event Scheduling Engine | BRIDGE | PACKAGE |
| 09 | Randomness & Chaos Engine | VALIDATOR | CHECK |

---

## 4) EXPRESSION ATOM STANDARD (MANDATORY)

Каждый atom (event/conflict/etc.) обязан иметь:
- ATOM_ID
- ATOM_TYPE
- SUBJECTS (who/what)
- CONTEXT (where/when in-story)
- TRIGGER (why it starts)
- PRESSURE (what grows)
- CHANGE (what changes after)
- CONSEQUENCES (links)
- DEPENDS_ON (constraints: world/character/narrative)
- CANON_LEVEL (L1/L2)
- REFERENCES (XREF pointers)

Rule:
> Atom без CHANGE + CONSEQUENCES считается “описанием”, а не atom.

---

## 5) FAMILY OUTPUT POLICY (WORKSHOP L0–L3) — MANDATORY

DEFAULT_PROJECT_OUTPUT_ROOT:
- `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/`

Primary categories:
- `06_EVENTS/EVT_<NAME>/` (если события заведены как сущности)
- `09_ARCS/ARC_<NAME>/` (атомы могут лежать рядом с аркой как пакеты)
- Project packs:
  - `05_PROJECT__L3/`

Recommended:
- L0: raw atoms наброски
- L1: formalized atoms drafts
- L2: canon atom packs (утверждённые)
- L3: output atom packs для production/narrative consumption

Hard rule:
> Event Scheduling описывает “когда по логике”, но не секунды монтажа.

---

## 6) REQUIRED REGISTRIES (MANDATORY)

REQUIRED_REGISTRIES (project-scoped):
- `REG.PRJ.<PROJECT_ID>.ENTITIES` (если events как сущности)
- `REG.PRJ.<PROJECT_ID>.CANON_L2` (canon atom packs)
- `REG.PRJ.<PROJECT_ID>.OUTPUT_L3` (atom packs outputs)

---

## 7) REQUIRED XREF INDEXES (MANDATORY)

REQUIRED_XREF (project-scoped):
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__DEPENDENCIES.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__PROVENANCE.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CANON_REFS.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__ENTITY_GRAPH.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CAUSE_EFFECT_GRAPH.md` (recommended)
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CONFLICTS.md` (for contradictions)

Hard rule:
> Cause–Effect связи должны быть отражены в XREF__CAUSE_EFFECT_GRAPH, не только в тексте.

---

## 8) INTERFACES (INPUT / OUTPUT ARTIFACT TYPES)

### 8.1 INPUT TYPES
- WORLD_CONSTRAINTS (laws/timeline)
- CHARACTER_CONSTRAINTS (motives/limits)
- NARRATIVE_REQUIREMENTS (what arc/scene needs)
- STYLE_CONSTRAINTS (presentation constraint)
- existing atoms drafts/canon

### 8.2 OUTPUT TYPES
- EVENT_ATOM
- CAUSE_EFFECT_LINK_SET
- CONFLICT_ATOM
- TURNING_POINT_ATOM
- CLIMAX_ATOM
- RESOLUTION_ATOM
- SYSTEM_SHOCK_ATOM
- EVENT_SCHEDULE (story logic)
- RANDOMNESS_PROFILE
- ATOM_PACK (bundle for arc/scene)

---

## 9) TEMPLATES (MANDATORY BLOCK)

Base templates:
- FAMILY README TEMPLATE (base) — `10_ENG__ENGINES/00__TEMPLATE__README__FAMILY__ENG.md`
- ENGINE TEMPLATE (base) — `10_ENG__ENGINES/00__TEMPLATE__ENGINE__ENG.md`

Family overlays:
- README TEMPLATE (this file) — `10_ENG__ENGINES/05_EXPRESSION_ENGINES/00__TEMPLATE__README__EXPRESSION_ENGINES.md`
- ENGINE TEMPLATE (family) — `10_ENG__ENGINES/05_EXPRESSION_ENGINES/00__TEMPLATE__ENGINE__EXPRESSION_ENGINES.md`

---

## 10) CANON ORDER (MANDATORY)

00 — README (Realm)  
01 — Event Engine  
02 — Cause–Effect Engine  
03 — Conflict Engine  
04 — Turning Point Engine  
05 — Climax Engine  
06 — Resolution Engine  
07 — System Shock Engine  
08 — Event Scheduling Engine  
09 — Randomness & Chaos Engine  

---

## 11) GOVERNANCE COMPATIBILITY (MANDATORY)

Canon atom rules changes:
- через governance pipeline (WHY)
- conflicts фиксируются в XREF__CONFLICTS
- cause-effect graph обновляется

---

## FINAL RULE (LOCK)

> Expression — атомы истории.  
> Narrative строит каркас из этих атомов.  
> Production определяет экранное время и монтаж.

OWNER: Universe Engine  
LOCK: FIXED
