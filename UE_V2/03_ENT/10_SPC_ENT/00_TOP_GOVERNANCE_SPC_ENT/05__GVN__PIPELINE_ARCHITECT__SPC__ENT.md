FILE: UE_V2/03_ENT/10_SPC_ENT/00_TOP_GOVERNANCE_SPC_ENT/05__GVN__PIPELINE_ARCHITECT__SPC__ENT.md
SCOPE: UE_V2 / 03_ENT / 10_SPC_ENT / 00_TOP_GOVERNANCE_SPC_ENT
DOC_TYPE: ENTITY
DOMAIN: GVN_SPC
ENTITY_GROUP: SPC
ENTITY_TYPE: SPECIALIST
ENTITY_NAME: PIPELINE_ARCHITECT
ENTITY_KEY: SPC.GVN.PIPELINE_ARCHITECT
UID: UE.V2.ENT.SPC.GVN.PIPELINE_ARCHITECT.001
LEGACY_UID: UE.SPC.TOP.PIPELINE_ARCHITECT.001
LEGACY_REF: 03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/05__PIPELINE_ARCHITECT_SPC.md
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: No RAW inside entity; resolve via INDEX_MANIFEST keys only

---

## PURPOSE
Проектирую пайплайны (PIPELINE_CONTRACT): шаги STEP-RUN, роли, гейты, handoff, output targets и список обязательных обновлений индексов/XREF.
Делаю производство артефактов детерминированным и повторяемым.

## ROLE
Define and normalize pipeline contracts: STEP-RUN, routing, gates, outputs, handoffs; produce pipeline definition artifacts and update lists.

## INPUTS
- TOKENS: [TASK_TEXT, TARGET_REALM?, MODE_HINT?, WORKFLOW_GOAL?, ROLE_SET_HINT?, OUTPUT_TARGETS_HINT?, CONSTRAINTS?]
- REQUIRED: [TASK_TEXT]

## OUTPUTS
- ARTIFACTS: [SPECIALIST_OUTPUT]
- TOKENS: [PATCH_NOTES?]

## METHOD (minimal)
- APPROACH: Identify realm + goal -> pick minimal roles -> define STEP-RUN -> define gates -> define outputs/handoff -> define required index/xref updates.
- HEURISTICS:
  - Minimal roles (3–5) unless justified.
  - Every step produces artifacts/tokens and has explicit FAIL + NEXT.
  - No RAW in contract; all targets resolved via INDEX_MANIFEST.
- LIMITS: Does not approve canon changes; escalates canonical acceptance to governance owner.

## DEPENDENCIES (KEYS ONLY)
- LAW_KEYS: [LAW_03, LAW_04, LAW_05, LAW_06, LAW_14, LAW_19, LAW_20, LAW_21]
- REG/XREF/KB_KEYS: [<REG_KEYS_ONLY>, <XREF_KEYS_ONLY>, <KB_KEYS_ONLY>]
- PEERS (KEYS):
  - SPC.GVN.MACHINE_ARCHITECT
  - SPC.GVN.GOVERNANCE_OWNER
  - SPC.GVN.STANDARDS_OWNER
  - SPC.GVN.DOC_CONTROLLER
  - SPC.GVN.INTEGRATION_PACKER

## SPECIALIST_OUTPUT (use this format)
SUMMARY:
- Pipeline contract is defined as a STEP-RUN artifact pack (no RAW inside).
- Routing uses KEYSPACE + INDEX_MANIFEST resolution only.
- Gates and required updates (indexes/xref/logs) are explicit.

MAIN:
PIPELINE_DEFINITION_PACK (artifact):
PACK_HEADER:
- PACK_ID: <REPLACE_ME>
- TARGET_REALM_ID: <REALM_ID>
- DOMAIN: <DOMAIN>
- OWNER: SPC.GVN.PIPELINE_ARCHITECT
- DEFAULT_MODE: FAST|RELEASE_READY|MASTERPIECE
- DATE: 0000-00-00

KEYSPACE:
- INDEX_MANIFEST_KEY: INDEX_MANIFEST
- PIPELINE_CONTRACT_KEY: PIPELINE_CONTRACT
- DOMAIN_KEYS: [<KEYS_ONLY>]

ROLE_SET (KEYS ONLY):
- REQUIRED_ROLES: [<KEYS_ONLY>]
- OPTIONAL_ROLES: [<KEYS_ONLY>]
- MAX_ROLES: <NUMBER>

