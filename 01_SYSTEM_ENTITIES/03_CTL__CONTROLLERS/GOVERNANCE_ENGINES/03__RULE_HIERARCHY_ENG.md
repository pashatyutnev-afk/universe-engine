# 🏗️ RULE HIERARCHY ENGINE
## Canonical Engine Specification  
**LEVEL: L1 · GOVERNANCE ENGINE · PRECEDENCE ORDER · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 03__RULE_HIERARCHY_ENG.md
- ENGINE_ID: L1-GOV-RULE-HIERARCHY-ENGINE-003
- UID: UE.ENT.ENG.GOV.RULE_HIERARCHY
- NAME: Rule Hierarchy Engine
- CLASS: Governance Engine
- CATEGORY: Rule Precedence & Conflict Resolution
- LEVEL: L1 (System Core)
- STATUS: FINAL
- FAILURE_MODE: fail-closed
- EDITABLE: false (changes only via Change Control Engine)
- BYPASS_ALLOWED: false

### ABSOLUTE RULE
> When rules conflict, only the highest-precedence rule may bind the system.

---

## 1. PURPOSE

Rule Hierarchy Engine defines the canonical **precedence ordering** of rules and documents.

It guarantees:
- deterministic conflict resolution
- consistent override semantics
- a single “source-of-binding” when contradictions exist

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define precedence tiers for rule sources
- Resolve conflicts between rules by tier ordering
- Detect “same-tier conflicts” and force governance decision
- Produce binding resolution verdicts with trace

### OUT-OF-SCOPE (FORBIDDEN)
- Creating new canon rules
- Editing rule text
- Proving truth
- Interpreting narrative meaning

---

## 3. PRECEDENCE MODEL

### 3.1 Precedence Tiers (highest → lowest)

TIER_0: System Canon (absolute)
TIER_1: L1 Governance Engines
TIER_2: L1 Core Engines
TIER_3: Master Index (INDEX__UNIVERSE_ENGINE)
TIER_4: Domain Indexes / Engine Families (L2/L3 registries)
TIER_5: Project Indexes
TIER_6: Drafts / proposals / chats (non-binding)

If two sources are in different tiers, higher tier wins.

### 3.2 Override Rules

- Higher tier may override lower tier only if:
  - the override is explicit
  - the change is approved via Change Control (if it changes canon)
  - the decision is audit-traced

Implicit override is forbidden.

---

## 4. INPUT ARTIFACTS

### 4.1 INPUT — RULE_CONFLICT_SET

**REQUIRED FIELDS**
- `conflict_id`
- `timestamp`
- `requestor_uid`
- `rule_refs` (list of conflicting rule refs)
- `rule_tiers` (mapped tiers)
- `conflict_context`
- `trace_id`

Missing any field → REJECT.

### 4.2 INPUT — PRECEDENCE_QUERY

**REQUIRED FIELDS**
- `query_id`
- `timestamp`
- `rule_ref`
- `trace_id`

Missing any field → REJECT.

---

## 5. OUTPUT ARTIFACTS

### 5.1 OUTPUT — PRECEDENCE_VERDICT
- `conflict_id` or `query_id`
- `verdict` = RESOLVED | UNRESOLVED | REJECTED
- `winning_rule_ref` (if resolved)
- `winning_tier`
- `losing_rule_refs`
- `required_action` (if unresolved)
- `trace_id`

---

## 6. CORE OPERATIONS

- OP_01: CLASSIFY_RULE_TIER
- OP_02: RESOLVE_CONFLICT_BY_TIER
- OP_03: DETECT_SAME_TIER_CONFLICT
- OP_04: REQUIRE_GOVERNANCE_DECISION (Decision Approval)

---

## 7. ACCESS MODEL

### WRITE
- Forbidden (writes nothing; verdicts logged via Audit Log)

### READ
- All engines/orchestrators (needed for gating)

### DELETE
- FORBIDDEN

---

## 8. DEPENDENCIES

### REQUIRED
- 01__AUDIT_LOG_ENG (record all verdicts)
- 04__CHANGE_CONTROL_ENG (any tier model changes)
- 07__DECISION_APPROVAL_ENG (resolving same-tier conflicts)

### FORBIDDEN
- Domain engines as authority source for tier ordering
- External web sources as precedence authority

---

## 9. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- Missing trace_id
- Unknown tier
- Attempted implicit override
- Same-tier conflict without approved governance decision

Reaction:
- UNRESOLVED
- Emit audit incident
- Block binding until resolved

---

## 10. TRACE RULES

- Every conflict resolution must be traceable
- Downstream bindings must reference winning_rule_ref + trace_id
- Trace gaps invalidate downstream binding

---

## 11. NON-GOALS
- Does not prove truth
- Does not edit rules
- Does not decide narrative outcomes

---

## 12. FINAL STATEMENT

When rules conflict, precedence decides.
No precedence verdict → no binding.

---

**STATUS:** Rule Hierarchy Engine v1.0  
**CANON:** FIXED · NON-BYPASSABLE
