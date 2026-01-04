# 💥 SYSTEM SHOCK ENGINE
## Canonical Engine Specification  
**LEVEL: L3 · EXPRESSION ENGINE · CASCADE DISRUPTION · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 07__SYSTEM_SHOCK_ENG.md
- ENGINE_ID: L3-EXP-SYSTEM-SHOCK-ENGINE-007
- UID: UE.ENT.ENG.EXP.SYSTEM_SHOCK
- NAME: System Shock Engine
- CLASS: Expression Engine
- LEVEL: L3
- STATUS: FINAL
- FAILURE_MODE: fail-closed (system integrity)
- EDITABLE: true

### ABSOLUTE RULE
> A system shock is not an event — it is an event that breaks the system’s normal rules and forces a new regime.

---

## 1. PURPOSE

System Shock Engine defines **disruptive cascade events**:
- rule-breaking incidents
- multi-layer propagation (society, economy, ecology, belief, tech)
- threshold behavior (tipping points)
- resilience tests and recovery paths

It produces:
- **SYSTEM_SHOCK_EVENT** specs
- cascade graphs (shock propagation)
- resilience map (what survives, what collapses)
- recovery/containment strategies for resolution planning

This engine enables collapses, revolutions, pandemics, wars, “black swans”.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define System Shock schema and taxonomy
- Detect shock candidates from event/conflict/causality
- Model cascades and tipping thresholds
- Define containment and recovery paths
- Validate shock feasibility under world laws/capabilities/ecology
- Emit shock registry for scheduling and narrative planning

### OUT-OF-SCOPE (FORBIDDEN)
- Scheduling shocks in time (Event Scheduling Engine)
- Writing scenes/prose
- Canon authority decisions

---

## 3. SYSTEM SHOCK MODEL

### 3.1 Shock Object — SYSTEM_SHOCK_SPEC (required fields)
- `ss_id`
- `name`
- `type` = WAR_OUTBREAK | REVOLUTION | ECONOMIC_CRASH | ECOLOGICAL_COLLAPSE | PANDEMIC | TECH_BREAKTHROUGH | TECH_FAILURE | COSMIC_EVENT | REGIME_CHANGE | MAGIC_BREACH | INFORMATION_BLACKOUT
- `scope` = REGION | GLOBAL | SYSTEMWIDE
- `trigger_event_id` (required)
- `pre_shock_baseline` (snapshot: key variables)
- `rule_break_description` (what normal rules stop holding)
- `tipping_thresholds` (list of threshold conditions)
- `cascade_graph` (list of cascade edges: layer→layer)
- `primary_losses` (list)
- `secondary_losses` (list)
- `winners` (optional list)
- `new_constraints` (what becomes forbidden/expensive)
- `new_capabilities` (optional: what becomes possible)
- `resilience_map` (what systems resist and why)
- `containment_options` (list)
- `recovery_paths` (list with costs/time)
- `irreversibility` = REVERSIBLE | IRREVERSIBLE | PARTIAL
- `evidence` (what shows shock is real)
- `notes`

Missing any required field → REJECT.

### 3.2 Cascade Edge (required fields)
- `edge_id`
- `from_layer` = ECOLOGY | ECONOMY | CIVILIZATION | GEOPOLITICS | BELIEF | TECHNOLOGY_MAGIC | SECURITY | INFORMATION
- `to_layer` (same enum)
- `mechanism` (how it propagates)
- `lag_time`
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

Missing any required field → REJECT.

---

## 4. SHOCK INTEGRITY RULES (HARD)

- Shock must break at least 2 layers:
  - example: economy + geopolitics, belief + civilization, ecology + economy.
- Must include thresholds:
  - shock does not happen “because author wants it”.
- Must include containment OR recovery path:
  - even if it fails, options must exist.
- Must be aligned to world laws/capabilities:
  - impossible shock must be priced as explicit exception rule.

---

## 5. INPUT ARTIFACTS

### 5.1 INPUT — SYSTEM_SHOCK_REQUEST
**REQUIRED FIELDS**
- `ss_req_id`
- `timestamp`
- `event_spec_library_ref` (required)
- `cause_effect_graph_ref` (required)
- `conflict_model_ref` (recommended)
- `world_package_ref` (recommended)
- `constraints_refs` (required)
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 6. OUTPUT ARTIFACTS

### 6.1 OUTPUT — SYSTEM_SHOCK_REGISTRY
**REQUIRED FIELDS**
- `ss_req_id`
- `shock_specs` (list of SYSTEM_SHOCK_SPEC)
- `cascade_summary` (per shock)
- `resilience_summary` (per shock)
- `integrity_report` (issues + fixes)
- `trace_id` (if provided)

### 6.2 OUTPUT — SYSTEM_SHOCK_VERDICT
- `ss_req_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 7. CORE OPERATIONS

- OP_01: INGEST_EVENT_AND_CAUSAL_ARTIFACTS
- OP_02: IDENTIFY_SHOCK_CANDIDATES (threshold + cascade potential)
- OP_03: BUILD_PRE_SHOCK_BASELINE
- OP_04: DEFINE_RULE_BREAK_AND_THRESHOLDS
- OP_05: BUILD_CASCADE_GRAPH (multi-layer propagation)
- OP_06: DEFINE_RESILIENCE_MAP_AND_FAILURE_POINTS
- OP_07: DEFINE_CONTAINMENT_AND_RECOVERY_PATHS
- OP_08: RUN_FEASIBILITY_AND_INTEGRITY_CHECKS
- OP_09: EMIT_SYSTEM_SHOCK_REGISTRY

---

## 8. DEPENDENCIES

### REQUIRED
- Event Spec Library
- Cause–Effect Graph
- Constraints refs

### OPTIONAL
- World package (laws, ecology, scarcity, capabilities)
- Conflict model

### FORBIDDEN
- Shocks with no thresholds
- Shocks that affect only one layer
- Shocks with no containment/recovery options
- World-law violations without explicit priced exception

---

## 9. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- Cascade graph missing or trivial
- Thresholds missing (“suddenly”)
- No recovery/containment options
- Shock contradicts world ecology/economy capabilities
- Irreversibility claimed without new constraints and losses

Reaction:
- Verdict INVALID (CRITICAL)
- Emit repair suggestions:
  - define thresholds
  - expand cascade edges
  - add resilience + recovery
  - price exception if needed

---

## 10. TRACE RULES

- trace_id optional unless pipeline requires traced execution
- if present, propagate into scheduling and resolution planning

---

## 11. NON-GOALS
- Does not schedule the shock date/time
- Does not write battle scenes or outbreak scenes
- Does not canonize history

---

## 12. FINAL STATEMENT

Shock is cascade with thresholds.
Model the cascade — and collapse becomes believable.

---

**STATUS:** System Shock Engine v1.0  
**REALM:** ACTIVE
