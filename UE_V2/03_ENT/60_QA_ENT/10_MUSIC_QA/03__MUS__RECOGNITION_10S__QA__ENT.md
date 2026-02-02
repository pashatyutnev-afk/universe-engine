# RECOGNITION 10s — QA
FILE: 03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/03__RECOGNITION_10S_QA.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: QUALITY (QA)
QA_REALM: 10_MUSIC_QA
DOC_TYPE: QA_CHECK
QA_TYPE: RECOGNITION_10S
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.QA.MUS.RECOGNITION_10S.001
OWNER: SYSTEM
ROLE: A fast recognition test:
within 10 seconds, can a listener identify the track’s identity and latch onto “what it is”?
Evaluates early stamp, clarity, and recognizability without needing full context.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created Recognition 10s QA: procedure and PASS/WARN/FAIL for early identity and recognizability."
- REASON: "Even with good hooks later, tracks fail if they’re unrecognizable early."
- IMPACT: "Higher retention and better short-form performance."
- CHANGE_ID: UE.CHG.2026-01-12.QA.RECOG10.001

---

## 0) PURPOSE (LAW)
Answer:
**“By 10 seconds, is the identity recognizable?”**

This is a human/heuristic gate used with Hook Timing VAL and Scroll Stop QA.

---

## 1) INPUTS
- audio take (candidate)
- optional: duration mode (SHORT/FULL)
- optional: group/style fingerprint anchors summary

---

## 2) PROCEDURE (HOW TO RUN)
1) Listen 0:00–0:10 once.
2) Ask:
   - “Do I know what this is?”
   - “Is there a clear identity stamp?”
3) Output RESULT + NOTES + FIX_SUGGESTION.

---

## 3) EVALUATION CRITERIA
### C1 — Identity stamp heard?
- signature tag / motif / obvious palette is present early

### C2 — Clarity
- lead element is clear (vocal or motif)
- no muddy fog masking identity

### C3 — Genre/vibe recognizability
- listener can describe it quickly (genre/vibe)
- feels intentional, not random

### C4 — No confusion
Avoid:
- slow ambiguous intro
- chaotic or directionless first 10s
- voice unclear (if lyrical)

---

## 4) RESULT (PASS/WARN/FAIL)
PASS when:
- identity is clear by 10s
- listener can describe it and expects the hook form

WARN when:
- identity is somewhat present but weak (fixable)

FAIL when:
- identity not recognizable by 10s
- intro is ambiguous/boring/confusing

---

## 5) FIX SUGGESTION KNOBS (1–2 MAX)
- EARLY_STAMP:
  - add S-tag / signature motif at 0–5s
- CLARITY_FIX:
  - bring lead element forward; reduce mud
- DIRECT_ENTRY:
  - start on groove/hook-adjacent material
- SIMPLIFY_START:
  - remove confusing layers; make palette obvious

---

## 6) OUTPUT TEMPLATE (MANDATORY)
RECOGNITION_10S_QA_RESULT:
- TRACK_UID:
- TAKE_ID:
- RESULT: {PASS | WARN | FAIL}
- NOTES:
  - 3–7 bullets
- FIX_SUGGESTION:
  - 1–2 knobs max

---

## 7) REFERENCES (RAW)
Paired validator:
- Hook Timing VAL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/01__HOOK_TIMING_VAL.md

Used in gate ORC:
- Track TEST → DOC Gate ORC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/03__TRACK_TEST_DOC_GATE_ORC.md

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
