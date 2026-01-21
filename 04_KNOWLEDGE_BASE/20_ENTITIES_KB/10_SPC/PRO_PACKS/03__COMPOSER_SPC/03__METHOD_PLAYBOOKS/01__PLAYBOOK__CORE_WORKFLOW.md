# 01__PLAYBOOK__CORE_WORKFLOW — COMPOSER_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/03__COMPOSER_SPC/03__METHOD_PLAYBOOKS/01__PLAYBOOK__CORE_WORKFLOW.md
SCOPE: KB — SPC Pro Pack — Composer — Playbook (Core Workflow)
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS / 03__METHOD_PLAYBOOKS
DOC_TYPE: PLAYBOOK
PLAYBOOK_TYPE: CORE_WORKFLOW
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.COMPOSER.PB.CORE.001
OWNER: SPC (Composer)
ROLE: Deterministic end-to-end composition workflow producing O1/O2 (and optional O3/O4/O5) without scope drift.

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Core workflow playbook initialized for Composer SPC pack."
- REASON: "Make composition decisions repeatable and testable."
- IMPACT: "Defines steps, outputs, and validation routing."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.COMPOSER.PB.CORE.001

---

## GOAL
Стабильно выдавать:
- O1 COMPOSER_TASK_CARD
- O2 COMPOSITION_EXEC_PLAN
и (если требуется задачей):
- O3 MOTIF_LIBRARY
- O4 HARMONY_MAP
- O5 MELODY_GUIDE

---

## REQUIRED INPUTS (MIN)
- TASK_GOAL (1 sentence)
- PLATFORM_INTENT (shorts/full/clip/etc)
- CONSTRAINTS (1–5 bullets)
Optional but useful:
- genre/mood
- reference vibe words
- target duration window

If missing mandatory → route to CHK-READINESS and STOP.

---

## OUTPUT CONTRACT (MUST)

### O1 — COMPOSER_TASK_CARD
Must contain:
- GOAL
- DELIVERABLES (O1/O2/(O3/O4/O5))
- CONSTRAINTS
- ACCEPTANCE (testable composition checks)
- SCOPE (in/out)
- ROUTING (handoffs, UID-only if present)
- TRACE_MIN

### O2 — COMPOSITION_EXEC_PLAN
Must contain:
- Form map (sections + timing + musical intent)
- Motif / hook plan (musical motif, not just lyric)
- Harmony logic (tonal center, cadence intent, tension/release)
- Melody contour guide (range, target notes, contour constraints)
- Contrast plan (where change happens and why)
- Repetition control (identity vs variation)
- Validation route + trace

Optional add-ons:
- O3 motif options (2–4) with identity anchors
- O4 progression sketch as function-level (no mix values)
- O5 melody guide for lead line (decision-level)

---

## CORE WORKFLOW (STEPS)

### STEP 0 — Apply boundaries
- Composer = musical decisions:
  - motif, harmony, melody contour, rhythm feel (high-level), form intent
- Not allowed:
  - EQ/LUFS/compression/limiter settings
  - legal certainty claims
  - prompt takeover if Prompt Architect is separate

### STEP 1 — Normalize intake
Create intake object:
- goal
- platform intent
- constraints
- mood/genre (if present)
- “must-feel” (1 line)
- “avoid” (1–3)

### STEP 2 — Set identity anchors
Decide 2–4 anchors that must persist:
- motif fingerprint (interval shape / rhythm cell / contour)
- tonal center or modal color
- hook placement window (e.g., <=10–12s)
- contrast rule (one lever changes at key points)

### STEP 3 — Build form map
Define:
- sections with approximate timings
- musical intent per section (build/release/reset)
- where hook motif first appears (<=10–12s target)

### STEP 4 — Design motif/hook
Produce motif plan:
- motif description (interval contour + rhythm cell)
- 1–2 variation rules (keep identity)
- recognition test:
  - “listener can hum after 1–2 repeats” / “recognizable within 10s”
If task asks: generate O3 motif options.

### STEP 5 — Harmony logic
Decision-level:
- tonal center / mode color
- tension ladder (where harmony increases/decreases tension)
- cadence intent (arrival points)
Avoid:
- exact chord voicings as “must”, unless needed conceptually.
If task asks: include O4 harmony map.

### STEP 6 — Melody contour guide
Decision-level:
- register (low/mid/high) per section
- contour constraints (rise/fall/plateau)
- target “must-hear” syllable-note alignment conceptually (no prompt takeover)
If task asks: include O5 melody guide.

### STEP 7 — Contrast & repetition control
Define:
- what stays stable (anchors)
- what changes and when (one lever change)
- anti-loop rule: variation token per repeat (rhythm swap / note swap / register shift)

### STEP 8 — Compile O1 + O2
- O1: clear, short, testable
- O2: executable plan with map + motif + harmony + melody + contrast + validation route

### STEP 9 — Pre-validate (quick rubric scan)
Ensure:
- acceptance tests exist
- hook placement window explicit
- no contradictions with constraints
- trace includes validations route

### STEP 10 — Route to checklists then gates
Deliver and instruct:
- run CHK set
- then run gates in order

If any fail later → PB-02 DIAGNOSE_AND_REWORK.

---

## EXIT CONDITIONS
READY when:
- O1/O2 complete
- anchors explicit
- acceptance is testable
- validation route + trace included
- no hard-limit violations

---

## REQUIRED UID REFERENCES
- CHECKLISTS:
  - UE.KB.SPC.PACK.COMPOSER.CHK.READINESS.001
  - UE.KB.SPC.PACK.COMPOSER.CHK.QUALITY.001
  - UE.KB.SPC.PACK.COMPOSER.CHK.COMPLIANCE.001
- GATES:
  - UE.KB.SPC.PACK.COMPOSER.GATE.CORE_QUALITY.001
  - UE.KB.SPC.PACK.COMPOSER.GATE.CONSISTENCY.001
- PLAYBOOK (repair):
  - UE.KB.SPC.PACK.COMPOSER.PB.DIAG_REWORK.001

---
END
