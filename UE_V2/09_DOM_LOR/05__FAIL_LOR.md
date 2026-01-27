# FILE: UE_V2/09_DOM_LOR/05__FAIL_LOR.md
SCOPE: UE_V2
LAYER: 09_DOM_LOR
DOC_TYPE: FAIL_SPEC
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.LOR.FAIL.001
OWNER: SYSTEM
TITLE: LORE FAIL CODES

## MARKERS
- [M] FAIL_LIST
- [M] REWORK_ACTIONS

## [M] FAIL_LIST
- REWORK.LOR.UNGROUNDED      : lore claims event without metric support
- REWORK.LOR.RI_MISMATCH     : language collapse claimed but RI high
- REWORK.LOR.CANON_CONFLICT  : contradicts locked canon
- REWORK.LOR.NEW_COSMOLOGY   : introduces new cosmology without allowance
- REWORK.LOR.TOO_VAGUE       : no concrete event/state, only vibes
- REWORK.LOR.NO_HOOK         : no rule hook / no trigger note
- REWORK.LOR.REPEAT          : repeats same event across tracks without variation

## [M] REWORK_ACTIONS
- tie event to a trigger (RI/WTI/CF/LRA/LAW-13)
- reduce scope: 1 event per track
- enforce CANON_LOCK constraints
- add 1-line “why” (trigger note)
