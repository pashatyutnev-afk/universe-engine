# 🧬 CREATIVE MUTATION ENGINE
## Canonical Engine Specification  
**LEVEL: L4 · META ENGINE · SAFE NOVELTY GENERATION · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 04__CREATIVE_MUTATION_ENG.md
- ENGINE_ID: L4-META-CREATIVE-MUTATION-ENGINE-004
- UID: UE.ENT.ENG.META.CREATIVE_MUTATION
- NAME: Creative Mutation Engine
- CLASS: Meta Evolution Engine
- LEVEL: L4
- STATUS: FINAL
- FAILURE_MODE: fail-closed (canon contamination)
- EDITABLE: true

### ABSOLUTE RULE
> Mutation is allowed only as a candidate.  
> Nothing mutates the system until approved.

---

## 1. PURPOSE

Creative Mutation Engine generates **MUTATION_CANDIDATES**:
- controlled novelty proposals (new patterns, new templates, new combinations)
- bounded by style fingerprint, canon limits, and scope constraints
- always reversible and testable
- packaged with risk, validation, and rollback

It exists to explore the solution space without breaking identity.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- propose novel variations of workflows/templates/patterns
- cross-combine existing patterns into new candidates
- generate “what-if” pipeline variants
- propose new engine spec extensions (as patches)
- generate experiment plans to test novelty safely

### OUT-OF-SCOPE (FORBIDDEN)
- writing canon as if it is approved
- bypassing governance
- producing unbounded novelty (“anything goes”)
- generating candidates without validation and rollback plans

---

## 3. INPUT / OUTPUT

### 3.1 INPUT — MUTATION_REQUEST
Required fields:
- `mut_req_id`
- `timestamp`
- `scope_context` (project/pipeline/engine family)
- `mutation_goal` = NOVELTY | SPEED | QUALITY | SIMPLICITY | STYLE_SHIFT
- `source_refs` (patterns/learnings/blueprints)
- `constraints_refs`
- `risk_tolerance` = LOW | MED | HIGH (default LOW)
- `identity_locks_refs` (style/canon locks)
- `trace_id` (optional)

Missing required input → REJECT.

### 3.2 OUTPUT — MUTATION_CANDIDATE
Required fields:
- `mut_id`
- `engine_id`
- `version`
- `status` = DRAFT | FINAL
- `scope_context`
- `mutation_goal`
- `candidate_name`
- `candidate_type` = TEMPLATE_VARIANT | WORKFLOW_VARIANT | ORCHESTRATION_VARIANT | VALIDATION_VARIANT | ENGINE_PATCH
- `what_changes`
- `why_this_is_new`
- `bounded_by` (constraints + locks)
- `expected_gain`
- `tradeoffs`
- `risk_assessment`
- `validation_plan`
- `rollback_plan`
- `compatibility_checks`
- `approval_required` (bool)
- `risk_level` = LOW | MED | HIGH | CRITICAL
- `scope_impact_guess`
- `trace_id` (if available)

Hard rule:
- bounded_by must reference identity_locks_refs.

---

## 4. MUTATION BOUNDARIES (IDENTITY LOCKS)

### 4.1 BOUNDED_BY (required fields)
- `canon_locks` (list)
- `style_locks` (list)
- `scope_constraints` (list)
- `forbidden_modifications` (list)
- `allowed_modification_space` (explicit)

Hard rule:
- allowed_modification_space must be explicit, not “free”.

---

## 5. CANDIDATE CONSTRUCTION

### 5.1 CANDIDATE RULES
Every candidate must:
- change only a few variables (controlled novelty)
- be testable via validation_plan
- be reversible via rollback_plan
- include compatibility_checks

Hard rule:
- candidates that require irreversible change must be DRAFT + approval_required true.

---

## 6. COMPATIBILITY CHECKS

