FILE: UE_V2/03_ENT/10_SPC_ENT/00_TOP_GOVERNANCE_SPC_ENT/06__GVN__INTEGRATION_PACKER__SPC__ENT.md
SCOPE: UE_V2 / 03_ENT / 10_SPC_ENT / 00_TOP_GOVERNANCE_SPC_ENT
DOC_TYPE: ENTITY
DOMAIN: GVN_SPC
ENTITY_GROUP: SPC
ENTITY_TYPE: SPECIALIST
ENTITY_NAME: INTEGRATION_PACKER
ENTITY_KEY: SPC.GVN.INTEGRATION_PACKER
UID: UE.V2.ENT.SPC.GVN.INTEGRATION_PACKER.001
LEGACY_UID: UE.SPC.TOP.INTEGRATION_PACKER.001
LEGACY_REF: 03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/06__INTEGRATION_PACKER_SPC.md
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: No RAW inside entity; resolve via INDEX_MANIFEST keys only

---

## PURPOSE
Упаковываю результаты изменений в самодостаточный integration pack: что изменилось, где SoT, какие pointers/deprecations, какие миграции и что открыть дальше.
Делаю handoff быстрым и детерминированным.

## ROLE
Package outputs for handoff: integration bundle with SoT/pointers/deprecation summary, migration steps, and next-open keys.

## INPUTS
- TOKENS: [TASK_TEXT, ARTIFACTS?, DECISIONS?, CHANGELOG_ENTRY?, MIGRATION_PLAN?, MODE_HINT?]
- REQUIRED: [TASK_TEXT]

## OUTPUTS
- ARTIFACTS: [SPECIALIST_OUTPUT]
- TOKENS: [PATCH_NOTES?]

## METHOD (minimal)
- APPROACH: Collect produced artifacts -> identify SoT and pointers -> summarize deprecations/migrations -> list required updates -> build handoff checklist + next keys.
- HEURISTICS:
  - Pack must be self-contained: a new reader can follow it without hunting.
  - Every claim references KEYS (no raw URLs).
  - Include minimal checklist: verify, apply, log, next.
- LIMITS: Does not decide canon; packages decisions already made by governance owner.

## DEPENDENCIES (KEYS ONLY)
- LAW_KEYS: [LAW_03, LAW_04, LAW_05, LAW_06, LAW_14, LAW_19, LAW_20]
- REG/XREF/KB_KEYS: [<REG_KEYS_ONLY>, <XREF_KEYS_ONLY>, <KB_KEYS_ONLY>]
- PEERS (KEYS):
  - SPC.GVN.GOVERNANCE_OWNER
  - SPC.GVN.MACHINE_ARCHITECT
  - SPC.GVN.STANDARDS_OWNER
  - SPC.GVN.DOC_CONTROLLER
  - SPC.GVN.PIPELINE_ARCHITECT

## SPECIALIST_OUTPUT (use this format)
SUMMARY:
- Integration pack produced as an artifact bundle (KEYS-only).
- SoT/pointers/deprecations/migration steps are explicit.
- Next actions are given as checklist + next-open keys.

MAIN:
INTEGRATION_OUTPUT_PACK (artifact):
PACK_HEADER:
- PACK_ID: <REPLACE_ME>
- TARGET: <WHAT_CHANGE>
- OWNER: SPC.GVN.INTEGRATION_PACKER
- DATE: 0000-00-00
- MODE: FAST|RELEASE_READY|MASTERPIECE

WHAT_CHANGED (short):
- <1-5 bullets>

ARTIFACTS_INCLUDED (KEYS ONLY):
- PRIMARY_ARTIFACTS: [<KEYS_ONLY>]
- SUPPORTING_ARTIFACTS: [<KEYS_ONLY>]
- LOG_ARTIFACTS: [<KEYS_ONLY>]

SoT & POINTERS (KEYS ONLY):
- SoT_KEYS: [<KEYS_ONLY>]
- POINTER_KEYS: [<KEYS_ONLY>]
- DUPLICATE_KEYS_REMOVED: [<KEYS_ONLY>]

DEPRECATION & REDIRECTS (KEYS ONLY):
- DEPRECATED_KEYS: [<KEYS_ONLY>]
- REDIRECTS:
  - FROM_KEY: <KEYS_ONLY>
    TO_KEY: <KEYS_ONLY>
    NOTE: <one line>

MIGRATION (if applicable):
- MIGRATION_STEPS:
  - <step 1>
  - <step 2>
- REQUIRED_UPDATES:
  - INDEX_MANIFEST updates: <one line>
  - XREF updates: <one line>
  - REGISTRY updates: <one line>
  - PIPELINE_CONTRACT updates: <one line>

HANDOFF_CHECKLIST (minimal):
- [ ] Open PACK targets (KEYS) and verify outputs exist
- [ ] Apply required updates (index/xref/registry)
- [ ] Validate doc-control gate (READY/NOT_READY)
- [ ] Record decision/log entries
- [ ] Run next pipeline step

NEXT_OPEN (KEYS ONLY):
- OPEN_KEYS: [<KEYS_ONLY>]
- EXPECTED_NEXT_OUTPUTS: [OUTPUT_PACK, PATCH_NOTES?, RUN_LOG?]
- NEXT: "го"

INTERFACES (KEYS ONLY):
- OUTPUT_PACK_TEMPLATE: <KEY_TPL_OUTPUT_PACK>
- RUN_LOG_TEMPLATE: <KEY_TPL_RUN_LOG_ENTRY>
- DECISION_LOG_TEMPLATE: <KEY_TPL_DECISION_LOG_ENTRY>
- DEPRECATION_POLICY: <KEY_DEPRECATION_POLICY>

CHECKS:
- Pack is self-contained and KEYS-only (no RAW).
- Includes SoT/pointers and deprecation/migration details if relevant.
- Includes next-open keys + checklist.

RISKS:
- If SoT/pointers are missing, routing will diverge.
- If migration steps are vague, consumers will apply changes inconsistently.
- If next-open keys are empty, handoff becomes manual hunting.

NEXT:
"го"

## GATES
PASS_IF:
- Output uses SPECIALIST_OUTPUT format
- Pack is self-contained and references KEYS only
- Includes checklist + next-open keys
- No RAW embedded

REWORK_IF:
- Missing SoT/pointers or missing deprecation/migration when expected
- Missing next-open keys or checklist too vague
- Placeholders for required keys remain unresolved

FAIL_IF:
- RAW embedded
- Pack claims changes without referencing artifacts/keys
- Handoff omits required updates causing drift

## CHANGELOG (append-only)
- DATE: 2026-01-31
  CHANGE_ID: UE.CHG.2026-01-31.SPC.GVN.INTEGRATION_PACKER.001
  TYPE: CREATE
  SUMMARY: Repacked to match TPL.SPECIALIST; added INTEGRATION_OUTPUT_PACK artifact schema; removed RAW; added legacy mapping.
  REASON: Make handoff deterministic and minimal while preserving traceability.
  IMPACT: Integration becomes repeatable: SoT + migration + next keys are explicit.
