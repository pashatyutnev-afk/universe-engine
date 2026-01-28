# KB — QA SCORING CONSISTENCY PROTOCOL (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/98__KB_QA_SCORING_CONSISTENCY_PROTOCOL.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: PROTOCOL
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.PROC.QA_SCORE_CONSIST.098
OWNER: SYSTEM
ROLE: Deterministic protocol to measure and improve QA scoring consistency across evaluators/entities using rubrics and exemplar calibration: repeated scoring, drift detection, discrepancy analysis, and remediation actions.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created QA scoring consistency protocol to reduce evaluator drift and stabilize PASS/FAIL decisions."
- REASON: "Without consistency, QA and certification become subjective; this protocol enforces stable scoring behavior."
- IMPACT: "More reliable QA scores and fewer disputes/regressions."
- CHANGE_ID: UE.CHG.2026-01-14.KB.PROC.098

---

## 0) PURPOSE (KB)
Ensure QA scoring is consistent:
- same gate + rubric applied yields similar scores
- drift is detected and corrected
- exemplar sets are used for calibration

---

## 1) INPUTS / OUTPUTS
INPUTS:
- Domain
- Rubric card template
- Key gate(s) and exemplar sets
- A set of outputs to score (test cases)

OUTPUTS:
- Consistency report (PASS/REWORK/FAIL)
- Drift metrics (variance, mismatch rate)
- Remediation actions (recalibrate, tighten gate, add examples)

---

## 2) CONSISTENCY TEST SET
Minimum test set:
- 5 outputs:
  - 2 expected PASS
  - 2 expected FAIL
  - 1 borderline REWORK

All test outputs must have:
- known gate linkage
- known expected label (from calibration set or prior certification records)

---

## 3) PROTOCOL (DETERMINISTIC)
Step 1: Calibration warm-up
- Review exemplar sets for the key gate(s).
- Confirm current calibration PASS status.

Step 2: Independent scoring rounds
- Each evaluator/entity scores all 5 outputs using:
  - same gates
  - same rubric axes
- Record:
  - axis scores
  - result PASS/REWORK/FAIL
  - key gate fail flag

Step 3: Compare results
Compute:
- label mismatch rate (% outputs where result differs)
- average score delta per axis
- key-gate disagreement count

Step 4: Diagnose discrepancies
If mismatch exists:
- identify which axis causes the drift
- check if gate criteria are ambiguous
- check if exemplars are weak/unclear

Step 5: Remediation
Choose one or more:
- add/curate exemplars (GOOD/BAD/BORDERLINE)
- tighten gate definition (more measurable criteria)
- update rubric notes/axis definitions
- run calibration protocol again

Step 6: Re-test
- Repeat scoring for the outputs after remediation.

---

## 4) PASS/REWORK/FAIL THRESHOLDS
PASS IF:
- mismatch rate ≤ 10%
- key gate disagreement = 0
- average axis delta ≤ 1.0

REWORK IF:
- mismatch rate 10–25% OR
- axis delta 1.0–2.0 OR
- borderline case inconsistent

FAIL IF:
- mismatch rate > 25% OR
- key gate disagreement > 0 OR
- axis delta > 2.0

---

## 5) OUTPUT TEMPLATE (COPY)
QA_SCORING_CONSISTENCY_REPORT:
- DATE: YYYY-MM-DD
- DOMAIN:
- GATES_USED:
  - <uid>
- RUBRIC_UID: UE.KB.STD.QA_RUBRIC.096
- TEST_SET:
  - OUTPUT_ID: T-01 | EXPECTED: PASS
  - OUTPUT_ID: T-02 | EXPECTED: FAIL
  - ...
- METRICS:
  - MISMATCH_RATE:
  - KEY_GATE_DISAGREEMENT:
  - AVG_AXIS_DELTA:
- RESULT: PASS/REWORK/FAIL
- REMEDIATION:
  - <action>
- RETEST_REQUIRED: YES/NO

---

## 6) HARD FAIL CONDITIONS
FAIL IF:
- scoring performed without gate linkage
- evaluators use different rubric axes
- key gate fail flags disagree (gate application inconsistent)
- results are “averaged” without resolving criterion ambiguity

---

## 7) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.STD.QA_RUBRIC.096 | WHY: rubric standard for consistent scoring
- XREF: UE.KB.TPL.QA_RUBRIC_CARD.097 | WHY: common scoring format
- XREF: UE.KB.PROC.DOMAIN_QA_CALIB.087 | WHY: exemplar calibration baseline
- XREF: UE.KB.RULE.GATE_EXAMPLE_BIND.090 | WHY: key gates require exemplars

--- END.
