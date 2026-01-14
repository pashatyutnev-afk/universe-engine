# CASE — BAD (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/06__CASE_LIBRARY/02__CASE__BAD.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: CASE
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.CASE.PROMPT_ARCHITECT.BAD.001
OWNER: SYSTEM
ROLE: A "bad" prompt contract example designed to FAIL key gates due to contradictions, genre soup, overload, and missing structure clarity. Used to calibrate Gate 01 (contract clarity) and Gate 04 (style stability).

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Added BAD case for PROMPT_ARCHITECT: contradictions + overload + genre soup + unclear structure."
- REASON: "Need a concrete FAIL anchor for early gates calibration."
- IMPACT: "Helps detect and fix common prompt failure patterns."
- CHANGE_ID: UE.CHG.2026-01-14.KB.SPC.CASE.BAD.001

---

## 0) CASE RECORD
CASE_RECORD:
- CASE_ID: CASE-BAD-001
- TYPE: BAD
- CONTEXT:
  - FORMAT: FULL_SONG (~3:00)
  - LANGUAGE: RU
  - VOCAL_MODE: unclear / conflicting
  - GENRE: genre soup (too many)
- INPUT_INTENT (short):
  - "Make it everything at once: many genres, many instruments, huge energy, and also minimal, and also lo-fi, and also clean."

---

## 1) PROMPT CONTRACT (BAD EXAMPLE)
STYLE_BLOCK:
- nu metal + trap + dnb + synthwave + reggae + orchestral + hardstyle + lo-fi (all together)
- ANCHORS:
  - (none; just a long list)
- texture direction: clean aggressive mix AND lo-fi muddy cassette vibe (contradiction)
- rhythm feel: half-time stomp AND ultra-fast breakcore (contradiction)

STRUCTURE_BLOCK:
- "full song with verse and chorus maybe"
- (no explicit chorus/hook labeling)
- (no section role map)

VOCAL_INTENT_BLOCK:
- "two different singers but also one singer only"
- "rap and also not rap"
- (no role ownership per section)
- (no contrast levers)

NEGATIVE_SPEC_BLOCK:
- "no bad stuff"
- 30+ random negatives including banning repetition everywhere while also wanting catchy hook repeated a lot (contradiction)
- bans: “no guitars” while also demanding “heavy guitars” (contradiction)

CONSTRAINTS_BLOCK:
- "make it 30 seconds and also 3 minutes"
- "super minimal and super dense wall of sound"
- "make it unique but exactly like (some famous band) 1:1" (boundary breach)

---

## 2) EXPECTED GATE RESULTS (UID-ONLY)
EXPECTED_GATE_RESULTS:
- UE.KB.SPC.GATE.PROMPT_CONTRACT_CLARITY.001 -> FAIL
- UE.KB.SPC.GATE.STYLE_FINGERPRINT_STABILITY.001 -> FAIL
- UE.KB.SPC.GATE.VOICE_DIVERSITY_INTENT.001 -> FAIL
- UE.KB.SPC.GATE.REPETITION_CONTROL_INTENT.001 -> REWORK/FAIL (contradiction: ban repetition everywhere but wants hook)
- UE.KB.SPC.GATE.ONE_AXIS_DISCIPLINE.001 -> N/A (no iteration log)

---

## 3) WHY THIS IS BAD (CALIBRATION NOTES)
WHY_BAD:
- Contract is overloaded: too many genres, no anchors → fails stability and controllability.
- Multiple direct contradictions (clean vs lo-fi muddy; half-time vs breakcore; 30 sec vs 3 min).
- Structure is vague; chorus/hook not defined → hook and role intent cannot be enforced.
- Vocal plan contradicts itself; no section role ownership and no contrast levers.
- Negatives are spammy and contradictory (ban repetition everywhere + want repeated hook).
- Boundary breach: “exactly like X 1:1” (must be rewritten as principles).

---

## 4) FIX PATH (WHAT TO DO)
Fix steps:
1) Run Gate 01 and prune contradictions:
   - choose primary genre + optional touch
   - choose ONE rhythm feel
   - choose ONE texture direction
   - choose ONE duration target
2) Rebuild with PB-01 CORE WORKFLOW:
   - explicit structure + chorus hook label
   - vocal role map
   - targeted negatives (≤ 8–12)
3) If style drift remains:
   - PB-07 STYLE STABILIZER (3–6 anchors + dominance)
4) If vocals remain same:
   - PB-05 VOCAL DIVERSITY BOOST
5) If repetition persists:
   - PB-06 ANTI-REPETITION FIX

---

## 5) TRACE
TRACE:
- MEMORY_REUSE: NO
- WEB_LOOKUP_USED: NO

--- END.
