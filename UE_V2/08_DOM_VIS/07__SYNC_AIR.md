# FILE: UE_V2/08_DOM_VIS/07__SYNC_AIR.md
SCOPE: UE_V2
LAYER: 08_DOM_VIS
DOC_TYPE: SYNC_SPEC
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.VIS.SYNC.AIR.001
OWNER: SYSTEM
TITLE: SYNC AIR (8–16k → TRANSPARENCY / DOF)

## MARKERS
- [M] INTENT
- [M] RULE
- [M] VIS_CONTROLS
- [M] FAIL

## [M] INTENT
“Воздух” в миксе должен ощущаться как открытие пространства и чистота света.

## [M] RULE
AIR_t correlates to:
- transparency (haze clarity)
- depth of field openness
- perceived “afterglow” in highlights

## [M] VIS_CONTROLS
- AIR high: sharper reflections, cleaner fog, deeper focus, more glow
- AIR low: matte textures, thicker fog, shallower focus, tighter framing

## [M] FAIL
- if “air high” causes overexposed whites → REWORK.VIS.BLOWOUT
- if “air low” becomes unreadable black crush → REWORK.VIS.BLACK_CRUSH
