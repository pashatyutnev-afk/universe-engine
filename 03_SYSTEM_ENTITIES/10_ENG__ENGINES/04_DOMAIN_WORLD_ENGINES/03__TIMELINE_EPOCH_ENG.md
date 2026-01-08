# TIMELINE & EPOCH ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/04_DOMAIN_WORLD_ENGINES/03__TIMELINE_EPOCH_ENG.md
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
UID: UE.ENG.DOM.WORLD.TIMELINE.EPOCH.001
OWNER: SYSTEM
ROLE: Defines world-state timeline: epochs, eras, transitions, and world evolution rules (NOT story beats). Produces deterministic epoch model and state-transition constraints.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Timeline & Epoch Engine created: epoch schema, transition rules, world-state deltas, and continuity checks."
- REASON: "World evolution must be explicit and separable from narrative structure."
- IMPACT: "World-state changes become auditable, consistent, and reusable across narratives."
- CHANGE_ID: UE.CHG.2026-01-08.DOM.WORLD.TIMELINE.EPOCH.001

---

## 0) PURPOSE (LAW)
This engine owns **world timeline** as world-state evolution:
- defines epochs/eras (as world conditions)
- defines transitions (what changes and why)
- defines state deltas across structure containers (physical/social/systems)
- defines continuity constraints (no impossible jumps vs world laws)
- provides an anchor for civilization/geopolitics/economy/ecology changes

Hard rule:
- Timeline here is NOT story beats, NOT episode/chapter structure.

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- define narrative arc structure, acts, scenes, pacing, twists (narrative family)
- define world laws/possibility (world law engine owns)
- define character development arcs (character family)
- define production formats or editing rhythm (production family)
- define “one-off story timeline shortcuts” unless recorded as a world exception under law protocol

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- WORLD_STRUCTURE_MODEL
- WORLD_TOPOLOGY_PRIMITIVES
- WORLD_INVARIANTS
- WORLD_LAWSET
- CAUSALITY_CONSTRAINTS
- TIMELINE_SEEDS (optional; epoch sketches)

PRODUCES:
- TIMELINE_EPOCH_MODEL
- EPOCH_TRANSITION_RULES
- WORLD_STATE_DELTA_LOG

DEPENDS_ON:
- [04_DOMAIN_WORLD_ENGINES/01__WORLD_STRUCTURE_ENG, 04_DOMAIN_WORLD_ENGINES/02__WORLD_LAW_ENG]

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/WORLD/TIMELINE/
OPTIONAL:
- KB/WORLD_TIMELINE (if project mirrors into KB)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Epoch: a period defined by stable world conditions (not by narrative milestones).
- Era: a subrange inside an epoch (optional).
- Transition: a change boundary between epochs (with causes and deltas).
- World State: values stored in world state containers (environment, civ level, geopolitics configuration, tech constraints, etc).
- Delta Log: explicit list of what changes between adjacent epochs.

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- epoch list and ordering
- epoch conditions (what is true during)
- transition causes and deltas
- continuity checks with world laws
- mapping to world topology (global/region/local)

OUT OF SCOPE (HARD):
- story beats/acts/scenes/chapter timeline
- character arcs
- production schedule/format
- “why a character did something” (character + narrative)

COLLISION RULE:
- If the timeline is about story sequence → route to `02_DOMAIN_NARRATIVE_ENGINES/*`
- If the question is “is this change possible” → route to `02__WORLD_LAW_ENG`
- If the change is primarily civilization-level content → define in `04__CIVILIZATION_ENG`, then reference epoch containers here

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: TIMELINE_EPOCH_MODEL defines ordered epochs with start/end boundaries (even if symbolic).
R2 (HARD) MUST: each epoch defines world-state conditions for at least PHYSICAL + SOCIAL or explicitly marks UNKNOWN with routing.
R3 (HARD) MUST: each transition provides causes + deltas and references laws/constraints.
R4 (HARD) FORBIDDEN: narrative constructs (act/scene/episode) as epoch markers.
R5 (HARD) MUST: WORLD_STATE_DELTA_LOG exists and matches transitions.
R6 (HARD) MUST: continuity checks exist against WORLD_LAWSET + CAUSALITY_CONSTRAINTS.
R7 (SOFT) SHOULD: allow multi-scale epochs (global baseline + regional variants).
R8 (HARD) MUST: if an epoch changes hard invariants, it must route to governance (canon-impacting).

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: TIMELINE_EPOCH_MODEL
- MUST:
  - timeline_id
  - version
  - epochs[] (non-empty; ordered)
  - ordering_rule (how ordering is defined)
  - topology_scope (global/region/local references)
  - invariants_ref
  - lawset_ref
  - open_unknowns[] (optional)
