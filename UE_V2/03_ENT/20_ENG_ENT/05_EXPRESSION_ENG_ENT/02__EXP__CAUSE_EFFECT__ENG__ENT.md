# CAUSE–EFFECT ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/05_EXPRESSION_ENGINES/02__CAUSE_EFFECT_ENG.md
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
UID: UE.ENG.EXP.CAUSE.EFFECT.001
OWNER: SYSTEM
ROLE: Converts events into deterministic causal graphs: causal links, conditions, constraints, chain validation, and paradox detection. Produces causal graph artifacts used by narrative logic/continuity and world causality alignment.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Cause–Effect Engine created: causal graph schema, link rules, chain validation, and paradox detection."
- REASON: "Events alone do not form logic; deterministic causality is required for consistency."
- IMPACT: "Narrative and world systems can audit 'why' paths and prevent impossible chains."
- CHANGE_ID: UE.CHG.2026-01-08.EXP.CAUSE.EFFECT.001

---

## 0) PURPOSE (LAW)
This engine owns **causality over events**:
- links events with directed causal edges (A → B)
- defines conditions (when the link holds)
- validates chains (no missing prerequisites, no impossible jumps)
- detects paradox/cycles and forces explicit handling
- produces a causal graph that downstream engines can consume

Hard rule:
- No “because it happened” chains; causality must be explicit.

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- define events themselves (event engine owns schema)
- define conflict as stakes/escalation (conflict engine)
- define narrative structure as acts/scenes (narrative family)
- define world laws (world law engine) — it may consume law constraints as validation references
- define production timing or montage logic

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- EVENT_PACK (one or more)
- EVENT_TYPE_REGISTRY
- EVENT_VALIDATION_GATES
- WORLD_LAWSET (optional but recommended)
- CAUSALITY_CONSTRAINTS (optional; from world law engine)

PRODUCES:
- CAUSAL_GRAPH
- CAUSAL_LINK_SET
- CAUSAL_VALIDATION_REPORT

