FILE: UE_V2/03_ENT/60_QA_ENT/00_GOVERNANCE_QA_ENT/03__GVN__ISSUE_LIFECYCLE__QA__ENT.md
SCOPE: UE_V2 / 03_ENT / 60_QA_ENT / 00_GOVERNANCE_QA_ENT
DOC_TYPE: QA_ENTITY
DOMAIN: GVN_QA_ENT
UID: UE.V2.ENT.QA.GVN.ISSUE_LIFECYCLE.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: QA_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: GVN_ISSUE_LIFECYCLE_QA
- ENTITY_CLASS: QA
- UID: UE.V2.ENT.QA.GVN.ISSUE_LIFECYCLE.001

## [M] PURPOSE
Канонический жизненный цикл QA-issues: статусы, severity, обязательные поля, правила закрытия.

## [M] SCOPE
- TARGET_DOMAIN: MULTI
- APPLIES_TO: [QA_ISSUES, QA_REPORTS]
- NON_GOALS: [автоматическое исправление]

## [M] ISSUE_SCHEMA (minimal)
- ISSUE_ID: <deterministic id or placeholder>
- TITLE: <short>
- SEVERITY: BLOCK|HIGH|MED|LOW
- STATUS: NEW|TRIAGED|FIXING|RECHECK|CLOSED|WONT_FIX
- EVIDENCE: <facts only>
- REQUIRED_FIX: <one-line actionable>
- OWNER: <team/person token or USER>
- CREATED: 0000-00-00
- UPDATED: 0000-00-00

## [M] STATUS RULES
- NEW -> TRIAGED
- TRIAGED -> FIXING
- FIXING -> RECHECK
- RECHECK -> CLOSED (if pass) or FIXING (if still failing)
- Any -> WONT_FIX (requires reason)

## [M] SEVERITY RULES
- BLOCK: стоп процесса, продолжать нельзя
- HIGH: продолжать только с явным решением и планом фикса
- MED: можно продолжать, но fixes обязательны
- LOW: замечание, не блокирует

## [M] CLOSURE REQUIREMENTS
- CLOSED requires:
  - evidence of fix (what changed)
  - recheck result = PASS or downgraded severity with reason
- WONT_FIX requires:
  - reason token
  - accepted risk statement (one line)

## [M] DECISION_MATRIX
- IF missing required fields -> FAIL (UE.FAIL.GATE_FAIL)
- IF status transition invalid -> FAIL (UE.FAIL.RULE_VIOLATION)
- ELSE -> PASS

## [M] FAIL_CODES
- UE.FAIL.GATE_FAIL
- UE.FAIL.RULE_VIOLATION

## [M] KB SCOPE
- KB Inputs: [issue records]
- KB Outputs: [normalized lifecycle status guidance]
- KB Boundaries: [no guessing evidence]
- KB RAW refs: []

## [M] GATES
- PASS if: issue record conforms and transitions are valid
- FAIL if: invalid transition or missing critical fields
