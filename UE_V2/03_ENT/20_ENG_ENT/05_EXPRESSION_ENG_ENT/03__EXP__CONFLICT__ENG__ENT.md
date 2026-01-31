# CONFLICT ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/05_EXPRESSION_ENGINES/03__CONFLICT_ENG.md
SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: ENGINE
FAMILY: 05_EXPRESSION_ENGINES
CLASS: EXPRESSION (L3)
LEVEL: L3
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.EXP.CONFLICT.001
OWNER: SYSTEM
ROLE: Builds deterministic conflict objects from events and causal links: opposing goals, obstacles, stakes refs, escalation states, and resolution conditions (primitive conflict units, not story arcs).

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Conflict Engine created: conflict schema, conflict types, escalation states, and validation gates."
- REASON: "Cause-effect graphs require a conflict primitive to represent opposition and pressure."
- IMPACT: "Turning points/climax/resolution engines can operate on standardized conflicts."
- CHANGE_ID: UE.CHG.2026-01-08.EXP.CONFLICT.001

---

## 0) PURPOSE (LAW)
This engine owns the **CONFLICT primitive** built from events:
- identifies opposing forces/goals
- binds obstacles and constraints
- enumerates escalation states (primitive ladder)
- defines what counts as “resolved” vs “shifted”
- emits conflict objects that other expression engines can transform (turning point, climax, resolution)

Hard rule:
- Conflict must be represented as structured opposition + stakes refs (if available), not as prose.

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- define character motivations/values (character family owns)
- define narrative arc pacing/structure (narrative family owns)
- define world-level conflict mechanics (world conflict/power engine owns)
- define turning points/climax/resolution as separate primitives (other expression engines)
- define production depiction

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- EVENT_PACK (one or more)
- CAUSAL_LINK_SET (optional but recommended)
- CAUSAL_GRAPH (optional)
- WORLD_LAWSET (optional)
- TENSION_STAKES_MAP (optional; from narrative tension engine if available)
- ACTOR_ENTITY_REFS (optional)
- LOCATION_ENTITY_REFS (optional)

PRODUCES:
- CONFLICT_OBJECT_SET
- CONFLICT_TYPE_REGISTRY
- ESCALATION_STATE_SCHEMA

