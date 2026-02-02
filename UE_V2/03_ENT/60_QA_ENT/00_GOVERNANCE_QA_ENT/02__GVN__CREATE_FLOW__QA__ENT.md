FILE: UE_V2/03_ENT/60_QA_ENT/00_GOVERNANCE_QA_ENT/02__GVN__CREATE_FLOW__QA__ENT.md
SCOPE: UE_V2 / 03_ENT / 60_QA_ENT / 00_GOVERNANCE_QA_ENT
DOC_TYPE: QA_ENTITY
DOMAIN: GVN_QA_ENT
UID: UE.V2.ENT.QA.GVN.CREATE_FLOW.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: QA_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: GVN_CREATE_FLOW_QA
- ENTITY_CLASS: QA
- UID: UE.V2.ENT.QA.GVN.CREATE_FLOW.001

## [M] PURPOSE
Канонический QA flow: как запускать проверку, как оформлять findings, fixes и issue tokens.
Не делает repo edits, только план и результаты.

## [M] SCOPE
- TARGET_DOMAIN: MULTI
- APPLIES_TO: [ANY_ARTIFACT_QA]
- NON_GOALS: [выполнение исправлений вместо исполнителя]

## [M] INPUTS / OUTPUTS
- Inputs: [TASK_TEXT?, ARTIFACT_TEXT?, ARTIFACT_TOKENS?]
- Outputs:
  - QA_RUN_PLAN: [steps]
  - QA_REPORT: [summary]
  - ISSUES?: [issue list]
  - REQUIRED_FIXES?: [fix list]

## [M] FLOW (canonical steps)
- S0: INTAKE
  - Collect minimal inputs: artifact text or token reference
  - If missing -> ASK
- S1: APPLY GOVERNANCE
  - Run governance entities (issue lifecycle policy, flow rules, minimal gate)
- S2: PRODUCE REPORT
  - Output QA_DECISION + findings + required fixes
- S3: ISSUE HANDOFF
  - If FAIL/WARN -> create issue tokens (per lifecycle)
  - If PASS -> no issues

## [M] REPORT FORMAT (minimal)
- QA_DECISION: PASS|WARN|ASK|FAIL
- QA_FINDINGS: 1–7 short bullets
- REQUIRED_FIXES: 1–7 actionable bullets (only if WARN/FAIL/ASK)
- ISSUES: optional list of issue records

## [M] DECISION_MATRIX
- IF no artifact input -> ASK
- IF critical blockers -> FAIL
- IF non-critical problems -> WARN
- ELSE -> PASS

## [M] KB SCOPE
- KB Inputs: [artifact text/tokens]
- KB Outputs: [qa report tokens]
- KB Boundaries: [no guessing; no repo edits]
- KB RAW refs: []

## [M] GATES
- PASS if: report produced with deterministic fields
- FAIL if: cannot produce report due to missing inputs
