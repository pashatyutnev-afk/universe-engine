# ENG FAMILY README — DOMAIN_NARRATIVE_ENGINES (TEMPLATE v2)
FILE: 00__TEMPLATE__README__DOMAIN_NARRATIVE_ENGINES.md

SCOPE: Universe Engine
LAYER: ENG
DOC_TYPE: TEMPLATE
ENTITY_GROUP: ENGINES (ENG)
TEMPLATE_KIND: FAMILY_README_OVERLAY
LEVEL: L2
STATUS: ACTIVE
VERSION: 2.0
ROLE: Family overlay for Narrative (Domain) realm README. Compatible with base family template v2 and base engine template v2. Defines narrative canon boundaries and required xref graphs.

LOCK: FIXED
OWNER: Universe Engine

---

## 0) PURPOSE (REALM LAW)

Семейство **DOMAIN_NARRATIVE_ENGINES** отвечает за сюжетную логику и структуру:
- логика повествования (narrative logic)
- структура истории (acts/beats)
- драматическая дуга
- конструирование сцен
- темп/ритм (story-time, не монтаж)
- напряжение/ставки
- предвосхищения
- повороты/раскрытия
- непрерывность (continuity)
- тема/смысл

EXISTENCE RULE:
> Любой сюжетный канон (L2) должен иметь: structure → arc → scenes → continuity → theme links.

---

## 1) FAMILY IDENTITY (MANDATORY)

FAMILY_NAME: DOMAIN_NARRATIVE_ENGINES
FAMILY_CODE: NAR
FAMILY_CLASS: DOMAIN
FAMILY_LEVEL: L2

FAMILY_PATH:
`03_SYSTEM_ENTITIES/10_ENG__ENGINES/02_DOMAIN_NARRATIVE_ENGINES/`

README_FILE:
`00__README__DOMAIN_NARRATIVE_ENGINES.md`

---

## 2) OWNERSHIP BOUNDARIES (ANTI-DUPLICATION)

### 2.1 OWNS
- story-time structure and logic (acts/beats/scenes as narrative units)
- dramatic arc as story meaning progression
- narrative continuity and canon coherence inside story
- pacing & rhythm in story-time terms (not seconds of screen)
- theme and meaning as narrative law

### 2.2 DOES NOT OWN (hard boundaries)
- screen-time rhythm / edit timing / montage → 08 Production Editing
- visual style and atmosphere rules → 06 Style
- character psychology and speech patterns → 03 Character (but narrative can reference them)
- world laws and economics → 04 World (but narrative can depend on them)
- music placement/sync → 08 Production; music as work → 09 Music
Rule:
> Narrative defines story logic, not production timing.

---

## 3) ROLE MAP (MANDATORY)

- FOUNDATION: logic/structure/arc
- BUILDER: scenes/pacing/tension/foreshadow/twist
- VALIDATOR: continuity/theme coherence
- OUTPUT: canon scene packs / arc packs / story bible parts

### 3.1 Canonical role map table
| Engine NN | Engine Name | ROLE_IN_FAMILY | PIPELINE_STAGE |
|---|---|---|---|
| 01 | Narrative Logic Engine | FOUNDATION | DEFINE |
| 02 | Story Structure Engine | FOUNDATION | DEFINE |
| 03 | Dramatic Arc Engine | FOUNDATION | DEFINE |
| 04 | Scene Construction Engine | BUILDER | BUILD |
| 05 | Pacing & Rhythm Engine | BUILDER | BUILD |
| 06 | Tension & Stakes Engine | BUILDER | BUILD |
| 07 | Foreshadowing Engine | BUILDER | BUILD |
| 08 | Twist & Reveal Engine | BUILDER | BUILD |
| 09 | Narrative Continuity Engine | VALIDATOR | CHECK |
| 10 | Theme & Meaning Engine | VALIDATOR | CHECK |

---

## 4) FAMILY OUTPUT POLICY (WORKSHOP L0–L3) — MANDATORY

Default roots:
`05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/`

Recommended domain folders (choose what fits your project):
- `06_EVENTS/` (events + beats)
- `09_ARCS/` (arcs)
- `03_OBJECTS/` (plot objects if needed)
- `07_CONCEPTS/` (themes, premises)
- `05_FACTIONS/` (if politics are story-critical)
- `05_PROJECT__L2/` (story bible / narrative canon packs)

Entity scope examples:
- `06_EVENTS/EVT_<NAME>/03_CANON_L2/`
- `09_ARCS/ARC_<NAME>/03_CANON_L2/`

Project scope examples:
- `05_PROJECT__L2/03_CANON_L2/` (Story Bible)

Rule:
> Narrative L2 canon must be stored in entity or project scope (not system scope).

---

## 5) REQUIRED REGISTRIES (MANDATORY)

Project-scoped:
- `00_REG__REGISTRIES/REG.PRJ.<PROJECT_ID>.ENTITIES.md`
- `00_REG__REGISTRIES/REG.PRJ.<PROJECT_ID>.CANON_L2.md`
- `00_REG__REGISTRIES/REG.PRJ.<PROJECT_ID>.OUTPUT_L3.md` (if narrative outputs are packaged)

---

## 6) REQUIRED XREF INDEXES (MANDATORY)

Project-scoped (core):
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CANON_REFS.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__DEPENDENCIES.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__PROVENANCE.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__ENTITY_GRAPH.md`

Narrative-specific (mandatory for story logic):
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CAUSE_EFFECT_GRAPH.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__ARC_GRAPH.md` (optional but recommended)
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__SCENE_GRAPH.md` (optional but recommended)

Rule:
> Cause-effect is mandatory for any narrative canon beyond a single scene.

---

## 7) TEMPLATES (MANDATORY BLOCK)

Base templates:
- ENGINE TEMPLATE (base) — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00__TEMPLATE__ENGINE__ENG.md
- FAMILY README TEMPLATE (base) — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00__TEMPLATE__README__FAMILY__ENG.md

Family overlays:
- ENGINE TEMPLATE (family) — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/02_DOMAIN_NARRATIVE_ENGINES/00__TEMPLATE__ENGINE__DOMAIN_NARRATIVE_ENGINES.md
- README TEMPLATE (family) — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/02_DOMAIN_NARRATIVE_ENGINES/00__TEMPLATE__README__DOMAIN_NARRATIVE_ENGINES.md

---

## 8) CANON ORDER (MANDATORY)

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

## 9) GOVERNANCE COMPATIBILITY (MANDATORY)

Narrative L2 canon changes must pass governance pipeline when:
- they modify locked canon
- they create/alter major arcs that affect multiple entities
- they require migrations (renaming/structural refactors)

---

## 10) RAW LINK (MANDATORY)

RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/02_DOMAIN_NARRATIVE_ENGINES/00__TEMPLATE__README__DOMAIN_NARRATIVE_ENGINES.md

---

## FINAL RULE (LOCK)

> Narrative defines story-time logic. Screen-time belongs to production editing.

LOCK: FIXED
