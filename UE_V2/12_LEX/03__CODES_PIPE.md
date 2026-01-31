# FILE: UE_V2/11_LEX/03__CODES_PIPE.md
SCOPE: UE_V2
LAYER: 11_LEX
DOC_TYPE: CODES
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.LEX.PIPE.001
OWNER: SYSTEM
TITLE: PIPELINE / STATUS CODES

## MARKERS
- [M] PIPE
- [M] FLAGS

## [M] PIPE
- P.DEF   : default pipeline
- P.GAP   : gap pipeline (create missing)
- P.AUD   : audio pipeline
- P.VIS   : visual pipeline
- P.LOR   : lore pipeline
- P.REL   : release pipeline

## [M] FLAGS
- R.OK    : readiness OK
- R.RWK   : REWORK_REQUIRED
- R.HOLD  : HOLD (missing inputs/package)
- R.ANOM  : anomaly allowed (L13 declared + profile match)
- R.STOP  : hard stop (only STOP rules)
