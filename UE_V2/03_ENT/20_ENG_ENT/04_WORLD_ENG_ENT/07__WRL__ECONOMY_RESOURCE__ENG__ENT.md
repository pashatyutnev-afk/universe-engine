# ECONOMY & RESOURCE ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/04_DOMAIN_WORLD_ENGINES/07__ECONOMY_RESOURCE_ENG.md
SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: ENGINE
FAMILY: 04_DOMAIN_WORLD_ENGINES
CLASS: DOMAIN (L2)
LEVEL: L2
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.DOM.WORLD.ECONOMY.RESOURCE.001
OWNER: SYSTEM
ROLE: Defines resource economy mechanics without currency: production/consumption, scarcity, logistics, allocation regimes, and constraints across epochs/regions. Produces deterministic resource models and flow constraints.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Economy & Resource Engine created: non-currency allocation model, resource taxonomy, flow constraints, scarcity dynamics, and epoch-scoped regimes."
- REASON: "World requires grounded resource mechanics; canon forbids currency for great civilizations."
- IMPACT: "Power/geopolitics/civilization become resource-consistent without money-based handwaving."
- CHANGE_ID: UE.CHG.2026-01-08.DOM.WORLD.ECONOMY.RESOURCE.001

---

## 0) PURPOSE (LAW)
This engine owns **economy as resources and allocation** (NOT currency):
- defines resource taxonomy (what matters and why)
- defines production/consumption/maintenance logic
- defines scarcity and bottleneck dynamics
- defines logistics and distribution constraints (routes, capacity)
- defines allocation regimes (how resources are assigned without money)
- defines epoch-scoped resource regimes and shocks (world-state)

Hard rule:
- Great civilizations in this universe do not use currency; economy must work without money primitives.

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- invent currency/price markets as primary mechanisms (FORBIDDEN for great civs)
- define geopolitical borders/alliances (06)
- define conflict escalation ladders (05)
- define detailed technology/magic systems (08) — consumes constraints
- define ecological/climate processes as primary (10)
- define character-level trade scenes (narrative)
- define world laws (02)

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- WORLD_STRUCTURE_MODEL
- WORLD_TOPOLOGY_PRIMITIVES
- WORLD_LAWSET
- TIMELINE_EPOCH_MODEL
- CIVILIZATION_MODEL_SET
- GEOPOLITICS_STATE_MODEL (optional but recommended)
- ECONOMY_SEEDS (optional)

PRODUCES:
- RESOURCE_TAXONOMY
- PRODUCTION_CONSUMPTION_MODEL
- LOGISTICS_FLOW_CONSTRAINTS
- ALLOCATION_REGIME_MODEL
- SCARCITY_BOTTLENECK_DYNAMICS

