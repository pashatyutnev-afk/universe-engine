FILE: UE_V2/03_ENT/60_QA_ENT/02__CREATE_FLOW__QA__ENT.md
SCOPE: UE_V2 / 03_ENT / 60_QA_ENT
DOC_TYPE: QA_ENTITY
DOMAIN: QA_ENT
UID: UE.V2.ENT.QA.CREATE_FLOW.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: QA_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: CREATE_FLOW_QA_ROOT
- ENTITY_CLASS: QA
- UID: UE.V2.ENT.QA.CREATE_FLOW.001

## [M] PURPOSE
Root “create flow” для QA: как собирать входы, как запускать проверки, как выдавать отчёт и fixes.
Никаких repo edits.

## [M] SCOPE
- TARGET_DOMAIN: MULTI
- APPLIES_TO: [ANY_QA_RUN]
- NON_GOALS: [исправлять артефакт вместо исполнителя]

## [M] INPUTS / OUTPUTS
- Inputs: [TASK_TEXT?, ARTIFACT_TEXT?, ARTIFACT_TOKENS?]
- Outputs:
  - QA_RUN_PLAN: [steps]
  - QA_REPORT: {QA_DECISION, QA_FINDINGS, REQUIRED_FIXES}
  - ISSUES?: [issue records] (optional)

## [M] FLOW (canonical)
- S0: INTAKE
  - Collect minimal inputs (text or token refs).
  - If missing -> ASK + list what is needed.
- S1: ROUTE
  - Use QA root PIPELINE_CONTRACT to choose realm.
- S2: APPLY CHECKS
  - Run realm pipeline plan (keys) and collect subreports.
- S3: AGGREGATE
  - Decision order: FAIL > ASK > WARN > PASS.
- S4: OUTPUT
  - Return QA_REPORT + REQUIRED_FIXES (if not PASS).

## [M] REPORT FORMAT (minimal)
- QA_DECISION: PASS|WARN|ASK|FAIL
- QA_FINDINGS: 1–7 bullets
- REQUIRED_FIXES: 1–7 bullets (if WARN/ASK/FAIL)
- ISSUES: optional

## [M] DECISION_MATRIX
- IF no inputs -> ASK
- IF any critical blocker -> FAIL
- IF issues exist but fixable -> WARN
- ELSE -> PASS

## [M] KB SCOPE
- KB Inputs: [artifact inputs]
- KB Outputs: [qa report tokens]
- KB Boundaries: [no guessing; no repo edits]
- KB RAW refs: []

## [M] GATES
- PASS if: report produced with deterministic fields
- FAIL if: cannot produce report due to missing inputs
