# FILE: UE_V2/07_DOM_AUD/08__FAIL_AUD.md
SCOPE: UE_V2
LAYER: 07_DOM_AUD
DOC_TYPE: FAIL_SPEC
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.AUD.FAIL.001
OWNER: SYSTEM
TITLE: AUDIO FAIL CODES

## MARKERS
- [M] FAIL_LIST
- [M] REWORK_ACTIONS
- [M] NOTES

## [M] FAIL_LIST
- REWORK.AUD.RI_LOW        : RI_t < 0.62 in lyric sections
- REWORK.AUD.MASK_250_500   : vocal masked by low-mids (mud)
- REWORK.AUD.CF_LOW         : CF_3s_P50 below threshold
- REWORK.AUD.LRA_ILLEGAL    : LRA > 12 without LAW-13 marker
- REWORK.AUD.CLONE_RISK     : ΔAIR/ΔLM too similar across tracks
- REWORK.AUD.LOW_END_LOOSE  : low end not tight, sub uncontrolled
- REWORK.AUD.HARSH_AIR      : 8–16k painful/aliasing (fatigue risk)
- REWORK.AUD.SMEAR_REVERB   : reverb smear kills consonants

## [M] REWORK_ACTIONS
- RI_LOW / MASK_250_500: carve 250–500 in guitars/bus; reduce vocal tail; push consonants
- CF_LOW: restore transients; ease bus limiting; re-balance kick/snare peaks
- LRA_ILLEGAL: either declare LAW-13 + justify, or compress arrangement to legal LRA
- CLONE_RISK: adjust ΔAIR/ΔLM within safe band; change arrangement texture
- LOW_END_LOOSE: anchor 30–60; tame 80–200; mono-sub policy

## [M] NOTES
Любой FAIL → REWORK_REQUIRED, кроме STOP (RAW/marker/input).
