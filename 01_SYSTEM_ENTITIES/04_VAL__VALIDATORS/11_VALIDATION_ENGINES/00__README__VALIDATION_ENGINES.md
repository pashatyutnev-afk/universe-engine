# ✅ VALIDATION ENGINES — README
## Realm Index (Family Overview)
**REALM:** 11_VALIDATION_ENGINES  
**CLASS:** VALIDATION (L4)  
**LEVEL:** L4 · System Verification Layer  
**STATUS:** ACTIVE  
**VERSION:** 1.0  
**ROLE:** Explain what validation engines do, how they are used, and how they interlock.

---

## 0. WHAT THIS REALM IS

Validation Engines are the **verification layer** of Universe Engine.

They do not create content.  
They do not decide governance.  
They do not generate production output.

They **validate** whether an artifact, claim, or plan is compliant with:
- Canon
- Rules
- Evidence requirements
- Logical consistency
- Language standards
- Cultural constraints
- Historical constraints
- Scientific plausibility constraints

### Prime function
> Convert “looks okay” into “passes defined gates”.

---

## 1. POSITION IN SYSTEM

Validation Engines are downstream of:
- Core Engines (identity/state/lifecycle)
- Governance Engines (audit/canon/rules/change/consistency/dependencies/approval/scope/risk/versioning)
- Domain Engines (narrative/character/world)
- Orchestrators (pipelines)
- Production Engines (image/video/edit/audio)

Validation Engines produce:
- verdicts
- issue lists
- repair plans
- severity ratings
- gate pass/fail signals

They are allowed to **block** execution by returning INVALID with CRITICAL severity.

---

## 2. NON-NEGOTIABLE RULES (VALIDATION)

### 2.1 Fail-Closed Default
If required data is missing → **INVALID**.

### 2.2 No Interpretation
Validation Engines do not “assume” missing facts.  
They either:
- pass (VALID)
- partially pass (PARTIAL) with repairs
- fail (INVALID)

### 2.3 Repair Plan Mandatory
Every INVALID/PARTIAL must include a repair plan:
- exact violations
- how to fix
- what to re-check after fix

### 2.4 Evidence Discipline (when applicable)
If an output requires evidence, then:
- claims must have evidence refs
- weak evidence must be flagged
- contradictions must be escalated

---

## 3. STANDARD OUTPUTS (COMMON ARTIFACTS)

All validation engines use common structures:

### 3.1 VALIDATION_VERDICT
Required fields:
- `val_id`
- `validator_engine_id`
- `artifact_ref`
- `timestamp`
- `verdict` = VALID | PARTIAL | INVALID
- `severity` = LOW | MEDIUM | HIGH | CRITICAL
- `issues` (list)
- `repair_plan` (list)
- `recheck_gates` (list)
- `trace_id` (optional)

### 3.2 ISSUE ITEM (canonical)
- `issue_id`
- `type` (missing_field / contradiction / invalid_format / implausible / unclear / forbidden_move)
- `location_ref` (file/section/field)
- `description`
- `severity`
- `fix`

---

## 4. SEVERITY SCALE (CANON)

- **LOW**: cosmetic; does not change meaning
- **MEDIUM**: quality risk; may confuse downstream systems
- **HIGH**: correctness risk; can break pipelines or canon alignment
- **CRITICAL**: system trust risk; must block execution (fail-closed)

Hard rule:
> CRITICAL means STOP.

---

## 5. REQUIRED INPUT DISCIPLINE

Validation Engines require:
- artifact to validate
- referenced upstream specs (if validation depends on them)
- declared constraints list
- canon locks (if any)
- trace_id (optional, but recommended in pipelines)

Missing required input → INVALID (CRITICAL).

---

## 6. ENGINE LIST (THIS REALM)

This realm contains the following engines:

- 01 — Error Detection Engine
- 02 — Fact Consistency Engine
- 03 — Language & Linguistics Engine
- 04 — Cultural Accuracy Engine
- 05 — Historical Accuracy Engine
- 06 — Scientific Plausibility Engine

---

## 7. INTERLOCKS (WHO THEY DEPEND ON)

Validation Engines rely on:
- Audit Log Engine (for trace integrity, if traced)
- Canon Authority Engine (what is canon)
- Rule Hierarchy Engine (which rules override which)
- Consistency Engine (system integrity and invariants)
- Dependency Registry Engine (dependency correctness)
- Versioning & Memory Engine (which version is active)

They must not depend on:
- Specialists (opinions)
- Production output without spec (raw outputs are not truth)
- Unregistered knowledge

---

## 8. COMMON FAILURE MODES

- “looks fine” without checks → forbidden
- missing fields accepted → forbidden
- no repair plan → forbidden
- severity under-rated → forbidden
- validator making new facts → forbidden

---

## 9. HOW TO USE (PIPELINE PATTERN)

Typical pipeline:
1) produce artifact/spec
2) run validation engines relevant to artifact class
3) if INVALID → repair then re-run
4) if PARTIAL → apply repairs then re-run
5) only VALID proceeds to approval/execution/output registry

---

## 10. FINAL RULE

> If it does not pass validation gates —  
> it must not be treated as true, safe, or production-ready.

---

**STATUS:** VALIDATION_ENGINES Realm v1.0  
**REALM:** ACTIVE
