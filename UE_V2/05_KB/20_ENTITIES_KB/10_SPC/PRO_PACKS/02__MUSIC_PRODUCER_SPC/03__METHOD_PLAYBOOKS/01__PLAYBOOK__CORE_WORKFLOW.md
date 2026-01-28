# 01__PLAYBOOK__CORE_WORKFLOW — MUSIC_PRODUCER_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/02__MUSIC_PRODUCER_SPC/03__METHOD_PLAYBOOKS/01__PLAYBOOK__CORE_WORKFLOW.md
SCOPE: KB — SPC Pro Pack — Music Producer — Playbook (Core Workflow)
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS / 03__METHOD_PLAYBOOKS
DOC_TYPE: PLAYBOOK
PLAYBOOK_TYPE: CORE_WORKFLOW
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.MUSIC_PRODUCER.PB.CORE.001
OWNER: SPC (Music Producer)
ROLE: Deterministic end-to-end workflow to produce O1/O2 (and O3 optional) without scope drift.

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Core workflow playbook initialized for Music Producer SPC pack."
- REASON: "Make producer execution repeatable and testable."
- IMPACT: "Defines steps, outputs, and validation routing."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.MPROD.PB.CORE.001

---

## GOAL
Стабильно выдавать:
- O1 PRODUCER_TASK_CARD
- O2 PRODUCTION_EXEC_PLAN
- (O3 VARIANTS_PLAN — только если требуется)

---

## REQUIRED INPUTS (MIN)
- TASK_GOAL (1 sentence)
- PLATFORM_INTENT (shorts/full/clip/etc)
- CONSTRAINTS (1–5 bullets)

If missing → route to CHK-READINESS and STOP.

---

## OUTPUT CONTRACT (MUST)
### O1 — PRODUCER_TASK_CARD (MUST)
Contains:
- GOAL
- DELIVERABLES (O1/O2/(O3))
- CONSTRAINTS
- ACCEPTANCE (testable)
- SCOPE (in/out)
- ROUTING (handoffs, UID-only if present)
- TRACE_MIN (task id, outputs list)

### O2 — PRODUCTION_EXEC_PLAN (MUST)
Contains:
- Section map (time + intent)
- Dynamics arc (peaks/contrast)
- Arrangement / seat plan (decision-level)
- Hook plan (must-hear + test)
- Performance / take direction (if vocal/lead present)
- Take acceptance criteria (PASS/REWORK triggers)
- Validation route (checklists/gates order)
- Minimum trace block

### O3 — VARIANTS_PLAN (OPTIONAL)
Only if requested:
- identity anchors
- allowed changes (one lever per variant)
- per-variant acceptance
- validation rerun notes

---

## CORE WORKFLOW (STEPS)

### STEP 0 — Read pack constraints (no drift)
- Apply PRINCIPLES + LIMITS.
- Confirm role boundaries:
  - no engineering recipes
  - no legal determinations
  - no prompt takeover (if separated)

### STEP 1 — Normalize input (producer intake)
Create a compact intake object:
- goal
- platform intent
- constraints
- “must-have outcome” (1 measurable)
- “avoid” (1–3)

### STEP 2 — Load TOPICS (deterministic)
Use TOPIC_BINDINGS:
- Load DEFAULT set.
- Load EXTENSIONS only if task requires.
Record:
- TOPICS_LOADED list in trace.

### STEP 3 — Draft O1 (task card)
Produce O1:
- make acceptance testable:
  - hook recognized <=10s
  - intelligible on phone (if relevant)
  - section contrast exists
- add scope boundaries + routing notes

### STEP 4 — Draft O2 (exec plan)
Build O2 in this order:
A) Section map (time + intent)
B) Dynamics arc (where peaks/dips)
C) Seat plan (foreground/mid/background + masking risks as decisions)
D) Hook plan (must-hear targets + test)
E) Performance/take direction (if relevant)
F) Acceptance triggers (PASS/REWORK conditions)
G) Validation route + minimal trace

### STEP 5 — Optional O3 (variants)
If variants requested:
- define identity anchors first
- then variant-by-variant “one lever change”
- define acceptance per variant
- note rerun: at least CONSISTENCY gate

### STEP 6 — Pre-validate (self-check)
Run quick rubric scan:
- D1 clarity
- D2 scope
- D3 structure
- D7 trace/validation
If any <6 → mark REWORK candidate.

### STEP 7 — Output + route to validation
Deliver O1/O2/(O3) and explicitly instruct:
- run checklists then gates (UIDs)

If any fail later:
- jump to PB-02 DIAGNOSE_AND_REWORK.

---

## EXIT CONDITIONS
- READY when:
  - O1/O2 complete
  - no hard limit violations
  - acceptance is testable
  - validation route is included

---

## REQUIRED UID REFERENCES
- PRINCIPLES:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.PRINCIPLES.001
- TOPIC BINDINGS:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.TOPIC_BINDINGS.001
- RUBRIC:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.RUBRIC.001
- CHECKLISTS:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.CHK.READINESS.001
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.CHK.QUALITY.001
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.CHK.COMPLIANCE.001
- GATES:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.CORE_QUALITY.001
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.CONSISTENCY.001

---
END
