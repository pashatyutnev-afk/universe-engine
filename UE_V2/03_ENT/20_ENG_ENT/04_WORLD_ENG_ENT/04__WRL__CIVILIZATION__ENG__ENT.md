# CIVILIZATION ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/04_DOMAIN_WORLD_ENGINES/04__CIVILIZATION_ENG.md
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
UID: UE.ENG.DOM.WORLD.CIVILIZATION.001
OWNER: SYSTEM
ROLE: Defines civilization models (societies at scale): governance structures, institutions, norms, capability levels, stability dynamics, and epoch-scoped state. Produces deterministic civ model and institution/constraint sets.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Civilization Engine created: civ schema, institution model, stability dynamics, capability tiers, and epoch-scoped state."
- REASON: "Downstream geopolitics/economy/conflict require stable civilization containers."
- IMPACT: "Civilizations become reusable components across epochs and narratives with clear constraints."
- CHANGE_ID: UE.CHG.2026-01-08.DOM.WORLD.CIVILIZATION.001

---

## 0) PURPOSE (LAW)
This engine owns **civilizations** as deterministic world entities:
- defines civilizations/societies at scale (not individual characters)
- defines institutions, governance patterns, social norms, taboos
- defines capability tiers (tech/organization/info)
- defines stability dynamics (how societies hold or collapse)
- defines epoch-scoped state of civilizations (how they change over epochs)

Primary outputs feed geopolitics, conflict/power, economy/resource, technology/magic.

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- define world topology or structure containers (01)
- define physical/magic possibility rules (02)
- define world timeline ordering (03) — it can attach civ states per epoch, but not create epoch rules
- define interpersonal psychology/relationships/dialogue (character family)
- define event primitives (expression family)
- define production depiction (production family)

Also NOT:
- define “plot factions” that exist only for a story without world grounding (must still be civ entities if they persist as world-state)

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- WORLD_STRUCTURE_MODEL
- WORLD_TOPOLOGY_PRIMITIVES
- WORLD_LAWSET
- TIMELINE_EPOCH_MODEL
- CIVILIZATION_SEEDS (optional)
- CULTURE_CONSTRAINTS (optional)
- TECHNOLOGY_MAGIC_MODEL (optional; if already defined in project pass)

PRODUCES:
- CIVILIZATION_MODEL_SET
- INSTITUTION_MODEL_SET
- CIV_STABILITY_DYNAMICS

