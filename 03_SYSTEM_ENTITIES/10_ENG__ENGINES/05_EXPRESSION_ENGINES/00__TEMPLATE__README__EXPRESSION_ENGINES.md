# EXPRESSION ENGINES — README TEMPLATE (ENG FAMILY) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/05_EXPRESSION_ENGINES/00__TEMPLATE__README__EXPRESSION_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: TEMPLATE
FAMILY: 05_EXPRESSION_ENGINES
CLASS: EXPRESSION (L3)
LEVEL: L3
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.EXP.TPL.README.001
OWNER: SYSTEM
ROLE: Mandatory README template for the EXPRESSION engine family. Defines boundaries, navigation rules, canonical outputs, and integration points for ORC pipelines and production layers.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Expression family README template standardized: scope, boundaries, task map, engine order, inputs/outputs, dependency rules, and S0 blockers."
- REASON: "Stop overlap with Narrative/Character/World/Production and make family usage deterministic."
- IMPACT: "Any Expression family README becomes consistent and index-readable."
- CHANGE_ID: UE.CHG.2026-01-08.EXP.TPL.README.001

---

## 0) PURPOSE (LAW)

This README defines the EXPRESSION family as:
- the canonical home for **event-mechanics primitives**
- a deterministic toolkit for “what happens” as mechanics:
  - events, causality, conflicts, turning points, climax/resolution mechanics, scheduling

It guarantees:
- strict boundaries (no meaning/psyche/world-law ownership)
- predictable input/output artifact types
- consistent navigation and engine order

---

## 1) WHAT THIS FAMILY IS (SCOPE)

EXPRESSION = mechanics layer.

It answers:
- what events exist (as mechanics)
- how events cause other events (causal links)
- where conflicts arise and how they escalate
- which events are turning points / climax / resolution (as phase mechanics)
- how events must be scheduled/ordered (constraints, not theme)

---

## 2) WHAT THIS FAMILY IS NOT (BOUNDARIES) (HARD)

This family does NOT own:
- narrative meaning/theme/structure/continuity as primary → 02_DOMAIN_NARRATIVE_ENGINES
- character identity/psyche/motivation/dialogue as primary → 03_DOMAIN_CHARACTER_ENGINES
- world laws/resources/tech/ecology as primary → 04_DOMAIN_WORLD_ENGINES
- media implementation (camera/editing/sound execution) → 08_KNOWLEDGE_PRODUCTION_ENGINES
- deep music composition/harmony/mix → 09_SOUND_MUSIC_ENGINES
- authority/pipeline/audit/memory/versioning → 00_GOVERNANCE_ENGINES
- system identity/state/lifecycle → 01_CORE_ENGINES

Rule:
- Expression can CONSUME outputs from these families, but must not redefine them.

---

## 3) TASK → ENGINE MAP (NAVIGATION BY INTENT)

Use this when you need mechanics:

A) Define atomic happenings → 01__EVENT_ENG  
B) Build causal chain/graph → 02__CAUSE_EFFECT_ENG  
C) Define opposing forces over stakes → 03__CONFLICT_ENG  
D) Locate story-state pivots (mechanically) → 04__TURNING_POINT_ENG  
E) Build peak mechanics (not theme) → 05__CLIMAX_ENG  
F) Close mechanics and stabilize state → 06__RESOLUTION_ENG  
G) System-level shocks (catastrophes, regime breaks) → 07__SYSTEM_SHOCK_ENG  
H) Scheduling / ordering constraints → 08__EVENT_SCHEDULING_ENG  
I) Controlled randomness / chaos injection → 09__RANDOMNESS_CHAOS_ENG  

---

## 4) CANON OUTPUTS (STANDARD ARTIFACTS)

Typical family outputs (engines may produce subsets):
- EVENT_LIST
- CAUSE_EFFECT_GRAPH
- CONFLICT_MODEL
- TURNING_POINT_SET
- CLIMAX_MECHANICS
- RESOLUTION_MECHANICS
- SHOCK_PROFILE
- SCHEDULE_CONSTRAINTS
- CHAOS_PARAMS

Rule:
- outputs must follow schemas defined inside each engine file.

---

## 5) DEPENDENCY RULES (STRICT)

Allowed dependency direction:
- Expression MAY depend on:
  - Narrative (structure/continuity as constraints/inputs)
  - Character (motivation/relationships as constraints/inputs)
  - World (laws/resources/tech as constraints/inputs)
- Expression MUST NOT create authority collisions by:
  - redefining narrative meaning
  - overriding world laws
  - replacing character psyche definitions

If a dependency exists:
- it must be listed in engine MINI-CONTRACT (DEPENDS_ON)
- and registered in the Dependency Registry Engine (governance)

---

## 6) ENGINE ORDER (CANON)

Order is fixed:
01 — Event
02 — Cause–Effect
03 — Conflict
04 — Turning Point
05 — Climax
06 — Resolution
07 — System Shock
08 — Event Scheduling
09 — Randomness & Chaos

Rule:
- If order changes, it is a canon change and must follow Change Control.

---

## 7) USAGE FLOW (RECOMMENDED)

Default deterministic pipeline:
1) Narrative/World/Character provide constraints (inputs)
2) Event Engine defines event atoms
3) Cause–Effect builds causal graph
4) Conflict defines opposing forces over stakes
5) Turning Point marks state pivots
6) Climax/Resolution define peak/closure mechanics
7) Scheduling constrains ordering/time windows
8) Chaos injects controlled variability (optional)

---

## 8) S0 BLOCKERS (STOP CONDITIONS)

S0-1: Any Expression engine claims ownership of theme/meaning/structure as primary  
S0-2: Any output violates declared world-law constraints without escalation  
S0-3: Any engine hides dependencies (not in MINI-CONTRACT)  
S0-4: Any engine produces undefined artifacts (no schema)  
S0-5: Duplicate “single source of truth” across families for same concept  

---

## 9) FAMILY FILES (MUST EXIST)

Inside `05_EXPRESSION_ENGINES/` the following must exist:
- 00__README__EXPRESSION_ENGINES.md (family realm/readme)
- 00__TEMPLATE__ENGINE__EXPRESSION_ENGINES.md
- 00__TEMPLATE__README__EXPRESSION_ENGINES.md
- NN__<ENGINE_NAME>_ENG.md (engines)

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)

- <raw links to family index and adjacent families>

--- END.