DEPENDS_ON:
- [05_EXPRESSION_ENGINES/01__EVENT_ENG, 05_EXPRESSION_ENGINES/02__CAUSE_EFFECT_ENG]

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/EXPRESSION/CONFLICTS/
OPTIONAL:
- KB/CONFLICTS (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Conflict: structured opposition between sides over an objective under constraints.
- Side: an actor/system representing an objective and capabilities (can be “environment/system”).
- Objective: what a side wants (in observable terms).
- Obstacle: what blocks objective.
- Escalation State: stage of intensification (primitive: not narrative acts).
- Resolution Condition: testable condition for conflict end or transformation.

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- building conflict objects from event sets
- defining conflict types and escalation states
- linking conflicts to events/causal chains
- conflict validation gates

OUT OF SCOPE (HARD):
- story arc design (narrative)
- deep stakes modeling (narrative tension engine)
- world geopolitics/power mechanics (world family)
- turning points/climax/resolution selection (separate expression engines)

COLLISION RULE:
- If conflict is world-scale power mechanics → route to 04_DOMAIN_WORLD_ENGINES/05__CONFLICT_POWER_ENG
- If conflict is about character morality/motives → character engines provide constraints; this engine only models opposition
- If conflict must map to story structure → narrative engines consume conflicts

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: each conflict references at least one event (source).
R2 (HARD) MUST: conflict has at least two sides OR one side vs SYSTEM/ENV constraint explicitly.
R3 (HARD) MUST: objective and obstacle are testable statements.
R4 (HARD) MUST: escalation states exist (at least 3) unless conflict is marked “instant”.
R5 (HARD) MUST: resolution conditions exist (win/lose/shift/stalemate).
R6 (HARD) FORBIDDEN: “conflict” described only as mood/vibe.
R7 (SOFT) SHOULD: stakes references included if tension/stakes map exists.
R8 (HARD) MUST: conflicts cannot contradict world laws if lawset provided (else S0).

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: CONFLICT_TYPE_REGISTRY
- MUST:
  - registry_id
  - version
  - conflict_types[] (non-empty)
- CONFLICT TYPE (minimum):
  - type_id
  - name
  - description (testable)
  - typical_sides (e.g., PERSON vs PERSON, PERSON vs SYSTEM)
  - typical_escalation_pattern_ref (optional)
- Minimum baseline types:
  - PERSON_VS_PERSON
  - PERSON_VS_SELF
  - PERSON_VS_SYSTEM
  - GROUP_VS_GROUP
  - CIV_VS_CIV
  - SYSTEM_VS_ENVIRONMENT
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/EXPRESSION/CONFLICTS/CONFLICT_TYPE_REGISTRY.md

VALIDATION:
- baseline types exist (unless explicitly overridden)

---

ARTIFACT: ESCALATION_STATE_SCHEMA
- MUST:
  - schema_id
  - version
  - states[] (non-empty)
  - transitions[] (optional)
  - checks[] (non-empty)
- STATE (minimum):
  - state_id
  - name
  - level (integer; increasing)
  - description (testable)
  - typical_triggers_in[] (optional)
  - typical_triggers_out[] (optional)
- Minimum baseline states:
  - S0_CONTACT (opposition appears)
  - S1_PRESSURE (pressure increases)
  - S2_COMMITMENT (sides commit resources)
  - S3_POINT_OF_NO_RETURN (irreversibility)
  - S4_COLLISION (direct clash)
- VALIDATION:
  - levels strictly increase
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/EXPRESSION/CONFLICTS/ESCALATION_STATE_SCHEMA.md

---

ARTIFACT: CONFLICT_OBJECT_SET
- MUST:
  - set_id
  - version
  - conflicts[] (non-empty)
  - open_unknowns[] (optional)
  - checks[] (non-empty)
- CONFLICT (minimum):
  - conflict_id
  - conflict_type (type_id)
  - title
  - sides[] (non-empty; >=2 or 1 + SYSTEM)
  - objective (testable)
  - obstacle (testable)
  - scope (PERSONAL|LOCAL|REGIONAL|GLOBAL|SYSTEM)
  - severity (S0|S1|S2|S3)
  - source_event_ids[] (non-empty)
  - causal_refs[] (optional link ids)
  - escalation_state (current or planned)
  - escalation_path[] (state_ids optional)
  - stakes_refs[] (optional)
  - resolution_conditions[] (non-empty)
  - notes
- SIDE (minimum):
  - side_id
  - actor_ref (character/civ/system)
  - role (enum: PROTAGONIST_SIDE|ANTAGONIST_SIDE|SYSTEM|ENV)
  - resources_or_capabilities[] (optional)
  - constraint_refs[] (optional)
- RESOLUTION CONDITION (minimum):
  - condition_id
  - outcome (enum: WIN_A|WIN_B|MIXED|SHIFT|STALEMATE|ABANDON)
  - condition (testable)
  - resulting_state_change (optional)
- CHECK (minimum):
  - check_id
  - description
  - severity
- VALIDATION:
  - conflict_type exists in registry
  - source_event_ids exist
  - objective/obstacle non-empty and testable
  - resolution conditions non-empty
  - if world lawset present, no forbidden capability is required
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/EXPRESSION/CONFLICTS/CONFLICT_OBJECT_SET.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Load events (+ causal links if available).
2) Detect candidate oppositions:
   - identify events with competing intents, blocks, threats, breaches
3) Assign conflict type and sides.
4) Build objective and obstacle (testable).
5) Attach escalation path (use schema).
6) Attach stakes refs (if available) and causal refs (if available).
7) Define resolution conditions.
8) Validate (S0 gates) and emit conflict object set.

---

## 8) S0 BLOCKERS (STOP)
- S0-1: conflict references unknown event ids.
- S0-2: fewer than 2 sides and not explicitly SYSTEM/ENV.
- S0-3: missing objective/obstacle or they are non-testable prose.
- S0-4: no resolution conditions.
- S0-5: conflict requires actions that violate hard world laws (if lawset provided).

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- Event engine supplies event schema.
- Cause-effect engine provides causal refs (optional).

Downstream consumers:
- `04__TURNING_POINT_ENG` (finds turning points inside conflict escalations)
- `05__CLIMAX_ENG` (selects peak collision events/conflicts)
- `06__RESOLUTION_ENG` (generates closure and resolution mapping)
- narrative engines (use conflicts as building blocks for scenes and arcs)

World integration:
- world conflict/power engine provides macro constraints; this engine can represent smaller scoped conflicts too.

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Family template:
  05_EXPRESSION_ENGINES/00__TEMPLATE__ENGINE__EXPRESSION_ENGINES.md

--- END.

LOCK: OPEN