DEPENDS_ON:
- [04_DOMAIN_WORLD_ENGINES/01__WORLD_STRUCTURE_ENG, 04_DOMAIN_WORLD_ENGINES/02__WORLD_LAW_ENG, 04_DOMAIN_WORLD_ENGINES/03__TIMELINE_EPOCH_ENG]

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/WORLD/CIVILIZATIONS/
OPTIONAL:
- KB/CIVILIZATIONS (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Civilization: a persistent society-scale entity with governance, norms, and capability level.
- Institution: stable mechanism (legal, religious, military, educational, trade, etc) that shapes behavior.
- Norm: default social rule; can be enforced by institutions.
- Taboo: hard social prohibition (in-scope here as civilization rule, not character morality).
- Capability Tier: structured level of organization/technology/magic access.
- Stability Dynamics: model describing pressures, resilience, and collapse modes.
- Epoch Civ State: civ parameters scoped per epoch (and optionally per region).

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- civ identities, types, and attributes
- institution sets and enforcement style
- norm/taboo catalogs (society-level)
- civ capability tiers
- stability/collapse dynamics
- epoch-scoped civ state

OUT OF SCOPE (HARD):
- geopolitics interactions between civs (belongs to `06__GEOPOLITICS_ENG`)
- war/conflict mechanics as primary (belongs to `05__CONFLICT_POWER_ENG`)
- resource accounting (belongs to `07__ECONOMY_RESOURCE_ENG`)
- detailed tech/magic system specs (belongs to `08__TECHNOLOGY_MAGIC_ENG`)
- individual character values/trauma/motivation (character engines)
- narrative factions that are not world persistent (route to narrative unless world-state persistent)

COLLISION RULE:
- If question is “how civ interacts with other civs/borders” → geopolitics engine
- If question is “internal law/possibility” → world law engine
- If question is “resource flows” → economy/resource engine
- If question is “values of a person” → moral/value engine (character)

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: CIVILIZATION_MODEL_SET defines each civilization with id, type, scope, and epoch-scoped state mapping.
R2 (HARD) MUST: INSTITUTION_MODEL_SET exists and each institution links to at least one civ.
R3 (HARD) MUST: norms/taboos must be explicit and enforceable (no vague “they are proud” without rule).
R4 (HARD) MUST: capability tier is declared per civ (or per epoch) and references laws/constraints.
R5 (HARD) MUST: CIV_STABILITY_DYNAMICS includes pressures + resilience + collapse modes.
R6 (HARD) FORBIDDEN: using currency primitives as civilization mechanics if canon forbids currency.
R7 (HARD) MUST: civ states per epoch must not contradict world laws and epoch conditions.
R8 (SOFT) SHOULD: include “institution failure modes” for realism and narrative hooks.
R9 (HARD) MUST: civ identifiers must be stable and referenceable by geopolitics/conflict/economy engines.

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: CIVILIZATION_MODEL_SET
- MUST:
  - civ_set_id
  - version
  - civilizations[] (non-empty)
  - epoch_binding_ref (timeline id)
  - topology_binding_ref (regions/places graph)
  - lawset_ref
  - open_unknowns[] (optional)
- CIVILIZATION (minimum):
  - civ_id
  - name
  - civ_type (enum: EMPIRE|KINGDOM|CITY_STATE|TRIBAL|FEDERATION|THEOCRACY|CORPORATE_POLITY|ANARCHIC_NETWORK|HYBRID)
  - scope (GLOBAL|REGIONAL|LOCAL)
  - core_identity (short)
  - population_model (rough; optional but recommended)
  - governance_pattern (short)
  - institution_refs[] (non-empty)
  - norm_taboo_ref (pointer)
  - capability_tier_ref (pointer)
  - stability_ref (pointer)
  - epoch_states[] (non-empty)
  - notes
- EPOCH_STATE (minimum):
  - epoch_id
  - region_scope (optional region_id list; default global)
  - parameters (object)
  - constraints[] (law/epoch constraints refs)
  - tensions[] (optional)
  - notes
- VALIDATION:
  - epoch_states reference existing epoch_ids
  - institution_refs exist in institution model set
  - no duplicate civ_id
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/WORLD/CIVILIZATIONS/CIVILIZATION_MODEL_SET.md

ARTIFACT: INSTITUTION_MODEL_SET
- MUST:
  - inst_set_id
  - version
  - institutions[] (non-empty)
  - enforcement_styles[] (optional)
- INSTITUTION (minimum):
  - inst_id
  - name
  - inst_type (enum: LEGAL|MILITARY|RELIGIOUS|ECONOMIC|EDUCATIONAL|SCIENTIFIC|MAGICAL|MEDIA|SECURITY|DIPLOMATIC|OTHER)
  - owner_civ_id
  - purpose
  - powers[] (non-empty)
  - enforcement (how rules are enforced)
  - failure_modes[] (optional)
  - dependency_refs[] (optional)
  - notes
- VALIDATION:
  - each institution links to a civ_id
  - powers must be actionable (verbs + objects)
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/WORLD/CIVILIZATIONS/INSTITUTION_MODEL_SET.md

ARTIFACT: CIV_STABILITY_DYNAMICS
- MUST:
  - stability_id
  - version
  - civ_dynamics[] (non-empty)
  - checks[] (non-empty)
- CIV_DYNAMIC (minimum):
  - civ_id
  - baseline_stability (0..100)
  - pressure_factors[] (non-empty)
  - resilience_factors[] (non-empty)
  - collapse_modes[] (non-empty)
  - recovery_paths[] (optional)
  - epoch_modifiers[] (optional)
  - notes
- FACTOR (minimum):
  - factor_id
  - type (RESOURCE|LEGITIMACY|VIOLENCE|INFORMATION|COHESION|ENVIRONMENT|TECH|EXTERNAL_PRESSURE)
  - description (testable)
  - direction (STABILIZE|DESTABILIZE)
  - triggers[] (optional)
- COLLAPSE_MODE (minimum):
  - mode_id
  - description
  - early_signals[]
  - thresholds[] (optional)
  - aftermath (short)
- CHECK (minimum):
  - check_id
  - description
  - severity (S0|S1|S2|S3)
- VALIDATION:
  - each civ_id in dynamics exists in civilization set
  - at least one collapse mode per civ
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/WORLD/CIVILIZATIONS/CIV_STABILITY_DYNAMICS.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Input validation:
   - structure + law + timeline exist
2) Define civilization candidates:
   - normalize seeds into civ entities with stable ids
3) Define institutions:
   - assign institution sets; define powers and enforcement
4) Define norms/taboos:
   - produce a norm/taboo catalog per civ (embedded or separate pointers)
5) Define capability tiers:
   - set per civ, possibly per epoch, constrained by laws
6) Define stability dynamics:
   - pressures/resilience/collapse modes
7) Bind to epochs:
   - create epoch_states for each civ (global and regional variants)
8) Run checks:
   - contradictions with epoch conditions or world laws
9) Emit artifacts

---

## 8) S0 BLOCKERS (STOP)
- S0-1: civilization references epochs that do not exist in timeline.
- S0-2: institution has no owner civ or no actionable powers.
- S0-3: civ epoch_state contradicts world laws/epoch conditions without exception protocol.
- S0-4: norms/taboos are vague and unenforceable.
- S0-5: introduces currency primitives if canon forbids currency.

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- structure/topology (01)
- world law + causality (02)
- timeline epochs + deltas (03)

Downstream consumers:
- `05__CONFLICT_POWER_ENG` (power dynamics uses civ capacity + institutions)
- `06__GEOPOLITICS_ENG` (borders/alliances/strategic interests use civ identities)
- `07__ECONOMY_RESOURCE_ENG` (resource regimes and production logic attach to civ)
- `08__TECHNOLOGY_MAGIC_ENG` (capability tiers constrain tech/magic)
- `09__MYTHOLOGY_BELIEF_ENG` (belief institutions can be referenced)
- `10__ENVIRONMENT_ECOLOGY_ENG` (environment pressures feed stability)

Narrative consumption:
- narrative may select civ+epoch context; must not contradict civ constraints.

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Family template:
  04_DOMAIN_WORLD_ENGINES/00__TEMPLATE__ENGINE__DOMAIN_WORLD_ENGINES.md

--- END.

LOCK: OPEN
