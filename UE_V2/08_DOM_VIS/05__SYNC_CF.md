# FILE: UE_V2/08_DOM_VIS/05__SYNC_CF.md
SCOPE: UE_V2
LAYER: 08_DOM_VIS
DOC_TYPE: SYNC_SPEC
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.VIS.SYNC.CF.001
OWNER: SYSTEM
TITLE: SYNC CF (CREST → IMPACT VISUALS)

## MARKERS
- [M] INTENT
- [M] RULE
- [M] OUTPUT_EFFECTS
- [M] FAIL

## [M] INTENT
Пики энергии должны иметь визуальный “удар”, но без разрушения кадра.

## [M] RULE
- if CF > 14 dB: allow GLT2 impacts on drum transients (snare/kick)
- if 12.5–14 dB: allow subtle impact cues (light pulse, ripple, vibration)
- if < 12.5: no glitch, only natural reactions (rain, fabric, reflections)

## [M] OUTPUT_EFFECTS
- puddle ripple synchronized
- light flicker synchronized
- micro vibration of cables / wet metal surfaces

## [M] FAIL
- if effects look like overlay/VFX layer → REWORK.VIS.GLT_OVERLAY
- if subject readability breaks → REWORK.VIS.SUBJECT_LOST
