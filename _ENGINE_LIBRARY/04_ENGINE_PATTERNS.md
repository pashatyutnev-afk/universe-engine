# ENGINE_LIBRARY/04_ENGINE_PATTERNS — MAX MONOLITH
## Canonical Architecture Patterns & Selection Rules (L0 · Machine Grade)

---

## 0) STATUS

- Layer: L0
- Object: Engine Architecture Patterns
- Authority: Governance Layer
- Scope: All ENGINES (L1–L3)
- Binding: Mandatory selection rules

Absolute Rule:
> Patterns are constraints. If you ignore them, architecture breaks.

---

## 1) PURPOSE

This document defines:
- **which architectural patterns exist**
- **when each pattern MUST be used**
- **what is FORBIDDEN inside each pattern**
- **how patterns may interact**
- **how to detect wrong pattern choice**

Patterns are **not optional styles**.  
They are **structural laws**.

---

## 2) PATTERN SELECTION MATRIX (MANDATORY)

Use this matrix before designing any Engine.

- Records facts/history → **Append-Only**
- Grants or denies authority → **Approval**
- Checks rules/consistency → **Validation**
- Executes production/process → **Execution**
- Observes and records without influence → **Observer/Witness**

If more than one applies:
> **Split into multiple engines.**

---

## 3) PATTERN — APPEND-ONLY ENGINE
### Immutable Memory / History / Ledger

---

### WHEN REQUIRED
- Audit logs
- History of changes
- Canon memory
- Integrity chains

---

### CORE RULES (NON-NEGOTIABLE)
- NO delete
- NO modify
- ONLY append
- Each record references previous (`prev_hash`)
- Integrity must be verifiable

---

### FORBIDDEN
- Editing past records
- Reordering history
- Partial writes
- “Cleanup” jobs

---

### FAILURE MODEL
- Fail-Closed
- If append fails → execution HALTS

---

### INTERACTIONS
- May receive events from other engines
- Must never influence decisions or execution

---

### DETECTION OF MISUSE
If engine:
- edits history
- hides records
- summarizes instead of recording facts

→ **Wrong pattern / redesign required**

---

### EXAMPLES
- Audit Log Engine

---

## 4) PATTERN — APPROVAL ENGINE
### Authority / Decision / Canon Gate

---

### WHEN REQUIRED
- Canon changes
- Rule approval
- Governance decisions
- Irreversible actions

---

### CORE RULES
- Requester ≠ Approver
- Explicit scope per request
- Explicit decision outcome (approve/reject)
- Decision itself is a fact (auditable)

---

### FORBIDDEN
- Self-approval
- Implicit approval
- “Auto-approve” without governance rule
- Silent rejection

---

### FAILURE MODEL
- Fail-Closed for canon-affecting actions
- No approval → no commit

---

### INTERACTIONS
- Receives requests
- Emits decision artifacts
- Does NOT execute production

---

### DETECTION OF MISUSE
If engine:
- both approves and executes
- modifies canon directly

→ **Split required**

---

### EXAMPLES
- Canon Authority Engine
- Decision Approval Engine

---

## 5) PATTERN — VALIDATION ENGINE
### Rules / Consistency / Integrity Check

---

### WHEN REQUIRED
- Rule enforcement
- Cross-engine consistency
- Canon integrity
- Preconditions for execution

---

### CORE RULES
- Validate BEFORE commit
- Deterministic outcome preferred
- Violations must be explicit and classifiable

---

### FORBIDDEN
- Auto-fixing data
- Mutating canon or state
- Ignoring violations

---

### FAILURE MODEL
- Reject on violation
- Escalate CRITICAL issues

---

### INTERACTIONS
- Receives candidate data
- Returns validation result
- Never executes or approves

---

### DETECTION OF MISUSE
If engine:
- fixes what it validates
- hides violations

→ **Architecture violation**

---

### EXAMPLES
- Consistency Engine
- Rule Hierarchy Engine

---

## 6) PATTERN — EXECUTION ENGINE
### Production / Pipeline / Action

---

### WHEN REQUIRED
- Content generation
- Data processing
- Pipelines
- Transformations

---

### CORE RULES
- Input must be validated
- Authorization must be respected
- Execution must be traceable
- Outcome must be explicit (success/failure/reject)

---

### FORBIDDEN
- Self-authorization
- Silent retries
- Canon mutation without approval
- Dropping trace_id

---

### FAILURE MODEL
- Depends on level:
  - L1/L2 → prefer Fail-Closed
  - L3 → may degrade but not corrupt

---

### INTERACTIONS
- Receives approved requests
- Produces artifacts/results
- Emits trace-compatible outcomes

---

### DETECTION OF MISUSE
If engine:
- decides if allowed
- executes without trace
- mutates canon directly

→ **Wrong pattern**

---

### EXAMPLES
- Production Engines
- Generation Pipelines

---

## 7) PATTERN — OBSERVER / WITNESS
### Independent Fact Recorder

---

### WHEN REQUIRED
- Independent observation
- Non-interfering monitoring
- Legal/forensic trace

---

### CORE RULES
- Observes only
- Does NOT decide
- Does NOT execute
- Records facts as-is

---

### FORBIDDEN
- Filtering facts
- Acting on observed data
- Modifying events

---

### FAILURE MODEL
- Fail-Closed if observation is mandatory
- Degrade if optional (but must signal)

---

### INTERACTIONS
- Subscribes to events
- Writes immutable records

---

### DETECTION OF MISUSE
If engine:
- reacts to observations
- changes system state

→ **Role corruption**

---

### EXAMPLES
- Audit Log Engine (as witness)

---

## 8) PATTERN COMPOSITION RULES (CRITICAL)

### ALLOWED
- Validation → Approval → Execution
- Execution → Observer
- Approval → Observer

### FORBIDDEN
- Approval + Execution (same engine)
- Validation + Execution
- Observer + Decision
- Append-Only + Analytics

If composition is needed → **split engines**.

---

## 9) PATTERN MISUSE QUICK CHECK

If you answer “yes” to any → redesign:

- Does the engine both decide and act?
- Can it edit its own history?
- Can it bypass governance?
- Can it hide failure?
- Can it change canon implicitly?

---

## 10) CANON STATEMENT

Patterns are the physics of architecture.  
Ignore physics — and systems collapse.
