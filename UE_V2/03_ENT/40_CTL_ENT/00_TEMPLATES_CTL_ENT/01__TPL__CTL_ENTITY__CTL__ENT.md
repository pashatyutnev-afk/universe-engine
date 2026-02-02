FILE: UE_V2/03_ENT/40_CTL_ENT/00_TEMPLATES_CTL_ENT/01__TPL__CTL_ENTITY__CTL__ENT.md
SCOPE: UE_V2 / 03_ENT / 40_CTL_ENT / 00_TEMPLATES_CTL_ENT
DOC_TYPE: TPL
DOMAIN: TPL_CTL_ENT
UID: UE.V2.ENT.TPL.CTL_ENTITY.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: CTL_ENT
NAV_RULE: Template doc contains no RAW

---

## [M] TEMPLATE_NAME
CTL_ENTITY_TEMPLATE

## [M] PURPOSE
Шаблон для CTL контроллера: правила, входы/выходы, матрица решений, нарушения, гейты.
Использовать для любых `__CTL__ENT.md` в реалмах CTL (MUS/VID/WEB/DOC/LIB).

---

# [T] FILE HEADER (copy and fill)
FILE: <PATH_TO_TARGET_DOC>
SCOPE: <SCOPE>
DOC_TYPE: CTL_ENTITY
DOMAIN: <MUS_CTL|VID_CTL|WEB_CTL|DOC_CTL|LIB_CTL|...>
UID: <UID>
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 0000-00-00
UPDATED: 0000-00-00
OWNER: CTL_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: <SHORT_NAME>
- ENTITY_CLASS: CTL
- UID: <UID>
- STATUS: ACTIVE|DRAFT|DEPRECATED
- OWNER: CTL_ENT
- VERSION: 1.0.0

## [M] PURPOSE
<1–2 строки: что контролирует и зачем>

## [M] SCOPE
- TARGET_DOMAIN: <MUS|VID|WEB|DOC|MULTI>
- APPLIES_TO: [<stage_or_artifact_1>, <stage_or_artifact_2>]
- NON_GOALS: [<what it does not control>]

## [M] INPUTS / OUTPUTS
- Inputs:
  - <TOKEN_A>: <one-line meaning>
  - <TOKEN_B>: <one-line meaning>
- Outputs:
  - CTL_DECISION: PASS|FAIL|WARN|ASK
  - CTL_FINDINGS: [<short finding items>]
  - REQUIRED_FIXES: [<minimal actionable fixes>]
  - FAIL_CODE?: <optional>

## [M] RULESET (rules as bullets, no prose)
- R1: <rule>
- R2: <rule>
- R3: <rule>

## [M] DECISION_MATRIX
- IF <condition> -> PASS
- IF <condition> -> WARN (+ REQUIRED_FIXES)
- IF <condition> -> ASK (+ REQUIRED_INPUTS)
- IF <condition> -> FAIL (+ FAIL_CODE + REQUIRED_FIXES)

## [M] VIOLATIONS (taxonomy used by this CTL)
- V1: <violation_id> — <one line meaning>
- V2: <violation_id> — <one line meaning>

## [M] FAIL_CODES
- UE.FAIL.RULE_VIOLATION
- UE.FAIL.GATE_FAIL
- UE.FAIL.INPUT_ABSENT
- <local_fail_code_1>
- <local_fail_code_2>

## [M] INTERFACES (RAW only)
- Entry points (RAW):
- Dependencies (RAW):

## [M] KB SCOPE
- KB Inputs: [<what knowledge can be used>]
- KB Outputs: [<what is produced as KB-safe outputs>]
- KB Boundaries: [<what must not be assumed/used>]
- KB RAW refs: []

## [M] GATES (pass/fail)
- PASS if:
  - <conditions>
- FAIL if:
  - <conditions>

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, VAL_ENT, QA_ENT, SPC_ENT]
- Handoff rules:
  - PASS -> <next module>
  - WARN -> <fix loop>
  - FAIL -> <block + required fixes>

## [M] CHANGELOG
- 0000-00-00: v1.0.0 init
