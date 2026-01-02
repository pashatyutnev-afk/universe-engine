# ENGINE_LIBRARY/02_ENGINE_CHECKLISTS
## Canonical Readiness, Safety & Quality Gates (L0 · Machine Grade)

---

## 0) STATUS

- Layer: L0
- Object: Engine Validation Gates
- Authority: Governance Layer
- Scope: All ENGINES (L1–L3)
- Application: Mandatory before BETA and FINAL

Absolute Rule:
> An Engine that fails a checklist must not execute.

---

## 1) PURPOSE

This document defines **non-negotiable gates** that determine
whether an Engine is:

- safe to exist
- safe to execute
- safe to scale
- safe to canonize

Checklists are **binary**:
- PASS → engine may proceed
- FAIL → engine is blocked

No “almost”.

---

## 2) CANONICAL READINESS CHECKLIST (STRUCTURE GATE)

### 2.1 Documentation Presence

**MUST**
- [ ] Single Monolithic Specification OR complete canonical set
- [ ] Engine ID is unique and stable
- [ ] Level (L1/L2/L3) explicitly stated
- [ ] Status declared (DRAFT / BETA / FINAL)

**FAIL if**
- any required section is missing
- status is ambiguous
- multiple conflicting specs exist

---

### 2.2 Purpose & Scope

**MUST**
- [ ] Purpose stated in 1–2 sentences
- [ ] Exactly one primary responsibility
- [ ] Explicit In-scope list
- [ ] Explicit Out-of-scope list

**FORBIDDEN**
- vague purpose (“handles everything about X”)
- empty Out-of-scope

**FAIL if**
- scope boundaries are unclear
- responsibilities overlap with other engines

---

### 2.3 Protocol Presence

**MUST**
- [ ] Step-by-step protocol
- [ ] Validation step exists
- [ ] Authorization step exists (if canon/state affecting)
- [ ] Clear execution step
- [ ] Defined result/return

**FAIL if**
- protocol skips validation
- protocol allows implicit execution
- protocol allows bypass

---

## 3) GOVERNANCE & AUTHORITY CHECKLIST (POWER GATE)

### 3.1 Authority Separation

**MUST**
- [ ] Requester ≠ Approver
- [ ] Engine cannot self-approve
- [ ] Specialist cannot Execute
- [ ] Governance role explicitly named

**FAIL if**
- any self-approval exists
- engine decides its own legitimacy

---

### 3.2 Canon Interaction

If engine affects canon or system truth:

**MUST**
- [ ] Governance approval required
- [ ] Approval outcome is explicit (approve/reject)
- [ ] No silent canon mutation

**FAIL if**
- canon can be changed without approval
- approval is implicit or assumed

---

## 4) ACCESS & INTERFACE SAFETY CHECKLIST

### 4.1 Interface Definition

**MUST**
- [ ] Request interface defined
- [ ] Execute interface defined (or explicitly forbidden)
- [ ] Read interface defined
- [ ] Write interface defined
- [ ] Access rules per interface

**FAIL if**
- any interface is implicit
- access is “by convention”

---

### 4.2 Forbidden Paths

**MUST CONFIRM**
- [ ] No Specialist → Execute path
- [ ] No Specialist → Canon path
- [ ] No Specialist → Audit write
- [ ] No direct Engine → Canon mutation (without governance)

**FAIL if**
- any direct forbidden path exists

---

## 5) TRACE & AUDIT COMPATIBILITY CHECKLIST

### 5.1 Trace Model

If engine participates in multi-step or cross-engine flow:

**MUST**
- [ ] Accept incoming trace_id
- [ ] Emit trace_id if starting flow
- [ ] Preserve trace_id across steps

**FAIL if**
- trace_id is dropped
- new trace_id created mid-chain without rule

---

### 5.2 Audit Expectations

If engine outcome affects system state or canon:

**MUST**
- [ ] Define which events are auditable
- [ ] Define success / failure / rejection facts
- [ ] No deferred or optional logging

**FAIL if**
- “log later” exists
- logging depends on implementation mood

---

## 6) FAILURE & VIOLATION CHECKLIST (RESILIENCE GATE)

### 6.1 Failure Model

**MUST**
- [ ] Severity levels defined (CRITICAL / MAJOR / MINOR)
- [ ] Reaction defined per severity
- [ ] Fail-open vs Fail-closed explicitly chosen

**DEFAULTS**
- L1 → Fail-Closed
- L2 → Prefer Fail-Closed
- L3 → May degrade, but must not corrupt canon

**FAIL if**
- failure behaviour is undefined
- silent failure is possible

---

### 6.2 Violation Handling

**MUST**
- [ ] Violations are detectable
- [ ] Violations trigger visible response
- [ ] CRITICAL violations halt or escalate

**FAIL if**
- violation can be ignored
- violation has no consequence

---

## 7) DEPENDENCY & COUPLING CHECKLIST

### 7.1 Dependency Declaration

**MUST**
- [ ] Dependencies listed explicitly
- [ ] Dependency level (L1/L2/L3) known

**FAIL if**
- hidden dependencies exist

---

### 7.2 Coupling Rules

**FORBIDDEN**
- L3 writing to L1
- Production engines approving canon
- Engines mutating Audit history
- Circular dependency in L1 core

**FAIL if**
- dependency graph creates power inversion

---

## 8) TERMINOLOGY & CONSISTENCY CHECKLIST

**MUST**
- [ ] Terms match ENGINE_TERMS
- [ ] No redefinition of canonical terms
- [ ] No ambiguous language (“maybe”, “sometimes”)

**FAIL if**
- terminology drifts
- same word used with different meanings

---

## 9) FINALIZATION GATE (GO / NO-GO)

An engine may be marked **FINAL** only if:

- [ ] All sections above PASS
- [ ] No FAIL conditions triggered
- [ ] Governance approval recorded
- [ ] Engine is predictable under failure

If any item FAILS:
> Engine status remains BLOCKED.

---

## 10) CANON STATEMENT

Checklists are not bureaucracy.  
They are the last line before corruption.
