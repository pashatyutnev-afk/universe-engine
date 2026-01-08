# LEARNING ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/10_META_EVOLUTION_ENGINES/01__LEARNING_ENG.md
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
UID: UE.ENG.META.LEARNING.001
OWNER: SYSTEM
ROLE: Converts execution feedback into deterministic learning artifacts: lesson capture, hypothesis registry, change candidates, and gates. Produces actionable learning outputs without directly modifying canon (routes via governance).

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Learning Engine created: lesson schema, hypothesis registry, change candidate packaging, and governance routing gates."
- REASON: "System needs deterministic learning loop to improve engines without ad-hoc edits."
- IMPACT: "Improvements become auditable, repeatable, and canon-safe via governance pipeline."
- CHANGE_ID: UE.CHG.2026-01-08.META.LEARNING.001

---

## 0) PURPOSE (LAW)
This engine owns **LEARNING LOOP artifacts**:
- captures lessons from executions (what worked/failed)
- formalizes hypotheses and tests (what to change and why)
- packages change candidates for engines/templates/rules
- enforces governance routing (no direct canon changes)
- emits gates for quality and evidence requirements

Hard rule:
- Learning outputs do not change canon directly. Any canon-impacting change must route through governance engines (change control + audit).

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- directly edit engine files or indexes (governance change control owns)
- generate creative content for projects (domain engines)
- replace QA/consistency engines (it consumes their outputs)

FORBIDDEN:
- “learning” as vague notes without evidence and proposed action
- direct canon edits without governance routing

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- EXECUTION_REPORT (optional)
- QA_REPORT (optional)
- CONSISTENCY_REPORT (optional)
- GATES_REPORT_SET (optional; from any engine)
- USER_FEEDBACK_LOG (optional)

PRODUCES:
- LESSON_LOG
- HYPOTHESIS_REGISTRY
- CHANGE_CANDIDATE_SET
- LEARNING_GATES_REPORT

DEPENDS_ON:
- [00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG, 00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG]

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/META/LEARNING/
OPTIONAL:
- KB/META/LEARNING (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Lesson: evidence-backed statement of what improved or failed.
- Hypothesis: testable claim about a change and expected effect.
- Change Candidate: a packaged proposed change (target file/engine, diff intent, risk).
- Evidence: references to reports, logs, or measured outcomes (IDs).
- Governance Routing: explicit path through change control + audit.

Enums (baseline):
- severity: S0|S1|S2|S3
- candidate_type: RULE_CHANGE|TEMPLATE_CHANGE|ENGINE_CHANGE|INDEX_CHANGE|PROCESS_CHANGE
- status: PROPOSED|TESTING|ACCEPTED|REJECTED|ARCHIVED

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- learning capture and packaging
- hypothesis/test registry
- change candidate artifacts and governance routing
- learning gates

OUT OF SCOPE (HARD):
- performing the canon changes itself
- rewriting project content
- replacing QA validation logic

COLLISION RULE:
- If request is “apply change to canon” → governance change control + audit
- If request is “validate quality” → QA engines (learning consumes their reports)

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: LESSON_LOG entries include evidence refs and a recommended action.
R2 (HARD) MUST: HYPOTHESIS_REGISTRY hypotheses are testable and include success criteria.
R3 (HARD) MUST: CHANGE_CANDIDATE_SET includes target, scope, risk, and governance routing.
R4 (HARD) FORBIDDEN: candidates without evidence (unless explicitly marked exploratory with S2+ risk).
R5 (HARD) MUST: LEARNING_GATES_REPORT detects missing evidence, missing routing, vague hypotheses.
R6 (SOFT) SHOULD: include rollback plan for each candidate.
R7 (HARD) MUST: any candidate affecting canon must reference governance pipeline engines.

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: LESSON_LOG
- MUST:
  - lesson_log_id
  - version
  - lessons[] (non-empty)
  - checks[] (non-empty)
- LESSON (minimum):
  - lesson_id
  - source (EXECUTION|QA|CONSISTENCY|USER)
  - statement (testable)
  - evidence_refs[] (non-empty)
  - impact (testable)
  - recommended_action (testable)
  - severity (S0|S1|S2|S3)
- VALIDATION:
  - lessons non-empty
  - evidence_refs non-empty for each lesson
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/META/LEARNING/LESSON_LOG.md

---

ARTIFACT: HYPOTHESIS_REGISTRY
- MUST:
  - registry_id
  - version
  - hypotheses[] (non-empty)
  - checks[] (non-empty)
- HYPOTHESIS (minimum):
  - hypothesis_id
  - claim (testable)
  - target_area (engine/template/rule/index)
  - proposed_change_summary (testable)
  - success_criteria[] (non-empty)
  - evaluation_method (testable)
  - status (PROPOSED|TESTING|ACCEPTED|REJECTED|ARCHIVED)
  - evidence_refs[] (optional but recommended)
- VALIDATION:
  - hypotheses non-empty
  - success_criteria non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/META/LEARNING/HYPOTHESIS_REGISTRY.md

---

ARTIFACT: CHANGE_CANDIDATE_SET
- MUST:
  - candidate_set_id
  - version
  - candidates[] (non-empty)
  - checks[] (non-empty)
- CANDIDATE (minimum):
  - candidate_id
  - type (RULE_CHANGE|TEMPLATE_CHANGE|ENGINE_CHANGE|INDEX_CHANGE|PROCESS_CHANGE)
  - target_ref (file path or engine id)
  - change_intent (testable)
  - expected_effect (testable)
  - risk_level (S0|S1|S2|S3)
  - evidence_refs[] (optional; required unless exploratory)
  - rollback_plan (optional but recommended)
  - governance_route (required):
    - change_control_ref
    - audit_log_ref
    - approval_required (bool)
- VALIDATION:
  - candidates non-empty
  - governance_route present for each candidate
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/META/LEARNING/CHANGE_CANDIDATE_SET.md

---

ARTIFACT: LEARNING_GATES_REPORT
- MUST:
  - report_id
  - version
  - gates[] (non-empty)
  - issues[] (can be empty)
  - overall (PASS|WARN|FAIL)
- Minimum required gates:
  - G1_LESSONS_EMPTY (S0)
  - G2_HYPOTHESES_EMPTY (S0)
  - G3_CANDIDATES_EMPTY (S0)
  - G4_MISSING_EVIDENCE (S1)
  - G5_MISSING_GOVERNANCE_ROUTE (S0)
  - G6_VAGUE_HYPOTHESIS (S1)
- VALIDATION:
  - FAIL if any S0 fails
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/META/LEARNING/LEARNING_GATES_REPORT.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Collect inputs (execution/QA/consistency/user feedback).
2) Produce lesson log (evidence-backed).
3) Convert lessons into hypotheses with success criteria.
4) Package change candidates with risk + rollback + governance route.
5) Run gates and emit artifacts.

---

## 8) S0 BLOCKERS (STOP)
- S0-1: lessons empty.
- S0-2: hypotheses empty.
- S0-3: change candidates empty.
- S0-4: missing governance routing for any candidate.
- S0-5: produced artifacts missing schemas/storage targets.

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- consumes reports from any engine family and user feedback logs

Downstream:
- governance change control processes change candidates
- audit log records canon-impacting changes
- pattern extraction/optimization engines can consume learning outputs

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Governance pipeline:
  00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md
  00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG.md
- Family template:
  10_META_EVOLUTION_ENGINES/00__TEMPLATE__ENGINE__META_EVOLUTION_ENGINES.md
- Family README:
  10_META_EVOLUTION_ENGINES/00__README__META_EVOLUTION_ENGINES.md

--- END.

LOCK: OPEN
