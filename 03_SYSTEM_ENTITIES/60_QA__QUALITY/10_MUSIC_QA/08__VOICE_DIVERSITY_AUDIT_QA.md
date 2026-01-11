# VOICE DIVERSITY AUDIT (QA)
SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: QUALITY (QA)
FAMILY: 10_MUSIC_QA
DOC_TYPE: QA_TEST
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.MUS.QA.VOICE_DIVERSITY.001
OWNER: SYSTEM
ROLE: Human/audio audit to confirm voices and roles are actually distinguishable.

---

## PURPOSE
Detect “one singer everywhere” problem early.

---

## METHOD
- Listen to:
  - 10s from 3 different tracks of the same group/album
  - chorus sections preferred
- Answer quickly:
  1) Can I tell different voices/roles apart?
  2) Does contrast exist (tone/delivery/role)?
  3) Is hook carrier consistent but not dominant?

---

## OUTPUT
- PASS/FAIL
- Notes:
  - what sounds same
  - what to change (cast swap, delivery change, prompt constraints)

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED
