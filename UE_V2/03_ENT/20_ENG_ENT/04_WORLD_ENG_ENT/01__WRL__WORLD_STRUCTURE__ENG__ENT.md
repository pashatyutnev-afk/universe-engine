# WORLD STRUCTURE ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/04_DOMAIN_WORLD_ENGINES/01__WORLD_STRUCTURE_ENG.md
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
UID: UE.ENG.DOM.WORLD.STRUCTURE.001
OWNER: SYSTEM
ROLE: Defines the world structure model: layers, scales, invariants, topology, and state containers that other world engines must respect.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "World Structure Engine created: world structure model, invariants, topology contracts, and integration hooks."
- REASON: "World engines need a shared structure container before laws/timelines/civilizations."
- IMPACT: "All downstream world engines can depend on a single stable world-state container."
- CHANGE_ID: UE.CHG.2026-01-08.DOM.WORLD.STRUCTURE.001

---

## 0) PURPOSE (LAW)
This engine owns **world structure** as a deterministic container:
- defines world layers (physical/social/systemic)
- defines scales (global/region/local)
- defines topology primitives (places, regions, connections)
- defines invariants that must remain consistent
- defines state containers that other engines write into (timeline/civilization/economy/etc.)

Guarantees:
- a stable structure contract exists before any world rules or systems are built
- downstream world artifacts can reference a shared topology + state model
- structure never depends on narrative story beats

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- define system identity/state/lifecycle (CORE)
- define authority/approvals/pipeline/audit/memory (GOVERNANCE)
- define narrative macro-structure/continuity as primary (NARRATIVE owns)
- define character psychology/motivation/dialogue as primary (CHARACTER owns)
- define event mechanics primitives (EXPRESSION owns)
- define media implementation (camera/editing/sound) as primary (PRODUCTION)

Also not owned here:
- world laws / causality rules (belongs to `02__WORLD_LAW_ENG`)
- world timeline/epochs content (belongs to `03__TIMELINE_EPOCH_ENG`)
- civilizations/economy/tech/ecology specifics (downstream engines)

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- CORE_IDENTITY
- CORE_STATE
- WORLD_STRUCTURE_SEEDS (optional; initial sketch/notes)

PRODUCES:
- WORLD_STRUCTURE_MODEL
- WORLD_TOPOLOGY_PRIMITIVES
- WORLD_INVARIANTS

DEPENDS_ON:
- [01_CORE_ENGINES/01__CORE_IDENTITY_ENG, 01_CORE_ENGINES/02__CORE_STATE_ENG]

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/WORLD/STRUCTURE/
OPTIONAL:
- KB/WORLD_STRUCTURE (if KB storage is used by project)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- World Layer: a structural layer (PHYSICAL / SOCIAL / SYSTEMS) used as a container for rules and state.
- Scale: the resolution level (GLOBAL / REGIONAL / LOCAL) used for scoping models.
- Topology Primitive: place/region/connection primitives used for referencing world state.
- World Invariant: a stability rule that must hold across time (unless explicitly changed by governance-approved canon change).

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- structure containers (layers/scales)
- topology primitives (place/region/connection)
- invariants of structure (what must not drift)
- reference conventions for downstream world models

OUT OF SCOPE (HARD):
- causal rules / physics / magic logic (WORLD LAW engine)
- plot timeline / beats (NARRATIVE)
- culture/psychology of individuals (CHARACTER)
- event primitives (EXPRESSION)
- production representation (PRODUCTION)

COLLISION RULE:
- If a question is about “what is possible” → route to `02__WORLD_LAW_ENG`
- If a question is about “when events happen in story” → route to narrative engines
- If a question is about “economy/resources/currency” → route to `07__ECONOMY_RESOURCE_ENG` (and enforce “no currency primitives” if canon forbids)
- If a question is about “how it looks/sounds” → route to production engines

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: WORLD_STRUCTURE_MODEL must define layers + scales + topology primitives.
R2 (HARD) MUST: Every produced topology primitive must have stable ids and be referenceable by downstream engines.
R3 (HARD) MUST: WORLD_INVARIANTS must be explicit and testable (no vague prose).
R4 (HARD) FORBIDDEN: This engine may not introduce narrative constructs (acts/beats/scenes) as structure primitives.
R5 (HARD) FORBIDDEN: This engine may not introduce character-domain constructs (motives/values/trauma) as world structure.
R6 (HARD) FORBIDDEN: Currency/finance primitives as world structure containers (if canon forbids currency).
R7 (SOFT) ALLOWED: Optional mapping notes to KB storage, but it must not redefine KB laws.

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: WORLD_STRUCTURE_MODEL
- MUST:
  - structure_id (string)
  - version (string)
  - layers[] (non-empty)
  - scales[] (non-empty)
  - topology (object: places/regions/connections)
  - state_containers[] (non-empty; what models plug in)
  - invariants_ref (pointer to WORLD_INVARIANTS)
  - naming_rules (short)
