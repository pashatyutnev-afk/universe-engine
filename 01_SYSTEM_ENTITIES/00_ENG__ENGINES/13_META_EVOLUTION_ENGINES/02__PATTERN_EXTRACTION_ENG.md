# 🧩 PATTERN EXTRACTION ENGINE
## Canonical Engine Specification  
**LEVEL: L4 · META ENGINE · REUSABLE PATTERN MINING · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 02__PATTERN_EXTRACTION_ENG.md
- ENGINE_ID: L4-META-PATTERN-EXTRACTION-ENGINE-002
- UID: UE.ENT.ENG.META.PATTERN_EXTRACTION
- NAME: Pattern Extraction Engine
- CLASS: Meta Evolution Engine
- LEVEL: L4
- STATUS: FINAL
- FAILURE_MODE: fail-closed (false pattern risk)
- EDITABLE: true

### ABSOLUTE RULE
> A pattern is valid only if it is traceable, repeated, and bounded by constraints.

---

## 1. PURPOSE

Pattern Extraction Engine mines repeated structures from:
- outcomes (Learning Notes)
- artifacts (blueprints, plans)
- audit logs
- QA reports
- project retros

It produces **PATTERN_PACKAGE** objects:
- named reusable pattern
- trigger conditions
- steps / template
- constraints and applicability
- risks and failure modes
- examples and counterexamples
- integration points with engines/orchestrators

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- detect recurring structures and workflows
- abstract reusable templates
- define pattern applicability constraints
- define anti-patterns
- define integration hooks (where pattern plugs in)
- propose pattern adoption as a change request

### OUT-OF-SCOPE (FORBIDDEN)
- declaring a pattern “true” without evidence
- forcing adoption (advisory only)
- rewriting canon/standards directly
- creating patterns that are vague or universal (“do better”)

---

## 3. INPUT / OUTPUT

### 3.1 INPUT — PATTERN_REQUEST
Required fields:
- `pat_req_id`
- `timestamp`
- `source_refs` (list)
- `scope_context` (project/pipeline/engine family)
- `min_repetition_count` (default 3)
- `constraints_refs` (optional)
- `trace_id` (optional)

Missing required input → REJECT.

### 3.2 OUTPUT — PATTERN_PACKAGE
Required fields:
- `pattern_id`
- `engine_id`
- `version`
- `status` = DRAFT | FINAL
- `pattern_name`
- `pattern_type` = WORKFLOW | TEMPLATE | DECISION_RULE | VALIDATION | ORCHESTRATION | RECOVERY
- `problem_statement`
- `trigger_conditions`
- `inputs_required`
- `steps`
- `outputs_expected`
- `constraints_applicability`
- `success_signals`
- `failure_signals`
- `risks`
- `anti_patterns`
- `examples` (traceable)
- `counterexamples` (traceable)
- `integration_hooks`
- `approval_required` (bool)
- `risk_level` = LOW | MED | HIGH | CRITICAL
- `trace_id` (if available)

Hard rule:
- examples must include source_refs; otherwise package cannot be FINAL.

---

## 4. PATTERN VALIDITY RULES

### 4.1 VALIDITY REQUIREMENTS
A pattern can be FINAL only if:
- repetition_count >= min_repetition_count
- examples >= 2
- counterexamples >= 1 (unless explicitly impossible and justified)
- constraints_applicability defined
- failure_signals defined

If missing → DRAFT.

---

## 5. TRIGGER CONDITIONS

### 5.1 TRIGGER_CONDITIONS (required)
Each trigger includes:
- `signal` (what is observed)
- `threshold` (when it triggers)
- `context` (where it applies)
- `exclusions` (when it must NOT apply)

Hard rule:
- no trigger may be “always”.

---

## 6. STEPS TEMPLATE

### 6.1 STEPS (required)
Each step includes:
- `step_id`
- `action`
- `who` (engine/orchestrator/human)
- `inputs`
- `outputs`
- `checks` (QA gates)
- `rollback` (if step fails)

