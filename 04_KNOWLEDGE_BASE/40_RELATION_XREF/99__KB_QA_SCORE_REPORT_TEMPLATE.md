# KB — QA SCORE CONSISTENCY REPORT TEMPLATE (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/99__KB_QA_SCORE_REPORT_TEMPLATE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: TEMPLATE
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.TPL.QA_SCORE_REPORT.099
OWNER: SYSTEM
ROLE: Compact template to record QA scoring consistency checks: test set, gates used, rubric, mismatch metrics, decision (PASS/REWORK/FAIL), and remediation plan.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created QA scoring consistency report template for standardized audits."
- REASON: "Consistency checks must produce comparable records; a template prevents missing fields and arbitrary reporting."
- IMPACT: "Faster calibration loops and clearer QA governance."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TPL.099

---

## 0) PURPOSE (KB)
Provide a copy-paste report format for QA scoring consistency runs.

---

## 1) REPORT (COPY)
QA_SCORE_CONSISTENCY_REPORT:
- REPORT_UID: QAS-YYYYMMDD-001
- DATE: YYYY-MM-DD
- DOMAIN:
- GATES_USED (UID-ONLY):
  - <uid>
- RUBRIC_USED:
  - UE.KB.STD.QA_RUBRIC.096
- TEST_SET:
  - T-01 | EXPECTED: PASS
  - T-02 | EXPECTED: FAIL
  - T-03 | EXPECTED: FAIL
  - T-04 | EXPECTED: PASS
  - T-05 | EXPECTED: REWORK

METRICS:
- MISMATCH_RATE: <percent>
- KEY_GATE_DISAGREEMENT: <count>
- AVG_AXIS_DELTA: <0..>

RESULT:
- PASS | REWORK | FAIL

TOP_DISAGREEMENTS:
- T-XX | EXPECTED: <label> | FOUND: <label> | WHY: <axis or gate mismatch>
- T-XX | ...

REMEDIATION PLAN:
- ACTION:
  - <add exemplars / tighten gate / clarify rubric axis>
- PRIORITY: P1/P2/P3
- DONE: YES/NO

RETEST:
- REQUIRED: YES/NO
- DATE: YYYY-MM-DD (optional)

RELATED_UIDS (UID-ONLY):
- <uid> | WHY: <calibration/exemplar set/standard>

---

## 2) RULES (STRICT)
- Gates are UID-only.
- Report must include metrics and a result.
- If RESULT != PASS, remediation plan is mandatory.

---

## 3) HARD FAIL CONDITIONS
FAIL IF:
- report omits metrics
- uses URL/PATH references
- RESULT is PASS but key gate disagreement > 0
- remediation missing when REWORK/FAIL

---

## 4) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.PROC.QA_SCORE_CONSIST.098 | WHY: protocol that this report documents
- XREF: UE.KB.STD.QA_RUBRIC.096 | WHY: rubric used for scoring
- XREF: UE.KB.PROC.DOMAIN_QA_CALIB.087 | WHY: calibration baseline for exemplars

--- END.
