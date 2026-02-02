FILE: UE_V2/03_ENT/50_VAL_ENT/00_TEMPLATES_VAL_ENT/01__TPL__VAL_ENTITY__VAL__ENT.md
SCOPE: UE_V2 / 03_ENT / 50_VAL_ENT / 00_TEMPLATES_VAL_ENT
DOC_TYPE: TPL
DOMAIN: TPL_VAL_ENT
UID: UE.V2.ENT.TPL.VAL_ENTITY.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: VAL_ENT
NAV_RULE: Template doc contains no RAW

---

## [M] TEMPLATE_NAME
VAL_ENTITY_TEMPLATE

## [M] PURPOSE
Шаблон для валидатора (VAL): входы/выходы, проверки, требования к evidence, матрица решений, нарушения и гейты.
Использовать для любых `__VAL__ENT.md` в реалмах VAL (MUS/VID/WEB/DOC/VAL_ENG/LIB).

---

# [T] FILE HEADER (copy and fill)
FILE: <PATH_TO_TARGET_DOC>
SCOPE: <SCOPE>
DOC_TYPE: VAL_ENTITY
DOMAIN: <MUS_VAL|VID_VAL|WEB_VAL|DOC_VAL|VAL_ENG|LIB_VAL|...>
UID: <UID>
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 0000-00-00
UPDATED: 0000-00-00
OWNER: VAL_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: <SHORT_NAME>
- ENTITY_CLASS: VAL
- UID: <UID>
- STATUS: ACTIVE|DRAFT|DEPRECATED
- OWNER: VAL_ENT
- VERSION: 1.0.0

## [M] PURPOSE
<1–2 строки: что валидирует и зачем>

## [M] SCOPE
- TARGET_DOMAIN: <MUS|VID|WEB|DOC|MULTI>
- APPLIES_TO: [<artifact_1>, <artifact_2>]
- NON_GOALS: [<what it does not validate>]

## [M] INPUTS / OUTPUTS
- Inputs:
  - <TOKEN_A>: <one-line meaning>
  - <TOKEN_B>: <one-line meaning>
- Outputs:
  - VAL_DECISION: PASS|FAIL|WARN|ASK
  - VAL_FINDINGS: [<short finding items>]
  - REQUIRED_FIXES: [<minimal actionable fixes>]
  - VIOLATIONS: [<violation ids>]
  - FAIL_CODE?: <optional>

## [M] CHECKS (deterministic)
- C1: <check> (Evidence: <required evidence>)
- C2: <check> (Evidence: <required evidence>)
- C3: <check> (Evidence: <required evidence>)

## [M] EVIDENCE_REQUIREMENTS
- E1: <what must be present to claim PASS>
- E2: <what must be present to claim FAIL>
- E3: <what is allowed as “assumption” vs what must be explicit>

## [M] DECISION_MATRIX
- IF <condition> -> PASS
- IF <condition> -> WARN (+ REQUIRED_FIXES)
- IF <condition> -> ASK (+ REQUIRED_INPUTS)
- IF <condition> -> FAIL (+ FAIL_CODE + REQUIRED_FIXES + VIOLATIONS)

## [M] VIOLATIONS (used by this validator)
- V1: <violation_id> — <one line meaning>
- V2: <violation_id> — <one line meaning>

## [M] FAIL_CODES
- UE.FAIL.RULE_VIOLATION
- UE.FAIL.GATE_FAIL
- UE.FAIL.INPUT_ABSENT
- <local_fail_code_1>

## [M] INTERFACES (RAW only)
- Entry points (RAW):
- Dependencies (RAW):

## [M] KB SCOPE
- KB Inputs: [<allowed knowledge>]
- KB Outputs: [<validation report tokens>]
- KB Boundaries: [no guessing, no repo edits]
- KB RAW refs: []

## [M] GATES
- PASS if:
  - <conditions>
- FAIL if:
  - <conditions>

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, CTL_ENT, QA_ENT, SPC_ENT]
- Handoff rules:
  - PASS -> continue
  - WARN -> fix loop
  - FAIL -> stop + REQUIRED_FIXES

## [M] CHANGELOG
- 0000-00-00: v1.0.0 init
