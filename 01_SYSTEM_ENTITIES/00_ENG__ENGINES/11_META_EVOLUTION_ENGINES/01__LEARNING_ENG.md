# 🧠 LEARNING ENGINE
## Canonical Engine Specification  
**LEVEL: L4 · META ENGINE · OUTCOME-DRIVEN LEARNING · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 01__LEARNING_ENG.md
- ENGINE_ID: L4-META-LEARNING-ENGINE-001
- UID: UE.ENT.ENG.META.LEARNING
- NAME: Learning Engine
- CLASS: Meta Evolution Engine
- LEVEL: L4
- STATUS: FINAL
- FAILURE_MODE: fail-closed (canon risk)
- EDITABLE: true

### ABSOLUTE RULE
> Learning is allowed only if it is traceable, scoped, and does not rewrite canon.

---

## 1. PURPOSE

Learning Engine converts real outcomes into **LEARNING_NOTES**:
- what was attempted
- what happened (facts)
- what worked / what failed
- why (bounded hypotheses)
- what to change next (proposals, not edits)
- what must never be repeated

This engine exists to prevent repeated mistakes and to accumulate durable improvements.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- ingest logs, metrics, QA reports, outputs
- classify outcomes (success/fail/partial)
- extract lessons (bounded, falsifiable)
- produce recommendations
- produce experiment plans
- escalate risks and regressions

### OUT-OF-SCOPE (FORBIDDEN)
- changing canon or standards
- deleting evidence
- “optimizing” by hiding failures
- inventing facts not supported by logs

---

## 3. INPUT / OUTPUT

### 3.1 INPUT — LEARNING_REQUEST
Required fields:
- `learn_req_id`
- `timestamp`
- `source_type` = AUDIT_LOG | QA_REPORT | OUTPUT_REVIEW | METRICS | INCIDENT
- `source_refs` (list)
- `scope_context` (what project/engine/pipeline)
- `outcome_label` = SUCCESS | FAIL | PARTIAL
- `constraints_refs` (optional)
- `trace_id` (optional but recommended)

Missing required input → REJECT.

### 3.2 OUTPUT — LEARNING_NOTE
Required fields:
- `learning_id`
- `engine_id`
- `version`
- `status` = DRAFT | FINAL
- `scope_context`
- `facts_observed` (only facts)
- `failures_observed` (facts)
- `successes_observed` (facts)
- `hypotheses` (clearly marked, bounded)
- `root_cause_guess` (optional; hypothesis)
- `recommendations` (actions/proposals)
- `do_not_repeat_rules`
- `risk_level` = LOW | MED | HIGH | CRITICAL
- `scope_impact_guess`
- `approval_required` (bool)
- `links` (to related artifacts)
- `trace_id` (if available)

Hard rule:
- facts_observed may not contain interpretation language.

---

## 4. FACT VS HYPOTHESIS SEPARATION

### 4.1 FACT LANGUAGE RULE
Facts must be written as:
- observable
- time-bound
- source-referenced

Forbidden in facts:
- “probably”, “seems”, “maybe”, “I think”, “because”

Hypotheses must be tagged:
- `HYP:` prefix or structured field (preferred).

---

## 5. OUTCOME CLASSIFICATION

### 5.1 OUTCOME LABEL RULES
- SUCCESS: gates passed, objectives reached
- PARTIAL: some objectives reached, gates partially passed
- FAIL: gates failed OR objective missed

Hard rule:
- if any CRITICAL gate fails, outcome must be FAIL even if partial value exists.

---

## 6. RECOMMENDATION TYPES

### 6.1 RECOMMENDATION ENUM
- PROCESS_CHANGE
- TEMPLATE_CHANGE
- ENGINE_SPEC_PATCH
- PIPELINE_CHANGE
- VALIDATION_ADDITION
- TRAINING_GUIDE_UPDATE
- TOOLING_UPDATE
- EXPERIMENT_REQUIRED
- GOVERNANCE_ESCALATION

Each recommendation must include:
- `what`
- `why`
- `expected_gain`
- `risk`
- `approval_required`

---

## 7. DO NOT REPEAT RULES

### 7.1 DNR RULE (required)
Each rule must include:
- `trigger_pattern` (what situation)
- `forbidden_action`
- `why_it_failed_before`
- `safe_alternative`

Hard rule:
- at least one DNR rule for any FAIL outcome.

---

## 8. EXPERIMENT PLAN (OPTIONAL)

### 8.1 EXPERIMENT_PLAN (required if present)
- `hypothesis_to_test`
- `variables`
- `control`
- `success_metrics`
- `failure_metrics`
- `sample_size` (conceptual)
- `duration` (conceptual)
- `rollback_plan`

Hard rule:
- experiment must be reversible or sandboxed if risk_level >= HIGH.

---

## 9. CANON RISK CHECK (FAIL-CLOSED)

Learning Engine must set:
- `approval_required = true`
when recommendations touch:
- standards
- canon
- governance core behavior
- index structure

If canon risk detected:
- output remains DRAFT until approved.

---

## 10. QA GATES

### 10.1 QA_GATES (required)
- `evidence_gate` (sources exist)
- `fact_gate` (facts separated from hypotheses)
- `recommendation_gate` (actionable, scoped)
- `risk_gate` (risk level declared)
- `governance_gate` (approval_required correct)

Fail rules:
- evidence_gate fail → INVALID
- fact_gate fail → INVALID
- governance_gate fail → PARTIAL (cannot be acted on)

---

## 11. REPAIR PLAN (MANDATORY)

### 11.1 REPAIR PLAN (required)
Common repairs:
- facts are opinions → rewrite facts to observable statements + add source refs
- recommendations vague → add what/why/risk/expected_gain
- scope unclear → add scope_context and impacted entities
- canon risk missing → set approval_required and route to governance

Include:
- `recheck_gates`
- `max_revision_cycles`

---

## 12. CORE OPERATIONS

- OP_01: INGEST_SOURCES
- OP_02: CLASSIFY_OUTCOME
- OP_03: EXTRACT_FACTS
- OP_04: EXTRACT_FAILURES_SUCCESSES
- OP_05: GENERATE_HYPOTHESES (bounded)
- OP_06: BUILD_RECOMMENDATIONS
- OP_07: BUILD_DNR_RULES
- OP_08: BUILD_EXPERIMENT_PLAN (optional)
- OP_09: RUN_CANON_RISK_CHECK
- OP_10: RUN_QA_GATES
- OP_11: BUILD_REPAIR_PLAN
- OP_12: EMIT_LEARNING_NOTE

---

## 13. FAILURE CONDITIONS (ENGINE)

CRITICAL:
- no sources
- facts/hypotheses mixed
- recommendation tries to directly rewrite canon

Reaction:
- reject (fail-closed)
- request proper evidence or route to governance

---

## 14. NON-GOALS
- does not decide what changes happen
- does not approve changes
- does not rewrite standards/canon

---

## 15. FINAL STATEMENT

Learn loudly.
Record truth.
Change only with permission.

---

**STATUS:** Learning Engine v1.0  
**REALM:** ACTIVE
