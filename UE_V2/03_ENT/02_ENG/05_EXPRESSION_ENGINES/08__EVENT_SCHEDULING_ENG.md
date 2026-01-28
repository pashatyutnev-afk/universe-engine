# EVENT SCHEDULING ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/05_EXPRESSION_ENGINES/08__EVENT_SCHEDULING_ENG.md
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
UID: UE.ENG.EXP.EVENT.SCHED.001
OWNER: SYSTEM
ROLE: Converts events into deterministic schedules: ordering, time modes, windows, dependencies, cadence constraints, and consistency gates. Produces event schedule artifacts compatible with timelines and narrative continuity.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Event Scheduling Engine created: schedule schema, ordering rules, window constraints, and validation gates."
- REASON: "Events need consistent ordering/time windows for continuity and pacing without mixing montage logic."
- IMPACT: "Event sequences become auditable; timeline alignment becomes deterministic."
- CHANGE_ID: UE.CHG.2026-01-08.EXP.EVENT.SCHED.001

---

## 0) PURPOSE (LAW)
This engine owns **EVENT SCHEDULING** (story-time ordering, not editing/montage):
- defines event ordering and temporal windows
- resolves relative time into schedule constraints
- encodes dependencies and minimum/maximum gaps
- validates schedule consistency (no impossible overlaps unless allowed)

Hard rule:
- This engine is **story-time** scheduling only.
- Screen-time rhythm belongs to editing/montage (production family).

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- define pacing/rhythm as narrative feel (pacing engine owns rhythm)
- define montage/edit timing (08_KNOWLEDGE_PRODUCTION_ENGINES/07__EDITING_MONTAGE_ENG)
- invent causality (cause-effect engine)
- define story structure (story structure engine)
- define timeline epochs (timeline engine owns epoch model; this engine aligns to it)

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- EVENT_PACK
- EVENT_SCHEMA_STANDARD
- CAUSAL_GRAPH (optional but recommended for dependencies)
- TIMELINE_EPOCH_MODEL (optional)
- WORLD_LAWSET (optional: time/physics constraints)
- SCHEDULING_CONSTRAINTS (optional)

PRODUCES:
- EVENT_SCHEDULE
- SCHEDULING_CONSTRAINT_SET
- SCHEDULING_VALIDATION_REPORT

