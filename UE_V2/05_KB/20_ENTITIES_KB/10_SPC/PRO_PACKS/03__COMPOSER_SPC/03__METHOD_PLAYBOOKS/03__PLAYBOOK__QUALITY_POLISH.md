# 03__PLAYBOOK__QUALITY_POLUM — COMPOSER_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/03__COMPOSER_SPC/03__METHOD_PLAYBOOKS/03__PLAYBOOK__QUALITY_POLISH.md
SCOPE: KB — SPC Pro Pack — Composer — Playbook (Quality Polish)
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS / 03__METHOD_PLAYBOOKS
DOC_TYPE: PLAYBOOK
PLAYBOOK_TYPE: QUALITY_POLISH
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.COMPOSER.PB.QUALITY_POLISH.001
OWNER: SPC (Composer)
ROLE: Upgrade PASS composition plan (7–8) to excellent (9–10) by strengthening motif memorability, harmonic logic, contrast, and executability.

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Quality polish playbook initialized for Composer SPC pack."
- REASON: "Provide safe post-pass upgrades without identity drift."
- IMPACT: "Defines polish levers + rerun guard."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.COMPOSER.PB.POLISH.001

---

## ENTRY CONDITIONS
Use this playbook only if:
- checklists PASS
- gates PASS (at least CORE + CONSISTENCY)
- no open contradictions / no missing required blocks

If not PASS → use PB-02.

---

## POLISH PRINCIPLES
- No scope drift (no new deliverables not requested)
- Keep identity anchors stable
- No engineering recipes (mix/master settings)
- Prefer musical clarity upgrades over “more complexity”

---

## POLISH LEVERS (CHOOSE 1–3 MAX)

### LVR-1 Motif memorability boost
- tighten motif fingerprint (interval contour + rhythm cell)
- add “hummability” test
- ensure motif repeats with controlled variation (1–2 rules)

### LVR-2 Harmony narrative clarity
- clarify tonal center / modal color
- define tension ladder and arrival points
- ensure harmony supports hook reveal and contrast dips

### LVR-3 Melody contour sharpening
- set register per section
- define contour constraints (rise/fall) and targets
- avoid “random walk” feel by adding anchor notes

### LVR-4 Contrast / pacing refinement
- make “peaks/dips” explicit in form map
- ensure one lever change at contrast points
- reduce sameness between sections

### LVR-5 Scanability / executability
- restructure O2 so it’s readable in 30 seconds
- convert vague descriptions to concrete decisions + tests
- add minimal trace clarity (what to run next)

---

## POLISH WORKFLOW

### Step P1 — Choose targets
- Keep: what already passes
- Improve: choose levers

### Step P2 — Apply minimal edits
- Small edits only
- Don’t rewrite everything

### Step P3 — Quick rubric bump scan
Aim to lift:
- clarity
- structure
- motif/harmony/melody adequacy
- consistency

### Step P4 — Regression rerun (mandatory)
- rerun CONSISTENCY gate:
  - UE.KB.SPC.PACK.COMPOSER.GATE.CONSISTENCY.001
If you changed musical core heavily:
- also rerun CORE_OUTPUT_QUALITY:
  - UE.KB.SPC.PACK.COMPOSER.GATE.CORE_QUALITY.001

Record:
- AXIS_CHANGED (should be limited to polish levers)
- BEFORE/PATCH/AFTER
- RERUN results

---

## STOP CONDITIONS
Stop polish if:
- it introduces contradictions
- it changes anchors
- it inflates scope
If any occurs → switch to PB-02.

---

## EXIT CONDITIONS
EXCELLENT when:
- motif is clearly recognizable + testable
- harmony/melody plans are executable and consistent
- contrast is explicit and meaningful
- rerun consistency passes

---

## REQUIRED UID REFERENCES
- RUBRIC:
  - UE.KB.SPC.PACK.COMPOSER.RUBRIC.001
- REGRESSION GUARD:
  - UE.KB.SPC.PACK.COMPOSER.REGRESSION_GUARD.001
- GATES:
  - UE.KB.SPC.PACK.COMPOSER.GATE.CORE_QUALITY.001
  - UE.KB.SPC.PACK.COMPOSER.GATE.CONSISTENCY.001

---
END
