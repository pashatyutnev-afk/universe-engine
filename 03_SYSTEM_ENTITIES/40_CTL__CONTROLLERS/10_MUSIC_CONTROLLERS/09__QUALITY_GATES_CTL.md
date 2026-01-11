# MUSIC QUALITY GATES — CONTROLLER (CTL)
SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: CONTROLLERS (CTL)
FAMILY: 10_MUSIC_CONTROLLERS
DOC_TYPE: CONTROLLER
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.MUS.CTL.QUALITY_GATES.001
OWNER: SYSTEM
ROLE: Single source of truth for music pass/fail gates used by ORC/VAL/QA.

---

## PURPOSE (LAW)
This controller defines mandatory quality gates for music production.

If a gate fails, the track is NOT promoted to documentation/release.

---

## GATES (MINIMUM SET)
1) PROMPT FIDELITY — platform executed the contract with minimal “from itself”
2) HOOK TIMING — micro hook + chorus hook deadlines met
3) EARWORM — hook stack exists; repeat-with-variation present
4) UGC READY — moment map + transition/stop moment + clip usability
5) REPEAT GUARD — no endless lyrical/melodic loops
6) POETRY RIGHTS — verbatim use allowed only for PD_OK sources (otherwise ADAPTATION mode)
7) CATALOG COLLISION — not too similar to our own released material
8) RELEASE PACK READY — required variants prepared (main/inst/cuts etc.)

---

## OUTPUT (STANDARD)
- A PASS/FAIL checklist for:
  - `VAL/10_MUSIC_VALIDATORS/*`
  - `QA/10_MUSIC_QA/*`
  - `ORC/10_MUSIC_ORCHESTRATORS/*`

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED
