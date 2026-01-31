FILE: UE_V2/12_LEX/00__PIPELINE_CONTRACT__LEX.md
SCOPE: UE_V2 / 12_LEX
DOC_TYPE: PIPELINE_CONTRACT
DOMAIN: LEX
UID: UE.V2.LEX.PIPELINE_CONTRACT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: Contract has no RAW

---

## [M] PURPOSE
Step-run contract for 12_LEX.
Selects lexicon reference sets by KEY only and opens minimal required docs.

## [M] HARD_RULES
- No RAW inside this contract.
- Resolve targets via INDEX_MANIFEST only.
- No guessing: LEX_HINT required unless default.

## [M] REQUIRED_KEYS (must exist in INDEX_MANIFEST)
- INDEX_MANIFEST
- PIPELINE_CONTRACT
- LEX.CODES.LAW
- LEX.CODES.MET
- LEX.CODES.PIPE
- LEX.CODES.VIS
- LEX.ABBR_RULES

## [M] SELECTOR (no guessing)
- ALL: [LEX.CODES.LAW, LEX.CODES.MET, LEX.CODES.PIPE, LEX.CODES.VIS, LEX.ABBR_RULES]
- LAW: [LEX.CODES.LAW]
- MET: [LEX.CODES.MET]
- PIPE: [LEX.CODES.PIPE]
- VIS: [LEX.CODES.VIS]
- ABBR: [LEX.ABBR_RULES]

## [M] STEP-RUN

S0) SANITY
- ensure TASK_TEXT exists
- resolve INDEX_MANIFEST via KEY: INDEX_MANIFEST
- validate REQUIRED_KEYS exist in INDEX_MANIFEST

S1) SELECT
- if LEX_HINT missing -> default to ALL
- else map via SELECTOR

S2) OPEN
- open selected docs by KEY (resolve via INDEX_MANIFEST)

S3) OUTPUT
- emit LEX_TOKEN:
  - opened_keys
  - next: "го"
