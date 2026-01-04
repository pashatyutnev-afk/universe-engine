# 🎯 EVENT ENGINE
## Canonical Engine Specification  
**LEVEL: L3 · EXPRESSION ENGINE · EVENT ATOMS · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 01__EVENT_ENG.md
- ENGINE_ID: L3-EXP-EVENT-ENGINE-001
- UID: UE.ENT.ENG.EXP.EVENT
- NAME: Event Engine
- CLASS: Expression Engine
- LEVEL: L3
- STATUS: FINAL
- FAILURE_MODE: fail-closed (event integrity)
- EDITABLE: true

### ABSOLUTE RULE
> If it cannot be described as an event, it cannot drive the story.

---

## 1. PURPOSE

Event Engine defines the **atomic unit of change**: the Event.

It produces:
- EVENT_SPEC objects
- event taxonomy
- event validation rules (trigger/effect/cost)
- event payload templates for downstream engines

This engine prevents “vibes-only scenes” with no change.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define Event schema (required fields)
- Define event types and categories
- Define event validation rules
- Convert narrative seeds into event list (non-scheduling)
- Emit EVENT_SPEC_LIBRARY

### OUT-OF-SCOPE (FORBIDDEN)
- Scheduling events on timeline (Event Scheduling Engine)
- Building full cause graphs (Cause–Effect Engine)
- Writing scenes/prose
- Canon authority decisions

---

## 3. EVENT MODEL

### 3.1 Event Object — EVENT_SPEC (required fields)
- `event_id`
- `name`
- `type` = ACTION | REACTION | DISCOVERY | LOSS | GAIN | REVELATION | ARRIVAL | DEPARTURE | CHOICE | FAILURE | SUCCESS | INTERRUPTION | SACRIFICE | BETRAYAL | TRUTH_DROP
- `scope` = MICRO | SCENE | SEQUENCE | ARC
- `actors_involved` (list)
- `location_ref` (optional)
- `preconditions` (list)
- `trigger` (single cause statement)
- `effects` (list of concrete changes)
- `costs` (list: price paid)
- `stakes_impact` (what stake rises/falls)
- `reversibility` = REVERSIBLE | IRREVERSIBLE | PARTIAL
- `visibility` = PUBLIC | PRIVATE | SECRET
- `evidence` (what proves it happened)
- `dependencies` (optional: other event_ids)
- `notes`

Missing any required field → REJECT.

### 3.2 Event Quality Rules (HARD)
- Event must change at least one of:
  - state of actor
  - state of relationship
  - access to resource
  - information state
  - location/state of world
- Event must have cost OR risk OR tradeoff
- Event must be constrained by world laws/capabilities

---

## 4. INPUT ARTIFACTS

### 4.1 INPUT — EVENT_REQUEST
**REQUIRED FIELDS**
- `ev_id`
- `timestamp`
- `narrative_seed_ref` (structure/scene list seed)
- `world_package_ref` (recommended)
- `character_package_ref` (recommended)
- `constraints_refs`
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 5. OUTPUT ARTIFACTS

### 5.1 OUTPUT — EVENT_SPEC_LIBRARY
**REQUIRED FIELDS**
- `ev_id`
- `event_specs` (list of EVENT_SPEC)
- `event_taxonomy` (types + meanings)
- `validation_report` (issues + fixes)
- `trace_id` (if provided)

### 5.2 OUTPUT — EVENT_VERDICT
- `ev_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 6. CORE OPERATIONS

- OP_01: DEFINE_EVENT_SCHEMA_AND_TAXONOMY
- OP_02: EXTRACT_EVENT_CANDIDATES_FROM_SEEDS
- OP_03: ENFORCE_TRIGGER_EFFECT_COST_RULES
- OP_04: CHECK_WORLD_AND_CHARACTER_CONSTRAINTS
- OP_05: EMIT_EVENT_SPEC_LIBRARY

---

## 7. ACCESS MODEL

### WRITE
- Expression pipeline outputs only

### READ
- Cause–Effect Engine (build graph)
- Conflict Engine (events as moves)
- Turning Point Engine (events that flip trajectory)
- Scheduling Engine (place events)
- Narrative engines (scene construction)

### DELETE
- Allowed for drafts; finalization per project governance

---

## 8. DEPENDENCIES

### REQUIRED
- Narrative seed reference (structure or scene list)
- Constraints (genre realism)

### OPTIONAL
- World package (laws/capabilities)
- Character package (motives/values)

### FORBIDDEN
- Events with no trigger
- Effects that are only “emotion” with no state change
- Zero-cost major events (free miracles)
- World-law violations without explicit exception pricing

---

## 9. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- Many events missing trigger/effect/cost
- Events violate world law/capability bounds
- Events contradict character core/value constraints with no mechanism
- Event list is pure “beats” with no state changes

Reaction:
- Verdict INVALID (CRITICAL)
- Emit repair suggestions per event.

---

## 10. TRACE RULES

- trace_id optional unless orchestrator requires traced pipeline
- if present, propagate into downstream graphs and schedules

---

## 11. NON-GOALS
- Does not schedule events
- Does not explain causality beyond trigger/effect
- Does not write scenes or dialogue

---

## 12. FINAL STATEMENT

Events are the atoms of story change.
Define atoms — and motion becomes possible.

---

**STATUS:** Event Engine v1.0  
**REALM:** ACTIVE