DEPENDS_ON:
- [05_EXPRESSION_ENGINES/01__EVENT_ENG]
(soft) [05_EXPRESSION_ENGINES/02__CAUSE_EFFECT_ENG] for dependency inference

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/EXPRESSION/SCHEDULE/
OPTIONAL:
- KB/SCHEDULE (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Schedule: ordered plan of events with time modes and constraints.
- Time Mode: EXACT, RANGE, RELATIVE, UNKNOWN (from Event schema).
- Window: allowed time span for an event.
- Gap: min/max distance between events.
- Dependency: requirement that one event must occur before another.
- Overlap: two events in the same time window; allowed only if explicitly flagged.

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- story-time ordering and time windows
- dependency and gap constraints
- schedule validation and repair suggestions

OUT OF SCOPE (HARD):
- pacing feel (belongs to 02_DOMAIN_NARRATIVE_ENGINES/05__PACING_RHYTHM_ENG)
- screen-time editing (belongs to 08_KNOWLEDGE_PRODUCTION_ENGINES/07__EDITING_MONTAGE_ENG)
- epoch definitions (belongs to 04_DOMAIN_WORLD_ENGINES/03__TIMELINE_EPOCH_ENG)

COLLISION RULE:
- If constraint is “audience experience timing” → editing/montage.
- If constraint is “dramatic rhythm” → pacing engine.
- If constraint is “calendar/epoch rules” → timeline epoch engine.

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: schedule contains all events from input pack or explicitly lists exclusions.
R2 (HARD) MUST: each scheduled item references an event_id and includes time_mode.
R3 (HARD) MUST: ordering is deterministic: either explicit order_index or dependency DAG.
R4 (HARD) MUST: overlaps require explicit allow flag and reason.
R5 (HARD) MUST: if causal graph exists, dependency violations are S0 for S0 events.
R6 (HARD) FORBIDDEN: using montage cuts as justification for story-time order.
R7 (SOFT) SHOULD: include min/max gaps for major causal links.
R8 (HARD) MUST: validation report includes repair actions for S0 issues.

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: SCHEDULING_CONSTRAINT_SET
- MUST:
  - constraint_set_id
  - version
  - constraints[] (non-empty)
  - checks[] (non-empty)
- CONSTRAINT (minimum):
  - constraint_id
  - type (DEPENDENCY|MIN_GAP|MAX_GAP|WINDOW|NO_OVERLAP|ALLOW_OVERLAP|ORDER_LOCK)
  - from_event_id (optional)
  - to_event_id (optional)
  - value (testable)
  - severity_if_broken (S0|S1|S2|S3)
  - rationale
- VALIDATION:
  - referenced event ids exist
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/EXPRESSION/SCHEDULE/SCHEDULING_CONSTRAINT_SET.md

---

ARTIFACT: EVENT_SCHEDULE
- MUST:
  - schedule_id
  - version
  - items[] (non-empty)
  - exclusions[] (optional)
  - topological_order (optional)
  - checks[] (non-empty)
- ITEM (minimum):
  - schedule_item_id
  - event_id
  - order_index (optional if dependencies provide order)
  - time_mode (EXACT|RANGE|RELATIVE|UNKNOWN)
  - time_value (string; ISO for EXACT if possible)
  - window (optional):
    - start (optional)
    - end (optional)
    - description (optional)
  - dependencies[] (optional: event_ids)
  - gap_constraints[] (optional: constraint_ids)
  - overlap_policy:
    - allowed (bool)
    - with_event_ids[] (optional)
    - reason (required if allowed=true)
  - epoch_id (optional)
  - notes
- EXCLUSION (minimum):
  - event_id
  - reason
- CHECK (minimum):
  - check_id
  - description
  - severity
- VALIDATION:
  - each event_id exists
  - either order_index is complete OR dependency graph is acyclic (unless explicitly allowed by rule)
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/EXPRESSION/SCHEDULE/EVENT_SCHEDULE.md

---

ARTIFACT: SCHEDULING_VALIDATION_REPORT
- MUST:
  - report_id
  - version
  - issues[] (can be empty)
  - severity_summary
  - recommended_repairs[] (required if S0 issues exist)
- ISSUE (minimum):
  - issue_id
  - type (MISSING_EVENT|ORDER_CONFLICT|DEPENDENCY_VIOLATION|OVERLAP_NOT_ALLOWED|WINDOW_CONTRADICTION|CYCLE_FOUND)
  - ref_ids[] (event/constraint ids)
  - severity (S0|S1|S2|S3)
  - description
  - fix_route (engine pointer)
- REPAIR (minimum):
  - issue_id
  - suggestion
  - action (REORDER|ADD_CONSTRAINT|ALLOW_OVERLAP|EXPAND_WINDOW|MARK_UNKNOWN|SPLIT_EVENT)
- VALIDATION:
  - S0 issues must have repairs
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/EXPRESSION/SCHEDULE/SCHEDULING_VALIDATION_REPORT.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Load events and normalize time modes.
2) Build initial order:
   - order_index if provided
   - else infer from dependencies (causal graph if available)
3) Apply constraints:
   - windows, gaps, no-overlap rules
4) Detect conflicts:
   - overlaps, cycles, window contradictions
5) Emit schedule + constraint set + validation report.

---

## 8) S0 BLOCKERS (STOP)
- S0-1: schedule references unknown event ids.
- S0-2: dependency cycle found and not explicitly allowed with resolution rule.
- S0-3: overlap exists but overlap_policy.allowed is false or missing reason.
- S0-4: S0 dependency violations when causal graph indicates hard prerequisite.
- S0-5: missing repairs for S0 issues in validation report.

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- event engine provides time modes and event schema.
- cause-effect engine optionally provides dependency inference.

Downstream:
- timeline & epoch engine consumes schedule alignment (optional)
- narrative continuity engine uses schedule as anchor
- pacing engine may reference schedule windows (but does not own scheduling)
- production engines convert schedule to depiction sequences (separate layer)

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Family template:
  05_EXPRESSION_ENGINES/00__TEMPLATE__ENGINE__EXPRESSION_ENGINES.md

--- END.

LOCK: OPEN
