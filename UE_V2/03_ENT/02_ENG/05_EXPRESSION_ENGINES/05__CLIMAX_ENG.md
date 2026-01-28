# CLIMAX ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/05_EXPRESSION_ENGINES/05__CLIMAX_ENG.md
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
UID: UE.ENG.EXP.CLIMAX.001
OWNER: SYSTEM
ROLE: Selects and specifies climax points from turning points + conflicts + events: peak collision, maximum stakes, irreversible commitments, and convergence constraints. Produces climax set and climax obligations.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Climax Engine created: climax schema, peak selection rules, convergence validation, and climax obligations."
- REASON: "Pipelines need explicit peak points to anchor resolution and pacing."
- IMPACT: "Climax becomes stampable and verifiable; resolution can be derived deterministically."
- CHANGE_ID: UE.CHG.2026-01-08.EXP.CLIMAX.001

---

## 0) PURPOSE (LAW)
This engine owns the **CLIMAX primitive**:
- selects peak event(s) / turning point(s) where conflict collision is maximal
- validates convergence (major obligations and stakes must intersect)
- declares what becomes irreversible at the climax
- emits obligations that resolution must pay

Hard rule:
- Climax is not “big action”; it is **peak decision/collision with irreversible consequence**.

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- create conflicts (conflict engine)
- detect turning points (turning point engine)
- define pacing/rhythm (pacing engine)
- write scenes (scene construction engine)
- define final closure logic (resolution engine does)
- define author theme (theme engine)

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- TURNING_POINT_SET
- TURNING_POINT_OBLIGATIONS (recommended)
- CONFLICT_OBJECT_SET
- EVENT_PACK
- CAUSAL_GRAPH (optional but recommended)
- TENSION_STAKES_MAP (optional)
- WORLD_LAWSET (optional)

PRODUCES:
- CLIMAX_SET
- CLIMAX_SELECTION_RULES
- CLIMAX_OBLIGATIONS

