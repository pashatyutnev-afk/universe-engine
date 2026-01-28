# GEOPOLITICS ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/04_DOMAIN_WORLD_ENGINES/06__GEOPOLITICS_ENG.md
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
UID: UE.ENG.DOM.WORLD.GEOPOLITICS.001
OWNER: SYSTEM
ROLE: Defines geopolitical state: territories, borders, control regimes, alliances/treaties, strategic interests, and region graphs across epochs (world-state, not narrative).

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Geopolitics Engine created: territory/border model, control regimes, alliance/treaty schema, and epoch-scoped geo state."
- REASON: "World conflicts and civilizations require explicit control maps and strategic constraints."
- IMPACT: "Geopolitical consistency becomes deterministic; downstream narrative and conflict planning stays grounded."
- CHANGE_ID: UE.CHG.2026-01-08.DOM.WORLD.GEOPOLITICS.001

---

## 0) PURPOSE (LAW)
This engine owns **geopolitics as world-state**:
- territories and regions (as control units)
- borders and border types (hard/soft/porous)
- control regimes (who controls what and how)
- alliances/treaties and diplomatic constraints
- strategic interests and red lines (at civilization scale)
- epoch-scoped geopolitical states and transitions

Hard rule:
- This is not “plot politics”; it is the world map of control and constraints.

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- define world topology primitives (01) — consumes them
- define world laws/possibility (02)
- define epoch ordering rules (03) — consumes timeline epochs
- define civilization internals (04) — consumes civ models
- define conflict escalation mechanics (05) — consumes conflict-power outputs
- define economy/resource accounting (07) — only references resource constraints
- define character-level politics/speech (character family)
- define production depiction (production)

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- WORLD_STRUCTURE_MODEL
- WORLD_TOPOLOGY_PRIMITIVES
- WORLD_LAWSET
- TIMELINE_EPOCH_MODEL
- CIVILIZATION_MODEL_SET
- INSTITUTION_MODEL_SET (optional)
- POWER_SOURCE_MODEL (optional but recommended)
- LEVERAGE_PRESSURE_MAP (optional)
- ESCALATION_LADDER_SET (optional)
- GEOPOLITICS_SEEDS (optional)

PRODUCES:
- GEOPOLITICS_STATE_MODEL
- TERRITORY_BORDER_MAP
- ALLIANCE_TREATY_REGISTRY

