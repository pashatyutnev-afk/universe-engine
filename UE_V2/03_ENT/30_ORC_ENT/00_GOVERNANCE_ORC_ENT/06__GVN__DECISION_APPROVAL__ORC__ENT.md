FILE: UE_V2/03_ENT/30_ORC_ENT/00_GOVERNANCE_ORC_ENT/06__GVN__DECISION_APPROVAL__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 00_GOVERNANCE_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: GVN_ORC_ENT
UID: UE.V2.ENT.ORC.GVN.DECISION_APPROVAL.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: GVN_DECISION_APPROVAL
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.GVN.DECISION_APPROVAL.001
- STATUS: ACTIVE
- OWNER: ORC_ENT
- VERSION: 1.0.0
- CREATED: 2026-02-02
- UPDATED: 2026-02-02

## [M] PURPOSE
Решает, требуется ли approval/эскалация для governance-операции.
Формирует DECISION_TOKEN и условия продолжения.

## [M] CAPABILITIES (what it can produce)
- Produces: [DECISION_TOKEN, APPROVAL_REQUIRED?, FAIL_CODE?]
- Edits: [] (MODE REPO)
- Never:
  - не утверждает изменения за пользователя
  - не продолжает прогон при required approval без явного подтверждения во внешнем контуре

## [M] INPUTS / OUTPUTS
- Inputs:
  - CHANGE_ENVELOPE
  - RISK_REPORT
  - GOVN_TASK_TOKEN
- Outputs:
  - DECISION_TOKEN: choice + why + impact + gates + next
  - APPROVAL_REQUIRED?: true|false
  - FAIL_CODE?: UE.FAIL.APPROVAL_REQUIRED | UE.FAIL.GATE_FAIL

## [M] INTERFACES (RAW only)
- Entry points (RAW):
- Dependencies (RAW):

## [M] KB SCOPE
- KB Inputs: [decision policy, risk thresholds, required logs]
- KB Outputs: [decision токены]
- KB Boundaries: [не принимать решение “за автора”; только формализовать требование]
- KB RAW refs: []

## [M] GATES (pass/fail)
- PASS if:
  - решение формализовано и совместимо с риском/режимом
- FAIL if:
  - approval требуется и отсутствует подтверждение
  - gates не могут быть выполнены в рамках режима

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, QA, CTL]
- Handoff rules:
  - Передаёт DECISION_TOKEN в AUDIT_LOG_BRIDGE и COMPLIANCE_REPORTER

## [M] CHANGELOG (minimal)
- 2026-02-02: v1.0.0 init
