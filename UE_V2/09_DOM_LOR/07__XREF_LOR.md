# FILE: UE_V2/09_DOM_LOR/07__XREF_LOR.md
SCOPE: UE_V2
LAYER: 09_DOM_LOR
DOC_TYPE: XREF
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.LOR.XREF.001
OWNER: SYSTEM
TITLE: XREF LORE ↔ AUDIO ↔ VISUAL

## MARKERS
- [M] INTENT
- [M] XREF_MAP
- [M] OUTPUT_FORMAT

## [M] INTENT
Единая карта соответствий: одно событие должно иметь аудио-причину и визуальную форму.

## [M] XREF_MAP
- LOR.STATE=LANG_FRACTURE
  - AUDIO: RI_t < 0.62 (>=2 sections)
  - VIS: tighter framing, matte textures, reduced AIR clarity

- LOR.STATE=EROSION
  - AUDIO: WTI_t ≥ 0.75 sustained
  - VIS: industrial wear textures, wet metal, grit, GLT1 only

- LOR.EVENT=HALL_FORMATION
  - AUDIO: CF peaks ≥ 13.5 + LRA ≥ 10
  - VIS: “street becomes hall then snaps back” beat

- LOR.STATE=ZERO_POINT_LOCK
  - AUDIO: LAW-13 + RMS drop ≥ 12 dB
  - VIS: ZP_MODE (white point on black)

## [M] OUTPUT_FORMAT
When referenced in reports:
- XREF: [LOR_EVENT_ID] → (AUDIO_HOOK) → (VIS_STATE)
