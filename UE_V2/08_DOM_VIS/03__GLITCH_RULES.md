# FILE: UE_V2/08_DOM_VIS/03__GLITCH_RULES.md
SCOPE: UE_V2
LAYER: 08_DOM_VIS
DOC_TYPE: RULES
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.VIS.RULE.GLITCH.001
OWNER: SYSTEM
TITLE: GLITCH RULES (ALLOWED / FORBIDDEN)

## MARKERS
- [M] ALLOWED
- [M] FORBIDDEN
- [M] INTENSITY_LEVELS
- [M] TRIGGERS

## [M] ALLOWED
- micro glitch on impacts (1–3 frames feel)
- subtle flicker, chromatic micro shift, scanline hint
- particle artifacts that look like environment (rain/steam noise)

## [M] FORBIDDEN
- UI overlays, HUD, visible “effects layer”
- heavy datamosh that breaks subject recognition
- split-screen, panels, montage frames
- glitch that changes character identity or location continuity

## [M] INTENSITY_LEVELS
- GLT0: none
- GLT1: minimal (rare, subtle)
- GLT2: impacts synced (allowed when CF > 14)
- GLT3: extreme (only if explicitly requested, otherwise illegal)

## [M] TRIGGERS
- CF > 14 dB → GLT2 permitted on transients
- otherwise default GLT1 or GLT0