- OPTIONAL:
  - visualization_notes
  - kb_links[]
- VALIDATION:
  - layers contain only allowed set {PHYSICAL, SOCIAL, SYSTEMS} unless explicitly extended with rationale
  - every connection references existing endpoints
  - state_containers names are unique
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/WORLD/STRUCTURE/WORLD_STRUCTURE_MODEL.md

ARTIFACT: WORLD_TOPOLOGY_PRIMITIVES
- MUST:
  - primitives_id
  - places[] (id, name, scale, tags[])
  - regions[] (id, name, scale, contains_place_ids[])
  - connections[] (id, from_id, to_id, type, constraints[])
- OPTIONAL:
  - coordinates (if needed)
- VALIDATION:
  - id uniqueness across all primitives
  - region contains_place_ids must exist
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/WORLD/STRUCTURE/WORLD_TOPOLOGY_PRIMITIVES.md

ARTIFACT: WORLD_INVARIANTS
- MUST:
  - invariants_id
  - hard_invariants[] (non-empty)
  - soft_invariants[] (optional)
  - change_protocol (how invariants can be changed)
- OPTIONAL:
  - test_questions[]
- VALIDATION:
  - every hard invariant is testable and has a violation example
  - change_protocol must route canon-impacting changes to governance
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/WORLD/STRUCTURE/WORLD_INVARIANTS.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Input validation:
   - confirm CORE inputs exist
   - normalize WORLD_STRUCTURE_SEEDS into candidate primitives
2) Construct structure:
   - define layers and scales
   - define topology primitives and id rules
3) Define state containers:
   - list which downstream engines attach outputs (timeline/civilization/etc.)
4) Define invariants:
   - hard/soft invariants + change protocol routing
5) Output formatting:
   - emit artifacts with schemas
6) Integration hooks:
   - document which engines consume structure outputs

---

## 8) S0 BLOCKERS (STOP)
- S0-1: Output contradicts CORE invariants.
- S0-2: Engine duplicates governance authority/pipeline rules.
- S0-3: Engine claims ownership of character-domain or narrative-structure primitives.
- S0-4: Engine outputs missing required schema fields.

---

## 9) INTEGRATION (SYSTEM FIT)
Consumers (typical):
- 04_DOMAIN_WORLD_ENGINES/02__WORLD_LAW_ENG (uses structure containers + invariants)
- 04_DOMAIN_WORLD_ENGINES/03__TIMELINE_EPOCH_ENG (uses topology + state containers)
- 04_DOMAIN_WORLD_ENGINES/04__CIVILIZATION_ENG (uses scales + regions)
- 04_DOMAIN_WORLD_ENGINES/05__CONFLICT_POWER_ENG (uses actors-at-scale slots)
- 04_DOMAIN_WORLD_ENGINES/06__GEOPOLITICS_ENG (uses region graph)
- 04_DOMAIN_WORLD_ENGINES/07__ECONOMY_RESOURCE_ENG (uses resource containers; must respect no-currency constraint if applicable)
- 04_DOMAIN_WORLD_ENGINES/08__TECHNOLOGY_MAGIC_ENG (uses law/constraints containers)
- 04_DOMAIN_WORLD_ENGINES/10__ENVIRONMENT_ECOLOGY_ENG (uses physical layer/topology)

ORC fit:
- This engine provides the base world container for ORC pipelines that assemble world-building passes.

Governance requirement:
- If changing WORLD_INVARIANTS (hard) → must route through governance change control + audit.

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- ENGINE TEMPLATE:
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/04_DOMAIN_WORLD_ENGINES/00__TEMPLATE__ENGINE__DOMAIN_WORLD_ENGINES.md

--- END.
