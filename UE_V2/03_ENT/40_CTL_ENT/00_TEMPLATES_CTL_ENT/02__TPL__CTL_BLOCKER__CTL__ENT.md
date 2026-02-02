FILE: UE_V2/03_ENT/40_CTL_ENT/00_TEMPLATES_CTL_ENT/02__TPL__CTL_BLOCKER__CTL__ENT.md
SCOPE: UE_V2 / 03_ENT / 40_CTL_ENT / 00_TEMPLATES_CTL_ENT
DOC_TYPE: TPL
DOMAIN: TPL_CTL_ENT
UID: UE.V2.ENT.TPL.CTL_BLOCKER.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: CTL_ENT
NAV_RULE: Template doc contains no RAW

---

## [M] TEMPLATE_NAME
CTL_BLOCKER_TEMPLATE

## [M] PURPOSE
Шаблон для “блокера” — документа, который фиксирует жёсткий запрет/политику стопа, нарушения и правила override.
Использовать для контроллеров, которые должны уметь сказать “СТОП”.

---

# [T] FILE HEADER (copy and fill)
FILE: <PATH_TO_TARGET_DOC>
SCOPE: <SCOPE>
DOC_TYPE: CTL_BLOCKER
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

## [M] BLOCKER_HEADER
- BLOCKER_NAME: <SHORT_NAME>
- BLOCKER_CLASS: CTL_BLOCKER
- UID: <UID>
- SEVERITY: BLOCK|HIGH|MED|LOW
- DEFAULT_ACTION: FAIL|ASK
- STATUS: ACTIVE|DRAFT|DEPRECATED

## [M] PURPOSE
<1–2 строки: что запрещает и почему>

## [M] TRIGGERS (when it fires)
- T1: <condition>
- T2: <condition>

## [M] BLOCK_REASON (facts only)
- <bullet list of factual reasons / constraints>

## [M] REQUIRED_FIXES (minimal)
- Fix1: <what to change>
- Fix2: <what to provide>

## [M] OVERRIDE_POLICY (if allowed)
- OVERRIDE_ALLOWED: true|false
- OVERRIDE_REQUIREMENTS:
  - <what evidence/approval is required>
- OVERRIDE_LOGGING:
  - <what must be logged (token-only in no-edit mode)>

## [M] VIOLATION_RECORD (format)
- VIOLATION_ID: <id>
- TITLE: <short>
- EVIDENCE: <what was observed>
- IMPACT: <one line>
- REQUIRED_FIX: <one line>
- FAIL_CODE: <code>

## [M] INTERFACES (RAW only)
- Entry points (RAW):
- Dependencies (RAW):

## [M] KB SCOPE
- KB Inputs: [<allowed knowledge>]
- KB Outputs: [<block decision token>]
- KB Boundaries: [no guessing, no repo edits]
- KB RAW refs: []

## [M] GATES
- PASS if:
  - blocker does not trigger
- FAIL if:
  - any trigger fires

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, QA_ENT, VAL_ENT, SPC_ENT]
- Handoff rules:
  - FAIL -> stop + REQUIRED_FIXES
  - ASK -> request minimal required inputs/approvals

## [M] CHANGELOG
- 0000-00-00: v1.0.0 init