DEPENDS_ON:
- [05_EXPRESSION_ENGINES/04__TURNING_POINT_ENG, 05_EXPRESSION_ENGINES/03__CONFLICT_ENG, 05_EXPRESSION_ENGINES/01__EVENT_ENG]

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/EXPRESSION/CLIMAX/
OPTIONAL:
- KB/CLIMAX (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Climax: peak collision where conflict trajectory locks into outcome space (irreversibility spike).
- Peak Metric: measurable driver for climax selection (stakes pressure, convergence, escalation max).
- Convergence: multiple obligations/chains meet in the same pivot window.
- Climax Window: a minimal range of events (1–3) that forms the peak.
- Climax Obligation: required payoff/consequence emitted by climax.

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- selecting and specifying climax points/windows
- defining peak metrics and validation
- declaring irreversibility and obligations

OUT OF SCOPE (HARD):
- turning point detection (turning point engine)
- resolution generation (resolution engine)
- pacing and montage rhythm (pacing/editing engines)
- story structure decisions (narrative family)

COLLISION RULE:
- If it’s “a pivot” but not peak → turning point engine.
- If it’s “closure” → resolution engine.
- If it’s “tension build pacing” → pacing engine.

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: each climax references at least one conflict_id and at least one turning point tp_id.
R2 (HARD) MUST: climax declares peak metrics and why this is the maximum.
R3 (HARD) MUST: climax declares irreversibility markers and what becomes locked.
R4 (HARD) MUST: climax defines a window (1–3 events) and references those event_ids.
R5 (HARD) MUST: climax emits obligations for resolution (non-empty) unless marked “terminal collapse climax”.
R6 (HARD) FORBIDDEN: climax as “largest fight” without metric and irreversibility.
R7 (SOFT) SHOULD: include convergence score if obligations/stakes map exists.
R8 (HARD) MUST: if world lawset provided, climax cannot require impossible actions.

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: CLIMAX_SELECTION_RULES
- MUST:
  - rules_id
  - version
  - peak_metrics[] (non-empty)
  - selection_steps[] (non-empty)
  - checks[] (non-empty)
- PEAK METRIC (minimum):
  - metric_id
  - name
  - definition (testable)
  - scoring_method (short; deterministic)
  - required_inputs[]
- Baseline metrics:
  - STAKE_PRESSURE_MAX
  - ESCALATION_MAX
  - CONVERGENCE_MAX
  - IRREVERSIBILITY_SPIKE
  - OPTION_CLOSURE (options collapse)
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/EXPRESSION/CLIMAX/CLIMAX_SELECTION_RULES.md

VALIDATION:
- baseline metrics exist (unless overridden)

---

ARTIFACT: CLIMAX_SET
- MUST:
  - set_id
  - version
  - climaxes[] (non-empty)
  - checks[] (non-empty)
- CLIMAX (minimum):
  - climax_id
  - title
  - conflict_ids[] (non-empty)
  - tp_ids[] (non-empty)
  - climax_window:
    - event_ids[] (1..3)
    - window_mode (SINGLE|RANGE)
  - peak_metrics_used[] (non-empty)
  - peak_scores (optional map metric->score)
  - convergence:
    - convergence_score (optional)
    - converging_refs[] (tp/obligation/stakes refs)
  - irreversibility:
    - level (COSTLY|IRREVERSIBLE|UNKNOWN)
    - locked_elements[] (non-empty)
    - markers[] (optional)
  - required_choice_or_collision (testable statement)
  - severity (S0|S1|S2|S3)
  - obligations_ref
  - notes
- CHECK (minimum):
  - check_id
  - description
  - severity
- VALIDATION:
  - referenced conflict_ids exist
  - referenced tp_ids exist
  - window event_ids exist
  - locked_elements non-empty if level=IRREVERSIBLE
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/EXPRESSION/CLIMAX/CLIMAX_SET.md

---

ARTIFACT: CLIMAX_OBLIGATIONS
- MUST:
  - obligations_id
  - version
  - obligations[] (non-empty)
  - checks[] (non-empty)
- OBLIGATION (minimum):
  - obligation_id
  - climax_id
  - type (enum: CONSEQUENCE|PAYOFF|COST|NEW_STATE|REVEAL_CONFIRMATION|MORAL_PRICE)
  - statement (testable)
  - due_by (optional: post-climax window marker)
  - severity_if_unpaid (S0|S1|S2|S3)
  - route_to (engine pointer: typically resolution or continuity)
  - notes
- CHECK (minimum):
  - check_id
  - description
  - severity
- VALIDATION:
  - climax_id exists in climax set
  - if any S0 obligations → route_to required
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/EXPRESSION/CLIMAX/CLIMAX_OBLIGATIONS.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Load conflicts, turning points, events (+ stakes/causal graph if available).
2) Score candidate tp/events using peak metrics.
3) Select peak(s):
   - 1 climax per major conflict cluster by default
4) Define climax window (1–3 events).
5) Determine irreversibility and locked elements.
6) Generate climax obligations (payoffs/costs/state changes).
7) Validate gates and emit artifacts.

---

## 8) S0 BLOCKERS (STOP)
- S0-1: climax references unknown conflict_id or tp_id.
- S0-2: climax window empty or >3 events without justification.
- S0-3: no peak metrics declared or no reason for maximum.
- S0-4: irreversibility marked IRREVERSIBLE but locked_elements empty.
- S0-5: S0 obligations exist without route_to.

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- turning points provide candidates
- conflicts provide opposition context
- events provide concrete occurrences

Downstream:
- `06__RESOLUTION_ENG` (pays climax obligations and closes conflicts)
- narrative engines (map climax into arc and scene placements)
- pacing engine (can use climax window as anchor)
- continuity engines (ensure obligations/payoffs occur)

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Family template:
  05_EXPRESSION_ENGINES/00__TEMPLATE__ENGINE__EXPRESSION_ENGINES.md

--- END.

LOCK: OPEN
