# 🧨 CLIMAX ENGINE
## Canonical Engine Specification  
**LEVEL: L3 · EXPRESSION ENGINE · PAYOFF PEAK · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 05__CLIMAX_ENG.md
- ENGINE_ID: L3-EXP-CLIMAX-ENGINE-005
- UID: UE.ENT.ENG.EXP.CLIMAX
- NAME: Climax Engine
- CLASS: Expression Engine
- LEVEL: L3
- STATUS: FINAL
- FAILURE_MODE: fail-closed (payoff integrity)
- EDITABLE: true

### ABSOLUTE RULE
> Climax is the moment where the story pays its biggest promise at the highest price.

---

## 1. PURPOSE

Climax Engine designs the **decisive peak**:
- the maximum collision of goals and opposition
- the highest priced decision
- irreversible change
- payoff of seeded promises

It produces:
- **CLIMAX_BLUEPRINT**
- decisive confrontation mechanics
- payoff mapping (setup → payoff)
- irreversibility and consequence surfaces
- eligibility checks for resolution

This engine prevents “random boss fight” endings.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define climax schema and categories
- Select climax candidates from turning points + conflict model + causality
- Validate payoff alignment (foreshadowing/promises must pay)
- Define decisive choice and confrontation structure
- Define maximum cost surface and irreversible consequences
- Emit Climax Blueprint for Resolution engine and production formats

### OUT-OF-SCOPE (FORBIDDEN)
- Writing full resolution (Resolution Engine)
- Scheduling events (Scheduling Engine)
- Writing scenes/prose
- Canon authority decisions

---

## 3. CLIMAX MODEL

### 3.1 Climax Object — CLIMAX_SPEC (required fields)
- `cx_id`
- `name`
- `scope` = SEQUENCE | ARC
- `linked_conflict_ids` (list, at least 1)
- `trigger_turning_point_id` (required)
- `decisive_question` (one sentence: “Will X … ?”)
- `decisive_choice` (choice A vs B with cost)
- `opposition_form` (who/what is faced at peak)
- `stakes_peak` (what is at maximum risk)
- `capability_constraints` (what limits actions)
- `setup_to_payoff_map` (list of {setup_ref, payoff_ref})
- `event_chain` (ordered list of event_ids)
- `causal_support` (edges/events that justify inevitability)
- `max_cost_surface` (resources/time/risk/relationships/irreversibility)
- `irreversibility_gate` (what becomes impossible after)
- `win_state` (what “win” means here)
- `lose_state` (what “lose” means here)
- `partial_state` (optional)
- `consequences` (short list of after-effects)
- `notes`

Missing any required field → REJECT.

### 3.2 Setup→Payoff Rule (HARD)
- Each payoff must have a prior setup (seed) unless genre permits “shock ending”.
- If “shock ending” is used, it must be declared and priced.

---

## 4. CLIMAX INTEGRITY RULES (HARD)

- Climax must resolve or transform the primary conflict(s).
- Climax must be supported by causality:
  - no “teleport escalation” (missing chain).
- Climax must include a decisive choice with cost.
- Climax must peak stakes and costs (max within arc).
- Irreversibility gate must be explicit.

---

## 5. INPUT ARTIFACTS

### 5.1 INPUT — CLIMAX_REQUEST
**REQUIRED FIELDS**
- `cx_req_id`
- `timestamp`
- `conflict_model_ref` (required)
- `turning_point_map_ref` (required)
- `cause_effect_graph_ref` (required)
- `foreshadowing_map_ref` (recommended)
- `constraints_refs` (required)
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 6. OUTPUT ARTIFACTS

### 6.1 OUTPUT — CLIMAX_BLUEPRINT
**REQUIRED FIELDS**
- `cx_req_id`
- `climax_specs` (list of CLIMAX_SPEC; usually 1 primary, optional secondary)
- `payoff_report` (setup→payoff coverage + gaps)
- `integrity_report` (issues + fixes)
- `trace_id` (if provided)

### 6.2 OUTPUT — CLIMAX_VERDICT
- `cx_req_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 7. CORE OPERATIONS

- OP_01: INGEST_CONFLICT_TURNINGPOINT_CAUSAL_ARTIFACTS
- OP_02: SELECT_PRIMARY_CONFLICTS_AND_PEAK_WINDOW
- OP_03: IDENTIFY_TRIGGER_TURNING_POINT
- OP_04: BUILD_DECISIVE_QUESTION_AND_CHOICE
- OP_05: BUILD_EVENT_CHAIN_AND_CAUSAL_SUPPORT
- OP_06: BUILD_SETUP_TO_PAYOFF_MAP (foreshadowing + promises)
- OP_07: DEFINE_MAX_COST_SURFACE_AND_IRREVERSIBILITY_GATE
- OP_08: RUN_INTEGRITY_CHECKS
- OP_09: EMIT_CLIMAX_BLUEPRINT

---

## 8. DEPENDENCIES

### REQUIRED
- Conflict Model
- Turning Point Map
- Cause–Effect Graph
- Constraints refs

### OPTIONAL
- Foreshadowing map / twist plan
- World/character refs (via upstream packages)

### FORBIDDEN
- Climax with no decisive choice
- Climax with no cost surface
- Payoffs without setups (unless declared shock and priced)
- Climax that does not transform main conflict

---

## 9. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- No decisive question/choice
- Event chain missing causality (gaps)
- Payoff gaps: major promises not paid
- Irreversibility claimed but not defined
- Costs do not peak (climax cheaper than earlier beats)

Reaction:
- Verdict INVALID (CRITICAL)
- Emit repair suggestions:
  - add setup seeds or revise payoffs
  - insert bridge events
  - define cost/irreversibility gate
  - rebuild decisive choice

---

## 10. TRACE RULES

- trace_id optional unless pipeline requires traced execution
- if present, propagate into resolution plan and production packaging

---

## 11. NON-GOALS
- Does not write resolution scenes
- Does not schedule timeline
- Does not decide theme meaning

---

## 12. FINAL STATEMENT

Climax is the priced payment of promises.
Pay what you promised — or the story collapses.

---

**STATUS:** Climax Engine v1.0  
**REALM:** ACTIVE
