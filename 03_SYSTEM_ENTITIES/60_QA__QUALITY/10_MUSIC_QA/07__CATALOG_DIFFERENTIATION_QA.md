# CATALOG DIFFERENTIATION — QA
FILE: 03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/07__CATALOG_DIFFERENTIATION_QA.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: QUALITY (QA)
QA_REALM: 10_MUSIC_QA
DOC_TYPE: QA_CHECK
QA_TYPE: CATALOG_DIFFERENTIATION
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.QA.MUS.CATALOG_DIFFERENTIATION.001
OWNER: SYSTEM
ROLE: A human/heuristic differentiation audit:
checks if the candidate track feels meaningfully different from the nearest neighbors in the catalog,
even if it passes validators. Prevents “same track again” syndrome by focusing on perception-level uniqueness.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created Catalog Differentiation QA: nearest-neighbor listening protocol and PASS/WARN/FAIL differentiation rubric."
- REASON: "Validator scores can pass while humans still hear sameness; QA catches perceptual duplicates."
- IMPACT: "Stronger catalog identity and higher listener trust."
- CHANGE_ID: UE.CHG.2026-01-12.QA.CATALOG_DIFF.001

---

## 0) PURPOSE (LAW)
Answer:
**“Does this feel like a new track, not a near-duplicate?”**

This is a perception-level QA check. It complements Collision Blocker VAL.

---

## 1) INPUTS
Required:
- Candidate take (audio)
- 1–3 nearest neighbor references (audio) from the same scope:
  - SCOPE_MODE: {GROUP | ALBUM | GLOBAL}
  - NEIGHBORS: [N1, N2, ...]
Optional:
- fingerprint summary (hooks/voices/palette tokens)
- collision score output (for context only)

---

## 2) PROCEDURE (HOW TO RUN)
1) Listen to candidate hook section + a 10–15s clip window.
2) Listen to the hook/clip of each nearest neighbor (same windows).
3) Answer quickly:
   - “If I heard this on a feed, would I think it’s the same song family or the same song?”
4) Output RESULT + NOTES + FIX_SUGGESTION.

---

## 3) DIFFERENTIATION RUBRIC (HEURISTIC)
Check these dimensions:

### D1 — Hook feel difference
- Is the hook grammar/contour noticeably different?
- Or does it chant the same type of slogan the same way?

### D2 — Vocal identity difference (if vocal)
- Does the voice character/role feel different?
- Or does it sound like the same singer again?

### D3 — Palette/timbre difference
- Does the dominant timbre palette change?
- Or is it the same synth/drum color again?

### D4 — Groove/tempo feel difference
- Is there a different rhythmic feel or tempo band?

### D5 — Signature tag behavior
- Is S-tag/motif distinct?
- Or does it reuse the same stamp pattern?

---

## 4) RESULT (PASS/WARN/FAIL)
PASS when:
- at least 2–3 dimensions (D1..D5) are clearly different
- listener would not confuse it with nearest neighbors

WARN when:
- feels too close in 1–2 major dimensions but fixable with one novelty knob

FAIL when:
- perceptually feels like the same track again
- multiple major dimensions match neighbors (hook + vocal + palette)

---

## 5) FIX SUGGESTION KNOBS (1–2 MAX)
Pick minimal changes:
- CHANGE_HOOK_GRAMMAR:
  - chant → motif, slogan → motif, etc.
- CHANGE_VOCAL_ROLE:
  - lead vs contrast, duet split, or instrumental variant
- CHANGE_PALETTE:
  - swap dominant timbre family
- CHANGE_GROOVE_BAND:
  - shift tempo band or groove feel
- CHANGE_S_TAG:
  - new signature tag stamp

---

## 6) OUTPUT TEMPLATE (MANDATORY)
CATALOG_DIFFERENTIATION_QA_RESULT:
- TRACK_UID:
- TAKE_ID:
- SCOPE_MODE:
- NEAREST_NEIGHBORS: [id...]
- RESULT: {PASS | WARN | FAIL}
- NOTES:
  - 3–10 bullets
- FIX_SUGGESTION:
  - 1–2 knobs max

---

## 7) REFERENCES (RAW)
Policy/validator context:
- Fingerprint Collision Thresholds CTL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/06__FINGERPRINT_COLLISION_THRESHOLDS_CTL.md
- Collision Blocker VAL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/05__COLLISION_BLOCKER_VAL.md

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
