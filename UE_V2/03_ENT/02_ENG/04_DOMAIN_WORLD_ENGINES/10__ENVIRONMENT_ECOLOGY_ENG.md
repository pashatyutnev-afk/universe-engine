# ENVIRONMENT & ECOLOGY ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/04_DOMAIN_WORLD_ENGINES/10__ENVIRONMENT_ECOLOGY_ENG.md
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
UID: UE.ENG.DOM.WORLD.ENV.ECOLOGY.001
OWNER: SYSTEM
ROLE: Defines environment and ecology as deterministic world-state: biomes, climate drivers, hazards, carrying capacity, ecological constraints, and epoch-scoped changes impacting civilization/economy/conflict.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Environment & Ecology Engine created: biome/ecology model, hazard catalog, carrying capacity constraints, and epoch environmental change map."
- REASON: "World requires explicit environmental limits and shocks for realism and deterministic downstream constraints."
- IMPACT: "Economy/logistics/settlement/conflict become environment-consistent; avoids handwavy worlds."
- CHANGE_ID: UE.CHG.2026-01-08.DOM.WORLD.ENV.ECOLOGY.001

---

## 0) PURPOSE (LAW)
This engine owns **environment + ecology** as world-state constraints:
- biomes and environmental zones
- climate/season drivers (as constraints, not full physics)
- hazards (natural, biological, magical-if-law-allows)
- carrying capacity (what regions can sustain)
- ecological dependencies (food webs in coarse form)
- epoch-scoped environmental changes and shocks

Hard rule:
- This engine provides constraints and drivers; it must be compatible with `WORLD_LAWSET`.

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- define world physical laws or cosmology (02)
- define civilization institutions/norms (04)
- define geopolitics control maps (06)
- define economy allocation regimes (07)
- define detailed tech/magic capability catalog (08) — only references environmental constraints
- define narrative “atmosphere” (style engines)

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- WORLD_STRUCTURE_MODEL
- WORLD_TOPOLOGY_PRIMITIVES
- WORLD_LAWSET
- TIMELINE_EPOCH_MODEL
- ENV_ECO_SEEDS (optional)

PRODUCES:
- BIOME_ECOLOGY_MODEL
- ENVIRONMENTAL_CONSTRAINTS
- HAZARD_CATALOG
- CARRYING_CAPACITY_MAP
- ENV_CHANGE_EPOCH_MAP

