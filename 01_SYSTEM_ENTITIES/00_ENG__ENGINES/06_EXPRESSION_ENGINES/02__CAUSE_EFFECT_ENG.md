# 🔗 CAUSE–EFFECT ENGINE
## Canonical Engine Specification  
**LEVEL: L3 · EXPRESSION ENGINE · CAUSAL GRAPH · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 02__CAUSE_EFFECT_ENG.md
- ENGINE_ID: L3-EXP-CAUSE-EFFECT-ENGINE-002
- UID: UE.ENT.ENG.EXP.CAUSE_EFFECT
- NAME: Cause–Effect Engine
- CLASS: Expression Engine
- LEVEL: L3
- STATUS: FINAL
- FAILURE_MODE: fail-closed (causal integrity)
- EDITABLE: true

### ABSOLUTE RULE
> If effects have no causes, the story becomes coincidence.

---

## 1. PURPOSE

Cause–Effect Engine builds an explicit **causality graph** from events.

It produces:
- **CAUSE_EFFECT_GRAPH** (nodes = events/states, edges = causal links)
- causal chain integrity checks
- gap detection (missing causes, missing consequences)
- loop classification (feedback vs contradiction)
- plausibility checks (world laws, costs, character constraints)

This engine prevents “because plot needs it”.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Convert EVENT_SPEC_LIBRARY into causality graph
- Define causal edge types and required semantics
- Detect missing links and orphan nodes
- Detect “deus ex” causes and coincidence clusters
- Detect broken chains (cause without effect, effect without cause)
- Emit repair suggestions (add event, revise trigger, price exception)

### OUT-OF-SCOPE (FORBIDDEN)
- Scheduling events in time (Event Scheduling Engine)
- Defining conflicts (Conflict Engine)
- Writing scenes/prose
- Canon authority decisions

---

## 3. CAUSAL MODEL

### 3.1 Graph Object — CAUSE_EFFECT_GRAPH (required fields)
- `ceg_id`
- `nodes` (events + optional state nodes)
- `edges` (causal links)
- `entry_points` (root causes)
- `terminal_points` (final consequences)
- `gaps` (missing causes/effects)
- `loops` (classified)
- `integrity_report` (summary + severity)
- `trace_id` (optional)

### 3.2 Node Types
- EVENT_NODE: reference to `event_id`
- STATE_NODE: explicit state variable (optional)  
  Examples: `trust(A,B)=2`, `resource_X=low`, `location=Zone_7`

### 3.3 Edge Types (fixed)
- DIRECT: A causes B directly
- INDIRECT: A enables conditions for B
- ESCALATION: A raises stakes → B becomes forced
- REACTION: B is a reaction to A by actor intent
- REVEAL: A provides information enabling B
- RESOURCE: A changes resource → B happens
- CONSTRAINT: A removes/creates constraint → B happens

### 3.4 Edge Required Fields
- `edge_id`
- `from_node_id`
- `to_node_id`
- `edge_type`
- `mechanism` (one sentence: how exactly it causes)
- `cost_transfer` (what cost/risk propagates)
- `world_law_alignment` = OK | VIOLATION | EXCEPTION_PRICED
- `character_alignment` = OK | TENSION | CONTRADICTION

Missing any required field → REJECT.

---

## 4. CAUSAL INTEGRITY RULES (HARD)

- Every non-root event must have at least one incoming causal edge.
- Every major event (scope ≥ SCENE) must have at least one outgoing consequence edge.
- Coincidence allowance is bounded:
  - max 1 “pure coincidence” per arc unless genre explicitly allows.
- If world law is violated:
  - must be marked EXCEPTION_PRICED and include explicit cost + counter-risk.
- Character intent must exist for REACTION edges:
  - reference motivation/value constraints (conceptually).

---

## 5. INPUT ARTIFACTS

### 5.1 INPUT — CAUSE_EFFECT_REQUEST
**REQUIRED FIELDS**
- `ce_id`
- `timestamp`
- `event_spec_library_ref` (required)
- `world_package_ref` (recommended)
- `character_package_ref` (recommended)
- `constraints_refs` (required)
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 6. OUTPUT ARTIFACTS

### 6.1 OUTPUT — CAUSE_EFFECT_GRAPH
(see model above)

### 6.2 OUTPUT — CAUSE_EFFECT_VERDICT
- `ce_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 7. CORE OPERATIONS

- OP_01: INGEST_EVENT_SPEC_LIBRARY
- OP_02: IDENTIFY_ROOT_AND_TERMINAL_POINTS
- OP_03: BUILD_INITIAL_CAUSAL_EDGES (trigger→effect mapping)
- OP_04: CLASSIFY_EDGE_TYPES_AND_MECHANISMS
- OP_05: DETECT_GAPS_ORPHANS_AND_COINCIDENCE_CLUSTERS
- OP_06: CHECK_WORLD_AND_CHARACTER_ALIGNMENT
- OP_07: CLASSIFY_LOOPS_AND_FEEDBACKS
- OP_08: EMIT_CAUSE_EFFECT_GRAPH

---

## 8. LOOP CLASSIFICATION (HARD)

Loops are allowed only if classified:
- FEEDBACK_LOOP: A worsens/helps conditions → B → reinforces A (allowed)
- DEADLOCK_LOOP: A prevents B and B prevents A (allowed but must be story-relevant)
- CONTRADICTION_LOOP: A causes not-A (INVALID unless paradox genre + priced)

Any CONTRADICTION_LOOP → FAIL unless explicitly permitted and priced.

---

## 9. DEPENDENCIES

### REQUIRED
- Event Spec Library
- Constraints refs

### OPTIONAL
- World package (laws/capabilities)
- Character package (intent constraints)

### FORBIDDEN
- Causal edges without mechanism
- “Because fate” as mechanism unless genre permits and it is priced as a world rule
- Unbounded coincidence clusters

---

## 10. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- Many orphan events (no incoming cause)
- Major events have no consequences
- Coincidence cluster exceeds allowed threshold
- World law violations not priced
- Reaction edges contradict character constraints without bridge event

Reaction:
- Verdict INVALID (CRITICAL)
- Emit repair plan:
  - add missing bridge events
  - revise triggers/effects
  - price exceptions
  - reroute consequences

---

## 11. TRACE RULES

- trace_id optional unless pipeline requires traced execution
- if present, propagate into conflict/turning-point maps and schedules

---

## 12. NON-GOALS
- Does not schedule time
- Does not decide stakes (Tension & Stakes Engine owns stakes)
- Does not write scenes

---

## 13. FINAL STATEMENT

Causality is story gravity.
Build the graph — and the world stops floating.

---

**STATUS:** Cause–Effect Engine v1.0  
**REALM:** ACTIVE