DEPENDS_ON:
- [04_DOMAIN_WORLD_ENGINES/01__WORLD_STRUCTURE_ENG, 04_DOMAIN_WORLD_ENGINES/03__TIMELINE_EPOCH_ENG, 04_DOMAIN_WORLD_ENGINES/04__CIVILIZATION_ENG, 04_DOMAIN_WORLD_ENGINES/05__CONFLICT_POWER_ENG]

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/WORLD/GEOPOLITICS/
OPTIONAL:
- KB/GEOPOLITICS (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Territory Unit: a stable control area (region/place group) used for governance and conflict.
- Border: a boundary between territory units with permeability constraints.
- Control Regime: the mechanism of control (direct rule, vassal, occupation, contested, influence).
- Treaty: formalized agreement with obligations and enforcement.
- Alliance: relationship between civilizations with scope, duration, and triggers.
- Strategic Interest: a stable priority (resource, security, route, ideology) driving geopolitics.
- Epoch Geo State: mapping of control/borders/alliances scoped per epoch.

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- territories + borders + control regimes
- alliances/treaties registry and constraints
- strategic interests and red lines per civilization
- epoch-scoped geo state and change constraints

OUT OF SCOPE (HARD):
- civilization internal institutions (04)
- conflict escalation mechanics (05)
- resource production/distribution accounting (07)
- tech/magic internals (08)
- narrative plotting of coups/episodes (narrative)

COLLISION RULE:
- If question is “why conflict escalates” → conflict & power engine
- If question is “who has which internal institution power” → civilization engine
- If question is “can this movement happen physically/magically” → world law engine
- If question is “resource flows cause this” → economy/resource engine

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: TERRITORY_BORDER_MAP defines territory units and border types with constraints.
R2 (HARD) MUST: GEOPOLITICS_STATE_MODEL defines who controls what, per epoch, with regime type.
R3 (HARD) MUST: ALLIANCE_TREATY_REGISTRY defines obligations, triggers, and enforcement for agreements.
R4 (HARD) MUST: strategic interests per civilization must be explicit and testable (no vague “wants power”).
R5 (HARD) MUST: any geo state change must align with timeline transitions and not violate world laws.
R6 (HARD) FORBIDDEN: narrative constructs as geo boundaries (“Act 2 border”).
R7 (HARD) MUST: contested territories must declare contest mechanisms (not just label).
R8 (SOFT) SHOULD: include information constraint notes (fog-of-war) without contradicting causality constraints.

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: TERRITORY_BORDER_MAP
- MUST:
  - map_id
  - version
  - territories[] (non-empty)
  - borders[] (non-empty)
  - topology_ref
  - checks[] (non-empty)
- TERRITORY (minimum):
  - territory_id
  - name
  - scope (GLOBAL|REGIONAL|LOCAL)
  - region_refs[] (non-empty; region/place ids)
  - strategic_value_tags[] (optional)
  - notes
- BORDER (minimum):
  - border_id
  - territory_a
  - territory_b
  - border_type (enum: HARD|SOFT|POROUS|NATURAL|MAGICAL|DEMILITARIZED|CONTESTED)
  - permeability (0..100)
  - constraints[] (law/civ constraints)
  - crossing_rules[] (optional)
  - notes
- CHECK (minimum):
  - check_id
  - description
  - severity (S0|S1|S2|S3)
- VALIDATION:
  - region_refs exist in topology
  - borders reference existing territory ids
  - permeability is 0..100
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/WORLD/GEOPOLITICS/TERRITORY_BORDER_MAP.md

ARTIFACT: GEOPOLITICS_STATE_MODEL
- MUST:
  - geo_state_id
  - version
  - epoch_states[] (non-empty)
  - interests[] (non-empty recommended)
  - red_lines[] (optional)
  - checks[] (non-empty)
- EPOCH_STATE (minimum):
  - epoch_id
  - control_entries[] (non-empty)
  - border_changes[] (optional)
  - notes
- CONTROL_ENTRY (minimum):
  - territory_id
  - controller_ref (civ_id/institution id)
  - control_regime (enum: DIRECT|VASSAL|OCCUPATION|INFLUENCE|CONTESTED|AUTONOMOUS|PROTECTORATE)
  - legitimacy (0..100)
  - enforcement_mechanism (short)
  - contesters[] (optional)
  - constraints[] (law/epoch constraints)
  - notes
- BORDER_CHANGE (minimum):
  - border_id
  - from_type (optional)
  - to_type
  - reason_ref (transition/cause id)
  - notes
- INTEREST (minimum):
  - civ_id
  - interest_id
  - type (enum: SECURITY|RESOURCE|ROUTE|BUFFER|IDEOLOGY|PRESTIGE|SURVIVAL|HEGEMONY)
  - target_ref (territory/region/civ)
  - priority (0..100)
  - justification (testable)
  - red_line_trigger (optional)
- CHECK (minimum):
  - check_id
  - description
  - severity
- VALIDATION:
  - epoch_id exists in timeline
  - each control entry references existing territory
  - contested entries include contesters and contest mechanism note (else S1)
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/WORLD/GEOPOLITICS/GEOPOLITICS_STATE_MODEL.md

ARTIFACT: ALLIANCE_TREATY_REGISTRY
- MUST:
  - registry_id
  - version
  - agreements[] (non-empty)
  - enforcement_rules[] (optional)
  - checks[] (non-empty)
- AGREEMENT (minimum):
  - agreement_id
  - type (enum: ALLIANCE|TREATY|PACT|NON_AGGRESSION|TRADE_ACCESS|DEFENSE_GUARANTEE|CEASEFIRE|VASSALAGE_CONTRACT)
  - parties[] (civ ids)
  - scope (GLOBAL|REGIONAL|LOCAL)
  - start_epoch_id (optional)
  - end_epoch_id (optional)
  - obligations[] (non-empty)
  - triggers[] (optional)
  - breach_consequences[] (non-empty recommended)
  - enforcement (who enforces, how)
  - notes
- OBLIGATION (minimum):
  - obligation_id
  - description (testable)
  - cost (what it costs)
  - enforcement_trigger (when enforced)
- BREACH (minimum):
  - breach_id
  - breach_type
  - consequence (sanctions/war/withdrawal)
  - severity (S0|S1|S2|S3)
  - route_to (engine pointer if it triggers conflict ladder)
- CHECK (minimum):
  - check_id
  - description
  - severity
- VALIDATION:
  - agreements must list parties and obligations
  - epoch bounds must be consistent with timeline ordering
  - any S0 breach must define route_to
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/WORLD/GEOPOLITICS/ALLIANCE_TREATY_REGISTRY.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Validate inputs:
   - topology, timeline, civ models exist
2) Define territories:
   - cluster topology regions into territory units
3) Define borders:
   - set border types + permeability + constraints
4) Define epoch geopolitical states:
   - assign controllers and regimes per epoch
5) Define interests and red lines per civ:
   - priorities and triggers
6) Define agreements:
   - alliances/treaties with obligations and breach consequences
7) Run checks:
   - timeline consistency, law compliance, contested territory completeness
8) Emit artifacts

---

## 8) S0 BLOCKERS (STOP)
- S0-1: epoch state references unknown epoch_id.
- S0-2: control entry violates world laws or epoch constraints without exception protocol.
- S0-3: agreements lack obligations or parties.
- S0-4: border map has invalid topology references.
- S0-5: contested control has no defined contest mechanism (if severity escalates to S0).

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- topology (01)
- laws (02)
- epochs (03)
- civs (04)
- conflict/power mechanics (05)

Downstream consumers:
- narrative engines (choose story windows inside geo state)
- conflict engine (uses treaty breaches as escalation triggers)
- economy/resource engine (ties resources/routes to territories)
- environment/ecology engine (geography constraints)

Governance:
- changes to territory ids or core control regimes may be canon-impacting; route via governance if FIXED/ACTIVE canon artifacts are affected.

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Family template:
  04_DOMAIN_WORLD_ENGINES/00__TEMPLATE__ENGINE__DOMAIN_WORLD_ENGINES.md

--- END.

LOCK: OPEN
