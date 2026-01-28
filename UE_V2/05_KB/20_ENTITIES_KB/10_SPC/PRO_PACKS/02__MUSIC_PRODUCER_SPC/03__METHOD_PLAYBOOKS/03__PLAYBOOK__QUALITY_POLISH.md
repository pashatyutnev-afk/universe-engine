# 03__PLAYBOOK__QUALITY_POLISH — MUSIC_PRODUCER_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/02__MUSIC_PRODUCER_SPC/03__METHOD_PLAYBOOKS/03__PLAYBOOK__QUALITY_POLISH.md
SCOPE: KB — SPC Pro Pack — Music Producer — Playbook (Quality Polish)
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS / 03__METHOD_PLAYBOOKS
DOC_TYPE: PLAYBOOK
PLAYBOOK_TYPE: QUALITY_POLISH
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.MUSIC_PRODUCER.PB.QUALITY_POLISH.001
OWNER: SPC (Music Producer)
ROLE: Upgrade PASS outputs (7–8) to EXCELLENT (9–10) without scope drift or breaking consistency.

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Quality polish playbook initialized for Music Producer SPC pack."
- REASON: "Provide a safe method to improve output quality after passing."
- IMPACT: "Defines polish levers + rerun guard."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.MPROD.PB.POLISH.001

---

## GOAL
Улучшить качество выдачи (scanability, testability, contrast clarity),
не меняя сути решения и не вводя новых обязательств.

---

## ENTRY CONDITIONS
Use this playbook only if:
- outputs already PASS (checklists + gates)
- no open contradictions
- no missing required blocks

If not PASS → use PB-02 instead.

---

## POLISH PRINCIPLES
- No new scope:
  - polish cannot add new deliverables not requested by task.
- No engineering recipes:
  - keep producer at decision-level.
- Prefer clarity & structure upgrades over “more content”.

---

## POLISH LEVERS (CHOOSE 1–3 MAX)

### LVR-1 Scanability upgrade
- add short headings
- convert long paragraphs to bullets
- add “Section Map” as compact table-like list
- ensure O1/O2 are readable in 30 seconds

### LVR-2 Acceptance tests sharpen
- rewrite acceptance into measurable checks:
  - hook recognition test
  - phone intelligibility cue
  - contrast presence check
- add explicit PASS/REWORK triggers

### LVR-3 Contrast & arc clarity
- add explicit “peaks/dips” and purpose
- ensure hook B changes one lever only
- clarify break purpose (reset tension)

### LVR-4 Seat plan coherence
- add foreground/mid/background roles
- add 1–2 “masking risk” notes phrased as decisions:
  - “reduce mid density during must-hear phrase”
- remove vague “add more instruments” statements

### LVR-5 Variant safety (only if O3 exists)
- make identity anchors explicit
- add “allowed changes” list
- enforce one lever per variant

---

## POLISH WORKFLOW

### Step P1 — Select targets
- What is already strong (keep unchanged)
- What to improve (pick levers)

### Step P2 — Apply minimal edits
- Small edits only.
- Do not restructure the entire doc unless scanability is broken.

### Step P3 — Quick rubric bump check
Aim to lift:
- D1 clarity
- D3 structure
- D7 trace/validation
- D8 consistency
(and D9 if variants)

### Step P4 — Regression guard rerun
Mandatory rerun:
- UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.CONSISTENCY.001
If you changed structure/completeness heavily:
- also rerun UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.CORE_QUALITY.001

Record patch log snippet:
- AXIS_CHANGED: <clarity|structure|consistency|variants>
- BEFORE/PATCH/AFTER
- RERUN results

---

## STOP CONDITIONS
Stop polish if:
- it creates new contradictions
- it introduces scope drift
- it degrades acceptance testability

If problems appear → switch to PB-02.

---

## EXIT CONDITIONS
- EXCELLENT when:
  - scanable in 30s
  - acceptance is testable and crisp
  - consistency remains PASS
  - no scope drift

---

## REQUIRED UID REFERENCES
- RUBRIC:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.RUBRIC.001
- REGRESSION GUARD:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.REGRESSION_GUARD.001
- GATES:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.CORE_QUALITY.001
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.CONSISTENCY.001

---
END
