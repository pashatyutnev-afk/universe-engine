# TURNING POINT ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/05_EXPRESSION_ENGINES/04__TURNING_POINT_ENG.md
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
UID: UE.ENG.EXP.TURNING.POINT.001
OWNER: SYSTEM
ROLE: Detects and specifies turning points from event + conflict structures: reversal/reveal/commitment pivots, direction changes, irreversibility markers, and required follow-through obligations.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Turning Point Engine created: turning point schema, pivot types, detection rules, and follow-through obligations."
- REASON: "Narrative and expression pipelines need explicit pivot points, not implicit assumptions."
- IMPACT: "Arcs become analyzable; climax/resolution can be derived consistently."
- CHANGE_ID: UE.CHG.2026-01-08.EXP.TURNING.POINT.001

---

## 0) PURPOSE (LAW)
This engine owns the **TURNING POINT primitive**:
- identifies events (or small clusters) that change the direction of a conflict/trajectory
- classifies pivot type (reveal, reversal, commitment, betrayal, etc.)
- marks irreversibility and consequences
- emits follow-through obligations (what must happen after)

Hard rule:
- If something is called a turning point, it must produce a measurable trajectory change.

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- define story acts/structure (narrative family)
- write scenes (scene construction engine)
- define climax (separate climax engine)
- define resolution (separate resolution engine)
- define conflict objects (conflict engine)
- define world laws (world law engine)

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- EVENT_PACK (one or more)
- CAUSAL_GRAPH (optional but recommended)
- CONFLICT_OBJECT_SET
- ESCALATION_STATE_SCHEMA
- TENSION_STAKES_MAP (optional)
- WORLD_LAWSET (optional)

PRODUCES:
- TURNING_POINT_SET
- PIVOT_TYPE_REGISTRY
- TURNING_POINT_OBLIGATIONS

