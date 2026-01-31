# CONFLICT & POWER ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/04_DOMAIN_WORLD_ENGINES/05__CONFLICT_POWER_ENG.md
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
UID: UE.ENG.DOM.WORLD.CONFLICT.POWER.001
OWNER: SYSTEM
ROLE: Defines world-scale conflict and power dynamics: power sources, leverage maps, escalation ladders, conflict archetypes, resolution constraints. Produces deterministic conflict-power models scoped by epoch/region.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Conflict & Power Engine created: power sources, leverage map, escalation ladder, conflict archetypes, and resolution constraints."
- REASON: "Geopolitics and narrative conflict require a stable world-power mechanics layer."
- IMPACT: "Conflicts become consistent, scalable, and compatible with civilization/economy/law constraints."
- CHANGE_ID: UE.CHG.2026-01-08.DOM.WORLD.CONFLICT.POWER.001

---

## 0) PURPOSE (LAW)
This engine owns **conflict + power mechanics** at world scale:
- defines what power is made of (sources)
- defines leverage/pressure mechanisms (who can force what)
- defines escalation ladders (how conflicts intensify)
- defines conflict archetypes and typical trajectories
- defines resolution constraints (what endings are possible in this world)

Hard rule:
- This is NOT narrative scene conflict; it is world mechanics and constraints.

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- define the world structure/topology (01)
- define possibility laws/casuality (02)
- define the world timeline (03)
- define geopolitics state (borders/treaties) as primary (06 owns)
- define economy/resource accounting as primary (07 owns)
- define character-level psychology/motivation/conflict (character family)
- define event primitives like “turning point/climax” (expression family)
- define production depiction (production family)

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- WORLD_STRUCTURE_MODEL
- WORLD_TOPOLOGY_PRIMITIVES
- WORLD_LAWSET
- CAUSALITY_CONSTRAINTS
- TIMELINE_EPOCH_MODEL
- CIVILIZATION_MODEL_SET
- INSTITUTION_MODEL_SET (optional but recommended)
- ECONOMY_RESOURCE_MODEL (optional if available)
- CONFLICT_SEEDS (optional)

PRODUCES:
- POWER_SOURCE_MODEL
- LEVERAGE_PRESSURE_MAP
- ESCALATION_LADDER_SET
- CONFLICT_ARCHETYPE_SET
- RESOLUTION_CONSTRAINTS

