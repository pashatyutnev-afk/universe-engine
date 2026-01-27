# FILE: UE_V2/08_DOM_VIS/08__FAIL_VIS.md
SCOPE: UE_V2
LAYER: 08_DOM_VIS
DOC_TYPE: FAIL_SPEC
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.VIS.FAIL.001
OWNER: SYSTEM
TITLE: VISUAL FAIL CODES

## MARKERS
- [M] FAIL_LIST
- [M] REWORK_ACTIONS

## [M] FAIL_LIST
- REWORK.VIS.GLT_OVERLAY     : glitch looks like overlay/effect layer
- REWORK.VIS.SUBJECT_LOST    : main character not readable / identity drift
- REWORK.VIS.CONTINUITY_BREAK: location/weather/wardrobe breaks without intent
- REWORK.VIS.TEXT_IN_ENV     : readable text/logos appear in environment
- REWORK.VIS.SPLIT_SCREEN    : any panels/frames/collage
- REWORK.VIS.DRONE_ILLEGAL   : drone/overseer angle used without allowance
- REWORK.VIS.LRA_ILLEGAL     : ZP_MODE used without LAW-13
- REWORK.VIS.BLOWOUT         : highlights blown, detail lost
- REWORK.VIS.BLACK_CRUSH     : crushed blacks, scene unreadable
- REWORK.VIS.TOO_MANY_CHARS  : extra characters appear

## [M] REWORK_ACTIONS
- reduce glitch level (GLT2→GLT1)
- lock continuity: same block, same figure, same lighting logic
- strengthen negative prompt block
- enforce “single full-frame shot” guidance