DEPENDS_ON:
- [04_DOMAIN_WORLD_ENGINES/02__WORLD_LAW_ENG, 04_DOMAIN_WORLD_ENGINES/03__TIMELINE_EPOCH_ENG, 04_DOMAIN_WORLD_ENGINES/04__CIVILIZATION_ENG, 04_DOMAIN_WORLD_ENGINES/06__GEOPOLITICS_ENG]

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/WORLD/ECONOMY_RESOURCES/
OPTIONAL:
- KB/ECONOMY_RESOURCES (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Resource: anything that is constrained and required for survival/capability (matter, energy, information, labor, access, time).
- Production: transformation of inputs into outputs (including maintenance).
- Consumption: depletion or usage rate per actor/system.
- Logistics: movement and storage constraints (capacity, routes, loss).
- Allocation Regime: rule system for deciding who gets what without currency.
- Scarcity: demand > supply or constraints prevent delivery.
- Bottleneck: a single constraint that dominates throughput (route, tech, institution, energy).

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- resource taxonomy + classification
- production/consumption rules
- logistics constraints and flow limits
- allocation regimes (non-currency)
- scarcity + bottleneck dynamics
- epoch/region scoped resource regimes

OUT OF SCOPE (HARD):
- political borders and treaties (06)
- conflict escalation design (05)
- tech/magic detailed catalog (08)
- ecology/climate primary models (10) (this engine consumes their constraints as inputs to production)
- “market price” mechanics as the main driver for great civs (FORBIDDEN)

COLLISION RULE:
- If question is “who controls the route/territory” → geopolitics engine
- If question is “how war escalates” → conflict/power engine
- If question is “what tech enables this production” → technology/magic engine
- If question is “environment changes production” → environment/ecology engine

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: RESOURCE_TAXONOMY exists; every resource has type and measurement proxy.
R2 (HARD) MUST: PRODUCTION_CONSUMPTION_MODEL defines at least one production chain per key resource category.
R3 (HARD) MUST: LOGISTICS_FLOW_CONSTRAINTS defines routes/capacity/loss and ties to topology/geopolitics.
R4 (HARD) MUST: ALLOCATION_REGIME_MODEL provides non-currency allocation rules for each civilization tier.
R5 (HARD) FORBIDDEN: introducing currency, prices, or “pay money” as primary mechanism for great civilizations.
R6 (HARD) MUST: scarcity/bottleneck dynamics declare triggers, signals, and consequences.
R7 (HARD) MUST: epoch-scoped variants exist OR explicitly declare economy is epoch-invariant with justification.
R8 (SOFT) SHOULD: include resilience strategies (buffers, redundancy, substitution).
R9 (HARD) MUST: economy outputs must not violate world laws and causality constraints.

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: RESOURCE_TAXONOMY
- MUST:
  - taxonomy_id
  - version
  - resources[] (non-empty)
  - categories[] (non-empty)
  - checks[] (non-empty)
- RESOURCE (minimum):
  - resource_id
  - name
  - category (enum: MATTER|ENERGY|INFORMATION|LABOR|ACCESS|TIME|MAGIC_MEDIUM)
  - scarcity_profile (enum: ABUNDANT|SEASONAL|LIMITED|RARE|CRITICAL)
  - measurement_proxy (how to estimate)
  - substitutable_with[] (optional)
  - constraints[] (law/tech/ecology constraints)
  - notes
- CATEGORY (minimum):
  - category_id
  - description
  - typical_bottlenecks[]
- CHECK (minimum):
  - check_id
  - description
  - severity (S0|S1|S2|S3)
- VALIDATION:
  - every resource has measurement_proxy
  - no undefined categories
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/WORLD/ECONOMY_RESOURCES/RESOURCE_TAXONOMY.md

ARTIFACT: PRODUCTION_CONSUMPTION_MODEL
- MUST:
  - pc_model_id
  - version
  - chains[] (non-empty)
  - consumers[] (optional but recommended)
  - checks[] (non-empty)
- CHAIN (minimum):
  - chain_id
  - output_resource_id
  - inputs[] (non-empty)
  - process_steps[] (non-empty)
  - capacity_limits[] (optional)
  - failure_modes[] (optional)
  - epoch_variants[] (optional)
  - notes
- INPUT (minimum):
  - resource_id
  - amount_proxy
  - criticality (LOW|MED|HIGH)
- STEP (minimum):
  - step_id
  - action
  - required_infrastructure (optional)
  - required_capability_tier (optional)
  - constraints[] (law/tech/ecology)
  - waste_or_loss (optional)
- CONSUMER (minimum):
  - consumer_id
  - actor_ref (civ/institution/region)
  - consumes[] (resource_id list)
  - baseline_rate_proxy
  - peaks[] (optional)
- CHECK (minimum):
  - check_id
  - description
  - severity
- VALIDATION:
  - chain references valid resource ids
  - at least one chain per critical resource category (or explicit exception)
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/WORLD/ECONOMY_RESOURCES/PRODUCTION_CONSUMPTION_MODEL.md

ARTIFACT: LOGISTICS_FLOW_CONSTRAINTS
- MUST:
  - logistics_id
  - version
  - routes[] (non-empty)
  - storage_nodes[] (optional)
  - constraints[] (non-empty)
  - checks[] (non-empty)
- ROUTE (minimum):
  - route_id
  - from_ref (territory/region)
  - to_ref (territory/region)
  - mode (enum: LAND|SEA|AIR|RIVER|SPACE|MAGIC_GATE|DATA_CHANNEL)
  - capacity_proxy
  - loss_proxy
  - control_dependency_ref (geopolitics control/border ids)
  - constraints[] (law/tech/ecology)
  - interdiction_risks[] (optional)
- CONSTRAINT (minimum):
  - c_id
  - description (testable)
  - severity (S0|S1|S2|S3)
  - detection_check (optional; required for S0)
- CHECK (minimum):
  - check_id
  - description
  - severity
- VALIDATION:
  - routes reference known topology/geopolitics entities
  - any S0 constraint has detection check
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/WORLD/ECONOMY_RESOURCES/LOGISTICS_FLOW_CONSTRAINTS.md

ARTIFACT: ALLOCATION_REGIME_MODEL
- MUST:
  - allocation_id
  - version
  - regimes[] (non-empty)
  - fairness_or_priority_rules[] (non-empty)
  - enforcement_refs[] (optional; institution refs)
  - checks[] (non-empty)
- REGIME (minimum):
  - regime_id
  - applies_to (civ_id or tier)
  - regime_type (enum: NEEDS_BASED|MERIT_TASK|CENTRAL_PLANNING|DISTRIBUTED_QUOTA|RITUAL_ALLOCATION|AI_OPTIMIZED|COMMONS_GOVERNANCE|HYBRID)
  - decision_unit (who decides)
  - allocation_rules[] (non-empty)
  - scarcity_mode_rules[] (non-empty)
  - abuse_vectors[] (optional)
  - notes
- RULE (minimum):
  - rule_id
  - condition (testable)
  - allocation_action (what gets allocated)
  - priority (0..100)
  - constraints[] (law/civ constraints)
- SCARCITY MODE RULE (minimum):
  - mode_id
  - trigger (resource scarcity signal)
  - action (rationing/priority shift/substitution)
  - exit_condition
- VALIDATION:
  - no “pay currency” actions for great civs
  - scarcity rules exist per regime
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/WORLD/ECONOMY_RESOURCES/ALLOCATION_REGIME_MODEL.md

ARTIFACT: SCARCITY_BOTTLENECK_DYNAMICS
- MUST:
  - scarcity_id
  - version
  - bottlenecks[] (non-empty)
  - shocks[] (optional)
  - resilience_strategies[] (optional)
  - checks[] (non-empty)
- BOTTLENECK (minimum):
  - bottleneck_id
  - resource_or_route_ref
  - type (ROUTE|PRODUCTION_STEP|INSTITUTION|ENERGY|INFORMATION|ENVIRONMENT)
  - trigger_signals[] (non-empty)
  - consequences[] (non-empty)
  - mitigation_options[] (optional)
  - severity (S0|S1|S2|S3)
- SHOCK (minimum):
  - shock_id
  - epoch_id (optional)
  - description (testable)
  - affected_refs[] (resources/routes/civs)
  - cascade_rules[] (optional)
- CHECK (minimum):
  - check_id
  - description
  - severity
- VALIDATION:
  - each bottleneck has trigger_signals + consequences
  - S0 bottlenecks have mitigation options OR explicit “unmitigable” rationale
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/WORLD/ECONOMY_RESOURCES/SCARCITY_BOTTLENECK_DYNAMICS.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Validate inputs:
   - topology + law + timeline + civ models exist
2) Build resource taxonomy:
   - classify resources, add proxies and constraints
