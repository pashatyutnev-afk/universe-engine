# 🧩 CONSISTENCY ENGINE
## Canonical Engine Specification  
**LEVEL: L1 · GOVERNANCE ENGINE · SYSTEM CONSISTENCY · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 05__CONSISTENCY_ENG.md
- ENGINE_ID: L1-GOV-CONSISTENCY-ENGINE-005
- UID: UE.ENT.ENG.GOV.CONSISTENCY
- NAME: Consistency Engine
- CLASS: Governance Engine
- CATEGORY: Cross-Canon Consistency & Constraint Enforcement
- LEVEL: L1 (System Core)
- STATUS: FINAL
- FAILURE_MODE: fail-closed
- EDITABLE: false
- BYPASS_ALLOWED: false

### ABSOLUTE RULE
> If the system is inconsistent, it must not bind decisions until inconsistency is resolved.

---

## 1. PURPOSE

Consistency Engine enforces **system-wide coherence** across:
- canon documents
- standards
- indexes
- engine specifications
- registries

It guarantees:
- detection of contradictions and mismatches
- deterministic reporting of violations
- blocking of binding decisions when critical inconsistencies exist

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Validate internal consistency of canonical artifacts
- Validate cross-file consistency (names, numbering, references)
- Detect contradictions between canon sources (by reference)
- Detect registry/index mismatches (listed vs missing)
- Detect schema mismatches (required fields vs actual)
- Emit consistency verdicts and violation records
- Gate approvals and changes (block when critical)

### OUT-OF-SCOPE (FORBIDDEN)
- Editing or fixing files automatically
- Proving truth of domain facts (validators)
- Deciding precedence (Rule Hierarchy Engine)
- Approving changes (Decision Approval Engine)
- Writing canon (Change Control Engine governs mutation)

---

## 3. CONSISTENCY DOMAINS (WHAT IT CHECKS)

### 3.1 Structural Consistency
- File naming format compliance
- Numbering consistency (INDEX ↔ filenames)
- Family path correctness (realm ↔ file location)
- Presence of required README for each family

### 3.2 Referential Consistency
- Broken links (refs to missing files)
- Orphan files (exist but not registered in index)
- Duplicate references (same engine registered twice)
- UID uniqueness (no collisions)

### 3.3 Semantic Consistency (governance-level only)
- Contradicting absolute rules between L1 engines
- Conflicting authority tier models
- Incompatible state/lifecycle phase definitions

Semantic checks are limited to governance primitives (not story meaning).

---

## 4. INPUT ARTIFACTS

### 4.1 INPUT — CONSISTENCY_CHECK_REQUEST

**REQUIRED FIELDS**
- `check_id`
- `timestamp`
- `requestor_uid`
- `check_scope` (files/realms/layers)
- `target_refs` (list; may be "ALL")
- `check_mode` = FAST | FULL
- `trace_id`

Missing any field → REJECT.

### 4.2 INPUT — CONSISTENCY_ASSERTION (optional)
A structured claim that something is inconsistent.

**REQUIRED FIELDS**
- `assertion_id`
- `timestamp`
- `assertion_type`
- `evidence_refs`
- `trace_id`

---

## 5. OUTPUT ARTIFACTS

### 5.1 OUTPUT — CONSISTENCY_VERDICT

- `check_id`
- `verdict` = CONSISTENT | INCONSISTENT | REJECTED
- `severity` = LOW | MEDIUM | HIGH | CRITICAL
- `violation_count`
- `violations` (list of violation records)
- `required_action`
- `trace_id`

### 5.2 OUTPUT — CONSISTENCY_VIOLATION_RECORD

Each violation includes:
- `violation_id`
- `type` (STRUCTURAL | REFERENTIAL | SEMANTIC)
- `severity` (LOW/MEDIUM/HIGH/CRITICAL)
- `location_ref` (file/section)
- `description`
- `evidence_refs`
- `recommended_fix` (non-binding)
- `trace_id`

All verdicts/violations must be recorded via Audit Log Engine.

---

## 6. CORE OPERATIONS

- OP_01: RUN_FAST_CHECK  
  Checks naming/numbering/obvious broken refs.

- OP_02: RUN_FULL_CHECK  
  Adds deep referential scanning + UID uniqueness + governance semantic checks.

- OP_03: CLASSIFY_SEVERITY  
  Produces severity based on what is broken and what it impacts.

- OP_04: EMIT_BLOCK_SIGNAL  
  If severity is CRITICAL, emit non-binding block recommendation for:
  - Change Control approvals
  - Decision Approval bindings
  - Canon Authority binding verdicts

(Blocking becomes effective through those engines’ gating rules.)

---

## 7. ACCESS MODEL

### WRITE
- Forbidden (no file edits)
- Writes only audit-traced violation records (via Audit Log)

### READ
- Governance engines
- Validators
- Orchestrators (for gating decisions)

### DELETE
- FORBIDDEN

---

## 8. DEPENDENCIES

### REQUIRED
- 01__AUDIT_LOG_ENG (record all verdicts/violations)
- 03__RULE_HIERARCHY_ENG (for tier-aware conflict reporting)
- 04__CHANGE_CONTROL_ENG (fix path requires controlled change)
- 06__DEPENDENCY_REGISTRY_ENG (cross-check dependencies vs reality)
- 10__VERSIONING_MEMORY_ENG (consistency per version baseline)

### FORBIDDEN
- Domain engines as authority for governance consistency rules
- External web sources as canon references

---

## 9. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- Missing trace_id
- Attempt to ignore CRITICAL inconsistency and proceed with binding
- UID collision detected
- Canon/index mismatch that breaks navigation truth
- Rule model contradiction at L1 level

Reaction:
- Verdict = INCONSISTENT (CRITICAL)
- Emit audit incident
- Signal block to Approval/Change pipelines until resolved

---

## 10. TRACE RULES

- Every check/verdict/violation must have trace_id
- Fixing any violation that touches canon must go through Change Control
- Downstream bindings must reference a CONSISTENT baseline (or explicit override via approved change)

---

## 11. NON-GOALS
- Does not auto-fix inconsistencies
- Does not decide precedence outcomes
- Does not validate domain truth
- Does not compress or summarize knowledge base

---

## 12. GOVERNANCE POSITION

Consistency Engine is the system’s coherence gate.
If coherence fails, binding must stop until resolved.

---

## 13. FINAL STATEMENT

Consistency is permission to proceed.
Inconsistency is a stop signal.

---

**STATUS:** Consistency Engine v1.0  
**CANON:** FIXED · NON-BYPASSABLE
