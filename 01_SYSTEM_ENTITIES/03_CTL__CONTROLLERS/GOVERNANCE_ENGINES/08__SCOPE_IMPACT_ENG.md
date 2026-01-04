# 🧭 SCOPE IMPACT ENGINE
## Canonical Engine Specification  
**LEVEL: L1 · GOVERNANCE ENGINE · IMPACT ANALYSIS · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 08__SCOPE_IMPACT_ENG.md
- ENGINE_ID: L1-GOV-SCOPE-IMPACT-ENGINE-008
- UID: UE.ENT.ENG.GOV.SCOPE_IMPACT
- NAME: Scope Impact Engine
- CLASS: Governance Engine
- CATEGORY: Scope Classification & Impact Reporting
- LEVEL: L1 (System Core)
- STATUS: FINAL
- FAILURE_MODE: fail-closed
- EDITABLE: false
- BYPASS_ALLOWED: false

### ABSOLUTE RULE
> If impact is unknown, the system must not approve or bind wide-scope changes.

---

## 1. PURPOSE

Scope Impact Engine produces deterministic **impact reports** for:
- change proposals (Change Control)
- binding decisions (Decision Approval)
- registry updates (Dependency / Index / Entity registries)

It guarantees:
- scope classification (small/medium/large/system-wide)
- affected targets enumeration
- downstream gate requirements based on impact

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Classify scope of a proposed change/decision
- Enumerate affected realms/files/entities by reference
- Estimate blast radius (what can break downstream)
- Require additional approvals based on scope tier
- Produce an impact report artifact used as prerequisite

### OUT-OF-SCOPE (FORBIDDEN)
- Approving or rejecting changes (Decision Approval)
- Editing files or applying diffs
- Risk safety judgement (Risk Safety Engine)
- Precedence resolution (Rule Hierarchy)
- Truth validation of domain content

---

## 3. SCOPE MODEL

### 3.1 Scope Tiers (fixed)

- S0: LOCAL (single file/engine, no external deps)
- S1: REALM (within one family/realm)
- S2: CROSS_REALM (touches multiple realms)
- S3: SYSTEM (touches canon/standards/master index/L1 rules)

### 3.2 Impact Dimensions (must be evaluated)

- `targets_affected` (UIDs / files / index sections)
- `rules_affected` (authority/precedence/state/lifecycle)
- `dependencies_affected` (required/forbidden graph changes)
- `bindings_affected` (what decisions become invalid)
- `migration_cost` (conceptual effort: LOW/MEDIUM/HIGH)
- `reversibility` (EASY/MODERATE/HARD)

---

## 4. INPUT ARTIFACT — IMPACT_ASSESSMENT_REQUEST

### REQUIRED FIELDS
- `impact_id`
- `timestamp`
- `requestor_uid`
- `request_type` = CHANGE_PROPOSAL | DECISION | REGISTRY_UPDATE
- `target_refs` (list of intended targets; may be "ALL" for system tier)
- `proposed_diff_summary` (what changes)
- `baseline_version` (optional)
- `trace_id`

Missing any field → REJECT.

---

## 5. OUTPUT ARTIFACT — IMPACT_REPORT

### GUARANTEED OUTPUT
- `impact_id`
- `scope_tier` = S0 | S1 | S2 | S3
- `targets_affected` (list)
- `dependencies_affected` (list)
- `rules_affected` (list)
- `bindings_affected` (list)
- `required_gates` (list of required prerequisites)
- `recommended_actions` (non-binding)
- `trace_id`

All impact reports must be recorded via Audit Log Engine.

---

## 6. REQUIRED GATES (BY SCOPE TIER)

### S0: LOCAL
- Canon refs check (if binding)
- Audit trace

### S1: REALM
- Dependency check (direct)
- Consistency check (FAST)
- Audit trace

### S2: CROSS_REALM
- Dependency check (TRANSITIVE)
- Consistency check (FULL)
- Decision Approval required
- Audit trace

### S3: SYSTEM
- Consistency check (FULL)
- Risk Safety gating required
- Decision Approval required
- Versioning plan required (effective_version + rollback)
- Audit trace

---

## 7. CORE OPERATIONS

- OP_01: CLASSIFY_SCOPE_TIER
- OP_02: ENUMERATE_TARGETS_AFFECTED
- OP_03: DERIVE_REQUIRED_GATES
- OP_04: EMIT_IMPACT_REPORT (audit-recorded)

---

## 8. ACCESS MODEL

### WRITE
- Governance layer only (impact report issuance)

### READ
- Change Control Engine
- Decision Approval Engine
- Risk Safety Engine
- Orchestrators (for gating execution)

### DELETE
- FORBIDDEN

---

## 9. DEPENDENCIES

### REQUIRED
- 01__AUDIT_LOG_ENG (record impact reports)
- 05__CONSISTENCY_ENG (required checks by tier)
- 06__DEPENDENCY_REGISTRY_ENG (dependency impact)
- 10__VERSIONING_MEMORY_ENG (baseline/effective versions for S3)
- 09__RISK_SAFETY_ENG (risk gating for S3)

### FORBIDDEN
- Domain engines as impact authority for governance scope tiers
- External web sources as authority

---

## 10. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- Missing trace_id
- Empty target_refs for non-trivial request
- Attempt to approve/bind S2/S3 without impact report
- Attempt to classify S3 without versioning/rollback notes
- Attempt to ignore required gates

Reaction:
- REJECT report request OR emit report with required_gates that block downstream approval
- Emit audit incident if bypass attempted

---

## 11. TRACE RULES

- Every report must carry trace_id
- Downstream approvals must reference an IMPACT_REPORT
- Trace gaps invalidate downstream binding

---

## 12. NON-GOALS
- Does not approve changes
- Does not judge safety
- Does not apply diffs
- Does not validate domain truth

---

## 13. FINAL STATEMENT

Scope defines what gates are required.
Unknown impact means approval must stop.

---

**STATUS:** Scope Impact Engine v1.0  
**CANON:** FIXED · NON-BYPASSABLE
