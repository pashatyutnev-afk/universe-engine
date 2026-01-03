# ENGINE_LIBRARY/05_ENGINE_EXAMPLES
## Canonical Architecture Examples & Failure Analysis (L0 · Machine Grade)

---

## 0) STATUS

- Layer: L0
- Object: Reference Examples (Didactic + Defensive)
- Authority: Governance Layer
- Scope: All ENGINES (L1–L3)
- Purpose: Pattern enforcement & anti-corruption

Absolute Rule:
> Examples exist to prevent repetition of known failures.

---

## 1) PURPOSE

This document provides:
- **reference shape of a good engine**
- **precise failure points of a bad engine**
- **diagnostic questions to classify engines**
- **decision guidance: fix, split, or discard**

Examples are **structural**, not thematic.

---

## 2) EXAMPLE — GOOD ENGINE (CANONICAL)

### 2.1 Profile

- Level: L1
- Pattern(s): Validation + Approval (split across engines)
- Responsibility: Single, explicit
- Canon Interaction: Governance-mediated
- Audit: Trace-based, append-only

---

### 2.2 Structural Properties (WHY IT WORKS)

**Purpose**
- Defined in 1–2 sentences
- Testable outcome (yes/no)

**Scope**
- In-scope: explicit actions only
- Out-of-scope: hard prohibitions listed

**Protocol**
- Step-by-step
- Validation precedes execution
- Authorization explicit
- Result deterministic

**Rules**
- Absolute rules override convenience
- Content rules formalized

**Failure Model**
- Severity levels defined
- Fail-closed where integrity matters
- No silent failure paths

**Trace & Audit**
- trace_id propagated end-to-end
- outcomes produce auditable facts

---

### 2.3 Boundary Discipline

- Does NOT execute what it approves
- Does NOT approve what it validates
- Does NOT mutate history
- Does NOT interpret facts as meaning

---

### 2.4 Diagnostic Questions (ALL MUST BE YES)

- Can this engine be simulated without guessing?
- Is every failure visible and classifiable?
- Can it be stopped without corrupting canon?
- Can another engine replace it without redesigning the system?

If all YES → **Good Engine**

---

### 2.5 Canon Statement

Good engines are boring.
Boring engines scale.

---

## 3) EXAMPLE — BAD ENGINE (ANTI-CANONICAL)

### 3.1 Profile

- Level: Mixed/Undefined
- Pattern(s): Mixed (Approval + Execution + Storage)
- Responsibility: Blurred
- Canon Interaction: Implicit
- Audit: Optional or missing

---

### 3.2 Structural Failures (WHERE IT BREAKS)

**Purpose**
- Vague (“handles everything about X”)
- Not testable

**Scope**
- Out-of-scope missing or implicit
- Responsibilities leak over time

**Protocol**
- Steps skipped (“if needed”)
- Validation optional
- Execution may happen implicitly

**Authority**
- Self-approval present
- Specialist can trigger execution
- Governance assumed, not enforced

**Failure**
- Silent retries
- “Log later”
- Partial success treated as success

---

### 3.3 Corruption Paths (CRITICAL)

- Engine edits its own history
- Engine decides if rules apply
- Engine mutates canon without approval
- Engine hides failed attempts

Each path = **latent system breach**

---

### 3.4 Diagnostic Questions (ANY YES = FAIL)

- Does the engine both decide and act?
- Can it change past records?
- Can it succeed without leaving trace?
- Can it bypass governance under “special case”?
- Can failure be ignored without consequence?

If any YES → **Bad Engine**

---

### 3.5 Canon Statement

Bad engines work — until they destroy trust.

---

## 4) BORDERLINE CASES (COMMON TRAPS)

### Trap A — “Just for performance”
- Skipping validation
- Caching approval
- Deferred audit

Result:
> Short-term speed, long-term corruption.

---

### Trap B — “Temporary shortcut”
- Direct execution path “for now”
- Missing Out-of-scope

Result:
> Shortcut becomes permanent attack surface.

---

### Trap C — “Smart engine”
- Engine interprets rules contextually
- Engine “decides” edge cases

Result:
> Authority drift → governance collapse.

---

## 5) DECISION GUIDE (WHAT TO DO)

When reviewing an engine:

- If **one responsibility violated** → **SPLIT**
- If **authority violated** → **REDESIGN**
- If **history mutable** → **DISCARD**
- If **silent failure possible** → **BLOCK**
- If **terminology drifts** → **REWRITE**

Never “patch” authority problems.

---

## 6) RED FLAGS (AUTO-REJECT)

If present → engine must not execute:

- “Auto-approve”
- “Best effort”
- “Eventually consistent canon”
- “Log if possible”
- “Temporary bypass”
- “Special case for admin”

---

## 7) CANON STATEMENT

Examples do not teach creativity.
They prevent stupidity.
