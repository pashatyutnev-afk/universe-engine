# VOICE DIVERSITY VALIDATOR (VAL)
SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: VALIDATORS (VAL)
FAMILY: 10_MUSIC_VALIDATORS
DOC_TYPE: VALIDATOR
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.MUS.VAL.VOICE_DIVERSITY.001
OWNER: SYSTEM
ROLE: Ensures tracks/albums do not collapse into “one same singer/voice”.

---

## PURPOSE
Prevent voice monotony and enforce cast diversity in group/album.

---

## INPUT
- Group Cast (vocal + instrument roles)
- Album Blueprint (voice rotation plan)
- Track Card (assigned artist/roles)
- QA Voice Audit results (if available)

---

## PASS CONDITIONS
- Track assigns correct member roles (Lead/Contrast/Narrator/Hook Carrier as needed)
- Album rotation limits are respected (Lead not 100% everywhere)
- No repeated identical “voice archetype” pattern across many tracks.

---

## FAIL CONDITIONS
- Same archetype dominates beyond allowed threshold.
- Track lacks planned contrast/secondary voice when required by blueprint.
- Voice assignment missing/undefined.

---

## OUTPUT
- PASS / FAIL + short reason + suggested fix (e.g., swap to Contrast)

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED
