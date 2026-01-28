# TPL QA — ENTITY TEMPLATE (CANON)
FILE: 03_SYSTEM_ENTITIES/01_TPL__TEMPLATES/60__TPL__QA.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: TEMPLATES (TPL)
DOC_TYPE: TEMPLATE
TEMPLATE_TYPE: ENTITY_QA
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.TPL.QA.001
OWNER: SYSTEM
ROLE: Canonical template to create QA checks/entities/issues (fast tests, human evaluation, and regression guard)

CHANGE_NOTE:
- DATE: 2026-01-11
- TYPE: MAJOR
- SUMMARY: "Created QA template: check definition, scoring, pass/fail, issue format, and integration notes."
- REASON: "QA must be consistent and usable as pipeline gates."
- IMPACT: "Quality evaluation becomes repeatable."
- CHANGE_ID: UE.CHG.2026-01-11.TPL.QA.001

---

## 0) PURPOSE
This template creates QA artifacts inside:
`03_SYSTEM_ENTITIES/60_QA__QUALITY/...`

QA differs from VAL:
- VAL = deterministic rule validation
- QA = human/experiential tests, quick panels, regression and taste checks

---

## 1) TARGET
TARGET_CLASS: QA  
TARGET_FOLDER: `03_SYSTEM_ENTITIES/60_QA__QUALITY/`  
REQUIRED_INDEX_OWNER (GLOBAL): `03_SYSTEM_ENTITIES/60_QA__QUALITY/02__INDEX_ALL_QA`  
REQUIRED_FAMILY_README: `03_SYSTEM_ENTITIES/60_QA__QUALITY/<FAMILY>/00__README__...` (if used)

---

## 2) STRUCTURE SKELETON (COPY BELOW INTO NEW QA FILE)
> IMPORTANT: keep the section order exactly.
> QA must be executable as a checklist without extra context.

--- CUT HERE ---

# <QA TITLE> — QA (QUALITY)
FILE: 03_SYSTEM_ENTITIES/60_QA__QUALITY/<FAMILY_PATH>/NN__<QA_NAME>_QA.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: QA (QUALITY)
DOC_TYPE: QA
QA_TYPE: <CHECK|ENTITY|ISSUE|PANEL|REGRESSION>
LEVEL: <L1|L2|L3>
STATUS: <DRAFT|ACTIVE|DEPRECATED|ARCHIVED>
LOCK: <OPEN|FIXED>
VERSION: <X.Y.Z>
UID: <UE.QA.<FAMILY>.<NAME>.<NNN>>
OWNER: SYSTEM
ROLE: <One-line: what this QA checks and why>

CHANGE_NOTE:
- DATE: <YYYY-MM-DD>
- TYPE: <MAJOR|MINOR|PATCH>
- SUMMARY: "<what changed>"
- REASON: "<why>"
- IMPACT: "<impact>"
- CHANGE_ID: <UE.CHG.YYYY-MM-DD....>

---

## 0) QA INTENT (LAW)
- WHAT IS TESTED: <artifact/output>
- WHY IT MATTERS: <impact on audience/quality>
- BLOCKING: <YES/NO> (if YES, ORC must not proceed on FAIL)

---

## 1) TEST SETUP (MANDATORY)
- TEST CONTEXT: <where/when this is executed>
- REQUIRED INPUTS: <what is needed to run the QA>
- DURATION: <how long to test / how many seconds for music tests>
- SAMPLE SIZE: <how many variants / how many listeners (if applicable)>

---

## 2) TEST PROCEDURE (STEPS)
1) <step>
2) <step>
3) <step>

---

## 3) SCORING / PASS FAIL (MANDATORY)
### 3.1 Score scale
- SCALE: <e.g., 0–10 or PASS/FAIL + notes>

### 3.2 PASS CONDITIONS
- <condition 1>
- <condition 2>

### 3.3 FAIL CONDITIONS
- <condition 1>
- <condition 2>

### 3.4 FIX GUIDANCE
- If FAIL: <what to change first>
- If borderline: <what to improve>

---

## 4) QA REPORT FORMAT (STANDARD)
QA_REPORT:
- QA_UID: <UID>
- RESULT: PASS | FAIL | BORDERLINE
- SCORE: <value or N/A>
- SUMMARY: "<1–3 lines>"
- KEY_OBSERVATIONS:
  - "<obs 1>"
  - "<obs 2>"
- FIX_RECOMMENDATIONS:
  - "<fix 1>"
  - "<fix 2>"
- NEXT_ACTION:
  - "<what to do next in pipeline>"

---

## 5) INTEGRATION (WHERE USED)
- Typical ORC stages that must call this QA:
  - <stage label>
- Connected CTL/VAL:
  - CTL: <RAW optional>
  - VAL: <RAW optional>

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: <OPEN|FIXED>

--- END.

--- CUT HERE ---

---

## 3) INDEX + REGISTRATION CHECKLIST (MANDATORY)
When a new QA file is created:
1) Add RAW link to `60_QA__QUALITY/02__INDEX_ALL_QA`
2) Ensure correct FAMILY folder + numbering `NN__`
3) If BLOCKING=YES → ORC must reference this QA explicitly as a gate
4) Ensure FIX GUIDANCE exists (no пустые “плохо/норм”)

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