DEPENDS_ON:
- [05_EXPRESSION_ENGINES/01__EVENT_ENG]

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/EXPRESSION/CAUSALITY/
OPTIONAL:
- KB/CAUSALITY (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Causal Link: directed edge `A -> B` with conditions and rationale.
- Condition: predicate that must be true for link activation (state, actor capacity, law constraint).
- Chain: ordered list of events connected by causal links.
- Paradox/Cycle: cycle in causal graph; allowed only if explicitly marked and resolved by rule.
- Causal Graph: graph of events (nodes) and causal links (edges).

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- causal linking rules and graph formation
- chain completeness and contradiction detection
- paradox/cycle detection and resolution routing
- validation report emission

OUT OF SCOPE (HARD):
- conflict/tension mapping (conflict engine)
- turning points/climax labeling (other expression engines)
- world law definition (world law engine)
- narrative arc design

COLLISION RULE:
- If “is this possible at all” → world law engine is authority; this engine only validates against it.
- If “what is the story meaning” → narrative engines.
- If “how conflict escalates emotionally” → conflict engine.

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: every causal link references existing event_ids.
R2 (HARD) MUST: each link has a rationale and at least one condition OR explicitly states unconditional causality with reason.
R3 (HARD) MUST: chain validation requires no missing prerequisites for S0 impacts.
R4 (HARD) MUST: paradox/cycles are flagged and require a resolution rule; hidden cycles forbidden.
R5 (HARD) FORBIDDEN: causality statements that are pure vibes (“destiny”, “plot”) without mapping to conditions.
R6 (HARD) MUST: causal graph supports multiple causes for one effect (AND/OR semantics must be explicit).
R7 (SOFT) SHOULD: causal links reference world causality constraints when applicable.
R8 (HARD) MUST: validation report includes S0 blockers and recommended repairs.

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: CAUSAL_LINK_SET
- MUST:
  - link_set_id
  - version
  - links[] (non-empty)
  - semantics (AND/OR rules)
  - checks[] (non-empty)
- LINK (minimum):
  - link_id
  - cause_event_ids[] (one or more)
  - effect_event_id
  - logic (enum: ALL_CAUSES_REQUIRED|ANY_CAUSE_SUFFICIENT)
  - conditions[] (optional but recommended)
  - rationale (testable)
  - world_constraint_refs[] (optional)
  - reversibility (REVERSIBLE|IRREVERSIBLE|UNKNOWN)
  - severity_if_broken (S0|S1|S2|S3)
  - notes
- CONDITION (minimum):
  - condition_id
  - type (STATE|RESOURCE|CAPABILITY|RELATIONSHIP|LAW|TIME_WINDOW|LOCATION)
  - expression (testable)
  - required (bool)
- CHECK (minimum):
  - check_id
  - description
  - severity
- VALIDATION:
  - every referenced event id exists
  - each link has rationale
  - S0 links must have at least one condition or explicit “unconditional” justification
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/EXPRESSION/CAUSALITY/CAUSAL_LINK_SET.md

---

ARTIFACT: CAUSAL_GRAPH
- MUST:
  - graph_id
  - version
  - nodes[] (event ids)
  - edges[] (link ids)
  - cycles[] (optional)
  - topological_order (optional if DAG)
  - open_unknowns[] (optional)
- EDGE (minimum):
  - link_id
  - from_event_ids[] (cause list)
  - to_event_id
- CYCLE (minimum):
  - cycle_id
  - event_ids[] (non-empty)
  - cycle_type (TIME_LOOP|INFO_LOOP|DEPENDENCY_LOOP|OTHER)
  - allowed (bool)
  - resolution_rule_ref (required if allowed=true)
  - severity (S0|S1|S2|S3)
- VALIDATION:
  - graph must be buildable from link set
  - if cycles exist and allowed=false → S0 fail unless resolved
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/EXPRESSION/CAUSALITY/CAUSAL_GRAPH.md

---

ARTIFACT: CAUSAL_VALIDATION_REPORT
- MUST:
  - report_id
  - version
  - issues[] (can be empty)
  - severity_summary
  - missing_prerequisites[] (optional)
  - paradoxes[] (optional)
  - recommended_repairs[] (non-empty if S0 issues exist)
- ISSUE (minimum):
  - issue_id
  - type (MISSING_CAUSE|MISSING_CONDITION|IMPOSSIBLE_CHAIN|CYCLE_UNRESOLVED|WORLD_LAW_VIOLATION|Rationale_VAGUE)
  - ref_ids[] (event/link ids)
  - severity (S0|S1|S2|S3)
  - description
  - fix_route (engine pointer)
- REPAIR (minimum):
  - issue_id
  - suggestion
  - route_to (engine pointer)
- VALIDATION:
  - any S0 issue must have a repair route
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/EXPRESSION/CAUSALITY/CAUSAL_VALIDATION_REPORT.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Load events and validate via EVENT gates.
2) Propose causal links:
   - derive candidate causes based on event types and preconditions
3) Attach conditions:
   - state/resource/law constraints
4) Build graph:
   - nodes = events, edges = links
5) Validate:
   - missing prerequisites for high-impact events
   - impossible chains vs world law constraints (if provided)
   - cycles/paradoxes
6) Emit:
   - link set + causal graph + validation report

---

## 8) S0 BLOCKERS (STOP)
- S0-1: link references unknown event id.
- S0-2: S0-severity link has no conditions and no unconditional justification.
- S0-3: unresolved cycle marked allowed=false (paradox not handled).
- S0-4: chain violates hard world law constraints (if lawset provided).
- S0-5: validation report missing repair routes for S0 issues.

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- Event engine provides schema and event typing.

Downstream consumers:
- `03__CONFLICT_ENG` (select conflict-relevant causal chains)
- `04__TURNING_POINT_ENG` (turning points emerge from causal reversals)
- `05__CLIMAX_ENG` (peak causal convergence)
- `06__RESOLUTION_ENG` (closure requires satisfied causal prerequisites)
- narrative logic & continuity engines (use causal graph to prevent holes)
- world law engine alignment (optional validation references)

Governance:
- If causal schema/rules change and affect multiple pipelines, route via governance change control + audit.

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Family template:
  05_EXPRESSION_ENGINES/00__TEMPLATE__ENGINE__EXPRESSION_ENGINES.md

--- END.

LOCK: OPEN
