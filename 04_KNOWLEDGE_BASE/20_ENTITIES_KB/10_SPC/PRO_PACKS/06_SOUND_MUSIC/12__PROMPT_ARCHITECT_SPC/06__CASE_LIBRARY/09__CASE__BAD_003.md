# CASE — BAD (VOICE PLAN MISSING / SAME SINGER SYNDROME) (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/06__CASE_LIBRARY/09__CASE__BAD_003.md

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
UID: UE.KB.SPC.CASE.PROMPT_ARCHITECT.BAD.003
OWNER: SYSTEM
ROLE: BAD case calibrating Gate 02 (voice diversity intent): prompt specifies multi-section song but provides no role ownership, no contrast levers, and no voice negatives—classic “same singer syndrome” setup. Should FAIL Gate 02.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Added BAD case #3: voice intent missing → same singer syndrome risk; Gate 02 should FAIL."
- REASON: "Need a dedicated FAIL anchor for voice diversity intent gate."
- IMPACT: "Improves detection of weak vocal plans and speeds up correct fixes."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.CASE.BAD.003

---

## 0) CASE RECORD
CASE_RECORD:
- CASE_ID: CASE-BAD-003
- TYPE: BAD
- CONTEXT:
  - FORMAT: FULL_SONG (~3:00)
  - LANGUAGE: RU
  - VOCAL_MODE: intended A/B (rap verse + melodic chorus) but not specified properly
  - GENRE: rap rock / electronic nu metal touch
- INPUT_INTENT (short):
  - Rap verses + melodic hook chorus with clearly different voices, but prompt does not encode how.

---

## 1) PROMPT CONTRACT (BAD EXAMPLE)
STYLE_BLOCK:
- rap rock / electronic nu metal vibe
- rhythm feel: half-time stomp
- heavy guitars + glitchy synth accents

STRUCTURE_BLOCK:
- Intro
- Verse 1 (rap)
- Chorus (melodic hook)
- Verse 2 (rap)
- Bridge
- Final chorus
- Outro

VOCAL_INTENT_BLOCK (PROBLEM):
- "russian male vocals"
- "rap verse + melodic chorus"
- "make it sound good"
- (NO role ownership per section)
- (NO contrast levers: delivery/range/timbre/call-response)
- (NO contrast rule: chorus differs from verse)
- (NO targeted voice negatives)

NEGATIVE_SPEC_BLOCK:
- avoid muddy low end
- avoid genre drift
- (no voice negatives)

CONSTRAINTS_BLOCK:
- full song ~3 minutes
- hook should be catchy

---

## 2) EXPECTED GATE RESULTS (UID-ONLY)
EXPECTED_GATE_RESULTS:
- UE.KB.SPC.GATE.PROMPT_CONTRACT_CLARITY.001 -> PASS
  NOTE: blocks exist; contract is readable (clarity can pass)

- UE.KB.SPC.GATE.VOICE_DIVERSITY_INTENT.001 -> FAIL
  WHY: no role map + no levers + no targeted negatives → vibes-only

- UE.KB.SPC.GATE.REPETITION_CONTROL_INTENT.001 -> REWORK/N/A (not specified; not primary)
- UE.KB.SPC.GATE.STYLE_FINGERPRINT_STABILITY.001 -> PASS/REWORK (depends on clutter; likely PASS here)
- UE.KB.SPC.GATE.ONE_AXIS_DISCIPLINE.001 -> N/A

---

## 3) WHY THIS IS BAD (CALIBRATION NOTES)
WHY_BAD:
- Multi-section song implies different section roles; voice plan must specify mechanics.
- “rap verse + melodic chorus” alone is insufficient; generator may reuse same voice fingerprint.
- Missing:
  - role ownership (A verses, B chorus)
  - contrast levers (delivery/range/timbre)
  - targeted negatives
→ Gate 02 must FAIL, not REWORK.

---

## 4) FIX PATH (WHAT TO DO)
Fix steps:
1) Apply PB-05 VOCAL DIVERSITY BOOST:
   - add role map (A verses, B chorus)
   - add 2–3 contrast levers (delivery + timbre/range)
   - add 1–3 voice negatives

2) If baseline otherwise good:
   - use PB-04 PATCH MIN (axis: vocals)
   - edit only VOCAL_INTENT_BLOCK + add voice negatives

Minimal patch snippet (example):
- "Verse = Voice A (rap, percussive, darker timbre principle)"
- "Chorus = Voice B (melodic, sustained, brighter timbre principle)"
- "avoid identical vocal timbre across sections"

Expected:
- Gate 02 becomes PASS.

---

## 5) TRACE
TRACE:
- MEMORY_REUSE: NO
- WEB_LOOKUP_USED: NO

--- END.
