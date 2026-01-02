# ENGINE_LIBRARY/SYSTEM_WORK_INSTRUCTION — MAX MONOLITH
## Canonical Operating Constitution for the System (L0 · Machine Grade)

---

## 0) STATUS

- Layer: **L0**
- Object: **System Operating Constitution**
- Authority: **Governance Layer**
- Scope: **Entire System**
- Binding: **Absolute**
- Change Policy: **Governance-only**

Absolute Rule:
> If an action is not permitted here, it is forbidden everywhere.

---

## 1) PURPOSE

This document defines **HOW THE SYSTEM IS OPERATED**:
- how new engines are created
- how existing engines are changed
- how specialists work
- how knowledge is used
- how canon is protected
- how failures are handled
- how L0 itself is changed (rarely)

This is not guidance.
This is **law**.

---

## 2) SYSTEM LAYERS & AUTHORITY MODEL

### Authority Hierarchy (Top → Bottom)

1) **Governance Layer** — decides & approves
2) **ENGINE_LIBRARY (L0)** — defines rules of construction
3) **L1 System Core Engines** — audit, canon, integrity
4) **L2 System Services** — coordination & validation
5) **L3 Domain/Production Engines** — content & processing
6) **Specialists (S1/S2)** — intent formation
7) **Knowledge Base** — information only (read-only)

**Inversion is forbidden.**

---

## 3) CANONICAL LIFE-CYCLE: ENGINE

### 3.1 Creation Pipeline (MANDATORY)

An Engine may exist only if ALL steps are completed:

1) Choose Level (L1 / L2 / L3)
2) Define Purpose (1–2 sentences)
3) Define Scope (In / Out)
4) Select Pattern(s) (Append / Approval / Validation / Execution / Observer)
5) Write **Engine Monolith** (using templates)
6) Define Failure Model
7) Define Interfaces & Access Rules
8) Define Trace & Audit compatibility
9) Pass **ENGINE_CHECKLISTS**
10) Pass **ENGINE_TEST_CASES**
11) Governance Review
12) Status assignment: `DRAFT → BETA → FINAL`

Skipping any step → **BLOCKED**.

---

### 3.2 Modification of Existing Engine

**Rules**
- No “small fixes”
- No direct edits to FINAL engines
- No silent changes

**Required Procedure**
1) Open change proposal (intent)
2) Impact analysis (what breaks?)
3) Re-run Checklists
4) Re-run Test Cases
5) Governance approval
6) Version bump
7) Audit fact recorded

Unapproved change → **CRITICAL violation**.

---

### 3.3 Engine Removal / Deprecation

- Engines are **deprecated**, not deleted
- Deprecation requires governance approval
- Canonical history remains immutable
- Replacement path must be defined

---

## 4) CANONICAL LIFE-CYCLE: SPECIALISTS

### 4.1 Specialist Creation

A Specialist must have:
- Canonical role definition
- Clear domain scope
- Explicit forbidden actions
- Knowledge Access Profile
- Trace requirements

Specialist without limits → **rejected**.

---

### 4.2 Specialist Operation Rules

- Specialists **only form Intent**
- Specialists **never execute**
- Specialists **never approve**
- Specialists **never write audit**
- Specialists **operate via trace**

Violation → **CRITICAL**.

---

### 4.3 Specialist Escalation

- Conflicts → S1 Lead Specialist
- Unresolved → Governance
- Repeated violations → Specialist blocked

---

## 5) KNOWLEDGE BASE USAGE

### Rules

- Knowledge Base is **read-only**
- Knowledge does not decide
- Knowledge does not override canon
- Knowledge is rejected if conflicting with canon

### Access

- Specialists: read-only (domain-based)
- Engines: read-only
- Governance: read + approval metadata

Knowledge without context → ignored.

---

## 6) TRACE, AUDIT & ACCOUNTABILITY

### Trace Rules

- Every multi-step action must have `trace_id`
- `trace_id` must propagate end-to-end
- Trace loss → rejection or failure

---

### Audit Rules

- Audit records **facts only**
- Audit is append-only
- Mandatory logging must not be skipped
- If audit unavailable → **fail-closed**

“If it is not logged — it did not happen.”

---

## 7) FAILURE & INCIDENT MANAGEMENT

### Severity Levels

- **CRITICAL** — threatens system integrity
- **MAJOR** — rule violation without core damage
- **MINOR** — deviation without risk

---

### Mandatory Reactions

- CRITICAL → HALT or ESCALATE
- MAJOR → REJECT + REVIEW
- MINOR → WARN + LOG

Silent failure is **forbidden**.

---

## 8) GOVERNANCE OPERATIONS

### Governance Powers

- Approve / reject canon changes
- Approve / reject engine status changes
- Approve term additions (ENGINE_TERMS)
- Block engines or specialists
- Trigger audits

Governance does NOT execute production.

---

### Governance Records

- All decisions are auditable
- Decisions are immutable facts
- Absence of decision = rejection

---

## 9) CHANGE POLICY FOR L0 (ENGINE_LIBRARY)

### Absolute Protection Rule

- L0 changes are **rare**
- L0 changes are **dangerous**
- L0 changes require:
  - explicit proposal
  - full system impact analysis
  - governance super-approval
  - versioned release

Ad-hoc L0 edits → **system fracture**.

---

## 10) FORBIDDEN PRACTICES (AUTO-BLOCK)

If detected → immediate block & review:

- Direct execution by Specialist
- Canon mutation without approval
- Editable history
- Silent failures
- Self-approval
- Authority inversion (L3 → L1)
- Flexible terminology
- “Temporary bypass”

---

## 11) SYSTEM INTEGRITY PRINCIPLES

- Structure > speed
- Control > convenience
- Explicit > implicit
- Deterministic > clever
- Audit > trust

---

## 12) FINAL CANON STATEMENT

Discipline is the price of immortality.
Systems that respect structure outlive creators.
