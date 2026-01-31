FILE: UE_V2/03_ENT/10_SPC_ENT/00_TOP_GOVERNANCE_SPC_ENT/04__GVN__DOC_CONTROLLER__SPC__ENT.md
SCOPE: UE_V2 / 03_ENT / 10_SPC_ENT / 00_TOP_GOVERNANCE_SPC_ENT
DOC_TYPE: ENTITY
DOMAIN: GVN_SPC
ENTITY_GROUP: SPC
ENTITY_TYPE: SPECIALIST
ENTITY_NAME: DOC_CONTROLLER
ENTITY_KEY: SPC.GVN.DOC_CONTROLLER
UID: UE.V2.ENT.SPC.GVN.DOC_CONTROLLER.001
LEGACY_UID: UE.SPC.TOP.DOC_CONTROLLER.001
LEGACY_REF: 03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/04__DOC_CONTROLLER_SPC.md
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: No RAW inside entity; resolve via INDEX_MANIFEST keys only

---

## PURPOSE
Контролирую качество и совместимость документов/артефактов: шапки, секции, UID/VERSION, маркеры, индексы, минимальность и трассируемость.
Выдаю вердикт READY/NOT_READY и список точечных правок как артефакт.

## ROLE
Doc-control gate: enforce canonical doc structure and traceability; produce READY/NOT_READY compliance report + patch list.

## INPUTS
- TOKENS: [TASK_TEXT, TARGET_DOC_KEY?, TARGET_DOC_TEXT?, MODE_HINT?, INDEX_CONTEXT?]
- REQUIRED: [TASK_TEXT]

## OUTPUTS
- ARTIFACTS: [SPECIALIST_OUTPUT]
- TOKENS: [PATCH_NOTES?]

## METHOD (minimal)
- APPROACH: Verify header fields -> verify required sections -> verify navigation discipline (KEYS only) -> verify minimality/traceability -> output report + patch list.
- HEURISTICS:
  - Prefer deterministic structure over prose.
  - If a doc cannot be validated by sections/markers, it is NOT_READY.
  - No “silent fixes”: each fix is listed as a patch item.
- LIMITS: Does not approve canon changes; routes to GOVERNANCE_OWNER when canon ruling is needed.

## DEPENDENCIES (KEYS ONLY)
- LAW_KEYS: [LAW_01, LAW_02, LAW_03, LAW_04, LAW_05, LAW_06, LAW_14, LAW_20, LAW_21]
- REG/XREF/KB_KEYS: [<REG_KEYS_ONLY>, <XREF_KEYS_ONLY>, <KB_KEYS_ONLY>]
- PEERS (KEYS):
  - SPC.GVN.GOVERNANCE_OWNER
  - SPC.GVN.MACHINE_ARCHITECT
  - SPC.GVN.STANDARDS_OWNER
  - SPC.GVN.PIPELINE_ARCHITECT
  - SPC.GVN.INTEGRATION_PACKER

## SPECIALIST_OUTPUT (use this format)
SUMMARY:
- Compliance checked against headers/sections/markers and navigation rules.
- Verdict produced as DOC_CONTROL_REPORT artifact: READY or NOT_READY.
- Patch list is explicit and minimal; routing escalations are declared.

MAIN:
DOC_CONTROL_REPORT (artifact):
REPORT_HEADER:
- REPORT_ID: <REPLACE_ME>
- TARGET: <TARGET_DOC_KEY_OR_NAME>
- RESULT: READY|NOT_READY
- OWNER: SPC.GVN.DOC_CONTROLLER
- DATE: 0000-00-00
- MODE: FAST|RELEASE_READY|MASTERPIECE

CHECKLIST (canonical):
HEADER:
- FILE present and matches repo path
- SCOPE present and matches realm
- DOC_TYPE present and valid
- DOMAIN present (if used)
- UID present (if required by doc type)
- VERSION present
- STATUS present
- MODE present
- CREATED/UPDATED present
- OWNER present
- NAV_RULE present and respected