DEPENDS_ON:
- [04_DOMAIN_WORLD_ENGINES/02__WORLD_LAW_ENG, 04_DOMAIN_WORLD_ENGINES/03__TIMELINE_EPOCH_ENG, 04_DOMAIN_WORLD_ENGINES/04__CIVILIZATION_ENG]

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/WORLD/CONFLICT_POWER/
OPTIONAL:
- KB/CONFLICT_POWER (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Power Source: a stable contributor to capability to impose outcomes (resources, legitimacy, force, tech, info, alliances).
- Leverage: ability to change another actor’s incentives/constraints.
- Pressure: applied leverage over time (sanctions, blockades, propaganda, force posture).
- Escalation Ladder: ordered states of intensification with triggers and constraints.
- Conflict Archetype: reusable conflict pattern (succession, resource contest, ideological split, independence, proxy war).
- Resolution Constraint: world-law and capability limits on what conflict outcomes are achievable.

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- power sources and conversion rules
- leverage/pressure mechanisms
- escalation ladders and triggers
- conflict archetypes at civ/region/global scale
- resolution constraints consistent with world laws + civ capabilities

OUT OF SCOPE (HARD):
- geopolitics mapping of borders/treaties (06)
- economic production/distribution accounting (07)
- tech/magic detailed implementation (08)
- character interpersonal conflict mechanics (character)
- narrative event beats (expression/narrative)

COLLISION RULE:
- If the question is “who controls which territory right now” → geopolitics engine
- If the question is “what resources enable this” → economy engine (this engine references it as power sources)
- If the question is “is this physically possible” → world law engine
- If the question is “scene-level escalation” → expression + narrative engines

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: POWER_SOURCE_MODEL defines sources and how they translate into capability.
R2 (HARD) MUST: LEVERAGE_PRESSURE_MAP defines mechanisms + conditions + targets (civ/institution/region).
R3 (HARD) MUST: ESCALATION_LADDER_SET defines ordered escalation states with triggers and constraints.
R4 (HARD) MUST: CONFLICT_ARCHETYPE_SET includes at least 5 archetypes with required inputs and likely outcomes.
R5 (HARD) MUST: RESOLUTION_CONSTRAINTS enumerates allowed endings given laws + capabilities (no deus ex machina).
R6 (HARD) FORBIDDEN: narrative constructs as escalation states (e.g., “Act 2”).
R7 (HARD) MUST: all outputs must be epoch-aware (either per-epoch variants or explicit “epoch invariant”).
R8 (HARD) MUST: power models must not contradict world laws/causality.
R9 (SOFT) SHOULD: include “misperception / fog-of-war” rules as information constraints (still testable).

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: POWER_SOURCE_MODEL
- MUST:
  - power_model_id
  - version
  - sources[] (non-empty)
  - conversion_rules[] (non-empty)
  - epoch_variants[] (optional)
  - checks[] (non-empty)
- SOURCE (minimum):
  - source_id
  - name
  - type (enum: FORCE|LEGITIMACY|RESOURCES|INFORMATION|TECH|ALLIANCE|GEOGRAPHY|MAGIC_ACCESS|INSTITUTIONAL_CONTROL)
  - description (testable)
  - measurement_proxy (how you estimate it)
  - constraints[] (law/civ constraints)
- CONVERSION RULE (minimum):
  - rule_id
  - input_sources[] (source_id)
  - output_capability (enum: COERCION|DEFENSE|PROJECTION|CONTROL|DISRUPTION|PERSUASION)
  - condition (when it works)
  - limit (hard cap or failure mode)
  - notes
- CHECK (minimum):
  - check_id
  - description
  - severity (S0|S1|S2|S3)
- VALIDATION:
  - each source has measurement_proxy
  - conversion rules reference existing sources
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/WORLD/CONFLICT_POWER/POWER_SOURCE_MODEL.md

ARTIFACT: LEVERAGE_PRESSURE_MAP
- MUST:
  - leverage_map_id
  - version
  - levers[] (non-empty)
  - pressures[] (non-empty)
  - countermeasures[] (optional)
  - checks[] (non-empty)
- LEVER (minimum):
  - lever_id
  - lever_type (enum: ECONOMIC|MILITARY|LEGAL|RELIGIOUS|INFO|DIPLOMATIC|TECH|MAGIC|ENVIRONMENTAL)
  - owner_actor_ref (civ_id/institution_id)
  - target_actor_ref (civ_id/institution_id/region_id)
  - mechanism (how it changes incentives/constraints)
  - prerequisites[] (optional)
  - limits[] (optional)
  - severity (S0|S1|S2|S3)
- PRESSURE (minimum):
  - pressure_id
  - lever_id
  - intensity_levels[] (ordered)
  - escalation_trigger (condition)
  - deescalation_trigger (condition)
  - expected_effects[] (testable)
  - risks[] (optional)
- VALIDATION:
  - each pressure references existing lever
  - intensity levels are ordered and distinct
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/WORLD/CONFLICT_POWER/LEVERAGE_PRESSURE_MAP.md

ARTIFACT: ESCALATION_LADDER_SET
- MUST:
  - ladder_set_id
  - version
  - ladders[] (non-empty)
  - checks[] (non-empty)
- LADDER (minimum):
  - ladder_id
  - name
  - scope (GLOBAL|REGIONAL|LOCAL)
  - parties[] (actor refs)
  - rungs[] (non-empty; ordered)
  - exit_routes[] (optional)
  - notes
- RUNG (minimum):
  - rung_id
  - level (integer; increasing)
  - state_name
  - triggers_in[] (conditions)
  - triggers_out[] (conditions)
  - constraints[] (law/civ constraints)
  - costs[] (optional)
  - observable_signals[] (non-empty recommended)
- VALIDATION:
  - rungs strictly increasing level
  - each rung has triggers_in and constraints
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/WORLD/CONFLICT_POWER/ESCALATION_LADDER_SET.md

ARTIFACT: CONFLICT_ARCHETYPE_SET
- MUST:
  - archetype_set_id
  - version
  - archetypes[] (non-empty)
  - mapping_rules[] (optional)
- ARCHETYPE (minimum):
  - archetype_id
  - name
  - type (enum: SUCCESSION|RESOURCE_CONTEST|IDEOLOGICAL_SPLIT|INDEPENDENCE|PROXY_WAR|CIVIL_WAR|BORDER_DISPUTE|REVOLT|HEGEMONY_CHALLENGE|RELIGIOUS_SCHISM)
  - required_inputs[] (e.g., power imbalance, resource scarcity, legitimacy crisis)
  - typical_triggers[] (conditions)
  - escalation_path_ref (ladder id or pattern)
  - likely_outcomes[] (constrained by resolution constraints)
  - prevention_levers[] (optional)
  - notes
- VALIDATION:
  - at least 5 archetypes
  - each archetype references an escalation path
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/WORLD/CONFLICT_POWER/CONFLICT_ARCHETYPE_SET.md

ARTIFACT: RESOLUTION_CONSTRAINTS
- MUST:
  - resolution_id
  - version
  - allowed_outcomes[] (non-empty)
  - forbidden_outcomes[] (optional)
  - outcome_conditions[] (non-empty)
  - checks[] (non-empty)
- OUTCOME (minimum):
  - outcome_id
  - name
  - type (enum: TRUCE|TREATY|ANNEXATION|PARTITION|REGIME_CHANGE|WITHDRAWAL|VASSALAGE|FEDERATION|TOTAL_COLLAPSE|STALEMATE)
  - prerequisites[] (conditions)
  - costs[] (what must be paid)
  - constraints[] (law/civ constraints)
  - aftermath (short)
- OUTCOME CONDITION (minimum):
  - condition_id
  - links_to_outcome_id
  - condition (testable)
  - severity_if_ignored (S0|S1|S2|S3)
- VALIDATION:
  - each allowed outcome has prerequisites + constraints
  - forbidden outcomes include why (law/capability violation)
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/WORLD/CONFLICT_POWER/RESOLUTION_CONSTRAINTS.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Validate inputs:
   - law + timeline + civilization exist
2) Build power sources:
   - define sources and measurement proxies
