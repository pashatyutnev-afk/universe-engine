FILE: UE_V2/10_REL/00__PIPELINE_CONTRACT__REL.md
SCOPE: UE_V2 / 10_REL
DOC_TYPE: PIPELINE_CONTRACT
DOMAIN: REL
UID: UE.V2.REL.PIPELINE_CONTRACT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: Contract has no RAW

---

## [M] PURPOSE
Step-run contract for 10_REL.
Resolves release docs by KEY via INDEX_MANIFEST and produces RELEASE_READY decisions / packaging pointers.

## [M] HARD_RULES
- No RAW inside this contract.
- Resolve targets via INDEX_MANIFEST only.
- Minimal opens: readiness matrix + pack rules first; open others only if needed.

## [M] REQUIRED_KEYS (must exist in INDEX_MANIFEST)
- INDEX_MANIFEST
- PIPELINE_CONTRACT
- REL.READINESS_MATRIX
- REL.PACK_REL
- REL.REWORK

## [M] STEP-RUN (high level)

S0) SANITY
- ensure TASK_TEXT exists
- resolve INDEX_MANIFEST
- validate REQUIRED_KEYS exist

S1) LOAD_READY_SET
- open: REL.READINESS_MATRIX
- open: REL.PACK_REL
- open: REL.REWORK

S2) DECIDE
- produce REL_TOKEN:
  - readiness_state (READY|NOT_READY|GAP)
  - required_fixes (if any)
  - packaging_pointers_required

S3) OPTIONAL_OPENS
- if task needs scheduling -> open REL.CAL_A
- if arc change risk -> open REL.ARC_IMPACT
- if UID audit needed -> open REL.UID_TRACK
- if drop policy question -> open REL.DROP_RULES
- if post-release plan -> open REL.POST_REL

S4) OUTPUT
- emit REL_TOKEN
- NEXT: "го"
