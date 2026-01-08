# OPTIMIZATION ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/10_META_EVOLUTION_ENGINES/03__OPTIMIZATION_ENG.md
SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: ENGINE
FAMILY: 10_META_EVOLUTION_ENGINES
CLASS: META (L4)
LEVEL: L4
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.META.OPTIMIZATION.001
OWNER: SYSTEM
ROLE: Selects and prioritizes improvement candidates deterministically: objective functions, tradeoff rules, optimization backlog, and gates. Consumes lessons/patterns/metrics and outputs ranked change plans routed through governance (no direct canon edits).

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Optimization Engine created: objective schema, scoring model, backlog prioritization, and governance routing."
- REASON: "System needs deterministic prioritization of improvements instead of ad-hoc edits."
- IMPACT: "Change selection becomes auditable, consistent, and canon-safe."
- CHANGE_ID: UE.CHG.2026-01-08.META.OPTIMIZATION.001

---

## 0) PURPOSE (LAW)
This engine owns **OPTIMIZATION selection**:
- defines objectives (what to optimize: coherence, speed, completeness, safety)
- defines metrics and scoring models (how to rank candidates)
- prioritizes change candidates into an optimization backlog
- outputs a ranked change plan with tradeoffs
- routes to governance pipeline (no direct canon edits)

Hard rule:
- Optimization chooses what to change; governance executes canon changes.

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- directly apply file changes
- create new learning hypotheses (learning engine owns)
- extract patterns (pattern extraction engine owns)
- validate correctness of outputs (QA engines own; optimization consumes their metrics)

FORBIDDEN:
- “optimize” without objective function and measurable scoring criteria
- bypassing governance routing

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- CHANGE_CANDIDATE_SET (recommended)
- LESSON_LOG (optional)
- HYPOTHESIS_REGISTRY (optional)
- PATTERN_LIBRARY (optional)
- METRICS_SNAPSHOT (optional)
- QA_REPORT_SET (optional)
- USER_FEEDBACK_LOG (optional)

PRODUCES:
- OPTIMIZATION_OBJECTIVE_SPEC
- SCORING_MODEL_SPEC
- PRIORITIZED_BACKLOG
- OPTIMIZATION_PLAN
- OPTIMIZATION_GATES_REPORT

