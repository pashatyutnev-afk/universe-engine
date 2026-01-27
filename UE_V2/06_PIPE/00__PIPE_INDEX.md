# FILE: UE_V2/06_PIPE/00__PIPE_INDEX.md
SCOPE: UE_V2
LAYER: 06_PIPE
DOC_TYPE: INDEX
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.PIPE.IDX.001
OWNER: SYSTEM
TITLE: PIPE INDEX

## MARKERS
- [M] PIPE_LIST
- [M] CTL_LIST
- [M] VAL_LIST
- [M] QA_LIST
- [M] SIGNOFF

## [M] PIPE_LIST
- 01__PIPE_DEFAULT : default runtime pipeline (task → artifact → gates)
- 02__PIPE_GAP     : missing entity/template → create → resume
- 03__PIPE_AUD     : audio production pipeline (ORUM-A/B)
- 04__PIPE_VIS     : visual production pipeline (LAW-15 mapping)
- 05__PIPE_LOR     : lore production pipeline (metrics→canon)

## [M] CTL_LIST
- 06__CTL_READINESS : readiness gate (inputs/markers/links)
- 07__CTL_NOISE     : noise budget enforcement

## [M] VAL_LIST
- 08__VAL_DOC : validate doc format/markers/uid/name
- 09__VAL_AUD : validate audio metrics thresholds/clone-safe deltas
- 10__VAL_VIS : validate visual mapping compliance

## [M] QA_LIST
- 11__QA_ACCEPT : acceptance scoring + rework routing
- 12__QA_PACK   : package completeness check

## [M] SIGNOFF
- 13__SIGNOFF : final signoff chain (CTL→VAL→QA→DOC CTRL→MA SPC)