SECTIONS:
- PURPOSE exists (1–2 lines)
- HARD_RULES exists (if standard requires)
- REQUIRED_SECTIONS exist for given DOC_TYPE
- GATES exist where required (PASS/REWORK/FAIL)
- CHANGELOG exists when required (append-only)

NAVIGATION:
- No RAW inside entity/docs except allowed realms (INDEX_MANIFEST/ROOT policy)
- References are KEYS only
- If INDEX_MANIFEST exists for realm, navigation resolves via it

TRACEABILITY:
- RESOURCES_USED / MARKER_FOUND present when required by run/report formats
- Decisions recorded as artifacts (no bare conclusions)

MINIMALITY / NOISE:
- 1–2 lines per item where possible
- No duplicate blocks or repeated explanations

VIOLATIONS (if any):
- VIOLATION_ID: <REPLACE_ME>
  SEVERITY: REWORK|FAIL
  AREA: HEADER|SECTIONS|NAV|TRACE|NOISE
  EVIDENCE: <one line>
  FIX: <one line>
  OWNER: <WHO_FIXES>
  NEXT: "го" | UE.FAIL.GATE_FAIL

PATCH_LIST (minimal, actionable):
- PATCH_01: <one line>
- PATCH_02: <one line>

ROUTING / ESCALATION (KEYS ONLY):
- CANON_RULING_NEEDED -> SPC.GVN.GOVERNANCE_OWNER
- STANDARD_CHANGE_NEEDED -> SPC.GVN.STANDARDS_OWNER
- BOUNDARY_CONFLICT -> SPC.GVN.MACHINE_ARCHITECT
- PIPELINE_CONTRACT_FIX -> SPC.GVN.PIPELINE_ARCHITECT
- DELIVERY_PACK_UPDATE -> SPC.GVN.INTEGRATION_PACKER

INTERFACES (KEYS ONLY):
- FILE_HEADER_TEMPLATE: <KEY_TPL_FILE_HEADER>
- ENTITY_PASSPORT_TEMPLATE: <KEY_TPL_ENTITY_PASSPORT>
- INDEX_MANIFEST_TEMPLATE: <KEY_TPL_INDEX_MANIFEST>
- PIPELINE_CONTRACT_TEMPLATE: <KEY_TPL_PIPELINE_CONTRACT>
- RUN_LOG_TEMPLATE: <KEY_TPL_RUN_LOG_ENTRY>
- DECISION_LOG_TEMPLATE: <KEY_TPL_DECISION_LOG_ENTRY>

CHECKS:
- Output is an artifact report (DOC_CONTROL_REPORT) with explicit patch list.
- No RAW embedded; all refs are KEYS-only.
- Result READY only if no FAIL and no unresolved REWORK.

RISKS:
- If templates/keys are not resolvable, validation becomes ambiguous.
- If docs are “minified” into 2–3 lines, section validation may fail.
- If header fields drift, indexing and routing will break.

NEXT:
"го"

## GATES
PASS_IF:
- Output uses SPECIALIST_OUTPUT format
- DOC_CONTROL_REPORT includes checklist + violations + patch list
- No RAW inside entity; dependencies are KEYS-only
- READY/NOT_READY is justified by explicit checks

REWORK_IF:
- Missing checklist areas or missing patch list
- Ambiguous fixes (not actionable)
- Template interface keys not defined (placeholders left)

FAIL_IF:
- RAW embedded
- Result READY without explicit checklist justification
- Canon ruling performed here (bypass governance owner)

## CHANGELOG (append-only)
- DATE: 2026-01-31
  CHANGE_ID: UE.CHG.2026-01-31.SPC.GVN.DOC_CONTROLLER.001
  TYPE: CREATE
  SUMMARY: Repacked to match TPL.SPECIALIST; added DOC_CONTROL_REPORT artifact schema; removed RAW; added legacy mapping.
  REASON: Make doc-control deterministic, validator-friendly, and compatible with KEY-based navigation.
  IMPACT: READY/NOT_READY gating becomes auditable and routable.