DEPENDS_ON:
- [04_DOMAIN_WORLD_ENGINES/01__WORLD_STRUCTURE_ENG, 04_DOMAIN_WORLD_ENGINES/02__WORLD_LAW_ENG, 04_DOMAIN_WORLD_ENGINES/03__TIMELINE_EPOCH_ENG]

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/WORLD/ENV_ECOLOGY/
OPTIONAL:
- KB/ENV_ECOLOGY (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Biome: region type with stable climate/ecology traits (desert, tundra, jungle, etc.).
- Ecological Constraint: limit on habitation/production/movement due to environment.
- Hazard: event/process that damages capacity or causes loss (storm, disease, drought, toxin, predator pressure).
- Carrying Capacity: sustainable population/production ceiling given constraints.
- Environmental Shock: epoch-scoped disruption (ice age, blight, volcanic winter, magic storm) consistent with laws.
- Driver: high-level factor (seasonality, currents, altitude) used as constraints/proxies.

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- biome mapping and traits
- constraints that affect economy/logistics/civs
- hazard definitions with triggers and signals
- carrying capacity proxies per region
- epoch environmental changes and shocks

OUT OF SCOPE (HARD):
- economy resource allocation rules (07)
- geopolitics control/borders (06)
- tech/magic internal mechanisms (08) (environment only constrains)
- narrative tone/atmosphere (06 style engines)
- “full climate simulation” (this engine is coarse deterministic constraints)

COLLISION RULE:
- If a change is “physical possibility” → world law engine
- If it’s “resource scarcity outcomes” → economy/resource engine consumes constraints
- If it’s “movement feasibility due to war/politics” → geopolitics/conflict engines
- If it’s “mood/feel” → style engines

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: BIOME_ECOLOGY_MODEL exists; each region binds to a biome or marks unknown.
R2 (HARD) MUST: ENVIRONMENTAL_CONSTRAINTS lists explicit constraints usable by other engines.
R3 (HARD) MUST: HAZARD_CATALOG defines triggers, signals, severity, and mitigation options (or unmitigable note).
R4 (HARD) MUST: CARRYING_CAPACITY_MAP provides proxies per region/biome.
R5 (HARD) MUST: ENV_CHANGE_EPOCH_MAP defines epoch-scoped environmental shifts and shocks.
R6 (HARD) FORBIDDEN: environment changes that violate world laws/causality.
R7 (SOFT) SHOULD: include seasonality windows relevant to logistics/war.
R8 (HARD) MUST: every S0 hazard has detection signals and mitigation/avoidance logic.

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: BIOME_ECOLOGY_MODEL
- MUST:
  - biome_model_id
  - version
  - biomes[] (non-empty)
  - region_bindings[] (non-empty)
  - lawset_ref
  - checks[] (non-empty)
- BIOME (minimum):
  - biome_id
  - name
  - climate_traits[] (non-empty)
  - ecology_traits[] (non-empty)
  - movement_modifiers[] (optional)
  - production_modifiers[] (optional)
  - notes
- REGION BINDING (minimum):
  - region_ref (region/place id)
  - biome_id
  - confidence (0..100)
  - notes
- CHECK (minimum):
  - check_id
  - description
  - severity (S0|S1|S2|S3)
- VALIDATION:
  - all biome ids referenced exist
  - confidence 0..100
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/WORLD/ENV_ECOLOGY/BIOME_ECOLOGY_MODEL.md

ARTIFACT: ENVIRONMENTAL_CONSTRAINTS
- MUST:
  - constraints_id
  - version
  - constraints[] (non-empty)
  - checks[] (non-empty)
- CONSTRAINT (minimum):
  - constraint_id
  - applies_to (region/biome/global)
  - type (enum: WATER|FOOD|TEMPERATURE|DISEASE|ALTITUDE|STORM|RADIATION|TOXIN|PREDATION|MAGIC_FIELD|SEASONALITY)
  - description (testable)
  - severity (S0|S1|S2|S3)
  - detection_signals[] (non-empty if severity S0)
  - downstream_impacts[] (economy/logistics/civ/conflict)
  - mitigation_options[] (optional)
- VALIDATION:
  - S0 constraints have detection_signals
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/WORLD/ENV_ECOLOGY/ENVIRONMENTAL_CONSTRAINTS.md

ARTIFACT: HAZARD_CATALOG
- MUST:
  - hazard_catalog_id
  - version
  - hazards[] (non-empty)
  - checks[] (non-empty)
- HAZARD (minimum):
  - hazard_id
  - name
  - hazard_type (enum: CLIMATE|GEOLOGIC|BIOLOGIC|HYDROLOGIC|FIRE|TOXIN|MAGIC_ANOMALY)
  - trigger_conditions[] (non-empty)
  - early_signals[] (non-empty)
  - impact_profile (testable)
  - severity (S0|S1|S2|S3)
  - affected_refs[] (regions/biomes)
  - mitigation_options[] (optional)
  - recovery_time_proxy (optional)
- VALIDATION:
  - early_signals non-empty
  - trigger_conditions non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/WORLD/ENV_ECOLOGY/HAZARD_CATALOG.md

ARTIFACT: CARRYING_CAPACITY_MAP
- MUST:
  - capacity_id
  - version
  - entries[] (non-empty)
  - checks[] (non-empty)
- ENTRY (minimum):
  - region_or_biome_ref
  - sustenance_resources[] (resource ids optional)
  - population_capacity_proxy (numeric or relative)
  - production_capacity_proxy (optional)
  - limiting_factors[] (non-empty)
  - seasonality_windows[] (optional)
  - notes
- LIMITING FACTOR (minimum):
  - factor_id
  - type (WATER|SOIL|TEMP|DISEASE|ROUTES|PREDATORS|MAGIC_FIELD|ALTITUDE|STORMS)
  - description (testable)
- VALIDATION:
  - each entry has at least one limiting factor
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/WORLD/ENV_ECOLOGY/CARRYING_CAPACITY_MAP.md

ARTIFACT: ENV_CHANGE_EPOCH_MAP
- MUST:
  - env_change_id
  - version
  - epoch_changes[] (non-empty)
  - checks[] (non-empty)
- EPOCH CHANGE (minimum):
  - epoch_id
  - changes[] (non-empty)
  - shocks[] (optional)
  - notes
- CHANGE (minimum):
  - change_id
  - affected_ref (region/biome/global)
  - type (enum: SHIFT|DEGRADATION|RECOVERY|NEW_HAZARD|REMOVED_HAZARD|SEASONALITY_CHANGE)
  - description (testable)
  - cause_ref (optional)
  - downstream_impacts[] (economy/logistics/civ/conflict)
- SHOCK (minimum):
  - shock_id
  - name
  - duration_proxy
  - severity (S0|S1|S2|S3)
  - early_signals[]
  - mitigation_notes (optional)
- VALIDATION:
  - epoch ids exist
  - each epoch change has at least one change
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/WORLD/ENV_ECOLOGY/ENV_CHANGE_EPOCH_MAP.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Validate inputs:
   - topology + laws + epochs exist
2) Define biomes:
   - biome set with traits and modifiers
3) Bind regions to biomes:
   - assign biome ids with confidence
4) Define constraints:
   - explicit constraints with severity and detection signals
5) Define hazards:
   - hazard catalog with triggers/signals/impacts
6) Define carrying capacity:
   - region/biome proxies + limiting factors
7) Bind to epochs:
   - environmental changes and shocks per epoch
8) Run checks:
   - law compliance, missing signals for S0, invalid region refs
9) Emit artifacts

---

## 8) S0 BLOCKERS (STOP)
- S0-1: environment change violates world laws or causality constraints.
- S0-2: S0 hazard/constraint lacks early signals (detection).
- S0-3: region bindings reference unknown topology ids.
- S0-4: carrying capacity entries missing limiting factors.
- S0-5: epoch changes reference unknown epoch ids.

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- world structure/topology (01)
- world laws (02)
- epochs (03)

Downstream consumers:
- economy/resource engine (uses constraints for production/logistics)
- geopolitics engine (routes and borders affected by hazards)
- conflict/power engine (seasonality, scarcity, terrain/hazard constraints)
- civilization engine (settlement patterns, institutional responses)
- technology/magic engine (environmental constraints and side effects)

Governance:
- if environmental constraints become hard canon invariants → route via governance pipeline when LOCK becomes FIXED.

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Family template:
  04_DOMAIN_WORLD_ENGINES/00__TEMPLATE__ENGINE__DOMAIN_WORLD_ENGINES.md

--- END.

LOCK: OPEN
