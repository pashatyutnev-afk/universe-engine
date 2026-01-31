# FILE: UE_V2/11_LEX/04__CODES_VIS.md
SCOPE: UE_V2
LAYER: 11_LEX
DOC_TYPE: CODES
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.LEX.VIS.001
OWNER: SYSTEM
TITLE: VISUAL STATE CODES (LAW-15)

## MARKERS
- [M] STATES
- [M] EVENTS
- [M] RULE_TAGS

## [M] STATES
- ZP      : Zero Point mode (black field + white point)
- GLT     : glitch burst (controlled)
- HALL    : fear-as-hall transform (industrial hall snap)
- AIR     : high transparency / DOF openness
- MAT     : matte wear texture (low sheen, gritty)
- NEON    : neon wet city block anchor
- STEAM   : fog/steam presence

## [M] EVENTS
- E.CFHI  : CF > threshold (crunch sync trigger)
- E.L13   : silence point active
- E.AIRUP : 8–16k energy rise (air opens)
- E.AIRDN : 8–16k drop (claustrophobic)

## [M] RULE_TAGS
- ONECHAR : only one character
- ONELOC  : same location continuity
- NOLOGO  : no logos/readable env text
- NOCOLL  : no collage/panels/splits
