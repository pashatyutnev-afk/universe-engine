# LOOP 15s — QA
FILE: 03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/02__LOOP_15S_QA.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: QUALITY (QA)
QA_REALM: 10_MUSIC_QA
DOC_TYPE: QA_CHECK
QA_TYPE: LOOP_15S
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.QA.MUS.LOOP_15S.001
OWNER: SYSTEM
ROLE: A short-form viability listening test:
can a 10–15s segment be looped multiple times without annoyance?
Evaluates “loop imprint”, repeat-safe hook feel, and edit-friendly continuity.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created Loop 15s QA: procedure and PASS/WARN/FAIL for loopability and annoyance risk."
- REASON: "UGC success requires loopable segments; non-loopable clips reduce creator reuse."
- IMPACT: "Higher replay potential and better clip economics."
- CHANGE_ID: UE.CHG.2026-01-12.QA.LOOP15.001

---

## 0) PURPOSE (LAW)
Answer:
**“Does a 10–15s clip loop cleanly and stay enjoyable after repeats?”**

This is a human/heuristic gate.

---

## 1) INPUTS
- audio take (candidate)
- selected clip window (preferred), or choose the best 10–15s window
- optional: UGC_INTENT (YES/NO)

---

## 2) PROCEDURE (HOW TO RUN)
1) Choose a candidate clip window (10–15s).
2) Loop it 3 times (minimum).
3) Evaluate:
   - does it still feel good?
   - is the seam ugly?
   - does repetition annoy quickly?

---

## 3) EVALUATION CRITERIA
### C1 — Seam quality
- loop point does not feel broken or awkward

### C2 — Repeat-safe hook feel
- repeats feel addictive, not irritating

### C3 — Density balance
- not too busy (fatiguing)
- not too empty (boring)

### C4 — Edit friendliness
- clip window has a clean cut point or obvious hook

---

## 4) RESULT (PASS/WARN/FAIL)
PASS when:
- clip loops cleanly
- no fast-annoyance after 3 repeats

WARN when:
- clip is loopable but seam or annoyance risk exists (fixable)

FAIL when:
- seam is ugly/broken
- repetition becomes irritating quickly
- clip feels unusable for creators

---

## 5) FIX SUGGESTION KNOBS (1–2 MAX)
- LOOP_IMPRINT:
  - add end-stamp / tail that loops cleanly
- SIMPLIFY_DENSITY:
  - reduce clutter, make hook clearer
- VARIATION_MICRO:
  - add tiny variation on repeat to avoid irritation
- CUT_POINT_REDESIGN:
  - create a cleaner edit point near hook

---

## 6) OUTPUT TEMPLATE (MANDATORY)
LOOP_15S_QA_RESULT:
- TRACK_UID:
- TAKE_ID:
- CLIP_WINDOW: [start_sec..end_sec]
- RESULT: {PASS | WARN | FAIL}
- NOTES:
  - 3–7 bullets
- FIX_SUGGESTION:
  - 1–2 knobs max

---

## 7) REFERENCES (RAW)
UGC policy context:
- UGC Viral Ruleset CTL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/02__UGC_VIRAL_RULESET_CTL.md

Used in gate ORC:
- Track TEST → DOC Gate ORC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/03__TRACK_TEST_DOC_GATE_ORC.md

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
