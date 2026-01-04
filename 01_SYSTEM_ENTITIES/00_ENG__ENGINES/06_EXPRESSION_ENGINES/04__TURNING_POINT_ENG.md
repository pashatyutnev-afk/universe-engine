# 🔥 TURNING POINT ENGINE
## Canonical Engine Specification  
**LEVEL: L3 · EXPRESSION ENGINE · TRAJECTORY FLIPS · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 04__TURNING_POINT_ENG.md
- ENGINE_ID: L3-EXP-TURNING-POINT-ENGINE-004
- UID: UE.ENT.ENG.EXP.TURNING_POINT
- NAME: Turning Point Engine
- CLASS: Expression Engine
- LEVEL: L3
- STATUS: FINAL
- FAILURE_MODE: fail-closed (trajectory integrity)
- EDITABLE: true

### ABSOLUTE RULE
> If nothing changes direction, it was not a turning point — it was a moment.

---

## 1. PURPOSE

Turning Point Engine identifies and formalizes **trajectory flips**.

It produces:
- **TURNING_POINT_MAP** (turning points with before/after states)
- pivot classification (reversal, revelation, sacrifice, betrayal, collapse)
- irreversibility flags
- escalation pivots (conflicts change phase)
- promise-payoff alignment hooks (for climax/resolution)

This engine ensures story motion is segmented by true direction changes.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define turning point schema
- Extract turning points from conflicts + causality graph
- Formalize before/after world/character/conflict states
- Tag irreversibility and escalation impacts
- Validate turning points are causally supported (no teleport pivots)
- Emit Turning Point Map for climax/resolution engines

### OUT-OF-SCOPE (FORBIDDEN)
- Choosing climax payoff (Climax Engine)
- Resolving arcs (Resolution Engine)
- Scheduling events (Scheduling Engine)
- Writing scenes/prose
- Canon authority decisions

---

## 3. TURNING POINT MODEL

### 3.1 Turning Point Object — TURNING_POINT_SPEC (required fields)
- `tp_id`
- `name`
- `scope` = SCENE | SEQUENCE | ARC
- `type` = REVERSAL | REVELATION | DECISION | SACRIFICE | BETRAYAL | FAILURE | VICTORY | COLLAPSE | ARRIVAL | DEPARTURE | TRAP_SPRUNG
- `trigger_event_id` (required)
- `linked_conflict_id` (required)
- `causal_support` (list of edges/events that justify the pivot)
- `before_state` (snapshot: key variables)
- `after_state` (snapshot: key variables)
- `trajectory_change` (one sentence: what direction flips)
- `stakes_delta` (what increases/decreases)
- `power_balance_shift` (A↔opposition shift)
- `irreversibility` = REVERSIBLE | IRREVERSIBLE | PARTIAL
- `cost_paid` (what was paid to flip)
- `new_constraints` (optional: new lock-ins)
- `promises_opened` (optional: new questions/promises)
- `promises_closed` (optional: closed threads)
- `notes`

Missing any required field → REJECT.

### 3.2 State Snapshot Rules (HARD)
Before/After must include at least 3 variables from:
- information state (who knows what)
- resource state (what is available)
- relationship state (trust, alliance)
- location/control state (territory, access)
- capability state (tools, permissions)
- time pressure (deadline, window)

---

## 4. TURNING POINT INTEGRITY RULES (HARD)

- Turning point must cause a measurable state transition:
  - before_state != after_state on at least 2 variables.
- Turning point must be grounded in causality:
  - trigger event must have incoming causal support.
- Turning point must affect a conflict:
  - linked_conflict_id is mandatory and must show phase shift.
- If irreversibility is claimed:
  - cost_paid and new_constraints must justify it.

---

## 5. INPUT ARTIFACTS

### 5.1 INPUT — TURNING_POINT_REQUEST
**REQUIRED FIELDS**
- `tp_req_id`
- `timestamp`
- `conflict_model_ref` (required)
- `cause_effect_graph_ref` (required)
- `event_spec_library_ref` (recommended)
- `constraints_refs` (required)
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 6. OUTPUT ARTIFACTS

### 6.1 OUTPUT — TURNING_POINT_MAP
**REQUIRED FIELDS**
- `tp_req_id`
- `turning_points` (list of TURNING_POINT_SPEC)
- `phase_shift_map` (conflict_id → phases via turning points)
- `irreversibility_index` (tp_id → level)
- `integrity_report` (issues + fixes)
- `trace_id` (if provided)

### 6.2 OUTPUT — TURNING_POINT_VERDICT
- `tp_req_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 7. CORE OPERATIONS

- OP_01: INGEST_CONFLICT_MODEL_AND_CAUSAL_GRAPH
- OP_02: IDENTIFY_PHASE_SHIFTS (power/stakes reversals)
- OP_03: SELECT_TRIGGER_EVENTS_AND_CAUSAL_SUPPORT
- OP_04: BUILD_BEFORE_AFTER_STATE_SNAPSHOTS
- OP_05: CLASSIFY_TURNING_POINT_TYPES
- OP_06: CHECK_INTEGRITY_RULES (state change + causality)
- OP_07: EMIT_TURNING_POINT_MAP

---

## 8. DEPENDENCIES

### REQUIRED
- Conflict Model
- Cause–Effect Graph
- Constraints refs

### OPTIONAL
- Event Spec Library

### FORBIDDEN
- Turning points that do not change state
- Turning points with no causal support (“suddenly”)
- Turning points not tied to conflicts
- Irreversibility with no cost/constraints

---

## 9. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- Turning points are “moments” (no state change)
- Multiple turning points rely on coincidence or missing causes
- Turning points do not map to conflict phase shifts
- Irreversible claims without cost/constraints

Reaction:
- Verdict INVALID (CRITICAL)
- Emit repair suggestions:
  - add bridge events
  - define state variables
  - tie pivot to conflict ladder
  - price irreversibility

---

## 10. TRACE RULES

- trace_id optional unless pipeline requires traced execution
- if present, propagate into climax and resolution artifacts

---

## 11. NON-GOALS
- Does not write climax
- Does not resolve arcs
- Does not schedule scenes

---

## 12. FINAL STATEMENT

Turning points are trajectory flips with a price.
Model the flip — and story gains direction.

---

**STATUS:** Turning Point Engine v1.0  
**REALM:** ACTIVE
