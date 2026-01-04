# ⚔️ CONFLICT ENGINE
## Canonical Engine Specification  
**LEVEL: L3 · EXPRESSION ENGINE · GOALS vs OPPOSITION · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 03__CONFLICT_ENG.md
- ENGINE_ID: L3-EXP-CONFLICT-ENGINE-003
- UID: UE.ENT.ENG.EXP.CONFLICT
- NAME: Conflict Engine
- CLASS: Expression Engine
- LEVEL: L3
- STATUS: FINAL
- FAILURE_MODE: fail-closed (stakes integrity)
- EDITABLE: true

### ABSOLUTE RULE
> No opposition = no conflict. No cost = no meaning.

---

## 1. PURPOSE

Conflict Engine defines conflicts as **structured contests**:
- goal
- opposition
- constraints
- costs
- escalation ladder
- win/lose conditions

It produces:
- **CONFLICT_MODEL** (conflict registry + mechanics)
- conflict-to-event mapping (conflicts expressed via event chains)
- escalation surfaces (what raises the price)
- resolution viability (what can realistically end it)

This engine prevents “argument scenes” that change nothing.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define conflict schema and categories
- Extract conflicts from event and causality artifacts
- Define stakes, goals, antagonistic forces, constraints
- Define escalation ladders and decision points
- Define win/lose/partial outcomes and costs
- Validate conflict feasibility under world laws/capabilities and character constraints
- Emit conflict library for turning point/climax/resolution engines

### OUT-OF-SCOPE (FORBIDDEN)
- Choosing story theme (Theme engine)
- Scheduling conflicts in time (Scheduling engine)
- Writing scenes/prose
- Canon authority decisions

---

## 3. CONFLICT MODEL

### 3.1 Conflict Object — CONFLICT_SPEC (required fields)
- `conflict_id`
- `name`
- `category` = INTERNAL | INTERPERSONAL | SOCIAL | POLITICAL | ECONOMIC | SURVIVAL | IDEOLOGICAL | MYSTERY | WAR
- `scope` = SCENE | SEQUENCE | ARC
- `goal` (what side A wants)
- `opposition` (who/what prevents it)
- `stakes` (what is lost if A fails)
- `constraints` (laws, resources, time, norms)
- `power_balance` (A vs opposition: underdog/equal/overpower)
- `cost_surface` (what costs rise with escalation)
- `escalation_ladder` (steps with triggers)
- `decision_points` (where choices matter)
- `win_conditions`
- `lose_conditions`
- `partial_outcomes` (optional)
- `exit_conditions` (what ends the conflict without “win”)
- `linked_events` (list of event_ids)
- `linked_causal_edges` (optional refs)
- `notes`

Missing any required field → REJECT.

### 3.2 Cost Surface (required structure)
- `resources` (what burns)
- `time` (deadlines)
- `risk` (injury/legal/social)
- `reputation` (status loss)
- `relationships` (trust damage)
- `irreversibility` (what cannot be undone)

---

## 4. HARD RULES (CONFLICT INTEGRITY)

- Every conflict must have:
  - a goal
  - an opposition force
  - a stake
  - a constraint
  - a cost surface
- Opposition must be active:
  - “bad luck” is not valid opposition unless world law defines it as system force.
- Escalation ladder must contain at least 3 steps for ARC scope.
- Win must be priced:
  - even victory causes loss (time, scars, exposure, debt, etc.)

---

## 5. INPUT ARTIFACTS

### 5.1 INPUT — CONFLICT_REQUEST
**REQUIRED FIELDS**
- `cf_id`
- `timestamp`
- `event_spec_library_ref` (recommended)
- `cause_effect_graph_ref` (required for integrity)
- `world_package_ref` (recommended)
- `character_package_ref` (recommended)
- `constraints_refs` (required)
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 6. OUTPUT ARTIFACTS

### 6.1 OUTPUT — CONFLICT_MODEL
**REQUIRED FIELDS**
- `cf_id`
- `conflict_specs` (list of CONFLICT_SPEC)
- `conflict_to_event_map` (conflict_id → event_ids)
- `escalation_summary` (per conflict)
- `feasibility_checks` (world/character alignment results)
- `integrity_report` (issues + fixes)
- `trace_id` (if provided)

### 6.2 OUTPUT — CONFLICT_VERDICT
- `cf_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 7. CORE OPERATIONS

- OP_01: INGEST_CAUSE_EFFECT_GRAPH
- OP_02: EXTRACT_CONFLICT_CANDIDATES (goals blocked by opposition)
- OP_03: DEFINE_GOAL_OPPOSITION_STAKES_CONSTRAINTS
- OP_04: BUILD_COST_SURFACE_AND_ESCALATION_LADDER
- OP_05: MAP_CONFLICTS_TO_EVENT_CHAINS
- OP_06: CHECK_WORLD_AND_CHARACTER_FEASIBILITY
- OP_07: RUN_CONFLICT_INTEGRITY_CHECKS
- OP_08: EMIT_CONFLICT_MODEL

---

## 8. FEASIBILITY CHECKS (HARD)

- World Law Alignment:
  - conflict moves must be possible under world laws/capabilities
- Scarcity Alignment:
  - resources used in escalation must exist and be limited (if applicable)
- Character Alignment:
  - conflict decisions must not contradict core values without a bridge event
- Causal Alignment:
  - conflicts must be embedded in causality graph (not floating)

Any CRITICAL mismatch → INVALID unless explicitly priced as exception.

---

## 9. DEPENDENCIES

### REQUIRED
- Cause–Effect Graph
- Constraints refs

### OPTIONAL
- Event spec library
- World package
- Character package

### FORBIDDEN
- Conflicts with no stakes
- Conflicts with passive opposition (no agency/system force)
- “Win for free” outcomes
- Conflicts not mapped to events/causality

---

## 10. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- Conflicts missing goal/opposition/stakes/constraints/costs
- Escalation ladder absent or <3 steps for ARC conflicts
- Conflicts violate world law/capability bounds
- Conflict not grounded in causality graph
- Win/lose conditions undefined

Reaction:
- Verdict INVALID (CRITICAL)
- Emit repair suggestions:
  - define opposition agency
  - add constraints/costs
  - add escalation steps
  - insert bridge events for feasibility

---

## 11. TRACE RULES

- trace_id optional unless pipeline requires traced execution
- if present, propagate into turning point/climax/resolution artifacts

---

## 12. NON-GOALS
- Does not pick climax
- Does not resolve conflicts
- Does not schedule scenes

---

## 13. FINAL STATEMENT

Conflict is a priced contest under constraints.
Model it — and every scene gains teeth.

---

**STATUS:** Conflict Engine v1.0  
**REALM:** ACTIVE