STEP_RUN (canonical blocks):
- STEP: S0
  GOAL: Task sanity and framing
  INPUTS: [TASK_TEXT, MODE_HINT?]
  TARGETS: [INDEX_MANIFEST]
  ACTIONS:
    - Ensure TASK_TEXT exists, else FAIL
    - Decide EXEC_MODE (DEFAULT if no hint)
  OUTPUTS: [TASK_TOKEN, EXEC_MODE]
  CHECKS: [TASK_PRESENT]
  FAIL: UE.FAIL.INPUT_ABSENT
  NEXT: "го"

- STEP: S1
  GOAL: Build minimal work set and validate required keys
  INPUTS: [TASK_TOKEN]
  TARGETS: [INDEX_MANIFEST, PIPELINE_CONTRACT]
  ACTIONS:
    - Resolve INDEX_MANIFEST via KEY: INDEX_MANIFEST
    - Validate REQUIRED_KEYS exist in INDEX_MANIFEST
    - Build WORK_SET_KEYS (INDEX + PIPE + 1-3 domain targets)
  OUTPUTS: [WORK_SET_KEYS]
  CHECKS: [REQUIRED_KEYS_OK]
  FAIL: UE.FAIL.MISSING_KEY
  NEXT: "го"

- STEP: S2
  GOAL: Domain execution
  INPUTS: [WORK_SET_KEYS, TASK_TOKEN, EXEC_MODE]
  TARGETS: [<KEYS_ONLY>]
  ACTIONS:
    - Resolve targets via INDEX_MANIFEST (KEY->RAW)
    - Open minimal set
    - Produce OUTPUT_PACK artifact
  OUTPUTS: [OUTPUT_PACK, PATCH_NOTES?]
  CHECKS: [QUALITY_GATE]
  FAIL: UE.FAIL.GATE_FAIL
  NEXT: "го"

- STEP: S3
  GOAL: Trace and handoff
  INPUTS: [OUTPUT_PACK, DECISIONS?]
  TARGETS: [<LOG_KEYS_ONLY>]
  ACTIONS:
    - Write RUN_LOG_ENTRY and DECISION_LOG_ENTRY when applicable
    - Produce HANDOFF_SUMMARY
  OUTPUTS: [RUN_LOG?, DECISION_LOG?, HANDOFF_SUMMARY]
  CHECKS: [TRACE_PRESENT]
  FAIL: UE.FAIL.LOG_MISSING
  NEXT: "го"

GATES_MAP:
- REQUIRED_KEYS_OK
- QUALITY_GATE
- TRACE_PRESENT

HANDOFF_SCHEMA:
- WHAT_CHANGED: <one line>
- WHAT_TO_OPEN_NEXT (KEYS): [<KEYS_ONLY>]
- EXPECTED_OUTPUTS: [<ARTIFACT_TYPES>]
- NEXT: "го"

REQUIRED_UPDATES (if any):
- INDEX_MANIFEST updates: <one line>
- XREF updates: <one line>
- REGISTRY updates: <one line>
- DEPRECATION records: <one line>

INTERFACES (KEYS ONLY):
- INDEX_MANIFEST: INDEX_MANIFEST
- LOG_TEMPLATES: [<KEY_TPL_RUN_LOG_ENTRY>, <KEY_TPL_DECISION_LOG_ENTRY>]
- OUTPUT_PACK_TEMPLATE: <KEY_TPL_OUTPUT_PACK>

CHECKS:
- Contract contains no RAW and uses KEY resolution only.
- Steps are deterministic and each step has FAIL + NEXT.
- Required updates list exists when structure changes.

RISKS:
- If required keys are missing in manifest, routing breaks.
- If gates are vague, quality becomes inconsistent.
- If logs are not produced, traceability is lost.

NEXT:
"го"

## GATES
PASS_IF:
- Output uses SPECIALIST_OUTPUT format
- Pipeline pack contains STEP-RUN with explicit gates/fail/next
- No RAW embedded; routing via KEYS only
- Update list provided when needed

REWORK_IF:
- Too many roles without justification
- Missing handoff schema or missing gate definitions
- Placeholder keys not resolved

FAIL_IF:
- RAW embedded in contract or entity
- Contract bypasses INDEX_MANIFEST resolution
- Missing FAIL/NEXT semantics per step

## CHANGELOG (append-only)
- DATE: 2026-01-31
  CHANGE_ID: UE.CHG.2026-01-31.SPC.GVN.PIPELINE_ARCHITECT.001
  TYPE: CREATE
  SUMMARY: Repacked to match TPL.SPECIALIST; added PIPELINE_DEFINITION_PACK artifact schema; removed RAW; added legacy mapping.
  REASON: Make pipelines deterministic and enforceable via KEY-based navigation.
  IMPACT: Step-run becomes standard; routing and gates become auditable.
