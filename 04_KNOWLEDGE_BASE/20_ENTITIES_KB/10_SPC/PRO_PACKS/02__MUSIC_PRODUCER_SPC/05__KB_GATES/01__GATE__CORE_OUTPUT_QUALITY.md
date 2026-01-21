# 01__GATE__CORE_OUTPUT_QUALITY — MUSIC_PRODUCER_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/02__MUSIC_PRODUCER_SPC/05__KB_GATES/01__GATE__CORE_OUTPUT_QUALITY.md
SCOPE: KB — SPC Pro Pack — Music Producer — Gate (Core Output Quality)
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS / 05__KB_GATES
DOC_TYPE: GATE
GATE_TYPE: CORE_OUTPUT_QUALITY
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.CORE_QUALITY.001
OWNER: SPC (Music Producer)
ROLE: Decide PASS/REWORK/FAIL for O1/O2 core quality using rubric thresholds + must-have blocks.

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Core output quality gate initialized for Music Producer SPC pack."
- REASON: "Enforce minimum producer quality standard."
- IMPACT: "Defines thresholds and repair routing."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.MPROD.GATE.CORE.001

---

## PREREQUISITE (MUST)
Checklists must be PASS:
- UE.KB.SPC.PACK.MUSIC_PRODUCER.CHK.READINESS.001
- UE.KB.SPC.PACK.MUSIC_PRODUCER.CHK.QUALITY.001
- UE.KB.SPC.PACK.MUSIC_PRODUCER.CHK.COMPLIANCE.001

If not PASS → STOP (do not run gate).

---

## INPUTS
- O1 PRODUCER_TASK_CARD
- O2 PRODUCTION_EXEC_PLAN
- Optional O3 VARIANTS_PLAN

---

## HARD FAIL TRIGGERS (FAIL)
If any true → FAIL:
- H1 Any compliance hard-limit violation present (engineering recipes/legal certainty)
- H2 O1 or O2 missing (core outputs absent)
- H3 Acceptance is non-testable AND cannot be fixed without rewriting most of doc (fundamental non-actionable)
- H4 Trace absent AND routing cannot be inferred (system cannot integrate)

---

## PASS THRESHOLDS (MUST)
### O1 thresholds
- P1 O1 includes testable acceptance (>=2 checks)
- P2 O1 includes scope boundaries + routing note if role split exists

### O2 thresholds
- P3 Section map has timings + intent
- P4 Hook plan contains must-hear + recognition test (<=10–12s target)
- P5 Seat plan is decision-level (foreground/mid/background + at least 1 risk note)
- P6 Acceptance triggers exist (PASS vs REWORK cues)
- P7 Validation route + trace exist

### Rubric thresholds (ROUGH)
- P8 No dimension below 6
- P9 Average >=7.0

---

## REWORK CONDITIONS
Return REWORK if:
- R1 any PASS threshold P1–P7 partially missing but fixable with one-axis patch
- R2 rubric average 6.0–6.9
- R3 one dimension = 5 due to clarity/structure/completeness

Axis recommendation:
- clarity (acceptance/testability)
- structure (map/scanability)
- completeness (missing required block)

---

## PASS CONDITIONS
Return PASS if:
- all P1–P7 satisfied
- rubric thresholds P8–P9 satisfied
- no hard fail triggers

---

## OUTPUT (MANDATORY)
- GATE_UID: UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.CORE_QUALITY.001
- DECISION: <PASS|REWORK|FAIL>
- FAIL_REASONS:
  - <list>
- AXIS_RECOMMENDATION (if REWORK):
  - <one axis>
- RERUN_SET (after patch):
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.CORE_QUALITY.001
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.CONSISTENCY.001

---

## CALIBRATION ANCHORS
- GOOD case:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.CASE.GOOD.001
- BORDERLINE case:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.CASE.BORDERLINE.001
- BAD case:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.CASE.BAD.001

---

## REQUIRED UID REFERENCES
- RUBRIC:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.RUBRIC.001
- PLAYBOOK (repair):
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.PB.DIAG_REWORK.001

---
END
