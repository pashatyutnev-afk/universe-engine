FILE: UE_V2/09_DOM_LOR/00__PIPELINE_CONTRACT__DOM__LOR.md
SCOPE: UE_V2 / 09_DOM_LOR
DOC_TYPE: PIPELINE_CONTRACT
DOMAIN: DOM_LOR
UID: UE.V2.DOM.LOR.PIPELINE_CONTRACT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: Contract has no RAW

---

## [M] PURPOSE
Step-run contract for LOR domain.
Resolves required LOR docs by KEY via INDEX_MANIFEST and executes minimal LOR workflow.

## [M] HARD_RULES
- No RAW inside this contract.
- Resolve targets via INDEX_MANIFEST only.
- Minimal opens first: LOR.TRIGGER + LOR.PACK (+ LOR.CANON_LOCK if canon-sensitive).

## [M] REQUIRED_KEYS (must exist in INDEX_MANIFEST)
- INDEX_MANIFEST
- PIPELINE_CONTRACT
- LOR.TRIGGER
- LOR.PACK
- LOR.CANON_LOCK

## [M] STEP-RUN (high level)

S0) SANITY
- ensure TASK_TEXT exists
- resolve INDEX_MANIFEST
- validate REQUIRED_KEYS exist

S1) LOAD_CORE
- open: LOR.TRIGGER
- open: LOR.PACK
- open: LOR.CANON_LOCK (only if canon changes implied)

S2) OPTIONAL_LOAD
- if language/readability constraint -> open LOR.RI_TO_LANG
- if arc/season context needed -> open LOR.ARC.S16
- if failure handling requested -> open LOR.FAIL
- if cross-links required -> open LOR.XREF

S3) OUTPUT
- emit LOR_TOKEN:
  - opened_keys
  - canon_sensitive (yes/no)
  - required_outputs (pack requirements)
- NEXT: "го"
