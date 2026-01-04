# 🧬 TECHNOLOGY & MAGIC ENGINE
## Canonical Engine Specification  
**LEVEL: L2 · DOMAIN ENGINE · CAPABILITIES & LIMITS · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 08__TECHNOLOGY_MAGIC_ENG.md
- ENGINE_ID: L2-DOM-TECHNOLOGY-MAGIC-ENGINE-008
- UID: UE.ENT.ENG.DOM.WORLD.TECHNOLOGY_MAGIC
- NAME: Technology & Magic Engine
- CLASS: Domain Engine
- DOMAIN: World
- CATEGORY: Capability Matrix, Tech Levels, Magic Rules & Exploit Prevention
- LEVEL: L2
- STATUS: FINAL
- FAILURE_MODE: fail-closed (for capability realism)
- EDITABLE: true
- BYPASS_ALLOWED: false (within world pipeline)

### ABSOLUTE RULE
> A capability without a limit becomes a cheat code.

---

## 1. PURPOSE

Technology & Magic Engine defines **what can be done** in the world and at what cost.

It produces:
- **CAPABILITY_MATRIX** (capabilities × limits × costs × availability)
- tech/magic levels by epoch and by actor
- prerequisites (infrastructure, knowledge, resources)
- side-effects and failure modes
- exploit checks (infinite energy, infinite healing, instant travel, etc.)

This engine binds power to laws and scarcity.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define capability categories (tech, magic, hybrid)
- Define tech/magic levels by epoch and civilization/actor
- Define prerequisites and dependencies (resources, institutions, training)
- Define limits (range, time, accuracy, scale) and costs (energy, risk, backlash)
- Define failure modes and safety constraints
- Define countermeasures (what can stop a capability)
- Validate compatibility with world lawset, timeline, economy, conflict matrix
- Detect exploit loopholes and propose mitigations

### OUT-OF-SCOPE (FORBIDDEN)
- World topology (World Structure Engine)
- Deep culture/institutions (Civilization Engine) beyond adoption rules
- War escalation logic (Conflict & Power Engine)
- Canon authority decisions (Governance)

---

## 3. CAPABILITY MODEL

### 3.1 Capability Categories (fixed)
- TRANSPORT (movement, travel)
- COMMUNICATION (signals, telepathy, networks)
- ENERGY (generation, storage, transfer)
- CONSTRUCTION (manufacture, fabrication)
- MEDICAL (healing, augmentation)
- WEAPONRY (damage systems)
- DEFENSE (shields, fortifications, countermeasures)
- SENSING (surveillance, detection)
- COMPUTATION (AI, prediction, control systems)
- REALITY_MANIPULATION (magic-only or extreme tech; must be HARD-limited)

### 3.2 Capability Object (required fields)
- `cap_id`
- `name`
- `category`
- `type` = TECH | MAGIC | HYBRID
- `description` (1–2 sentences)
- `availability` (who has it: actors/regions/epochs)
- `prerequisites` (resources, knowledge, infrastructure)
- `limits` (range/scale/time/precision)
- `costs` (energy, materials, risk, social/legal)
- `side_effects` (optional)
- `failure_modes` (optional)
- `countermeasures` (how it is stopped)
- `exploit_risk` = LOW | MEDIUM | HIGH
- `notes`

### 3.3 Tech/Magic Level (0..10)
- 0 = primitive / none
- 10 = near-total mastery (must still obey HARD world laws)

Levels must be defined by:
- epoch (timeline model)
- actor (civilization/geopolitics)

---

## 4. INPUT ARTIFACTS

### 4.1 INPUT — TECH_MAGIC_REQUEST
**REQUIRED FIELDS**
- `tm_id`
- `timestamp`
- `world_lawset_ref` (required)
- `timeline_model_ref` (recommended)
- `civilization_passports_refs` (recommended)
- `economy_resource_model_ref` (recommended)
- `conflict_power_matrix_ref` (recommended)
- `tech_magic_presence` (none/tech/magic/both)
- `constraints_refs` (project/genre constraints)
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 5. OUTPUT ARTIFACTS

### 5.1 OUTPUT — CAPABILITY_MATRIX
**REQUIRED FIELDS**
- `tm_id`
- `capability_registry` (list of Capability Objects)
- `level_map_by_epoch` (epoch_id → level 0..10, notes)
- `level_map_by_actor` (actor_id → level 0..10, notes)
- `prereq_dependency_graph` (capability → prerequisites)
- `countermeasure_library` (capability → counters)
- `legal_social_constraints` (what’s banned/restricted and why)
- `exploit_checks` (auto-detected loopholes + fixes)
- `compatibility_checks` (lawset/scarcity/timeline alignment)
- `trace_id` (if provided)

### 5.2 OUTPUT — TECH_MAGIC_VERDICT
- `tm_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 6. CORE OPERATIONS

- OP_01: DEFINE_CAPABILITY_CATEGORIES_AND_REGISTRY
- OP_02: MAP_LEVELS_BY_EPOCH_AND_ACTOR
- OP_03: DEFINE_PREREQUISITES_LIMITS_COSTS
- OP_04: DEFINE_FAILURE_MODES_AND_COUNTERMEASURES
- OP_05: RUN_EXPLOIT_AND_COMPATIBILITY_CHECKS
- OP_06: EMIT_CAPABILITY_MATRIX

---

## 7. ACCESS MODEL

### WRITE
- Domain pipeline outputs only

### READ
- Conflict & Power Engine (what warfare is possible)
- Geopolitics Engine (leverage via tech denial)
- Economy & Resource Engine (production feasibility)
- World Law Engine (hard constraints)
- Timeline & Epoch Engine (tech progression)
- Validation engines (scientific plausibility)

### DELETE
- Allowed for drafts; finalization per project governance

---

## 8. DEPENDENCIES

### REQUIRED
- World lawset (hard limits)
- Constraints (genre/realism)

### FORBIDDEN
- Capabilities with no limits/costs
- Instant travel/instant healing/infinite energy without HARD pricing and counters
- Level 10 capability that violates HARD world laws
- Capability availability “everyone has everything”
- Treating capability matrix as canon authority

---

## 9. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- No capability registry (undefined world abilities)
- Many HIGH exploit_risk capabilities with no mitigation
- Contradictions with scarcity (advanced tech everywhere with no infrastructure)
- No counters (unstoppable powers)
- Epoch levels inconsistent with timeline (regressions without cause)

Reaction:
- Verdict INVALID (CRITICAL)
- Provide repairs: add limits/costs/counters, align levels to epochs, fix infrastructure dependencies.

---

## 10. TRACE RULES

- trace_id optional unless orchestrator requires traced pipeline
- if present, propagate into conflict/economy/geopolitics references

---

## 11. NON-GOALS
- Does not simulate R&D progress
- Does not write spell lists or weapon catalogs as canon
- Does not grant canon authority

---

## 12. FINAL STATEMENT

Capabilities shape power.
Limits shape meaning.

---

**STATUS:** Technology & Magic Engine v1.0  
**DOMAIN:** ACTIVE
