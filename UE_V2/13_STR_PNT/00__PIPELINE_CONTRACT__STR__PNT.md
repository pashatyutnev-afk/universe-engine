FILE: UE_V2/13_STR_PNT/00__PIPELINE_CONTRACT__STR__PNT.md
SCOPE: UE_V2 / 13_STR_PNT
DOC_TYPE: PIPELINE_CONTRACT
DOMAIN: STR_PNT
UID: UE.V2.STR_PNT.PIPELINE_CONTRACT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: Contract has no RAW

---

## [M] PURPOSE
Step-run contract for STR_PNT realm.
Selects a start point by KEY only and hands off execution.

## [M] HARD_RULES
- No RAW inside this contract.
- Resolve targets via INDEX_MANIFEST only.
- Start points are deterministic presets; no guessing.

## [M] REQUIRED_KEYS (must exist in INDEX_MANIFEST)
- INDEX_MANIFEST
- PIPELINE_CONTRACT
- STR_PNT.NEW_TASK
- STR_PNT.PATCH_FIX
- STR_PNT.QA_FAIL
- STR_PNT.RELEASE_READY

## [M] SELECTOR (no guessing)
- NEW_TASK: STR_PNT.NEW_TASK
- PATCH_FIX: STR_PNT.PATCH_FIX
- QA_FAIL: STR_PNT.QA_FAIL
- RELEASE_READY: STR_PNT.RELEASE_READY

## [M] STEP-RUN

S0) SANITY
- ensure TASK_TEXT exists
- resolve INDEX_MANIFEST
- validate REQUIRED_KEYS exist

S1) SELECT
- if STR_PNT_HINT provided -> map via SELECTOR
- else default -> STR_PNT.NEW_TASK

S2) OPEN
- open selected start point doc by KEY (resolve via INDEX_MANIFEST)

S3) OUTPUT
- emit START_POINT_TOKEN:
  - selected_key
  - purpose_brief
  - next: "го"
