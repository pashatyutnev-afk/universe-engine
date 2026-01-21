# 01__GATE__CORE_OUTPUT_QUALITY — COMPOSER_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/03__COMPOSER_SPC/05__KB_GATES/01__GATE__CORE_OUTPUT_QUALITY.md
SCOPE: KB — SPC Pro Pack — Composer — Gate (Core Output Quality)
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS / 05__KB_GATES
DOC_TYPE: GATE
GATE_TYPE: CORE_OUTPUT_QUALITY
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.COMPOSER.GATE.CORE_QUALITY.001
OWNER: SPC (Composer)
ROLE: Decide PASS/REWORK/FAIL for O1/O2 core quality using rubric thresholds + composition must-have blocks.

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Core output quality gate initialized for Composer SPC pack."
- REASON: "Enforce minimum composition plan quality standard."
- IMPACT: "Defines thresholds and repair routing."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.COMPOSER.GATE.CORE.001

---

## PREREQUISITE (MUST)
Checklists must be PASS:
- UE.KB.SPC.PACK.COMPOSER.CHK.READINESS.001
- UE.KB.SPC.PACK.COMPOSER.CHK.QUALITY.001
- UE.KB.SPC.PACK.COMPOSER.CHK.COMPLIANCE.001

If not PASS → STOP.

---

## INPUTS
- O1 COMPOSER_TASK_CARD
- O2 COMPOSITION_EXEC_PLAN
- Optional O3 motif/harmony/melody add-ons (task-driven)

---

## HARD FAIL TRIGGERS (FAIL)
If any true → FAIL:
- H1 Any compliance hard-limit violation present (engineering recipes/legal certainty)
- H2 O1 or O2 missing (core outputs absent)
- H3 Acceptance is non-testable AND cannot be fixed without rewriting most of doc
- H4 Trace absent AND routing cannot be inferred

---

## PASS THRESHOLDS (MUST)

### O1 thresholds
- P1 O1 includes testable acceptance (>=2 checks)
- P2 O1 includes scope boundaries + routing note if role split exists

### O2 thresholds (composition-specific)
- P3 Form map has timings + musical intent per section
- P4 Hook/motif plan includes fingerprint + recognition test (<=10–12s placement or explicit)
- P5 Harmony logic includes tonal center/modal color + tension/release notes
- P6 Melody contour guide exists OR explicitly N/A (if no lead line)
- P7 Contrast plan exists (peaks/dips + one-lever change)
- P8 Repetition control rules exist (identity vs variation)
- P9 Validation route + trace exist

### Rubric thresholds (ROUGH)
- P10 No dimension below 6
- P11 Average >=7.0

---

## REWORK CONDITIONS
Return REWORK if:
- R1 any PASS threshold P1–P9 partially missing but fixable with one-axis patch
- R2 rubric average 6.0–6.9
- R3 one dimension = 5 due to clarity/structure/motif/harmony/melody

Axis recommendation:
- motif / harmony / melody / structure / clarity / consistency

---

## PASS CONDITIONS
Return PASS if:
- all P1–P9 satisfied
- rubric thresholds P10–P11 satisfied
- no hard fail triggers

---

## OUTPUT (MANDATORY)
- GATE_UID: UE.KB.SPC.PACK.COMPOSER.GATE.CORE_QUALITY.001
- DECISION: <PASS|REWORK|FAIL>
- FAIL_REASONS:
  - <list>
- AXIS_RECOMMENDATION (if REWORK):
  - <one axis>
- RERUN_SET (after patch):
  - UE.KB.SPC.PACK.COMPOSER.GATE.CORE_QUALITY.001
  - UE.KB.SPC.PACK.COMPOSER.GATE.CONSISTENCY.001

---

## CALIBRATION ANCHORS
- GOOD: UE.KB.SPC.PACK.COMPOSER.CASE.GOOD.001
- BORDERLINE: UE.KB.SPC.PACK.COMPOSER.CASE.BORDERLINE.001
- BAD: UE.KB.SPC.PACK.COMPOSER.CASE.BAD.001

---

## REQUIRED UID REFERENCES
- RUBRIC:
  - UE.KB.SPC.PACK.COMPOSER.RUBRIC.001
- PLAYBOOK (repair):
  - UE.KB.SPC.PACK.COMPOSER.PB.DIAG_REWORK.001

---
END