3) Build leverage mechanisms:
   - map levers and pressure programs
4) Build escalation ladders:
   - define rungs + triggers + constraints
5) Build conflict archetypes:
   - create reusable patterns tied to ladders
6) Build resolution constraints:
   - list allowed outcomes + prerequisites + costs
7) Run checks:
   - contradictions with law/epoch/civ capability
8) Emit artifacts

---

## 8) S0 BLOCKERS (STOP)
- S0-1: escalation rung violates hard laws or causality constraints.
- S0-2: resolution outcome is listed without prerequisites/costs/constraints.
- S0-3: levers/pressures lack clear mechanisms (vague “influence”).
- S0-4: archetype outputs contradict resolution constraints.
- S0-5: engine introduces narrative act/scene constructs as mechanics.

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- world law + causality (02)
- epochs (03)
- civilization + institutions (04)

Downstream consumers:
- `06__GEOPOLITICS_ENG` (uses power/leverage to derive borders/alliances)
- `07__ECONOMY_RESOURCE_ENG` (resource constraints feed power sources)
- `08__TECHNOLOGY_MAGIC_ENG` (tech/magic constraints define capability)
- narrative engines (consume ladders/archetypes as world-consistent conflict frameworks)

Governance:
- if conflict mechanics change hard invariants or law constraints → route via governance pipeline + audit.

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Family template:
  04_DOMAIN_WORLD_ENGINES/00__TEMPLATE__ENGINE__DOMAIN_WORLD_ENGINES.md

--- END.

LOCK: OPEN