DEPENDS_ON:
- [10_META_EVOLUTION_ENGINES/01__LEARNING_ENG]
(soft) [00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG, 00_GOVERNANCE_ENGINES/07__DECISION_APPROVAL_ENG]

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/META/OPTIMIZATION/
OPTIONAL:
- KB/META/OPTIMIZATION (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Objective: named optimization goal with weight (e.g., reduce S0 failures).
- Metric: measurable signal (counts, pass/fail rates, latency proxies).
- Scoring Model: rule mapping candidates to scores via objective weights.
- Backlog: ordered list of candidates with rationale and risk.
- Tradeoff: explicit rule explaining why some objectives lose.

Enums (baseline):
- objective_type: QUALITY|CONSISTENCY|SPEED|COMPLETENESS|SAFETY|MAINTAINABILITY
- severity: S0|S1|S2|S3
- status: PLANNED|IN_PROGRESS|DONE|DEFERRED

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- defining objective + scoring models
- ranking/prioritizing candidates
- creating optimization plan and backlog
- gates ensuring governance routing

OUT OF SCOPE (HARD):
- applying changes
- auditing changes (audit engine)
- collecting raw lessons (learning engine)

COLLISION RULE:
- If request is “change files now” → governance change control
- If request is “generate new candidates from lessons” → learning engine

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: objective spec defines objectives with weights and success metrics.
R2 (HARD) MUST: scoring model is deterministic and references objective spec.
R3 (HARD) MUST: prioritized backlog ranks candidates with score, risk, and rationale.
R4 (HARD) MUST: optimization plan defines execution order and governance route per item.
R5 (HARD) FORBIDDEN: backlog entries missing risk or governance route.
R6 (SOFT) SHOULD: include “quick wins” vs “deep changes” categorization.
R7 (HARD) MUST: gates detect missing objectives, missing scoring, and non-deterministic ranking.

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: OPTIMIZATION_OBJECTIVE_SPEC
- MUST:
  - objective_spec_id
  - version
  - objectives[] (non-empty)
  - checks[] (non-empty)
- OBJECTIVE (minimum):
  - objective_id
  - type (QUALITY|CONSISTENCY|SPEED|COMPLETENESS|SAFETY|MAINTAINABILITY)
  - description (testable)
  - weight (0..100)
  - success_metrics[] (non-empty)
  - failure_signals[] (optional)
- VALIDATION:
  - objectives non-empty
  - weights sum > 0
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/META/OPTIMIZATION/OPTIMIZATION_OBJECTIVE_SPEC.md

---

ARTIFACT: SCORING_MODEL_SPEC
- MUST:
  - scoring_model_id
  - version
  - objective_spec_ref
  - scoring_rules[] (non-empty)
  - normalization_rules[] (optional)
  - checks[] (non-empty)
- SCORING RULE (minimum):
  - rule_id
  - input_signal (metric or attribute)
  - transformation (testable; e.g., linear clamp)
  - weight_ref (objective_id)
  - notes
- VALIDATION:
  - objective_spec_ref present
  - scoring_rules non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/META/OPTIMIZATION/SCORING_MODEL_SPEC.md

---

ARTIFACT: PRIORITIZED_BACKLOG
- MUST:
  - backlog_id
  - version
  - items[] (non-empty)
  - checks[] (non-empty)
- ITEM (minimum):
  - item_id
  - candidate_ref
  - score (number)
  - risk_level (S0|S1|S2|S3)
  - effort_proxy (optional)
  - rationale (testable)
  - category (QUICK_WIN|STRUCTURAL|RISK_REDUCTION|QUALITY_BOOST) (optional)
  - governance_route (required)
- VALIDATION:
  - items non-empty
  - each item has governance_route
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/META/OPTIMIZATION/PRIORITIZED_BACKLOG.md

---

ARTIFACT: OPTIMIZATION_PLAN
- MUST:
  - plan_id
  - version
  - execution_order[] (non-empty)
  - milestones[] (optional)
  - tradeoffs[] (non-empty)
  - rollback_policy (optional)
  - checks[] (non-empty)
- EXECUTION ORDER ENTRY (minimum):
  - order_index
  - backlog_item_ref
  - why_now (testable)
  - dependency_refs[] (optional)
- TRADEOFF (minimum):
  - tradeoff_id
  - statement (testable)
  - affected_objectives[] (non-empty)
  - justification (testable)
- VALIDATION:
  - execution_order non-empty
  - tradeoffs non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/META/OPTIMIZATION/OPTIMIZATION_PLAN.md

---

ARTIFACT: OPTIMIZATION_GATES_REPORT
- MUST:
  - report_id
  - version
  - gates[] (non-empty)
  - issues[] (can be empty)
  - overall (PASS|WARN|FAIL)
- Minimum required gates:
  - G1_OBJECTIVES_EMPTY (S0)
  - G2_SCORING_MODEL_MISSING (S0)
  - G3_BACKLOG_EMPTY (S0)
  - G4_PLAN_EMPTY (S0)
  - G5_NON_DETERMINISTIC_RANKING (S1)
  - G6_MISSING_GOVERNANCE_ROUTE (S0)
- VALIDATION:
  - FAIL if any S0 fails
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/META/OPTIMIZATION/OPTIMIZATION_GATES_REPORT.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Load candidates and metrics snapshots.
2) Define objective spec (weights + success metrics).
3) Define scoring model (rules).
4) Score and rank candidates into backlog.
5) Create optimization plan (execution order + tradeoffs + routing).
6) Run gates and emit artifacts.

---

## 8) S0 BLOCKERS (STOP)
- S0-1: objectives empty.
- S0-2: scoring model missing.
- S0-3: backlog empty.
- S0-4: plan empty.
- S0-5: any backlog item missing governance route.

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- consumes learning outputs and candidate sets
- consumes metrics and QA outputs

Downstream:
- governance change control executes selected candidates
- decision approval engine can gate high-risk items
- audit log records changes

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Governance:
  00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md
  00_GOVERNANCE_ENGINES/07__DECISION_APPROVAL_ENG.md
- Family template:
  10_META_EVOLUTION_ENGINES/00__TEMPLATE__ENGINE__META_EVOLUTION_ENGINES.md
- Family README:
  10_META_EVOLUTION_ENGINES/00__README__META_EVOLUTION_ENGINES.md

--- END.

LOCK: OPEN
