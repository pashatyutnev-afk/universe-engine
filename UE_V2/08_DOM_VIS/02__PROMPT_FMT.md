# FILE: UE_V2/08_DOM_VIS/02__PROMPT_FMT.md
SCOPE: UE_V2
LAYER: 08_DOM_VIS
DOC_TYPE: FORMAT_SPEC
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.VIS.FMT.PROMPT.001
OWNER: SYSTEM
TITLE: PROMPT FORMAT (5s CHUNKS)

## MARKERS
- [M] INTENT
- [M] STRUCTURE
- [M] REQUIRED_FIELDS
- [M] NEGATIVE
- [M] CONTINUITY

## [M] INTENT
Единый формат, чтобы видео было “одним фильмом”, а не набором разных клипов.

## [M] STRUCTURE
Каждый чанκ (5s) = один промпт:
- TITLE
- DURATION
- SCENE (what/where)
- SHOTS (timecodes inside 5s)
- CAMERA / LOOK
- SYNC NOTES (CF/LRA/AIR triggers)
- NEGATIVE (strict)

## [M] REQUIRED_FIELDS
- location: one consistent place (unless narrative says change)
- subject: count + description (usually 1 lone figure)
- lighting: consistent logic (neon/rain/fog etc.)
- lens: fixed per sequence (example 35mm cinematic)
- motion: smooth + subtle handheld (no drone unless allowed)

## [M] NEGATIVE
Always include “NO” list:
- NO split-screen / collage / frames / borders
- NO drones / surveillance / robots / extra characters
- NO weapons / explosions
- NO logos / readable text in environment / burned subtitles

## [M] CONTINUITY
- keep same main character
- keep same wardrobe silhouette
- keep same weather/atmosphere unless change is an explicit beat
