FILE: UE_V2/11_TKN/00__PIPELINE_CONTRACT__TKN.md
SCOPE: UE_V2 / 11_TKN
DOC_TYPE: PIPELINE_CONTRACT
DOMAIN: TKN
UID: UE.V2.TKN.PIPELINE_CONTRACT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: Contract has no RAW

---

## [M] PURPOSE
Step-run contract for 11_TKN.
Selects token schema docs by KEY only and opens minimal required set.

## [M] HARD_RULES
- No RAW inside this contract.
- Resolve targets via INDEX_MANIFEST only.
- No guessing: TKN_HINT required unless default ALL.

## [M] REQUIRED_KEYS (must exist in INDEX_MANIFEST)
- INDEX_MANIFEST
- PIPELINE_CONTRACT
- TKN.BRIEF
- TKN.STYLE
- TKN.STRUCTURE
- TKN.LYRICS
- TKN.QA

## [M] SELECTOR (no guessing)
- ALL: [TKN.BRIEF, TKN.STYLE, TKN.STRUCTURE, TKN.LYRICS, TKN.QA]
- BRIEF: [TKN.BRIEF]
- STYLE: [TKN.STYLE]
- STRUCTURE: [TKN.STRUCTURE]
- LYRICS: [TKN.LYRICS]
- QA: [TKN.QA]

## [M] STEP-RUN

S0) SANITY
- ensure TASK_TEXT exists
- resolve INDEX_MANIFEST via KEY: INDEX_MANIFEST
- validate REQUIRED_KEYS exist in INDEX_MANIFEST

S1) SELECT
- if TKN_HINT missing -> default to ALL
- else map via SELECTOR

S2) OPEN
- open selected token docs by KEY (resolve via INDEX_MANIFEST)

S3) OUTPUT
- emit TKN_TOKEN:
  - opened_keys
  - next: "го"
