# CREDITS & METADATA POLICY (CTL)
SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: CONTROLLERS (CTL)
FAMILY: 10_MUSIC_CONTROLLERS
DOC_TYPE: CONTROLLER
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.MUS.CTL.CREDITS_METADATA.001
OWNER: SYSTEM
ROLE: Defines the minimum required credits/metadata fields for every track release and documentation.

---

## PURPOSE
Ensure releases are consistent, searchable, and rights-safe (especially when using poetic sources).

---

## MINIMUM METADATA (REQUIRED)
- GROUP_NAME
- ALBUM_NAME (or SINGLE)
- TRACK_TITLE
- TRACK_UID
- RELEASE_VERSION
- PLATFORM_TARGETS (TikTok/Shorts/Spotify/YT etc.)
- LANGUAGE (primary)
- GENRE_STACK (short)
- MOOD_STACK (short)

---

## CREDITS (REQUIRED)
### Core music
- Music: (AI-assisted / system)
- Arrangement:
- Mix:
- Master:

### Vocals / roles (if applicable)
- Lead vocal:
- Contrast vocal:
- Hook carrier:
- Choir/stack:

### Poetry / text (if applicable)
- TEXT_MODE: VERBATIM_PD | ADAPTATION | INSPIRED
- AUTHOR:
- WORK:
- SOURCE_REF (internal ref to PD corpus record)
- ATTRIBUTION_LINE (how to credit)

---

## RIGHTS RULES (HARD)
- VERBATIM usage allowed only when PD_OK is confirmed (per POET_PD_POLICY_CTL).
- If PD_OK not confirmed: only ADAPTATION/INSPIRED allowed and must be labeled.

---

## OUTPUT STANDARD (WHERE THIS APPLIES)
- Track Card: must include TEXT_MODE + basic credits
- Track Release document: must include full credits block

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED
