# ⚙️ ECONOMY & RESOURCE ENGINE
## Canonical Engine Specification  
**LEVEL: L2 · DOMAIN ENGINE · SCARCITY & FLOWS · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 07__ECONOMY_RESOURCE_ENG.md
- ENGINE_ID: L2-DOM-ECONOMY-RESOURCE-ENGINE-007
- UID: UE.ENT.ENG.DOM.WORLD.ECONOMY_RESOURCE
- NAME: Economy & Resource Engine
- CLASS: Domain Engine
- DOMAIN: World
- CATEGORY: Scarcity Rules, Flow Graphs, Production Chains & Logistics
- LEVEL: L2
- STATUS: FINAL
- FAILURE_MODE: fail-closed (for scarcity realism)
- EDITABLE: true
- BYPASS_ALLOWED: false (within world pipeline)

### ABSOLUTE RULE
> If resources are unlimited, conflict becomes cosmetic and power becomes meaningless.

---

## 1. PURPOSE

Economy & Resource Engine defines **what is scarce**, **what flows**, and **what breaks**.

It produces:
- **RESOURCE_FLOW_MODEL** (resources, sources, sinks, routes)
- production chains and bottlenecks
- logistics constraints (time/cost/risk)
- black-market and leakage channels
- “no free lunch” rules (every production has inputs + costs)

This engine does not use “currency” by default (if the canon says no currency).
It models value as **resources, obligations, access, and control**.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define core resources and scarcity levels
- Define sources (where it comes from) and sinks (who consumes)
- Define production chains (inputs → process → outputs)
- Define logistics routes and constraints (time/cost/risk)
- Define bottlenecks and strategic chokepoints (aligned to world structure)
- Define allocation rules (rationing, privilege, quotas, access)
- Define black market / leakage / corruption pathways
- Validate economy compatibility with world laws, geopolitics, conflict matrix
- Detect “free resource” loopholes and repair suggestions

### OUT-OF-SCOPE (FORBIDDEN)
- Defining geography (World Structure Engine)
- Defining laws (World Law Engine)
- Full political simulation (Geopolitics Engine)
- Canon authority decisions (Governance)

---

## 3. ECONOMY MODEL (NON-CURRENCY DEFAULT)

### 3.1 Value Carriers (fixed set)
- RESOURCE (material/energy/food/water)
- ACCESS (permission to use locations/tech)
- OBLIGATION (debts of duty/favor)
- STATUS (rank, privileges)
- INFORMATION (exclusive knowledge)
- PROTECTION (security guarantee)

### 3.2 Resource Object (required)
- `res_id`
- `name`
- `type` = MATERIAL | ENERGY | FOOD | WATER | DATA | SERVICE | CAPABILITY
- `scarcity_level` = LOW | MEDIUM | HIGH | CRITICAL
- `substitutes` (optional list)
- `storage_difficulty` (LOW/MEDIUM/HIGH)
- `spoilage` (none/slow/fast)
- `strategic_value` 0..10

### 3.3 Flow Edge (required)
- `edge_id`
- `from_node` (source/producer)
- `to_node` (consumer/warehouse)
- `resource_id`
- `capacity`
- `time_cost`
- `risk_level` (LOW/MEDIUM/HIGH)
- `loss_rate` (optional)
- `control_actor_ref` (who controls the route)

### 3.4 Production Chain (required)
- `chain_id`
- `output_resource_id`
- `inputs` (list)
- `process` (short)
- `required_infrastructure`
- `failure_points` (bottlenecks)
- `externalities` (pollution, social cost, etc.)

---

## 4. INPUT ARTIFACTS

### 4.1 INPUT — ECON_RESOURCE_REQUEST
**REQUIRED FIELDS**
- `er_id`
- `timestamp`
- `world_structure_graph_ref` (required)
- `world_lawset_ref` (required)
- `actor_map_ref` (civilizations/geopolitics) (recommended)
- `conflict_power_matrix_ref` (recommended)
- `resource_seed_list` (optional; otherwise engine proposes baseline set)
- `constraints_refs` (project/genre constraints)
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 5. OUTPUT ARTIFACTS

### 5.1 OUTPUT — RESOURCE_FLOW_MODEL
**REQUIRED FIELDS**
- `er_id`
- `resource_registry` (list of Resource Objects)
- `sources_and_sinks` (nodes categorized)
- `flow_graph` (list of Flow Edges)
- `production_chains` (list)
- `bottlenecks` (list: {what, why, impact})
- `logistics_constraints` (summary of time/cost/risk patterns)
- `allocation_rules` (who gets what and why; access-based)
- `black_market_channels` (list: leakage routes + actors)
- `stability_profile` (what keeps economy stable / what collapses it)
- `loophole_checks` (auto-detected free-resource issues)
- `trace_id` (if provided)

### 5.2 OUTPUT — ECON_RESOURCE_VERDICT
- `er_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 6. CORE OPERATIONS

- OP_01: DEFINE_RESOURCE_REGISTRY_AND_SCARCITY
- OP_02: MAP_SOURCES_SINKS_TO_WORLD_STRUCTURE
- OP_03: BUILD_FLOW_GRAPH
- OP_04: DEFINE_PRODUCTION_CHAINS_AND_BOTTLENECKS
- OP_05: DEFINE_ALLOCATION_AND_LEAKAGE_RULES
- OP_06: RUN_STABILITY_AND_LOOPHOLE_CHECKS
- OP_07: EMIT_RESOURCE_FLOW_MODEL

---

## 7. ACCESS MODEL

### WRITE
- Domain pipeline outputs only

### READ
- Conflict & Power Engine (war capacity + chokepoints)
- Geopolitics Engine (trade/sanctions leverage)
- Civilization Engine (institutions of allocation)
- Technology & Magic Engine (production possibilities)
- Environment & Ecology Engine (externalities/limits)
- Narrative engines (stakes from scarcity)

### DELETE
- Allowed for drafts; finalization per project governance

---

## 8. DEPENDENCIES

### REQUIRED
- World structure graph (routes and nodes)
- World lawset (production limits, illegal flows)

### FORBIDDEN
- Unlimited resources without costs (free lunch)
- Flows without capacity/time/risk
- Production chains with no inputs/infrastructure
- Black market absent in a world with restrictions (unless justified)
- Treating flow model as canon authority

---

## 9. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- No scarce resources defined
- No flow graph (economy not moving)
- No bottlenecks (world has no pressure points)
- Allocation rules undefined (who gets what is random)
- Contradictions with world laws (impossible production) without exceptions pricing

Reaction:
- Verdict INVALID (CRITICAL)
- Provide repairs: define scarcity, add flows, add bottlenecks, define allocation.

---

## 10. TRACE RULES

- trace_id optional unless orchestrator requires traced pipeline
- if present, propagate into geopolitics/conflict continuity references

---

## 11. NON-GOALS
- Does not require currency
- Does not simulate markets turn-by-turn
- Does not grant canon authority

---

## 12. FINAL STATEMENT

Economy is reality under scarcity.
Define flows and bottlenecks — and the world gains weight.

---

**STATUS:** Economy & Resource Engine v1.0  
**DOMAIN:** ACTIVE
