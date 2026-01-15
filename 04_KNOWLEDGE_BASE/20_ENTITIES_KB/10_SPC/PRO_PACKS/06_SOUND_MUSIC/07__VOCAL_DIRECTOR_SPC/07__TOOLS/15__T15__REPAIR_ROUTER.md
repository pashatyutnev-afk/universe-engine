# SPC PRO PACK — TOOL (T15) — REPAIR_ROUTER (TYPE→AXIS→PB) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/07__TOOLS/15__T15__REPAIR_ROUTER.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: TOOL
TOOL_ID: T15
TOOL_NAME: REPAIR_ROUTER
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.TOOL.VOCAL_DIRECTOR.T15.REPAIR_ROUTER.001
OWNER: SYSTEM
ROLE: Deterministic router from failure type (T1..T9) to a single repair axis (A1..A7), primary playbook (PB-01..PB-08), and required rerun gates. Enforces one-axis discipline.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Tool T15 REPAIR_ROUTER for VOCAL_DIRECTOR."
- REASON: "Repairs must be consistent and non-regressive; one-axis routing prevents multi-fix chaos."
- IMPACT: "Faster triage, fewer loops, deterministic playbook application."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.TOOL.VD.T15.001

---

## 0) PURPOSE
Given a failure type code, output:
- REPAIR_ROUTE (single-axis patch plan)

Used in:
- DURING_RUN checklist
- Case Library
- Post-run remediation

---

## 1) INPUTS (REQUIRED)
- type_code: T1..T9
Optional:
- stacking_used (YES/NO)
- phrases_present (YES/NO)
- gate_failed (G#)
- note (short)

Rules:
- Router selects ONE axis and ONE primary playbook per run.
- If multiple type codes exist, run router separately per type (separate iterations).

---

## 2) OUTPUT BLOCK (STABLE NAME)
T15 MUST output:

### REPAIR_ROUTE
- type_code:
- chosen_axis: A?
- primary_playbook: PB-0?
- tools_to_run:
  - T?? (optional)
- rerun_gates:
  - G?
  - G? (optional)
- stop_until_pass: YES/NO
- notes (optional):
  - 1)

---

## 3) AXIS MAP (A1..A7) (REFERENCE)
A1 — Attacks/clarity micro-directives
A2 — Arc/contrast lever selection (<=3)
A3 — Breath/density safety
A4 — Profile coherence (prune contradictions)
A5 — Stacking safety (protected zones + QC)
A6 — Take pack repeatability
A7 — Compliance / escalation-only patch

---

## 4) TYPE → ROUTE MAP (DETERMINISTIC)
### T1 (consonant loss)
- axis: A1
- PB: PB-03
- tools: T05
- rerun: G3

### T2 (breath split P0)
- axis: A3
- PB: PB-04
- tools: T09 + T10
- rerun: G6 → G3

### T3 (targets bloat/missing)
- axis: A1
- PB: PB-02
- tools: T02 + T03
- rerun: G2 → G3

### T4 (density/unsingable R2)
- axis: A3
- PB: PB-04
- tools: T10 + (T14 if escalation needed)
- rerun: G6 → G3
- note: "If R2 persists, escalation is mandatory (T14)."

### T5 (delivery masking)
- default axis: A1
- PB: PB-03
- tools: T05
- rerun: G3
- exception:
  - if contradiction/profile drift is the root → axis A4, PB-01, tools T06/T07, rerun G4 → (verify) G3

### T6 (stacking masking)
- axis: A5
- PB: PB-07
- tools: T11
- rerun: G7 → G3

### T7 (arrangement seat conflict)
- axis: A7
- PB: NONE (escalation-only)
- tools: T14
- rerun: G3 (after owner response)

### T8 (arc overload/flat)
- axis: A2
- PB: PB-05
- tools: T08
- rerun: G5 → (verify) G3

### T9 (scope violation)
- axis: A7
- PB: PB-08
- tools: T13 (+ T14 if converting ownership)
- rerun: G9

---

## 5) STOP RULES
- stop_until_pass must be YES for:
  - T1..T6, T8, T9 (cannot proceed while failing primary gate)
- stop_until_pass for T7:
  - YES (pause until owner response)

---

## 6) ANTI-SCOPE / ANTI-GUESSING
Forbidden:
- recommending multiple PBs in a single route
- “try everything” routing
Allowed:
- single PB route + explicit rerun gates

---

## 7) TRACE
TRACE:
- TOOL: T15
- OUTPUT: REPAIR_ROUTE
- MAP: T1..T9 → A1..A7 → PB/Tools/Gates

--- END.
