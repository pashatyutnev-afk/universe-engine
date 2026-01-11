# REGRESSION GUARD (QA)
SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: QUALITY (QA)
FAMILY: 10_MUSIC_QA
DOC_TYPE: QA_TEST
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.MUS.QA.REGRESSION_GUARD.001
OWNER: SYSTEM
ROLE: Ensures new releases do not get worse than the group’s “golden set”.

---

## PURPOSE
Stop quality degradation over time.

---

## INPUT
- Golden Set references (best tracks so far)
- Candidate track (best take)

---

## CHECKS (MINIMUM)
- 5s scroll-stop not worse
- hook clarity not worse
- UGC usability not worse
- mix translation not worse

---

## OUTPUT
- PASS/FAIL + short reason
- If FAIL: specify what needs improvement before promotion

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED
