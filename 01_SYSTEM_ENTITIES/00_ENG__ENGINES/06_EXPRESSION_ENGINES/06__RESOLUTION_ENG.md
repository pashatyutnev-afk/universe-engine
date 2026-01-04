# ✅ RESOLUTION ENGINE
## Canonical Engine Specification  
**LEVEL: L3 · EXPRESSION ENGINE · NEW EQUILIBRIUM · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 06__RESOLUTION_ENG.md
- ENGINE_ID: L3-EXP-RESOLUTION-ENGINE-006
- UID: UE.ENT.ENG.EXP.RESOLUTION
- NAME: Resolution Engine
- CLASS: Expression Engine
- LEVEL: L3
- STATUS: FINAL
- FAILURE_MODE: fail-closed (closure integrity)
- EDITABLE: true

### ABSOLUTE RULE
> Resolution is not “ending the text”. Resolution is establishing the new equilibrium and paying the costs.

---

## 1. PURPOSE

Resolution Engine designs the **post-climax settlement**.

It produces:
- **RESOLUTION_PLAN**
- closure map (what arcs close, what remains open)
- cost aftermath (what victory/defeat permanently changed)
- new equilibrium state (world/relationships/resources)
- sequel hooks as explicit OPEN_LOOPS (never accidental)

This engine prevents “climax → fade to black” with no consequence.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define resolution schema and closure rules
- Convert Climax Blueprint into a resolution plan
- Close arcs with explicit state transitions
- Register open loops with declared intent
- Validate consistency with causality and world constraints
- Emit resolution plan for production formats

### OUT-OF-SCOPE (FORBIDDEN)
- Selecting climax (Climax Engine)
- Scheduling events in time (Event Scheduling Engine)
- Writing full prose
- Canon authority decisions

---

## 3. RESOLUTION MODEL

### 3.1 Resolution Object — RESOLUTION_SPEC (required fields)
- `rs_id`
- `name`
- `scope` = SEQUENCE | ARC
- `linked_climax_id` (required)
- `closed_conflict_ids` (list)
- `closure_actions` (list of concrete settlement actions)
- `after_effects` (list of permanent consequences)
- `cost_aftermath` (resources/time/risk/reputation/relationships)
- `new_equilibrium_state` (snapshot: key variables)
- `open_loops` (list of OPEN_LOOP objects; can be empty)
- `truth_reconciliation` (what is now known vs still hidden)
- `justice_or_balance` (optional: moral/accounting settlement)
- `final_image_or_state` (optional: last state anchor)
- `notes`

Missing any required field → REJECT.

### 3.2 Open Loop Object — OPEN_LOOP (required fields)
- `loop_id`
- `question` (what remains unresolved)
- `type` = MYSTERY | RELATIONSHIP | WORLD_THREAT | INTERNAL_CHANGE | POWER_VACUUM | DEBT | PROMISE
- `reason_to_keep_open` (why it must remain open)
- `containment_rule` (how it doesn’t break current equilibrium)
- `sequel_dependency` (optional: what future arc needs)

Missing any required field → REJECT.

---

## 4. CLOSURE RULES (HARD)

- Every primary conflict addressed in climax must have one of:
  - CLOSED (resolved)
  - TRANSFORMED (becomes a different conflict with new rules)
  - DECLARED_OPEN (explicit open loop object)
- “Accidental open loops” are forbidden:
  - if a promise is not paid, it must be declared OPEN_LOOP with reason.
- New equilibrium must differ from pre-arc equilibrium on at least 2 variables.

---

## 5. INPUT ARTIFACTS

### 5.1 INPUT — RESOLUTION_REQUEST
**REQUIRED FIELDS**
- `rs_req_id`
- `timestamp`
- `climax_blueprint_ref` (required)
- `turning_point_map_ref` (recommended)
- `cause_effect_graph_ref` (required)
- `conflict_model_ref` (recommended)
- `constraints_refs` (required)
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 6. OUTPUT ARTIFACTS

### 6.1 OUTPUT — RESOLUTION_PLAN
**REQUIRED FIELDS**
- `rs_req_id`
- `resolution_specs` (list of RESOLUTION_SPEC; usually 1 primary)
- `closure_map` (conflict_id → CLOSED/TRANSFORMED/OPEN)
- `open_loop_registry` (list of OPEN_LOOP)
- `equilibrium_delta_report` (before vs after variables)
- `integrity_report` (issues + fixes)
- `trace_id` (if provided)

### 6.2 OUTPUT — RESOLUTION_VERDICT
- `rs_req_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 7. CORE OPERATIONS

- OP_01: INGEST_CLIMAX_AND_CAUSAL_ARTIFACTS
- OP_02: IDENTIFY_CONFLICT_CLOSURE_REQUIREMENTS
- OP_03: BUILD_CLOSURE_ACTIONS_AND_AFTER_EFFECTS
- OP_04: BUILD_NEW_EQUILIBRIUM_STATE_SNAPSHOT
- OP_05: REGISTER_OPEN_LOOPS (explicit + contained)
- OP_06: RUN_CLOSURE_AND_EQUILIBRIUM_CHECKS
- OP_07: EMIT_RESOLUTION_PLAN

---

## 8. DEPENDENCIES

### REQUIRED
- Climax Blueprint
- Cause–Effect Graph
- Constraints refs

### OPTIONAL
- Turning Point Map
- Conflict Model

### FORBIDDEN
- Resolution with no new equilibrium
- Conflicts left unresolved without OPEN_LOOP objects
- “Everything is fine” after high-cost climax without aftermath cost
- Resolution actions that violate world law/capability bounds

---

## 9. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- Primary conflicts have no closure status
- Open loops exist but are not contained (break equilibrium immediately)
- New equilibrium identical to before (no real change)
- Aftermath costs missing (victory with no scars)
- Causality breaks (resolution actions not supported by prior states)

Reaction:
- Verdict INVALID (CRITICAL)
- Emit repair suggestions:
  - define closure_map
  - add aftermath costs
  - declare/open loops properly
  - rebuild equilibrium snapshot

---

## 10. TRACE RULES

- trace_id optional unless pipeline requires traced execution
- if present, propagate into scheduling and production packaging

---

## 11. NON-GOALS
- Does not write epilogues as prose
- Does not schedule timeline
- Does not choose climax

---

## 12. FINAL STATEMENT

Resolution is the bill.
Pay it — and the story earns its ending.

---

**STATUS:** Resolution Engine v1.0  
**REALM:** ACTIVE
