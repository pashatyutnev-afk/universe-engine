# TPL VALIDATOR — ENTITY TEMPLATE (CANON)
FILE: 03_SYSTEM_ENTITIES/01_TPL__TEMPLATES/50__TPL__VALIDATOR.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: TEMPLATES (TPL)
DOC_TYPE: TEMPLATE
TEMPLATE_TYPE: ENTITY_VALIDATOR
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.TPL.VAL.001
OWNER: SYSTEM
ROLE: Canonical template to create any VAL Validator file (check definition + fail/fix + violation reporting)

CHANGE_NOTE:
- DATE: 2026-01-11
- TYPE: MAJOR
- SUMMARY: "Created VAL validator template: explicit checks, fail conditions, fix procedure, and violation output format."
- REASON: "Validators must be deterministic gates inside pipelines."
- IMPACT: "Validation becomes auditable and repeatable."
- CHANGE_ID: UE.CHG.2026-01-11.TPL.VAL.001

---

## 0) PURPOSE
This template creates a VAL Validator file:
`03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/<FAMILY>/NN__<VALIDATOR_NAME>_VAL`

Validators:
- check outputs against rules/policies
- produce PASS/FAIL and a structured violation report
- can act as blocking gates inside ORC pipelines

---

## 1) TARGET
TARGET_CLASS: VAL  
TARGET_FOLDER: `03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/`  
REQUIRED_INDEX_OWNER (GLOBAL): `03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/02__INDEX_ALL_VALIDATORS`  
REQUIRED_FAMILY_README: `03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/<FAMILY>/00__README__...` (if family uses a README)

---

## 2) STRUCTURE SKELETON (COPY BELOW INTO NEW VAL FILE)
> IMPORTANT: keep the section order exactly.
> Validator must be testable and produce a consistent violation report.

--- CUT HERE ---

# <VALIDATOR TITLE> — VALIDATOR (VAL)
FILE: 03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/<FAMILY_PATH>/NN__<VALIDATOR_NAME>_VAL.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: VALIDATORS (VAL)
DOC_TYPE: VALIDATOR
VALIDATOR_TYPE: <MUSIC|NARRATIVE|VISUAL|PIPELINE|GOVERNANCE|OTHER>
LEVEL: <L1|L2|L3>
STATUS: <DRAFT|ACTIVE|DEPRECATED|ARCHIVED>
LOCK: <OPEN|FIXED>
VERSION: <X.Y.Z>
UID: <UE.VAL.<FAMILY>.<NAME>.<NNN>>
OWNER: SYSTEM
ROLE: <One-line: what this validator checks>

CHANGE_NOTE:
- DATE: <YYYY-MM-DD>
- TYPE: <MAJOR|MINOR|PATCH>
- SUMMARY: "<what changed>"
- REASON: "<why>"
- IMPACT: "<impact>"
- CHANGE_ID: <UE.CHG.YYYY-MM-DD....>

---

## 0) VALIDATION INTENT (LAW)
- WHAT IT VALIDATES: <artifact/output>
- WHY IT MATTERS: <risk prevented>
- BLOCKING: <YES/NO> (if YES, it is a gate)

---

## 1) INPUTS / OUTPUTS (VALIDATOR CONTRACT)
CONSUMES:
- <artifact(s) to validate>

PRODUCES:
- PASS/FAIL
- VIOLATION_REPORT (structured)

DEPENDS_ON:
- [] OR
- - <RAW references (optional)>

OUTPUT_TARGET:
- <where the violation report is recorded (log/pack/path)>

---

## 2) CHECKLIST (MANDATORY)
List checks as strict items.

### Check 01 — <NAME>
RULE:
- <what must be true>

CHECK:
- <how to check>

FAIL CONDITION:
- <what counts as fail>

FIX PROCEDURE:
- <how to fix>

SEVERITY:
- <S0|S1|S2|S3>

(repeat)

---

## 3) VIOLATION REPORT FORMAT (STANDARD)
Return violations using this structure:

VIOLATION_REPORT:
- VALIDATOR_UID: <UID>
- RESULT: PASS | FAIL
- SUMMARY: "<1–3 lines>"
- FAIL_ITEMS:
  - ID: <CHECK_01>
    SEVERITY: <S0..S3>
    WHAT: "<what failed>"
    WHERE: "<where in artifact>"
    WHY: "<why it matters>"
    FIX: "<how to fix>"
- NOTES:
  - "<optional notes>"
- NEXT_ACTION:
  - "<what to do next>"

---

## 4) EDGE CASES (OPTIONAL)
- <edge case>
- <how to handle>

---

## 5) INTEGRATION (WHERE USED)
- Typical ORC stages that call this validator:
  - <stage label>
- Typical CTL policies connected:
  - <RAW optional>

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: <OPEN|FIXED>

--- END.

--- CUT HERE ---

---

## 3) INDEX + REGISTRATION CHECKLIST (MANDATORY)
When a new VAL file is created:
1) Add RAW link to `50_VAL__VALIDATORS/02__INDEX_ALL_VALIDATORS`
2) Ensure correct FAMILY folder + numbering `NN__`
3) Ensure ORC gates reference this validator explicitly
4) If validator is BLOCKING=YES → ensure there is a clear FIX procedure

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
