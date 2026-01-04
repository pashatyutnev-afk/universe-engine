# 🧠 CORE LIFECYCLE ENGINE
## Canonical Engine Specification  
**LEVEL: L1 · CORE ENGINE · LIFECYCLE MODEL · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 03__CORE_LIFECYCLE_ENG.md
- ENGINE_ID: L1-CORE-LIFECYCLE-ENGINE-003
- UID: UE.ENT.ENG.CORE.CORE_LIFECYCLE
- NAME: Core Lifecycle Engine
- CLASS: Core Engine
- CATEGORY: Lifecycle Phases & Phase Transitions
- LEVEL: L1 (System Core)
- STATUS: FINAL
- FAILURE_MODE: fail-closed
- EDITABLE: false
- BYPASS_ALLOWED: false

### ABSOLUTE RULE
> If lifecycle phase is not explicit and valid, the entity is not allowed to change or bind anything.

---

## 1. PURPOSE

Core Lifecycle Engine defines **lifecycle phases** for entities and artifacts,
and enforces **allowed phase transitions**.

It guarantees:
- deterministic phase model
- deterministic transition gating
- traceable lifecycle history (via Audit Log)

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define canonical lifecycle phases
- Validate phase transition requests
- Enforce allowed/forbidden transitions
- Require trace_id for every lifecycle event
- Emit lifecycle transition records via Audit Log

### OUT-OF-SCOPE (FORBIDDEN)
- Editing content inside artifacts
- Deciding narrative meaning of phases
- Creating new phases without Change Control
- Silent phase changes

---

## 3. CANONICAL LIFECYCLE MODEL

### 3.1 Canonical Phases (fixed)

- PLANNED      (exists as intent, not yet active)
- DRAFT        (editable, not binding)
- ACTIVE       (operational; may participate in system)
- FROZEN       (locked; may be referenced as stable)
- DEPRECATED   (should not be used for new work)
- ARCHIVED     (historical; non-operational)
- TERMINATED   (hard stop; no further transitions)

### 3.2 Allowed Transitions (default)

- PLANNED → DRAFT
- DRAFT → ACTIVE
- ACTIVE → FROZEN
- ACTIVE → DEPRECATED
- FROZEN → DEPRECATED
- DEPRECATED → ARCHIVED
- ARCHIVED → TERMINATED

Any other transition is forbidden unless explicitly approved via Change Control + Decision Approval.

---

## 4. INPUT ARTIFACT — LIFECYCLE_TRANSITION_REQUEST

### REQUIRED FIELDS
- `entity_uid`
- `entity_type`
- `from_phase`
- `to_phase`
- `transition_reason`
- `timestamp`
- `requested_by`
- `trace_id`

Missing any field → REJECT.

---

## 5. OUTPUT ARTIFACT — LIFECYCLE_TRANSITION_VERDICT

### GUARANTEED OUTPUT
- `entity_uid`
- `verdict` = APPROVED | REJECTED
- `from_phase`
- `to_phase`
- `rejection_reason` (if rejected)
- `trace_id`

Approved transitions must be recorded as append-only lifecycle records via Audit Log.

---

## 6. CORE OPERATIONS

- OP_01 — VALIDATE_PHASE
- OP_02 — VALIDATE_TRANSITION
- OP_03 — APPLY_TRANSITION (conceptual; emits audit record)
- OP_04 — DETECT_BYPASS (phase used as if changed without verdict)

---

## 7. ACCESS MODEL

### WRITE
- Core Engines (for core-owned entities)
- Governance Engines (for governance-owned entities)

### READ
- All engines/orchestrators (to gate behavior by phase)

### DELETE
- FORBIDDEN

---

## 8. DEPENDENCIES

### REQUIRED
- 01__CORE_IDENTITY_ENG (entity_uid grounding)
- 01__AUDIT_LOG_ENG (append-only lifecycle history)
- 04__CHANGE_CONTROL_ENG (introducing new phases or non-default transitions)

### FORBIDDEN
- Specialists as lifecycle authority
- Silent mutation without trace/audit

---

## 9. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- Missing `trace_id`
- Unknown phase
- Forbidden transition
- Attempt to treat DRAFT as binding
- Attempt to bypass lifecycle (use to_phase effects without approved verdict)

Reaction:
- REJECT
- Emit Audit incident
- Governance lock escalation if repeated

---

## 10. TRACE RULES

- Every phase transition must have `trace_id`
- Trace gaps invalidate downstream approvals and bindings
- Entities not in ACTIVE/FROZEN are non-binding by default

---

## 11. NON-GOALS
- Does not edit content
- Does not decide story meaning
- Does not compress history
- Does not “auto-upgrade” phases

---

## 12. FINAL STATEMENT
Lifecycle phase is the system’s permission boundary.
No valid phase → no valid change → no valid binding.

---

**STATUS:** Core Lifecycle Engine v1.0  
**CANON:** FIXED · NON-BYPASSABLE
