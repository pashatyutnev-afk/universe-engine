# DOMAIN WORLD ENGINES — REALM README TEMPLATE (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/04_DOMAIN_WORLD_ENGINES/00__TEMPLATE__README__DOMAIN_WORLD_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: TEMPLATE
FAMILY: 04_DOMAIN_WORLD_ENGINES
CLASS: DOMAIN (L2)
LEVEL: L2
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.DOM.WORLD.TPL.README.001
OWNER: SYSTEM
ROLE: Mandatory template for the family realm README. Defines boundaries, ownership, allowed outputs, navigation rules, and the canonical engine order for world-domain engines.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "World family realm template fixed: scope boundaries, ownership map, output contracts, navigation + anti-duplication rules."
- REASON: "Stop collisions with Narrative/Character/Expression/Production and prevent mixed authority."
- IMPACT: "World engines become predictable, composable and index-friendly."
- CHANGE_ID: UE.CHG.2026-01-08.DOM.WORLD.TPL.README.001

---

## 0) PURPOSE (LAW)

This README defines the **realm** of `04_DOMAIN_WORLD_ENGINES`:
- what this family **owns**
- what this family **must not** own
- the **engine order** and how to navigate it
- the **output contract style** expected from every engine in the family

Existence rule reminder:
- If an engine is not registered in `02__INDEX_ALL_ENGINES.md` → it does not exist for the system.

---

## 1) WHAT THIS FAMILY IS (OWNER DEFINITION)

**Domain World Engines** own the construction and maintenance of:
- world structure, world laws, constraints
- epochs/timelines as *world-state*, not story beats
- civilizations, factions-at-scale, geopolitics
- resources, economy (as world mechanics, not currency system if forbidden in canon)
- technology/magic systems (as rules, constraints, capabilities)
- mythology/belief systems (as world framework)
- environment/ecology (as living rules, survival constraints)

Primary output: **WORLD MODELS + WORLD RULESETS** that other layers consume.

---

## 2) HARD BOUNDARIES (ANTI-DUPLICATION)

This family MUST NOT own:

### 2.1 CORE ownership (system identity)
- system identity/state/lifecycle → `01_CORE_ENGINES/*`

### 2.2 GOVERNANCE ownership (authority + pipeline)
- canon authority, approvals, audits, dependency registry, change pipeline → `00_GOVERNANCE_ENGINES/*`

### 2.3 NARRATIVE ownership (story as primary)
- plot structure, arcs, foreshadowing, twists, narrative continuity as story-law  
→ `02_DOMAIN_NARRATIVE_ENGINES/*`

### 2.4 CHARACTER ownership (psychology/behavior)
- motivation, morality, dialogue, speech naturalization, trauma/growth  
→ `03_DOMAIN_CHARACTER_ENGINES/*`

### 2.5 EXPRESSION ownership (event primitives)
- event/cause-effect/conflict/turning point/climax/resolution primitives  
→ `05_EXPRESSION_ENGINES/*`

### 2.6 PRODUCTION ownership (media execution)
- camera/editing/lighting/generation/sound placement as production layer  
→ `08_KNOWLEDGE_PRODUCTION_ENGINES/*` and `09_SOUND_MUSIC_ENGINES/*`

Collision rule:
- If a file overlaps: it must declare the owner family/engine and route work there.

---

## 3) WHAT “WORLD” MEANS HERE (OPERATIONAL)

World-domain = **constraints + affordances**:
- constraints: what cannot happen / limits
- affordances: what can happen / capabilities
- stable invariants: what must remain consistent
- state model: what changes over time as world state (not plot)

---

## 4) FAMILY OUTPUT CONTRACT (MANDATORY)

Every engine in this family MUST:
- include MINI-CONTRACT with **concrete artifact names**
- define **output schema** (fields + validation)
- declare **boundaries** explicitly
- include **S0 blockers** (stop conditions)

Recommended artifact categories produced by this family:
- WORLD_STRUCTURE_MODEL
- WORLD_LAWSET
- TIMELINE_EPOCH_MODEL (world-state timeline)
- CIVILIZATION_MODEL
- GEOPOLITICS_MODEL
- ECONOMY_RESOURCE_MODEL (resource logic; no currency if canon forbids it)
- TECHNOLOGY_MAGIC_MODEL
- MYTHOLOGY_BELIEF_MODEL
- ENVIRONMENT_ECOLOGY_MODEL

---

## 5) NAVIGATION RULES (HOW TO USE)

1) Start from the lowest-level structural invariants:
   - World Structure → World Law
2) Only then move to systems:
   - Timeline/Epoch → Civilization → Conflict/Power → Geopolitics
3) Then “deep layers”:
   - Economy/Resource → Technology/Magic → Mythology/Belief → Environment/Ecology
4) If you create a new engine:
   - register in `02__INDEX_ALL_ENGINES.md` first
   - then create file using the family engine template
   - then add dependencies to dependency registry if needed

---

## 6) ENGINE ORDER (CANON LIST SKELETON)

IMPORTANT:
- Order is canonical and must match `02__INDEX_ALL_ENGINES.md`.
- Numbers must match file names.

01 — World Structure Engine — `01__WORLD_STRUCTURE_ENG.md`  
02 — World Law Engine — `02__WORLD_LAW_ENG.md`  
03 — Timeline & Epoch Engine — `03__TIMELINE_EPOCH_ENG.md`  
04 — Civilization Engine — `04__CIVILIZATION_ENG.md`  
05 — Conflict & Power Engine — `05__CONFLICT_POWER_ENG.md`  
06 — Geopolitics Engine — `06__GEOPOLITICS_ENG.md`  
07 — Economy & Resource Engine — `07__ECONOMY_RESOURCE_ENG.md`  
08 — Technology & Magic Engine — `08__TECHNOLOGY_MAGIC_ENG.md`  
09 — Mythology & Belief Engine — `09__MYTHOLOGY_BELIEF_ENG.md`  
10 — Environment & Ecology Engine — `10__ENVIRONMENT_ECOLOGY_ENG.md`

---

## 7) REQUIRED TEMPLATES (RAW LINKS IN INDEX)

This family uses:
- ENGINE TEMPLATE: `00__TEMPLATE__ENGINE__DOMAIN_WORLD_ENGINES.md`
- README TEMPLATE: `00__TEMPLATE__README__DOMAIN_WORLD_ENGINES.md`

Rule:
- Index must reference these templates via raw-links.

---

## 8) DEPENDENCY PATTERNS (RECOMMENDED)

Typical dependencies:
- CORE prerequisites:
  - Core Identity / Core State (if referencing entity types, system state invariants)
- GOVERNANCE prerequisites:
  - Change Control / Consistency / Dependency Registry (for canon changes)

Forbidden dependency pattern:
- World engines must not depend on narrative engines “to define world rules”.
Narrative may consume world rules, not the opposite (unless explicitly tiered and justified).

---

## 9) S0 BLOCKERS (FAMILY LEVEL)

- S0-1: Any engine redefines ownership already owned by another family.
- S0-2: Any engine produces outputs without schema + validation.
- S0-3: Any engine introduces currency/finance primitives if canon forbids currency.
- S0-4: Engine numbers in file names mismatch index ordering.
- S0-5: Missing mini-contract.

---

## 10) QUICK CHECKLIST (BEFORE ACTIVE)

- [ ] Header schema correct
- [ ] Boundaries explicit
- [ ] Mini-contract concrete
- [ ] Output schemas defined
- [ ] S0 blockers present
- [ ] References are raw-only where required by index

--- END.
