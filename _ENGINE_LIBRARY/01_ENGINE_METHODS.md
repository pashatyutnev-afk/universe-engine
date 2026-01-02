# ENGINE_LIBRARY/01_ENGINE_METHODS
## Canonical Engineering Methods for Engines (L0 · Machine Grade)

---

## 0) STATUS

- Layer: L0
- Object: Methods (design discipline)
- Authority: Governance Layer
- Change Policy: Governance-controlled
- Scope: All ENGINES (L1-L3)

Absolute Rule:
> An Engine is defined by boundaries and protocol, not by features.

---

## 1) ENGINE DESIGN PIPELINE (Canonical)

This is the only allowed pipeline to create an Engine.

### Stage A — Intent of Engine (Purpose)
**MUST**
- Purpose in 1–2 sentences
- One primary responsibility
- One explicit non-goal

**FORBIDDEN**
- “improves system” without defining action
- “handles everything related to X”
- “decides and executes” in same Engine

Acceptance:
- Purpose is testable: you can say “did it do it?” yes/no.

---

### Stage B — Scope (In / Out)
**MUST**
- In-scope list (concrete actions)
- Out-of-scope list (hard prohibitions)

**FORBIDDEN**
- Out-of-scope = empty
- “not responsible for other things” (non-specific)

Acceptance:
- Any unclear item is moved to Out-of-scope until specified.

---

### Stage C — Authority & Governance Position
**MUST**
- Who may REQUEST
- Who may AUTHORIZE
- Who may EXECUTE
- Who may READ
- Who may WRITE

**FORBIDDEN**
- self-approval
- direct specialist execute
- hidden authority (“system decides automatically”) without naming Governance

Acceptance:
- A role map exists and prevents bypass.

---

### Stage D — Interface Contract
Define the engine as contract.

**MUST**
- Inputs (types/fields)
- Outputs (types/fields)
- Side-effects (explicit if any)
- Error outcomes (reject/fail/halt)

**FORBIDDEN**
- implicit side-effects
- “returns success” without specifying artifact/result

Acceptance:
- You can simulate the interface without implementation.

---

### Stage E — Protocol First (Behavior Contract)
Protocol is the legal behavior.

**MUST**
- Step-by-step
- Validation points
- Authorization point (if canon-affecting)
- Trace creation/propagation (if multi-step)
- Audit fact generation (if required)

Canonical Protocol Skeleton:
1) Trigger / Receive request  
2) Validate (schema/taxonomy/rules)  
3) Authorize (Governance)  
4) Execute (engine action)  
5) Record facts (Audit via trace if applicable)  
6) Return result (artifact + status)

**FORBIDDEN**
- “then do stuff”
- “may skip validation”
- “logs if needed” (audit policy must be explicit)

Acceptance:
- Every step has deterministic entry/exit conditions.

---

### Stage F — Rules (Hard Constraints)
Rules are stronger than protocol.

**MUST**
- Absolute rules (FORBIDDEN actions)
- Content rules (what is allowed)
- Conflict handling rule (what happens if rules conflict)
- Default severity mapping

**FORBIDDEN**
- rules that depend on mood/interpretation
- “allowed unless…” without formal condition

Acceptance:
- A violation is machine-detectable.

---

### Stage G — Failure Model & Violations
**MUST**
- Severity levels (CRITICAL/MAJOR/MINOR)
- Reaction per level
- Fail-open vs fail-closed defined

Default:
- L1 engines: prefer Fail-Closed
- L3 engines: may degrade, but must not corrupt canon

**FORBIDDEN**
- silent failure
- “retry until success” without cap and governance

Acceptance:
- You can describe what happens under failure without guessing.

---

### Stage H — Dependencies & Coupling Control
**MUST**
- Dependencies list
- Coupling rule (what cannot depend on what)

Default Coupling Rules:
- L3 must not write to L1
- Specialists must not execute engines directly
- Knowledge Base is read-only for all
- Audit Log is write-only except Audit Engine

Acceptance:
- Dependency graph is acyclic for L1 core.

---

### Stage I — Canonization Gate
An engine cannot be FINAL without gates.

**MUST**
- Checklist pass (canonical + safety)
- Test-case pass (bypass/audit/conflict/access)
- Terms compliance

Acceptance:
- FINAL means “predictable in scale”.

---

## 2) RESPONSIBILITY SEPARATION (Non-Negotiable)

**One Engine = One Responsibility**

Forbidden combinations (examples):
- Decision + Execution (must split Approval Engine vs Execution Engine)
- Audit + Analytics (audit records facts, analytics interprets)
- Storage + Interpretation (memory engine vs reasoning engine)
- Governance + Production (authority vs content generation)

Canon Statement:
> Mixed responsibilities create corruption paths.

---

## 3) LEVELS & CRITICALITY (Operational)

### L1 System Core
MUST:
- strict access control
- fail-closed on integrity/audit failures
- immutable or governance-controlled changes only

### L2 Services
MUST:
- degrade gracefully
- never bypass L1 rules

### L3 Domain/Production
MUST:
- never mutate canon directly
- use governance-mediated flows

---

## 4) TRACE MODEL (System-wide)

If an engine participates in multi-step operations, it must be traceable.

**MUST**
- accept `trace_id` if provided
- emit `trace_id` if creating new operation
- propagate `trace_id` to downstream requests

**FORBIDDEN**
- creating new trace_id mid-chain without reason
- losing trace_id across steps

Acceptance:
- Any artifact/result can be linked to its request and governance decision.

---

## 5) AUDIT COMPATIBILITY RULE

If engine outcome changes system state or canon-related artifacts:

**MUST**
- produce auditable fact via trace
- define which outcomes are logged (attempt/success/failure/reject)

**FORBIDDEN**
- “log later”
- “log only failures” if canon-affecting

---

## 6) ANTI-PATTERN CATALOG (Quick Kill Switch)

If you see any of these → redesign:

- “Engine decides if allowed”
- “Specialist triggers execution directly”
- “No out-of-scope”
- “Protocol optional”
- “Silent failure acceptable”
- “Terms are flexible”
- “History editable”
- “Approval and execution in one place”

---

## 7) REQUIRED ARTIFACT FORMS (Minimal Contracts)

### ENGINE_REQUEST (when applicable)
Required fields:
- trace_id (or request generates it)
- requester_type / requester_id
- engine_id
- intent_ref
- payload
- constraints
- expected_output

### ENGINE_RESULT (when applicable)
Required fields:
- trace_id
- status (success/failure/reject)
- artifact_ref
- errors (if any)
- references (kb/canon refs)

---

## 8) CANON STATEMENT

Discipline builds immortal systems.