3) Build production chains:
   - map input→steps→output; define capacity limits
4) Build logistics constraints:
   - routes, capacity, loss, control dependencies
5) Build allocation regimes:
   - non-currency decision rules + scarcity modes
6) Build scarcity/bottleneck dynamics:
   - triggers, consequences, mitigation
7) Epoch binding:
   - attach epoch variants or declare invariance
8) Run checks:
   - law compliance, no currency introduction, route references valid
9) Emit artifacts

---

## 8) S0 BLOCKERS (STOP)
- S0-1: any currency/price mechanism used as primary allocation for great civilizations.
- S0-2: logistics route references unknown topology/geo entities.
- S0-3: S0 constraint lacks detection check.
- S0-4: production chain violates world laws/tech constraints.
- S0-5: scarcity dynamics are missing triggers or consequences for critical bottlenecks.

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- laws (02), epochs (03), civs (04), geopolitics (06)

Downstream consumers:
- conflict/power engine (power sources and pressures reference scarcity)
- technology/magic engine (enables production/logistics capabilities)
- environment/ecology engine (sets environmental constraints and shocks)
- narrative engines (can use scarcity as driver, but must respect regimes)

Governance:
- if economy model changes hard canon constraints (e.g., “currency forbidden”) → governance pipeline + audit.

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Family template:
  04_DOMAIN_WORLD_ENGINES/00__TEMPLATE__ENGINE__DOMAIN_WORLD_ENGINES.md

--- END.

LOCK: OPEN