### 6.1 COMPATIBILITY_CHECKS (required fields)
- `depends_on` (engines/patterns)
- `breaks` (what it would break if applied)
- `migration_needed` (bool)
- `index_impact` (none/local/global)
- `notes`

Hard rule:
- index_impact global ⇒ approval_required true.

---

## 7. RISK ASSESSMENT

### 7.1 RISK_ASSESSMENT (required fields)
- `risk_level`
- `risk_sources`
- `failure_modes`
- `blast_radius`
- `canon_risk` (bool)
- `style_identity_risk` (bool)
- `notes`

Hard rule:
- canon_risk true ⇒ approval_required true.

---

## 8. VALIDATION PLAN

### 8.1 VALIDATION_PLAN (required fields)
- `method` = QA_ONLY | A_B | SHADOW_RUN | PILOT | SANDBOX
- `success_criteria`
- `failure_criteria`
- `metrics`
- `sample_definition`
- `duration_definition`
- `stop_conditions`
- `notes`

Hard rule:
- failure_criteria must include at least one identity/consistency failure.

---

## 9. ROLLBACK PLAN

### 9.1 ROLLBACK_PLAN (required fields)
- `rollback_triggers`
- `rollback_steps`
- `data_integrity_rule` = NO_DELETION
- `post_rollback_checks`
- `notes`

Hard rule:
- rollback must restore the previous stable pipeline behavior.

---

## 10. APPROVAL POLICY

Set `approval_required = true` if:
- candidate_type = ENGINE_PATCH
- canon_locks or index structure touched
- reversibility != EASY
- blast_radius != local

Otherwise candidate remains advisory and sandboxable.

---

## 11. QA GATES

### 11.1 QA_GATES (required)
- `boundedness_gate` (locks + constraints explicit)
- `novelty_gate` (what is new clearly stated)
- `validation_gate` (success/failure criteria exist)
- `rollback_gate` (rollback exists)
- `compatibility_gate` (checks defined)
- `risk_gate` (risk declared + consistent)
- `governance_gate` (approval_required correct)

Fail rules:
- boundedness_gate fail → INVALID
- rollback_gate fail → INVALID
- governance_gate fail → PARTIAL (cannot execute)

---

## 12. REPAIR PLAN (MANDATORY)

### 12.1 REPAIR PLAN (required)
Common repairs:
- candidate too broad → reduce variables; split into smaller candidates
- novelty unclear → specify exact differences and baseline
- boundaries missing → add locks and forbidden modifications
- validation weak → add stop conditions + identity checks
- rollback missing → define rollback + post checks

Include:
- `recheck_gates`
- `max_revision_cycles`

---

## 13. CORE OPERATIONS

- OP_01: INGEST_REQUEST
- OP_02: LOAD_LOCKS_AND_CONSTRAINTS
- OP_03: GENERATE_CANDIDATE_SPACE
- OP_04: SELECT_CONTROLLED_VARIATIONS
- OP_05: BUILD_CANDIDATE_DEFINITION
- OP_06: BUILD_COMPATIBILITY_CHECKS
- OP_07: ASSESS_RISK
- OP_08: BUILD_VALIDATION_PLAN
- OP_09: BUILD_ROLLBACK_PLAN
- OP_10: RUN_APPROVAL_POLICY
- OP_11: RUN_QA_GATES
- OP_12: BUILD_REPAIR_PLAN
- OP_13: EMIT_MUTATION_CANDIDATE

---

## 14. FAILURE CONDITIONS (ENGINE)

CRITICAL:
- unbounded candidate space
- candidate presented as canon
- no rollback
- no identity locks

Reaction:
- reject (fail-closed)
- request boundaries + rollback

---

## 15. NON-GOALS
- does not apply mutations
- does not approve changes
- does not rewrite canon

---

## 16. FINAL STATEMENT

Mutation is exploration.
Approval is reality.

---

**STATUS:** Creative Mutation Engine v1.0  
**REALM:** ACTIVE
