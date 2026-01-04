# 🧷 DEPENDENCY REGISTRY ENGINE
## Canonical Engine Specification  
**LEVEL: L1 · GOVERNANCE ENGINE · DEPENDENCY TRUTH · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 06__DEPENDENCY_REGISTRY_ENG.md
- ENGINE_ID: L1-GOV-DEPENDENCY-REGISTRY-ENGINE-006
- UID: UE.ENT.ENG.GOV.DEPENDENCY_REGISTRY
- NAME: Dependency Registry Engine
- CLASS: Governance Engine
- CATEGORY: Dependency Declaration, Validation & Enforcement
- LEVEL: L1 (System Core)
- STATUS: FINAL
- FAILURE_MODE: fail-closed
- EDITABLE: false (registry evolves only via Change Control)
- BYPASS_ALLOWED: false

### ABSOLUTE RULE
> If a dependency is not registered and validated, it must not be assumed or used.

---

## 1. PURPOSE

Dependency Registry Engine is the system’s **single source of dependency truth**.

It guarantees:
- explicit dependency declarations (no hidden coupling)
- validation of required/forbidden dependencies
- enforcement gates before execution/approval
- deterministic detection of missing or broken prerequisites

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Register dependency declarations between entities
- Validate dependencies (exists/compatible/allowed)
- Classify dependencies: REQUIRED / OPTIONAL / FORBIDDEN
- Detect circular dependencies (critical)
- Produce dependency verdicts used as gates
- Emit dependency violation records (via Audit Log)
- Support “dependency snapshots” per version baseline

### OUT-OF-SCOPE (FORBIDDEN)
- Creating or editing entities
- Approving changes (Decision Approval Engine)
- Fixing missing dependencies automatically
- Interpreting domain meaning
- Using external sources as dependency truth

---

## 3. DEPENDENCY MODEL

### 3.1 Dependency Types (fixed)

- REQUIRED  (must exist and be compatible)
- OPTIONAL  (may exist; never blocks)
- FORBIDDEN (must not be present or referenced)

### 3.2 Dependency Relation Kinds (fixed)
- ENGINE_DEPENDS_ON_ENGINE
- INDEX_DEPENDS_ON_INDEX
- ENTITY_DEPENDS_ON_ENTITY
- TEMPLATE_DEPENDS_ON_SPEC
- PROJECT_DEPENDS_ON_MODEL

### 3.3 Compatibility Rules (governance-level)
- dependency target must be registered (by UID or canonical ref)
- dependency must be version-compatible (if versions exist)
- forbidden dependency presence triggers fail-closed block

---

## 4. INPUT ARTIFACTS

### 4.1 INPUT — DEPENDENCY_DECLARATION

**REQUIRED FIELDS**
- `declaration_id`
- `timestamp`
- `source_uid` (who depends)
- `source_type`
- `target_uid` (what is depended on)
- `target_type`
- `dependency_type` = REQUIRED | OPTIONAL | FORBIDDEN
- `relation_kind`
- `reason`
- `scope` (where it applies: realm/project/system)
- `trace_id`

Missing any field → REJECT.

### 4.2 INPUT — DEPENDENCY_CHECK_REQUEST

**REQUIRED FIELDS**
- `check_id`
- `timestamp`
- `source_uid`
- `check_scope` (DIRECT | TRANSITIVE)
- `baseline_version` (optional; if omitted = current)
- `trace_id`

Missing any field → REJECT.

---

## 5. OUTPUT ARTIFACTS

### 5.1 OUTPUT — DEPENDENCY_VERDICT

- `check_id`
- `source_uid`
- `verdict` = PASS | FAIL | REJECTED
- `missing_required` (list)
- `violated_forbidden` (list)
- `cycle_detected` (true/false)
- `incompatible_targets` (list)
- `recommended_action`
- `trace_id`

### 5.2 OUTPUT — DEPENDENCY_VIOLATION_RECORD

- `violation_id`
- `source_uid`
- `type` = MISSING_REQUIRED | FORBIDDEN_PRESENT | INCOMPATIBLE | CYCLE
- `severity` = LOW | MEDIUM | HIGH | CRITICAL
- `evidence_refs`
- `trace_id`

All verdicts/violations are recorded via Audit Log Engine.

---

## 6. CORE OPERATIONS

- OP_01: REGISTER_DECLARATION  
  Accepts DEPENDENCY_DECLARATION and records it (via audit-traced registry update process).

- OP_02: VALIDATE_DIRECT_DEPENDENCIES  
  Checks REQUIRED/OPTIONAL/FORBIDDEN dependencies for a source_uid.

- OP_03: VALIDATE_TRANSITIVE_DEPENDENCIES  
  Checks full dependency graph closure.

- OP_04: DETECT_CYCLES  
  If cycle detected → FAIL (CRITICAL).

- OP_05: EMIT_GATE_SIGNAL  
  If FAIL: blocks binding approvals/execution until resolved (through consumers).

---

## 7. ACCESS MODEL

### WRITE
- Governance layer only (declarations/registry snapshots)
- Changes to registry must be change-controlled

### READ
- All engines/orchestrators (for gating decisions/execution)

### DELETE
- FORBIDDEN

---

## 8. DEPENDENCIES

### REQUIRED
- 01__AUDIT_LOG_ENG (record declarations/verdicts/violations)
- 04__CHANGE_CONTROL_ENG (registry evolution)
- 10__VERSIONING_MEMORY_ENG (baseline versions & snapshots)
- 05__CONSISTENCY_ENG (cross-check registry vs reality)

### FORBIDDEN
- Unregistered entities as dependency targets
- External web sources as dependency truth

---

## 9. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- Missing trace_id
- Required dependency missing
- Forbidden dependency present
- Dependency cycle detected
- Dependency target unregistered
- Attempt to proceed after FAIL verdict without approved override

Reaction:
- FAIL verdict
- Emit audit incident
- Block downstream binding/execution until resolved

---

## 10. TRACE RULES

- Every declaration and verdict must have trace_id
- Downstream approvals/execution must reference PASS verdict where required
- Overrides require Change Control + Decision Approval

---

## 11. NON-GOALS
- Does not auto-install dependencies
- Does not rewrite projects/engines to fix dependencies
- Does not decide precedence
- Does not validate domain truth

---

## 12. GOVERNANCE POSITION

Dependency Registry Engine prevents hidden coupling.
No validated dependency graph → no safe approval → no safe execution.

---

## 13. FINAL STATEMENT

Dependencies must be explicit, registered, and validated.
Assumed dependencies are illegal.

---

**STATUS:** Dependency Registry Engine v1.0  
**CANON:** FIXED · NON-BYPASSABLE
