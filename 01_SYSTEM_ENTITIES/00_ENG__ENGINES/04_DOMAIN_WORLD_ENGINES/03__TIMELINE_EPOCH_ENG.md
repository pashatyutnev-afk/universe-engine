# ⏳ TIMELINE & EPOCH ENGINE
## Canonical Engine Specification  
**LEVEL: L2 · DOMAIN ENGINE · HISTORY SEGMENTATION · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 03__TIMELINE_EPOCH_ENG.md
- ENGINE_ID: L2-DOM-TIMELINE-EPOCH-ENGINE-003
- UID: UE.ENT.ENG.DOM.WORLD.TIMELINE_EPOCH
- NAME: Timeline & Epoch Engine
- CLASS: Domain Engine
- DOMAIN: World
- CATEGORY: Epochs, Event Registry, Causality Anchors & Retcon Flags
- LEVEL: L2
- STATUS: FINAL
- FAILURE_MODE: fail-closed (for continuity)
- EDITABLE: true
- BYPASS_ALLOWED: false (within world pipeline)

### ABSOLUTE RULE
> If time is undefined, cause and effect cannot be trusted.

---

## 1. PURPOSE

Timeline & Epoch Engine defines **how the world’s history is structured**.

It produces:
- **EPOCH_MAP** (segmented eras)
- **EVENT_REGISTRY** (key events with causality links)
- **TIMELINE_MODEL** (ordered, constrained time model)

It guarantees:
- explicit “before/after” anchors
- causality integrity (events have reasons and consequences)
- prevention of silent retcons (history changes must be flagged)
- space-time alignment (events reference places where relevant)

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define timeline scale (years, cycles, generations, etc.)
- Segment history into epochs with clear boundaries
- Register canonical-ish world events (domain-level; non-canon unless approved)
- Define causal chains (event → consequences)
- Define uncertainty zones (unknown periods) explicitly
- Define time constraints (travel time, communication delays alignment)
- Detect continuity breaks and propose repair suggestions
- Flag retcons and require governance handling if promoted to canon

### OUT-OF-SCOPE (FORBIDDEN)
- Defining geography/topology (World Structure Engine)
- Defining laws of physics/magic (World Law Engine)
- Deep culture/institutions (Civilization Engine)
- Canon authority decisions (Governance)

---

## 3. TIMELINE MODEL

### 3.1 Core Objects
- TIME_AXIS: unit system (years/cycles/eras)
- EPOCH: named segment with start/end markers
- EVENT: occurrence with timestamp/era placement
- CAUSAL_LINK: event A causes event B (direct/indirect)
- UNCERTAINTY_ZONE: unknown/contested period
- RETCON_FLAG: revision without bridge (requires governance if used as canon)

### 3.2 Epoch Fields (required)
- `epoch_id`
- `name`
- `start_marker`
- `end_marker`
- `defining_features`
- `dominant_powers` (optional)
- `tech_magic_level` (optional)
- `stability` = STABLE | UNSTABLE | COLLAPSE

### 3.3 Event Fields (required)
- `event_id`
- `name`
- `epoch_id`
- `time_marker` (relative or absolute)
- `location_ref` (optional)
- `actors` (optional)
- `cause_summary`
- `consequence_summary`
- `severity` = LOW | MEDIUM | HIGH | WORLD_SHIFT
- `evidence_level` = CONFIRMED | PLAUSIBLE | LEGEND | UNKNOWN
- `links` (causal links to other events)

---

## 4. INPUT ARTIFACTS

### 4.1 INPUT — TIMELINE_REQUEST
**REQUIRED FIELDS**
- `tl_id`
- `timestamp`
- `world_scope_ref`
- `world_structure_graph_ref` (recommended)
- `world_lawset_ref` (recommended)
- `known_history_seed` (one paragraph or list)
- `time_scale` (years/cycles/etc.)
- `constraints_refs` (project/genre constraints)
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 5. OUTPUT ARTIFACTS

### 5.1 OUTPUT — TIMELINE_MODEL
**REQUIRED FIELDS**
- `tl_id`
- `time_axis` (unit + calibration notes)
- `epoch_map` (list of Epochs)
- `event_registry` (list of Events)
- `causal_graph` (list of links: {from_event, to_event, type, strength})
- `uncertainty_zones` (list)
- `continuity_checks` (auto-detected inconsistencies)
- `retcon_flags` (if any)
- `anchor_points` (few “fixed pillars” of history)
- `trace_id` (if provided)

### 5.2 OUTPUT — TIMELINE_VERDICT
- `tl_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 6. CORE OPERATIONS

- OP_01: DEFINE_TIME_AXIS_AND_SCALE
- OP_02: SEGMENT_EPOCHS
- OP_03: REGISTER_EVENTS
- OP_04: BUILD_CAUSAL_GRAPH
- OP_05: DEFINE_UNCERTAINTY_ZONES
- OP_06: RUN_CONTINUITY_AND_RETCON_CHECKS
- OP_07: EMIT_TIMELINE_MODEL

---

## 7. ACCESS MODEL

### WRITE
- Domain pipeline outputs only

### READ
- Civilization Engine (institutions evolve across epochs)
- Geopolitics Engine (actor history)
- Conflict & Power Engine (wars/shift events)
- Mythology & Belief Engine (legend vs confirmed layering)
- Narrative Continuity Engine (story events align to time)
- Validation engines (historical plausibility checks)

### DELETE
- Allowed for drafts; finalization per project governance

---

## 8. DEPENDENCIES

### REQUIRED
- World scope reference
- Project constraints (scope, realism)

### FORBIDDEN
- Events with no causes and no consequences (dead history)
- Epochs with no boundaries (blurred eras)
- Retcons without flags/bridges
- Treating timeline model as canon authority

---

## 9. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- No epochs (history unstructured)
- Events exist but no causal links (no reason-chain)
- Contradictions with world laws (impossible events) without exception pricing
- Time axis undefined (no unit model)
- Retcon flags present with no repair suggestions

Reaction:
- Verdict INVALID (CRITICAL)
- Provide repairs: define epochs, add anchors, link causes/consequences, flag retcons.

---

## 10. TRACE RULES

- trace_id optional unless orchestrator requires traced pipeline
- if present, propagate into continuity records

---

## 11. NON-GOALS
- Does not write story plot
- Does not define geography or physics
- Does not grant canon authority

---

## 12. FINAL STATEMENT

History is a chain.
Break the chain, and the world becomes a dream.

---

**STATUS:** Timeline & Epoch Engine v1.0  
**DOMAIN:** ACTIVE
