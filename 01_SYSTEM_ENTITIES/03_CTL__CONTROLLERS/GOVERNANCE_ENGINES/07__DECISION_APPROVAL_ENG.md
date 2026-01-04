# ✅ DECISION APPROVAL ENGINE
## Canonical Engine Specification  
**LEVEL: L1 · GOVERNANCE ENGINE · BINDING APPROVALS · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 07__DECISION_APPROVAL_ENG.md
- ENGINE_ID: L1-GOV-DECISION-APPROVAL-ENGINE-007
- UID: UE.ENT.ENG.GOV.DECISION_APPROVAL
- NAME: Decision Approval Engine
- CLASS: Governance Engine
- CATEGORY: Binding Decision Authorization & Approval Records
- LEVEL: L1 (System Core)
- STATUS: FINAL
- FAILURE_MODE: fail-closed
- EDITABLE: false
- BYPASS_ALLOWED: false

### ABSOLUTE RULE
> A decision binds the system only if it is explicitly approved, traceable, and canon-referenced.

---

## 1. PURPOSE

Decision Approval Engine is the system’s **binding authorization gate**.

It guarantees:
- decisions have explicit scope
- decisions reference canon authority
- approvals are traceable and audit-recorded
- same-tier conflicts are resolved only through explicit approvals

This engine is the place where “YES/NO” becomes **binding**.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Accept decision approval requests
- Validate canonical authority references for decisions
- Validate scope/impact prerequisites
- Issue binding approval records (or rejection records)
- Enforce fail-closed when prerequisites are missing
- Require audit trace for every approval/rejection
- Support approvals for:
  - change proposals
  - conflict resolutions
  - governance overrides

### OUT-OF-SCOPE (FORBIDDEN)
- Creating canon text (Change Control)
- Editing canon (forbidden)
- Precedence definition (Rule Hierarchy defines tiers)
- Truth validation (validators)
- Execution of decisions (orchestrators)

---

## 3. DECISION MODEL

### 3.1 Decision Classes (fixed)
- CHANGE_APPROVAL
- CONFLICT_RESOLUTION
- POLICY_EXCEPTION
- SCOPE_OVERRIDE
- SAFETY_OVERRIDE (rare; must be strictly gated)

### 3.2 Binding Scope (mandatory)
Every decision must declare its binding scope:
- `scope_targets` (UIDs / files / realms affected)
- `scope_layer` (CORE / GOVERNANCE / DOMAIN / PROJECT)
- `scope_duration` (ONE_TIME | VERSIONED | PERMANENT)
- `effective_version` (if versioned)

No scope → no binding.

---

## 4. INPUT ARTIFACT — DECISION_APPROVAL_REQUEST

### REQUIRED FIELDS
- `decision_id`
- `timestamp`
- `requestor_uid`
- `decision_class`
- `decision_text`
- `binding_scope` (structured scope object)
- `canon_refs` (non-empty list)
- `precedence_context` (optional; required if conflict resolution)
- `impact_report_ref` (required for non-trivial scope)
- `risk_assessment_ref` (required if safety-related or wide scope)
- `dependency_verdict_ref` (required if dependencies involved)
- `trace_id`

Missing any required field → REJECT.

---

## 5. OUTPUT ARTIFACTS

### 5.1 OUTPUT — DECISION_APPROVAL_VERDICT
- `decision_id`
- `verdict` = APPROVED | REJECTED
- `rejection_reason` (if rejected)
- `binding_scope`
- `canon_refs_used`
- `effective_version`
- `trace_id`

### 5.2 OUTPUT — BINDING_DECISION_RECORD (binding)
- `decision_id`
- `approved_by` (authority record; human/system)
- `decision_class`
- `binding_scope`
- `canon_refs_used`
- `prerequisites_summary`
- `trace_id`

All approval/rejection must be recorded via Audit Log Engine.

---

## 6. CORE OPERATIONS

- OP_01: VALIDATE_REQUEST_COMPLETENESS  
  Reject if any required field is missing.

- OP_02: VALIDATE_CANON_REFS  
  Must pass Canon Authority Engine checks (authorized sources only).

- OP_03: VALIDATE_PRECEDENCE_CONTEXT  
  If resolving conflict, must align with Rule Hierarchy Engine tiers.

- OP_04: VALIDATE_IMPACT_AND_RISK  
  Must include impact + risk refs when scope is non-trivial.

- OP_05: VALIDATE_DEPENDENCIES  
  If dependencies involved, must reference PASS verdict.

- OP_06: ISSUE_APPROVAL_OR_REJECTION  
  Produce verdict and emit binding record when approved.

---

## 7. ACCESS MODEL

### WRITE
- Governance layer (approval pipeline)
- Human/system authority inputs (requestor/approver)

### READ
- All engines/orchestrators (to verify binding status)

### DELETE
- FORBIDDEN

---

## 8. DEPENDENCIES

### REQUIRED
- 01__AUDIT_LOG_ENG (record approvals/rejections)
- 02__CANON_AUTHORITY_ENG (validate canon refs)
- 03__RULE_HIERARCHY_ENG (tier conflict rules)
- 08__SCOPE_IMPACT_ENG (impact report requirement)
- 09__RISK_SAFETY_ENG (risk gating / safety locks)
- 06__DEPENDENCY_REGISTRY_ENG (dependency verdict refs)
- 10__VERSIONING_MEMORY_ENG (effective_version semantics)

### FORBIDDEN
- Domain engines as approvers
- External web as canon authority

---

## 9. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- Missing trace_id
- Empty canon_refs
- Missing binding_scope
- Conflict resolution without precedence context
- Safety override without risk gating approval
- Attempt to treat unapproved decision as binding
- Attempt to approve while Consistency Engine reports CRITICAL inconsistency

Reaction:
- REJECT
- Emit audit incident
- Governance lock escalation for repeated bypass attempts

---

## 10. TRACE RULES

- Every request/verdict/record must carry trace_id
- Downstream bindings must reference a BINDING_DECISION_RECORD
- Trace gaps invalidate binding effect

---

## 11. NON-GOALS
- Does not execute decisions
- Does not edit canon text
- Does not define precedence tiers
- Does not validate domain truth

---

## 12. GOVERNANCE POSITION

Decision Approval Engine is where authorization becomes binding.
No approval record → no binding effect.

---

## 13. FINAL STATEMENT

A decision is real only when approved and recorded.
Unapproved decisions are non-binding by definition.

---

**STATUS:** Decision Approval Engine v1.0  
**CANON:** FIXED · NON-BYPASSABLE