- EPOCH (minimum):
  - epoch_id
  - name
  - start_ref (symbolic or numeric)
  - end_ref (symbolic or numeric)
  - scope (GLOBAL|REGIONAL|LOCAL|MIXED)
  - conditions (object)
  - key_constraints[] (law_id / constraint ids)
  - state_container_values[] (refs or embedded)
  - transition_in_ref (optional)
  - transition_out_ref (optional)
  - notes
- CONDITIONS (minimum):
  - physical (summary, constraints refs)
  - social (summary, constraints refs)
  - systems (summary, constraints refs) (optional if not applicable)
- VALIDATION:
  - epochs ordered; no overlaps unless explicitly allowed by ordering_rule
  - every epoch includes at least physical+social summaries
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/WORLD/TIMELINE/TIMELINE_EPOCH_MODEL.md

ARTIFACT: EPOCH_TRANSITION_RULES
- MUST:
  - transitions_id
  - version
  - transitions[] (non-empty)
  - checks[] (non-empty)
- TRANSITION (minimum):
  - transition_id
  - from_epoch_id
  - to_epoch_id
  - causes[] (structured)
  - deltas_ref (pointer to delta log segment)
  - constraint_refs[] (laws/causality constraints)
  - allowed_variants[] (optional)
  - forbidden_variants[] (optional)
  - severity_if_violated (S0|S1|S2|S3)
  - notes
- CAUSE (minimum):
  - cause_id
  - cause_type (ENV_SHIFT|TECH_SHIFT|CIV_COLLAPSE|RESOURCE_EXHAUST|WAR|DISCOVERY|CATASTROPHE|REFORM|CONTACT)
  - description (testable)
  - prerequisite_refs[] (optional)
- CHECK (minimum):
  - check_id
  - description
  - severity
- VALIDATION:
  - every transition references existing epochs
  - S0 transitions have explicit checks and constraint refs
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/WORLD/TIMELINE/EPOCH_TRANSITION_RULES.md

ARTIFACT: WORLD_STATE_DELTA_LOG
- MUST:
  - delta_log_id
  - version
  - deltas[] (non-empty)
  - merge_rules (optional)
- DELTA (minimum):
  - delta_id
  - transition_id
  - changes[] (non-empty)
  - cost_or_tradeoff (optional)
  - notes
- CHANGE (minimum):
  - container (which state container)
  - scope (GLOBAL|REGIONAL|LOCAL)
  - target_ref (region/place id if not global)
  - path (field name)
  - from (optional)
  - to
  - reason (cause_id or constraint ref)
  - verification_check (optional)
- VALIDATION:
  - each delta links to one transition
  - no delta violates hard laws without exception protocol
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/WORLD/TIMELINE/WORLD_STATE_DELTA_LOG.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Input validation:
   - confirm structure + law outputs exist
2) Draft epoch list:
   - normalize seeds into candidate epochs
3) Define epoch conditions:
   - fill conditions per layer and per scope
4) Define transitions:
   - define causes and allowed sequences
5) Compute deltas:
   - explicit state changes by container
6) Continuity checks:
   - run against WORLD_LAWSET + CAUSALITY constraints + invariants
7) Emit artifacts:
   - epoch model + transitions + delta log

---

## 8) S0 BLOCKERS (STOP)
- S0-1: epochs overlap without explicit ordering_rule allowance.
- S0-2: transition produces deltas that violate hard laws with no exception protocol reference.
- S0-3: timeline uses narrative constructs as epoch boundaries.
- S0-4: missing deltas for transitions (or mismatched ids).
- S0-5: continuity checks missing for any S0 transition.

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- structure + topology (01)
- lawset + causality (02)

Downstream consumers:
- `04__CIVILIZATION_ENG` (civilization states by epoch)
- `05__CONFLICT_POWER_ENG` (power dynamics per epoch)
- `06__GEOPOLITICS_ENG` (border/order over epochs)
- `07__ECONOMY_RESOURCE_ENG` (resource regimes by epoch)
- `08__TECHNOLOGY_MAGIC_ENG` (tech constraints evolve by epoch)
- `10__ENVIRONMENT_ECOLOGY_ENG` (climate/ecology regimes per epoch)

Narrative consumption:
- narrative engines may pick story time windows inside an epoch, but cannot contradict epoch conditions.

Governance:
- any change that alters hard invariants or reorders canonical epochs requires governance pipeline and audit.

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Family template:
  04_DOMAIN_WORLD_ENGINES/00__TEMPLATE__ENGINE__DOMAIN_WORLD_ENGINES.md

--- END.

LOCK: OPEN
