# FILE: UE_V2/08_DOM_VIS/01__LAW15_MAP.md
SCOPE: UE_V2
LAYER: 08_DOM_VIS
DOC_TYPE: SPEC
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.VIS.LAW15.001
OWNER: SYSTEM
TITLE: LAW-15 MAP (AUDIO → VISUAL BRIDGE)

## MARKERS
- [M] INTENT
- [M] INPUTS
- [M] OUTPUTS
- [M] CORE_MAP
- [M] PRIORITIES
- [M] LEGALITY

## [M] INTENT
Математический мост: звук управляет картиной. Визуал обязан быть интерпретацией метрик, а не случайной иллюстрацией.

## [M] INPUTS
- CF_3s_P50 (crest)
- LRA (loudness range)
- AIR energy proxy (8–16 kHz band energy) → AIR_t
- LAW-13 flag (silence point declared)
- section map (A/B, timestamps or chunk map)

## [M] OUTPUTS
- VIS_STATE timeline (переключатели)
- per-chunk prompt directives (camera, texture, light, glitch)
- fail/pass notes by rules

## [M] CORE_MAP
1) Crest Factor Sync (CF → glitch/impact)
- if CF > 14 dB: enable GLT_IMPACTS (micro glitch artifacts) on transients
- else: GLT minimized or off

2) LRA Inversion Sync (LAW-13)
- if LAW-13 true and RMS drop ≥ 12 dB: enter ZP_MODE (Zero Point)
- ZP_MODE: white point on black / minimal motion / near-silence visual tension

3) Spectral Mapping (AIR 8–16 kHz)
- AIR_t ↑ → transparency ↑, depth-of-field “opens”, haze becomes clean
- AIR_t ↓ → claustro: matte, fog thick, shallow visibility, tighter framing

## [M] PRIORITIES
- continuity > spectacle
- single location/character continuity unless explicitly changed
- sync events must be readable: do not overload with effects

## [M] LEGALITY
- “glitch” is allowed only as micro artifacts, never as UI overlays or split screens
- no readable text in environment, no logos, no subtitles burned into scene
