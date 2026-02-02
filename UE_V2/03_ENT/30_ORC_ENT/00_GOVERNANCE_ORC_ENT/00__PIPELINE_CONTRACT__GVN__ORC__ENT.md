FILE: UE_V2/03_ENT/30_ORC_ENT/00_GOVERNANCE_ORC_ENT/00__PIPELINE_CONTRACT__GVN__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 00_GOVERNANCE_ORC_ENT
DOC_TYPE: PIPELINE_CONTRACT
DOMAIN: GVN_ORC_ENT
UID: UE.V2.ENT.PIPE.GVN_ORC_ENT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: Contract has no RAW

---

## [M] PURPOSE
PIPELINE_CONTRACT — навигатор действий для реалма Governance ORC ENT.
Не хранит RAW-адреса. Работает через KEY и резолвит адреса в INDEX_MANIFEST.

## [M] HARD_RULES
- Запрещено хранить RAW внутри CONTRACT.
- Все обращения: TARGET_KEY -> resolve via INDEX_MANIFEST -> open.
- Выполнение по STEP-RUN: один шаг = одна пачка действий.
- Каждый шаг должен выдавать NEXT_PROMPT: "го" или FAIL_CODE.
- Минимальные открытия: только то, что нужно для текущего шага.
- Любое изменение/правка репо запрещены в MODE REPO (USAGE-ONLY, NO-EDIT).

## [M] REQUIRED_KEYS (must exist in INDEX_MANIFEST)
- INDEX_MANIFEST
- PIPELINE_CONTRACT
- GVN.ENTRY_GUARD
- GVN.RULE_ENFORCER
- GVN.DEPENDENCY_RESOLVER
- GVN.CHANGE_CONTROL
- GVN.RISK_SAFETY
- GVN.DECISION_APPROVAL
- GVN.AUDIT_LOG_BRIDGE
- GVN.COMPLIANCE_REPORTER

## [M] CONTRACT_HEADER
- REALM_ID: UE_V2/03_ENT/30_ORC_ENT/00_GOVERNANCE_ORC_ENT
- DOMAIN: GVN_ORC_ENT
- ARTIFACT_TYPES: [PIPE, ENTITY_PASSPORT, RUN_LOG, DECISION_LOG, COMPLIANCE_REPORT]
- DEFAULT_MODE: RELEASE_READY

## [M] EXEC_MODEL (how it runs)
1) Resolve INDEX_MANIFEST via KEY: INDEX_MANIFEST
2) Validate REQUIRED_KEYS exist
3) Build WORK_SET_KEYS (what to open) using KEYS only
4) Run steps sequentially (STEP-RUN)
5) Emit: RUN_LOG + (optional) DECISION_LOG + COMPLIANCE_REPORT summary

## [M] STEP-RUN (canonical)
Each step block format:
- STEP: S
  GOAL:
  INPUTS: []
  TARGETS: []
  ACTIONS:
    - 
  OUTPUTS: []
  CHECKS: []
  FAIL:
  NEXT: "го"

## [M] STEPS (governance skeleton)

- STEP: S0
  GOAL: Entry sanity and governance framing
  INPUTS: [TASK_TEXT, MODE_HINT?]
  TARGETS: [INDEX_MANIFEST]
  ACTIONS:
    - Ensure TASK_TEXT exists, else FAIL
    - Decide EXEC_MODE using MODE_HINT or DEFAULT_MODE
    - Normalize task into GOVN_TASK_TOKEN (intent, scope, targets, constraints)
    - Declare CHANGE_INTENT (e.g. create/update/deprecate/route/check)
  OUTPUTS: [GOVN_TASK_TOKEN, EXEC_MODE, CHANGE_INTENT]
  CHECKS: [TASK_PRESENT]
  FAIL: UE.FAIL.INPUT_ABSENT
  NEXT: "го"

- STEP: S1
  GOAL: Load minimal navigation layer for realm
  INPUTS: [GOVN_TASK_TOKEN]
  TARGETS: [INDEX_MANIFEST, PIPELINE_CONTRACT]
  ACTIONS:
    - Resolve REQUIRED_KEYS and confirm they exist
    - Build WORK_SET_KEYS for governance run (min set):
      - GVN.ENTRY_GUARD
      - plus only the modules needed by CHANGE_INTENT
  OUTPUTS: [WORK_SET_KEYS]
  CHECKS: [REQUIRED_KEYS_OK]
  FAIL: UE.FAIL.MISSING_KEY
  NEXT: "го"

- STEP: S2
  GOAL: Governance execution (policy routing)
  INPUTS: [WORK_SET_KEYS, GOVN_TASK_TOKEN, CHANGE_INTENT]
  TARGETS: []
  ACTIONS:
    - Run GVN.ENTRY_GUARD: validate inputs, mode, target scope
    - Run GVN.RULE_ENFORCER: apply hard rules (RAW-only, no-edit, key-only routing)
    - Run GVN.DEPENDENCY_RESOLVER: compute required keys and minimal load order
    - Run GVN.CHANGE_CONTROL: decide allowed change envelope + required logs
    - Run GVN.RISK_SAFETY: assess risk, require safeguards or block
    - Run GVN.DECISION_APPROVAL: decide approval required or not, emit decision token
    - Run GVN.AUDIT_LOG_BRIDGE: prepare audit/run log hooks (keys only)
    - Run GVN.COMPLIANCE_REPORTER: synthesize compliance status (pass/fail, violations)
  OUTPUTS: [GOVN_RESULT_TOKEN, COMPLIANCE_REPORT, DECISION_TOKEN?]
  CHECKS: [QUALITY_GATE, NO_RULE_VIOLATION]
  FAIL: UE.FAIL.GATE_FAIL
  NEXT: "го"

- STEP: S3
  GOAL: Log and archive tokens
  INPUTS: [GOVN_RESULT_TOKEN, COMPLIANCE_REPORT, DECISION_TOKEN?]
  TARGETS: []
  ACTIONS:
    - Emit RUN_LOG_ENTRY (what ran, what keys touched, outcomes)
    - Emit DECISION_LOG_ENTRY if any routing/approval/choice occurred
    - Attach COMPLIANCE_REPORT summary to output pack (if required by calling realm)
  OUTPUTS: [RUN_LOG, DECISION_LOG?, OUTPUT_SUMMARY]
  CHECKS: [LOG_WRITTEN]
  FAIL: UE.FAIL.LOG_MISSING
  NEXT: "го"

## [M] FAIL_CODES (local)
- UE.FAIL.INPUT_ABSENT
- UE.FAIL.MISSING_KEY
- UE.FAIL.RULE_VIOLATION
- UE.FAIL.UNSAFE_CHANGE
- UE.FAIL.APPROVAL_REQUIRED
- UE.FAIL.GATE_FAIL
- UE.FAIL.LOG_MISSING

## [M] CHANGELOG (minimal)
- 2026-02-02: v1.0.0 init
