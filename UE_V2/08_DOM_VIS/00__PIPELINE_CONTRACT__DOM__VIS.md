FILE: UE_V2/08_DOM_VIS/00__PIPELINE_CONTRACT__DOM__VIS.md
SCOPE: UE_V2 / 08_DOM_VIS
DOC_TYPE: PIPELINE_CONTRACT
DOMAIN: DOM_VIS
UID: UE.V2.DOM.VIS.PIPELINE_CONTRACT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: Contract has no RAW

---

## [M] PURPOSE
Step-run contract for VIS domain.
Resolves VIS documents by KEY via INDEX_MANIFEST and executes minimal VIS workflow for prompt/render output.

## [M] HARD_RULES
- No RAW inside this contract.
- Resolve targets via INDEX_MANIFEST only.
- Minimal opens first: VIS.INDEX + VIS.PROMPT_FMT + VIS.SHOT_RULES + VIS.PACK.
- Law mapping is mandatory for canon constraints: VIS.LAW15_MAP.

## [M] REQUIRED_KEYS (must exist in INDEX_MANIFEST)
- INDEX_MANIFEST
- PIPELINE_CONTRACT
- VIS.INDEX
- VIS.LAW15_MAP
- VIS.PROMPT_FMT
- VIS.SHOT_RULES
- VIS.PACK

## [M] STEP-RUN (high level)

S0) SANITY
- ensure TASK_TEXT exists
- resolve INDEX_MANIFEST
- validate REQUIRED_KEYS exist

S1) LOAD_CORE (MUST_LOAD)
- open: VIS.INDEX
- open: VIS.LAW15_MAP
- open: VIS.PROMPT_FMT
- open: VIS.SHOT_RULES
- open: VIS.PACK

S2) OPTIONAL_LOAD (by need)
- if glitch topic present / style risky -> open VIS.GLITCH_RULES
- if external pipeline sync required -> open VIS.SYNC.CF / VIS.SYNC.LRA / VIS.SYNC.AIR
- if recovery needed -> open VIS.FAIL

S3) OUTPUT
- emit VIS_TOKEN:
  - opened_keys
  - prompt_format (key reference)
  - shot_constraints (key reference)
  - packaging_requirements (key reference)
- NEXT: "го"
