# 00__README__CASES — MUSIC_PRODUCER_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/02__MUSIC_PRODUCER_SPC/06__CASE_LIBRARY/00__README__CASES.md
SCOPE: KB — SPC Pro Pack — Music Producer — Case Library (README)
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: README
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.MUSIC_PRODUCER.CASES.README.001
OWNER: SPC (Music Producer)
ROLE: Calibrated examples used to train scoring, gates, and regression guard for producer outputs.

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Case library README initialized for Music Producer SPC pack."
- REASON: "Provide concrete pass/fail anchors for arrangement and energy-curve decisions."
- IMPACT: "Enables consistent gate decisions and rubric calibration."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.MPROD.CASES.README.001

---

## PURPOSE
Cases define:
- what “GOOD / BAD / BORDERLINE / EDGE” means for producer outputs
- which failures map to which axis
- what minimal patch looks like (one-axis)

---

## HOW TO USE
- Use cases as calibration anchors for:
  - rubric scoring
  - gate decisions
  - regression guard reruns
- Extract pattern + apply to current task.
- Never copy instrumentation lists blindly; keep role-based thinking.

---

## CASE SET (THIS PACK)
- GOOD:
  - FILE: 01__CASE__GOOD.md
  - UID: UE.KB.SPC.PACK.MUSIC_PRODUCER.CASE.GOOD.001
- BAD:
  - FILE: 02__CASE__BAD.md
  - UID: UE.KB.SPC.PACK.MUSIC_PRODUCER.CASE.BAD.001
- BORDERLINE:
  - FILE: 03__CASE__BORDERLINE.md
  - UID: UE.KB.SPC.PACK.MUSIC_PRODUCER.CASE.BORDERLINE.001
- EDGE:
  - FILE: 04__CASE__EDGE_001.md
  - UID: UE.KB.SPC.PACK.MUSIC_PRODUCER.CASE.EDGE.001

---

## REQUIRED FIELDS PER CASE
- CONTEXT
- INPUTS (MIN)
- OUTPUTS (O1/O2 excerpts)
- CHECKLIST/GATE OUTCOME
- WHY
- AXIS (single axis)
- MIN_PATCH
- RERUN_SET

---

## REQUIRED UID REFERENCES
- RUBRIC:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.RUBRIC.001
- GATES:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.CORE_QUALITY.001
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.CONSISTENCY.001
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.EDGE_CASES.001
- REGRESSION:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.REGRESSION_GUARD.001

---
END
