# 🎛️ ORCHESTRATORS — REALM README
## Canonical Realm Specification  
**LEVEL: L3 · ORCHESTRATION LAYER · PIPELINE CONTROL · MACHINE-GRADE**

---

## 0. REALM STATUS

- REALM: 06_ORCHESTRATORS
- CLASS: ORCHESTRATOR
- LEVEL: L3 (Orchestration Layer)
- STATUS: ACTIVE
- OWNER: System / Human
- BYPASS_ALLOWED: false (orchestration defines order)
- NON_CANON: true (orchestrators are execution controllers, not canon authority)

### REALM ABSOLUTE RULE
> Orchestrator does not create truth. It routes work and enforces order.

---

## 1. PURPOSE

Orchestrators are **pipeline controllers**.

They:
- select which engines run
- enforce execution order
- pass artifacts between engines
- validate completeness before allowing downstream steps
- emit final assembled outputs (non-canon unless governance registers)

Orchestrators convert a set of engines into a working production line.

---

## 2. ORCHESTRATOR CONTRACT

### INPUT
- project request / goal
- constraints (genre, scope, realism, deadlines)
- references to existing artifacts (if any)
- trace_id (recommended for auditability)

### OUTPUT
- execution plan (ordered steps)
- artifact routing map
- orchestration verdicts (pass/fail/partial)
- assembled outputs ready for registration

---

## 3. ORCHESTRATOR RULES (HARD)

- Orchestrators must not contradict Governance engines.
- Orchestrators must not edit L1 Canon.
- Every step must declare:
  - required inputs
  - produced outputs
  - gating conditions (what must be true to continue)
- Missing required artifact → fail-closed.
- Optional artifacts must be explicitly marked OPTIONAL.

---

## 4. ENGINE LIST (ORDER IS MANDATORY)

00 — README (this file)

01 — Narrative Orchestrator  
02 — Character Orchestrator  
03 — World Orchestrator  
04 — Production Orchestrator  
05 — Multi-Engine Pipeline Orchestrator

---

## 5. REQUIRED DEPENDENCIES (CROSS-LAYER)

Common dependencies:
- Governance Engines (audit, change control, consistency)
- Validation Engines (optional gates)
- Domain engines and production engines (depending on orchestrator)

---

## 6. FINAL STATEMENT

Engines define rules.
Orchestrators make them run in the right order.