DEPENDS_ON:
- [05_EXPRESSION_ENGINES/01__EVENT_ENG, 05_EXPRESSION_ENGINES/03__CONFLICT_ENG]

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/EXPRESSION/TURNING_POINTS/
OPTIONAL:
- KB/TURNING_POINTS (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Turning Point: an event that changes trajectory (goal, power balance, available options, stakes).
- Pivot Type: class of turning point (REVEAL, REVERSAL, COMMITMENT, etc.).
- Trajectory: measurable direction of conflict (escalation state, power balance, stake pressure).
- Irreversibility Marker: signal that returning to prior state is impossible or costly.
- Follow-through Obligation: requirement created by the pivot (payoff, consequence, new constraint).

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- turning point detection and classification
- trajectory delta specification
- irreversibility and obligations emission

OUT OF SCOPE (HARD):
- conflict creation (conflict engine)
- climax selection (climax engine)
- resolution closure (resolution engine)
- narrative act placement rules (narrative engines)

COLLISION RULE:
- If you need “peak of story” → climax engine.
- If you need “final closure” → resolution engine.
- If you need “why pivot is possible” → cause-effect and/or world law validation.

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: each turning point references at least one event_id and one conflict_id.
R2 (HARD) MUST: turning point declares trajectory delta (before → after) in measurable terms.
R3 (HARD) MUST: pivot type is from registry.
R4 (HARD) MUST: if pivot is irreversible, must define irreversibility markers and costs.
R5 (HARD) MUST: turning point creates obligations (non-empty) unless explicitly “terminal pivot”.
R6 (HARD) FORBIDDEN: labeling a turning point without delta (pure label).
R7 (SOFT) SHOULD: align with stakes map if provided.
R8 (HARD) MUST: if world lawset provided, pivot must not require impossible capability.

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: PIVOT_TYPE_REGISTRY
- MUST:
  - registry_id
  - version
  - pivot_types[] (non-empty)
- PIVOT TYPE (minimum):
  - pivot_id
  - name
  - definition (testable)
  - typical_signals[]
  - typical_obligations[]
- Baseline pivot types:
  - REVEAL
  - REVERSAL
  - COMMITMENT
  - BETRAYAL
  - SACRIFICE
  - POWER_SHIFT
  - TRAP_SPRING
  - ESCAPE
  - MORAL_CHOICE
  - LOSS_CONFIRMATION
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/EXPRESSION/TURNING_POINTS/PIVOT_TYPE_REGISTRY.md

VALIDATION:
- baseline set exists (unless overridden)

---

ARTIFACT: TURNING_POINT_SET
- MUST:
  - set_id
  - version
  - turning_points[] (non-empty)
  - checks[] (non-empty)
- TURNING POINT (minimum):
  - tp_id
  - title
  - conflict_id
  - source_event_ids[] (non-empty)
  - pivot_type (pivot_id)
  - trajectory_delta:
    - metric (enum: ESCALATION_STATE|POWER_BALANCE|OPTIONS|STAKE_PRESSURE|GOAL_DIRECTION)
    - before
    - after
    - explanation (short, testable)
  - irreversibility:
    - level (enum: REVERSIBLE|COSTLY|IRREVERSIBLE|UNKNOWN)
    - markers[] (optional)
    - costs[] (optional)
  - stakes_refs[] (optional)
  - causal_refs[] (optional)
  - obligations_ref (pointer)
  - severity (S0|S1|S2|S3)
  - notes
- CHECK (minimum):
  - check_id
  - description
  - severity
- VALIDATION:
  - conflict_id exists
  - source_event_ids exist
  - trajectory_delta before/after are not identical (unless pivot_type explicitly allows “clarification pivot” with reason)
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/EXPRESSION/TURNING_POINTS/TURNING_POINT_SET.md

---

ARTIFACT: TURNING_POINT_OBLIGATIONS
- MUST:
  - obligations_id
  - version
  - obligations[] (non-empty)
  - checks[] (non-empty)
- OBLIGATION (minimum):
  - obligation_id
  - tp_id
  - type (enum: CONSEQUENCE|PAYOFF|NEW_CONSTRAINT|NEW_GOAL|ESCALATION_REQUIREMENT|REPAIR_REQUIREMENT)
  - statement (testable)
  - due_by (optional: time/segment marker)
  - severity_if_unpaid (S0|S1|S2|S3)
  - route_to (engine pointer)
  - notes
- CHECK (minimum):
  - check_id
  - description
  - severity
- VALIDATION:
  - every tp_id exists in turning point set
  - any S0 obligation has route_to
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/EXPRESSION/TURNING_POINTS/TURNING_POINT_OBLIGATIONS.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Load conflicts + events (+ causal graph if available).
2) Identify candidate pivot events:
   - escalation state jumps
   - power balance shifts
   - option set changes
   - major reveals/breaches
3) Classify pivot type using registry.
4) Compute trajectory delta (before/after).
5) Determine irreversibility level, markers, and costs.
6) Generate obligations (consequences/payoffs/constraints).
7) Validate gates and emit artifacts.

---

## 8) S0 BLOCKERS (STOP)
- S0-1: turning point references unknown conflict_id or event_id.
- S0-2: missing or non-measurable trajectory delta.
- S0-3: pivot type not in registry.
- S0-4: S0 obligations exist without route_to.
- S0-5: pivot requires impossible capability under world lawset (if provided).

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- conflicts from conflict engine
- events from event engine
- causality refs from cause-effect engine (optional)

Downstream:
- `05__CLIMAX_ENG` (selects peak turning point(s))
- `06__RESOLUTION_ENG` (pays obligations and closes conflicts)
- narrative engines (map turning points into scenes/arc shape)
- continuity engines (ensure obligations are paid)

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Family template:
  05_EXPRESSION_ENGINES/00__TEMPLATE__ENGINE__EXPRESSION_ENGINES.md

--- END.

LOCK: OPEN
