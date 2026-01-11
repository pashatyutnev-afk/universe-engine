# CREDITS & RIGHTS VALIDATOR (VAL)
SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: VALIDATORS (VAL)
FAMILY: 10_MUSIC_VALIDATORS
DOC_TYPE: VALIDATOR
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.MUS.VAL.CREDITS_RIGHTS.001
OWNER: SYSTEM
ROLE: PASS/FAIL validation for credits and rights compliance (especially poetry sources).

---

## PURPOSE
Block release/documentation promotion if rights/credits metadata is incomplete or inconsistent.

---

## INPUT
- Track Card (POET_SOURCE + mode)
- Release Pack Manifest (credits/metadata section)
- CTL: POET_PD_POLICY_CTL
- CTL: CREDITS_METADATA_POLICY_CTL (when created)

---

## PASS CONDITIONS
- If POETRY is used verbatim:
  - source is PD_OK recorded
  - attribution fields present (author/work)
- If not PD_OK:
  - mode is explicitly ADAPTATION/INSPIRED (not verbatim)
- Credits block exists and contains required minimum fields.

---

## FAIL CONDITIONS
- Missing author/work attribution when poetry is used.
- Verbatim usage without PD_OK proof.
- Credits missing in release documentation.

---

## OUTPUT
- PASS / FAIL + short reason

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED
