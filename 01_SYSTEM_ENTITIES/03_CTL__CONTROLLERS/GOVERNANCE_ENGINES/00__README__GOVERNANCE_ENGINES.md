# 🏛️ GOVERNANCE ENGINES — REALM README
## Canonical Realm Specification  
**LEVEL: L1 · GOVERNANCE LAYER · SYSTEM CONTROL · MACHINE-GRADE**

---

## 0. REALM STATUS

- REALM: 02_GOVERNANCE_ENGINES
- CLASS: GOVERNANCE
- LEVEL: L1 (System Control Layer)
- STATUS: ACTIVE
- OWNER: System / Human
- BYPASS_ALLOWED: false

### REALM ABSOLUTE RULE
> If governance rules are not applied, the system has no authority to decide.

---

## 1. PURPOSE

Governance Engines define:
- what is canonical and binding
- how rules are ordered and enforced
- how changes are proposed, approved, and recorded
- how system integrity is protected

Governance exists to make the system:
- auditable
- non-bypassable
- deterministic under conflict

---

## 2. REALM CONTRACT (INPUT / OUTPUT)

### INPUT (what Governance accepts)
- Canon claims and binding requests
- Change proposals
- Consistency checks and violations
- Dependency declarations
- Approval requests
- Risk/safety signals
- Versioning and memory operations

### OUTPUT (what Governance guarantees)
- Authority verdicts
- Rule precedence resolution
- Approved/Rejected changes
- Immutable audit records
- Dependency registry and enforcement
- Decisions with explicit binding scope
- System protection actions (fail-closed)

---

## 3. ENGINE LIST (ORDER IS MANDATORY)

00 — README (this file)

01 — Audit Log Engine  
- Absolute memory: records facts only, append-only, non-bypassable.

02 — Canon Authority Engine  
- Defines what is authoritative and what becomes binding.

03 — Rule Hierarchy Engine  
- Defines precedence ordering and conflict resolution between rules.

04 — Change Control Engine  
- Controls proposals, approvals, and canon changes.

05 — Consistency Engine  
- Enforces cross-document and cross-engine consistency constraints.

06 — Dependency Registry Engine  
- Registers and validates dependencies between entities/engines/artifacts.

07 — Decision Approval Engine  
- Approves binding decisions, links them to canon and audit trace.

08 — Scope Impact Engine  
- Evaluates scope/impact of changes and decisions.

09 — Risk Safety Engine  
- Detects unsafe operations and enforces safety locks.

10 — Versioning & Memory Engine  
- Defines version semantics and historical continuity rules.

---

## 4. REQUIRED DEPENDENCIES (CROSS-REALM)

Governance requires:
- Core Identity Engine (UID grounding)
- Core State Engine (state gating for approvals/changes)
- Core Lifecycle Engine (phase gating: DRAFT/ACTIVE/FROZEN, etc.)

---

## 5. FORBIDDEN (GOVERNANCE MUST NOT)

- Produce domain narrative content
- Replace validation engines’ truth checks
- Operate without audit trace
- Allow silent canon mutation
- Treat external sources as canon authority

---

## 6. FINAL STATEMENT

Governance Engines are the system’s authority layer.
Bypass of governance equals system non-compliance.
