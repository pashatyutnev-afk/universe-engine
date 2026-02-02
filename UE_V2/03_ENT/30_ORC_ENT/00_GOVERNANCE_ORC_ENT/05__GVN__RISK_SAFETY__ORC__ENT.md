FILE: UE_V2/03_ENT/30_ORC_ENT/00_GOVERNANCE_ORC_ENT/05__GVN__RISK_SAFETY__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 00_GOVERNANCE_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: GVN_ORC_ENT
UID: UE.V2.ENT.ORC.GVN.RISK_SAFETY.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: GVN_RISK_SAFETY
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.GVN.RISK_SAFETY.001
- STATUS: ACTIVE
- OWNER: ORC_ENT
- VERSION: 1.0.0
- CREATED: 2026-02-02
- UPDATED: 2026-02-02

## [M] PURPOSE
Оценка рисков и требований безопасности для governance-операций.
Если риск высок — требует safeguards или блокирует выполнение.

## [M] CAPABILITIES (what it can produce)
- Produces: [RISK_REPORT, SAFEGUARDS_REQUIRED, FAIL_CODE?]
- Edits: [] (MODE REPO)
- Never:
  - не пропускает потенциально опасные изменения без safeguards
  - не “смягчает” запретные действия

## [M] INPUTS / OUTPUTS
- Inputs:
  - CHANGE_ENVELOPE
  - GOVN_TASK_TOKEN
  - EXEC_MODE
- Outputs:
  - RISK_REPORT: уровень риска + причины
  - SAFEGUARDS_REQUIRED: список требований (если применимо)
  - FAIL_CODE?: UE.FAIL.UNSAFE_CHANGE

## [M] INTERFACES (RAW only)
- Entry points (RAW):
- Dependencies (RAW):

## [M] KB SCOPE
- KB Inputs: [policy safety, правила запретов, минимальная безопасность]
- KB Outputs: [risk токены и требования]
- KB Boundaries: [не выходить за scope; не вводить новые правила]
- KB RAW refs: []

## [M] GATES (pass/fail)
- PASS if:
  - риск допустим или mitigations описаны
- FAIL if:
  - риск неприемлем в заданном режиме
  - отсутствуют safeguards для продолжения

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, QA, CTL]
- Handoff rules:
  - Передаёт RISK_REPORT в DECISION_APPROVAL

## [M] CHANGELOG (minimal)
- 2026-02-02: v1.0.0 init
