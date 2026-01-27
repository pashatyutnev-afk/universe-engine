# FILE: UE_V2/08_DOM_VIS/06__SYNC_LRA.md
SCOPE: UE_V2
LAYER: 08_DOM_VIS
DOC_TYPE: SYNC_SPEC
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.VIS.SYNC.LRA.001
OWNER: SYSTEM
TITLE: SYNC LRA (LAW-13 SILENCE POINT)

## MARKERS
- [M] INTENT
- [M] ENTRY_CONDITION
- [M] ZP_MODE
- [M] EXIT_CONDITION
- [M] LEGALITY

## [M] INTENT
Определить “тишину” как художественный режим, который удерживает внимание.

## [M] ENTRY_CONDITION
Enter ZP_MODE if:
- LAW-13 flag true
- RMS drop ≥ 12 dB (declared section)
- sub anchor remains (optional but recommended)

## [M] ZP_MODE
- visual: black field + single white point (or minimal silhouette)
- motion: almost none, slow drift only
- sound-driven note: point pulses faintly with sub-bass

## [M] EXIT_CONDITION
- return on next impact/chorus hit
- use snap-back transition (no long montage)

## [M] LEGALITY
If LRA > 12 but LAW-13 is not declared → REWORK.VIS.LRA_ILLEGAL
