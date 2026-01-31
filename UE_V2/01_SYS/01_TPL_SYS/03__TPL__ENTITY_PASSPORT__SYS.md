FILE: 0000-00-00__TPL__ENTITY_PASSPORT__SYS.md
SCOPE: UE_V2 / SYS
DOC_TYPE: TEMPLATE
TEMPLATE_FOR: ENTITY_PASSPORT
UID: UE.V2.SYS.TPL.ENTITY_PASSPORT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-30
UPDATED: 2026-01-30
OWNER: SYS

---

## [M] ENTITY_HEADER
- ENTITY_NAME: <REPLACE_ME>
- ENTITY_CLASS: SPC|ENG|ORC|CTL|VAL|QA|XREF
- UID: <REPLACE_ME>
- STATUS: ACTIVE|DRAFT|DEPRECATED
- OWNER: SYS|RUNTIME|USER
- VERSION: 0.0.0
- CREATED: 0000-00-00
- UPDATED: 0000-00-00

## [M] PURPOSE
<one paragraph max>

## [M] CAPABILITIES (what it can produce)
- Produces: [TOKENS/ARTIFACTS]
- Edits: [what it may edit] | In MODE REPO usually: none
- Never: [hard prohibitions]

## [M] INPUTS / OUTPUTS
- Inputs:
  - <TOKEN>: <meaning>
- Outputs:
  - <TOKEN>: <meaning>

## [M] INTERFACES (RAW only)
- Entry points (RAW):
  - <RAW_LINK_TO_PIPELINE_CONTRACT_OR_OPERATION_GUIDE>
- Dependencies (RAW):
  - <RAW_LINKS_IF_ALLOWED_BY_SYSTEM>
# если по твоему закону ссылки в сущностях не нужны — оставляй этот блок пустым или только 1 ссылку на эксплуатацию

## [M] KB SCOPE
- KB Inputs: [what knowledge it reads]
- KB Outputs: [what knowledge it writes]
- KB Boundaries: [what it must not assume]
- KB RAW refs: [<RAW1>, <RAW2>]

## [M] GATES (pass/fail)
- PASS if: [conditions]
- FAIL if: [conditions]

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [SPC/ORC/CTL/VAL/QA roles list]
- Handoff rules: [short]

## [M] CHANGELOG (minimal)
- 0000-00-00: v0.0.0 init
