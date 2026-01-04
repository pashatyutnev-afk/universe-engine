# ⚔️ CONFLICT & POWER ENGINE
## Canonical Engine Specification  
**LEVEL: L2 · DOMAIN ENGINE · POWER DYNAMICS · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 05__CONFLICT_POWER_ENG.md
- ENGINE_ID: L2-DOM-CONFLICT-POWER-ENGINE-005
- UID: UE.ENT.ENG.DOM.WORLD.CONFLICT_POWER
- NAME: Conflict & Power Engine
- CLASS: Domain Engine
- DOMAIN: World
- CATEGORY: Power Resources, Escalation Ladders & Conflict Logic
- LEVEL: L2
- STATUS: FINAL
- FAILURE_MODE: fail-closed (for stakes integrity)
- EDITABLE: true
- BYPASS_ALLOWED: false (within world pipeline)

### ABSOLUTE RULE
> Power must be sourced and priced; conflict is the accounting of power under pressure.

---

## 1. PURPOSE

Conflict & Power Engine defines **how power works** and **how conflicts escalate**.

It produces:
- **POWER_CONFLICT_MATRIX** (actors × power resources × leverage)
- escalation ladders (from tension to war)
- deterrence and retaliation rules
- internal conflict patterns (coups, revolts, purges)
- victory conditions and cost models

This engine prevents “random wars” and “free victories”.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define power resources and how they convert into outcomes
- Define actor capabilities and constraints (non-simulation)
- Define escalation ladder and de-escalation paths
- Define deterrence/retaliation logic
- Define conflict archetypes (war, insurgency, sabotage, proxy, civil war)
- Define victory/defeat conditions and cost categories
- Define “power loophole checks” (unearned dominance)
- Validate compatibility with world laws and economy scarcity

### OUT-OF-SCOPE (FORBIDDEN)
- Full geopolitical move simulation (Geopolitics Engine)
- Detailed resource flow models (Economy & Resource Engine)
- Civilization deep design (Civilization Engine) beyond actor notes
- Canon authority decisions (Governance)

---

## 3. POWER & CONFLICT MODEL

### 3.1 Power Resources (fixed set)
- MILITARY_FORCE
- ECONOMIC_CAPACITY
- TECHNOLOGICAL_EDGE
- INFORMATION_CONTROL
- LEGITIMACY
- ALLIANCES
- TERRITORY_ADVANTAGE
- POPULATION_SUPPORT
- COERCION_FEAR
- SYMBOLIC_POWER (myth, prophecy, ideology)

### 3.2 Conflict Types (fixed set)
- COLD_TENSION
- SANCTIONS_PRESSURE
- PROXY_CONFLICT
- INSURGENCY
- COUP
- CIVIL_WAR
- BORDER_WAR
- TOTAL_WAR
- SABOTAGE_SHADOW_WAR
- CULTURE_WAR (soft power)

### 3.3 Escalation Ladder (required)
- STEP_0: baseline tension
- STEP_1: incident / provocation
- STEP_2: threats / mobilization
- STEP_3: limited action
- STEP_4: retaliation cycle
- STEP_5: open conflict
- STEP_6: catastrophic escalation (optional)

Each step must have:
- trigger conditions
- typical actions
- deterrence options
- cost rise profile

### 3.4 Cost Categories (fixed)
- HUMAN_COST
- MATERIAL_COST
- LEGITIMACY_COST
- TIME_COST
- ECOLOGY_COST
- CULTURAL_COST

---

## 4. INPUT ARTIFACTS

### 4.1 INPUT — POWER_CONFLICT_REQUEST
**REQUIRED FIELDS**
- `pc_id`
- `timestamp`
- `actor_list_ref` (civilizations/factions/polities)
- `world_structure_graph_ref` (recommended)
- `world_lawset_ref` (required)
- `timeline_model_ref` (recommended)
- `economy_resource_model_ref` (recommended)
- `constraints_refs` (genre/project constraints)
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 5. OUTPUT ARTIFACTS

### 5.1 OUTPUT — POWER_CONFLICT_MATRIX
**REQUIRED FIELDS**
- `pc_id`
- `actors` (list)
- `power_resources` (fixed set mapping per actor: 0..10)
- `leverage_map` (actor → leverage sources + against whom)
- `conflict_type_library` (definitions + when used)
- `escalation_ladders` (one or more ladders)
- `deterrence_rules` (list: {rule_id, threat, credibility_source, failure_consequence})
- `retaliation_rules` (list: {rule_id, trigger, response, cost_profile})
- `victory_conditions` (per conflict type)
- `defeat_conditions` (per conflict type)
- `cost_models` (cost category → typical impacts)
- `power_loophole_checks` (auto-detected “free dominance” risks)
- `trace_id` (if provided)

### 5.2 OUTPUT — CONFLICT_POWER_VERDICT
- `pc_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 6. CORE OPERATIONS

- OP_01: DEFINE_ACTORS_AND_POWER_SCORES
- OP_02: BUILD_LEVERAGE_MAP
- OP_03: DEFINE_CONFLICT_TYPE_LIBRARY
- OP_04: BUILD_ESCALATION_LADDERS
- OP_05: DEFINE_DETERRENCE_AND_RETALIATION
- OP_06: DEFINE_VICTORY_DEFEAT_AND_COST_MODELS
- OP_07: RUN_POWER_LOOPHOLE_CHECKS
- OP_08: EMIT_POWER_CONFLICT_MATRIX

---

## 7. ACCESS MODEL

### WRITE
- Domain pipeline outputs only

### READ
- Geopolitics Engine (moves constrained by power)
- Economy & Resource Engine (war capacity constraints)
- Technology & Magic Engine (capability bounds)
- Timeline & Epoch Engine (conflict history anchors)
- Narrative engines (stakes, escalation logic)

### DELETE
- Allowed for drafts; finalization per project governance

---

## 8. DEPENDENCIES

### REQUIRED
- World lawset (what violence/power is possible)
- Actor list reference (who has power)

### FORBIDDEN
- Conflicts with no escalation triggers (random war)
- Victory conditions with zero cost (free win)
- Power scores without sources (handwavy power)
- Deterrence with no credibility source
- Treating matrix as canon authority

---

## 9. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- No escalation ladder defined
- No cost models (conflict has no price)
- One actor dominates all resources without scarcity/limits explanation
- Contradictions with world laws (impossible warfare) without exception pricing
- Retaliation loops infinite with no breaking conditions

Reaction:
- Verdict INVALID (CRITICAL)
- Provide repairs: add ladder, price conflict, add constraints, add breakpoints.

---

## 10. TRACE RULES

- trace_id optional unless orchestrator requires traced pipeline
- if present, propagate to geopolitics and continuity references

---

## 11. NON-GOALS
- Does not simulate geopolitics turn-by-turn
- Does not write battles or scenes
- Does not grant canon authority

---

## 12. FINAL STATEMENT

Conflict is power under stress.
Price the power, and the stakes become real.

---

**STATUS:** Conflict & Power Engine v1.0  
**DOMAIN:** ACTIVE