Hard rule:
- any irreversible step must reference governance approval or rollback policy.

---

## 7. CONSTRAINTS & APPLICABILITY

### 7.1 CONSTRAINTS_APPLICABILITY (required)
- `applies_to` (list of scopes)
- `does_not_apply_to` (list)
- `dependency_requirements`
- `resource_requirements` (optional)
- `risk_bounds`

Hard rule:
- must declare at least one does_not_apply_to.

---

## 8. SUCCESS / FAILURE SIGNALS

### 8.1 SUCCESS_SIGNALS (required)
- measurable or observable outcomes that indicate success
- must be checkable (by QA or logs)

### 8.2 FAILURE_SIGNALS (required)
- signals that indicate pattern misuse or breakdown
- must include severity mapping

---

## 9. ANTI-PATTERNS

### 9.1 ANTI_PATTERNS (required)
Each anti-pattern includes:
- `name`
- `what_people_do`
- `why_it_fails`
- `how_to_fix`
- `signals`

Hard rule:
- at least one anti-pattern per pattern package.

---

## 10. INTEGRATION HOOKS

### 10.1 INTEGRATION_HOOKS (required)
Each hook includes:
- `hook_point` (engine operation / pipeline stage)
- `pre_conditions`
- `post_conditions`
- `artifact_links` (what it reads/writes)
- `compatibility_notes`

Hard rule:
- must map to at least one engine family or orchestrator.

---

## 11. CANON RISK CHECK

Set `approval_required = true` if pattern adoption would:
- modify standards/canon
- change governance behavior
- change index structure
- introduce new required artifacts globally

Otherwise advisory by default.

---

## 12. QA GATES

### 12.1 QA_GATES (required)
- `evidence_gate` (sources exist + traceable)
- `repetition_gate` (min repetition satisfied)
- `boundedness_gate` (constraints_applicability defined)
- `counterexample_gate` (exists or justified)
- `integration_gate` (hooks defined)
- `risk_gate` (risk level declared)
- `governance_gate` (approval_required correct)

Fail rules:
- evidence_gate fail → INVALID
- repetition_gate fail → DRAFT (cannot be FINAL)
- boundedness_gate fail → INVALID

---

## 13. REPAIR PLAN (MANDATORY)

### 13.1 REPAIR PLAN (required)
Common repairs:
- pattern too vague → add trigger thresholds + exclusions
- no counterexample → add one or mark boundary conditions explicitly
- unclear steps → add inputs/outputs/rollback per step
- risky adoption → set approval_required + route to governance
- weak evidence → add sources or downgrade to DRAFT

Include:
- `recheck_gates`
- `max_revision_cycles`

---

## 14. CORE OPERATIONS

- OP_01: INGEST_SOURCES
- OP_02: FIND_REPETITIONS
- OP_03: PROPOSE_CANDIDATE_PATTERNS
- OP_04: BUILD_TRIGGER_CONDITIONS
- OP_05: BUILD_STEPS_TEMPLATE
- OP_06: DEFINE_CONSTRAINTS_APPLICABILITY
- OP_07: DEFINE_SUCCESS_FAILURE_SIGNALS
- OP_08: DEFINE_ANTI_PATTERNS
- OP_09: DEFINE_INTEGRATION_HOOKS
- OP_10: RUN_CANON_RISK_CHECK
- OP_11: RUN_QA_GATES
- OP_12: BUILD_REPAIR_PLAN
- OP_13: EMIT_PATTERN_PACKAGE

---

## 15. FAILURE CONDITIONS (ENGINE)

CRITICAL:
- no sources
- fabricated examples
- pattern declared universal
- no constraints boundary

Reaction:
- reject (fail-closed)
- request evidence or narrow scope

---

## 16. NON-GOALS
- does not enforce adoption
- does not rewrite canon
- does not optimize pipelines directly (that’s 03)

---

## 17. FINAL STATEMENT

Patterns are reusable memory.
Unbounded patterns are lies.

---

**STATUS:** Pattern Extraction Engine v1.0  
**REALM:** ACTIVE
