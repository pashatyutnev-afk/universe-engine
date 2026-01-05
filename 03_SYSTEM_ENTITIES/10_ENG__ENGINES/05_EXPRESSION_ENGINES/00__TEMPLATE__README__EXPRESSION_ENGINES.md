# ENG FAMILY README — EXPRESSION_ENGINES (TEMPLATE v2)
FILE: 00__TEMPLATE__README__EXPRESSION_ENGINES.md

SCOPE: Universe Engine
LAYER: ENG
DOC_TYPE: TEMPLATE
ENTITY_GROUP: ENGINES (ENG)
TEMPLATE_KIND: FAMILY_README_OVERLAY
LEVEL: L3
STATUS: ACTIVE
VERSION: 2.0
ROLE: Family overlay for Expression realm README. Compatible with base family template v2 and base engine template v2. Defines “expression atoms” used by Narrative and Production as building blocks.

LOCK: FIXED
OWNER: Universe Engine

---

## 0) PURPOSE (REALM LAW)

Семейство **EXPRESSION_ENGINES** — это атомы выражения истории:
- событие как факт изменения
- причинно-следственная связка как “мотор”
- конфликт как столкновение сил
- turning point как перелом
- climax как пик
- resolution как закрытие
- system shock как резкий сдвиг состояния мира/персонажа
- scheduling как “когда” в логике мира (не монтаж)
- randomness/chaos как управляемая неопределённость

EXISTENCE RULE:
> Если Narrative делает сцены, Expression даёт “механику” сцены: что произошло, почему, чем столкнулось, где перелом, чем завершилось.

---

## 1) FAMILY IDENTITY (MANDATORY)

FAMILY_NAME: EXPRESSION_ENGINES
FAMILY_CODE: EXP
FAMILY_CLASS: EXPRESSION
FAMILY_LEVEL: L3

FAMILY_PATH:
`03_SYSTEM_ENTITIES/10_ENG__ENGINES/05_EXPRESSION_ENGINES/`

README_FILE:
`00__README__EXPRESSION_ENGINES.md`

---

## 2) OWNERSHIP BOUNDARIES (ANTI-DUPLICATION)

### 2.1 OWNS
- event/beat mechanics and their structured representation
- cause-effect entries as canonical graph edges
- conflict mechanics (forces, stakes, outcomes)
- turning/climax/resolution patterns as reusable units

### 2.2 DOES NOT OWN (hard boundaries)
- story structure (acts, arcs) → 02 Narrative
- character psyche/motivation definition → 03 Character
- world law facts (physics/economy/civs) → 04 World
- screen-time montage/seconds/shot lists → 08 Production
Rule:
> Expression outputs units; Narrative composes them; Production times them.

---

## 3) ROLE MAP (MANDATORY)

- FOUNDATION: Event + Cause–Effect
- BUILDER: Conflict + Turning + Climax + Resolution + Shock
- OUTPUT: Scheduling + Chaos control patterns

### 3.1 Canonical role map table
| Engine NN | Engine Name | ROLE_IN_FAMILY | PIPELINE_STAGE |
|---|---|---|---|
| 01 | Event Engine | FOUNDATION | DEFINE |
| 02 | Cause–Effect Engine | FOUNDATION | DEFINE |
| 03 | Conflict Engine | BUILDER | BUILD |
| 04 | Turning Point Engine | BUILDER | BUILD |
| 05 | Climax Engine | BUILDER | BUILD |
| 06 | Resolution Engine | BUILDER | BUILD |
| 07 | System Shock Engine | BUILDER | BUILD |
| 08 | Event Scheduling Engine | OUTPUT | PRODUCE |
| 09 | Randomness & Chaos Engine | OUTPUT | PRODUCE |

---

## 4) FAMILY OUTPUT POLICY (WORKSHOP L0–L3) — MANDATORY

Default root:
`05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/`

Recommended storage:
- events/beats:
  `06_EVENTS/EVT_<NAME>/<LEVEL_FOLDER>/`
- conflicts:
  `06_EVENTS/CON_<NAME>/<LEVEL_FOLDER>/` (optional)
- scheduling packs:
  `06_EVENTS/SCH_<NAME>/<LEVEL_FOLDER>/` (optional)
- project-level expression library:
  `05_PROJECT__L2/<LEVEL_FOLDER>/` (if you store reusable patterns)

Rule:
> Expression artifacts are usually entity-scoped under Events. Canon ones are registered.

---

## 5) REQUIRED REGISTRIES (MANDATORY)

Project-scoped:
- `00_REG__REGISTRIES/REG.PRJ.<PROJECT_ID>.ENTITIES.md`
- `00_REG__REGISTRIES/REG.PRJ.<PROJECT_ID>.CANON_L2.md` (for canon events/atoms)
- `00_REG__REGISTRIES/REG.PRJ.<PROJECT_ID>.OUTPUT_L3.md` (if packaged)

---

## 6) REQUIRED XREF INDEXES (MANDATORY)

Project-scoped (core):
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CANON_REFS.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__DEPENDENCIES.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__PROVENANCE.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__ENTITY_GRAPH.md`

Expression-specific (mandatory):
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CAUSE_EFFECT_GRAPH.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CONFLICT_GRAPH.md` (recommended)
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__TURNING_POINTS.md` (recommended)

---

## 7) TEMPLATES (MANDATORY BLOCK)

Base templates:
- ENGINE TEMPLATE (base) — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00__TEMPLATE__ENGINE__ENG.md
- FAMILY README TEMPLATE (base) — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00__TEMPLATE__README__FAMILY__ENG.md

Family overlays:
- ENGINE TEMPLATE (family) — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/05_EXPRESSION_ENGINES/00__TEMPLATE__ENGINE__EXPRESSION_ENGINES.md
- README TEMPLATE (family) — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/05_EXPRESSION_ENGINES/00__TEMPLATE__README__EXPRESSION_ENGINES.md

---

## 8) CANON ORDER (MANDATORY)

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

## 9) GOVERNANCE COMPATIBILITY (MANDATORY)

Governance required when:
- changing canon events that are referenced by arcs/scenes
- changing cause-effect edges that propagate to multiple entities
- refactoring IDs and routing structure

---

## 10) RAW LINK (MANDATORY)

RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/05_EXPRESSION_ENGINES/00__TEMPLATE__README__EXPRESSION_ENGINES.md

---

## FINAL RULE (LOCK)

> Expression produces atomic mechanics; Narrative composes; Production times.

LOCK: FIXED
