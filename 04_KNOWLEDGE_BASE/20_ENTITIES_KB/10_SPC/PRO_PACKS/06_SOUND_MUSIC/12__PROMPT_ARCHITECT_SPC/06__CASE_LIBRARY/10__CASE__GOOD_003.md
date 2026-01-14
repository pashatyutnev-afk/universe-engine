# CASE — GOOD (STRONG VOICE DIVERSITY INTENT A/B + CALL-RESPONSE) (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/06__CASE_LIBRARY/10__CASE__GOOD_003.md

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
UID: UE.KB.SPC.CASE.PROMPT_ARCHITECT.GOOD.003
OWNER: SYSTEM
ROLE: GOOD case calibrating Gate 02 (voice diversity intent): explicit role ownership per section, compact contrast levers, targeted negatives, and a controlled call-response bridge. Should PASS voice gate while keeping the contract concise.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Added GOOD case #3: strong A/B voice intent with call-response bridge, compact levers, and targeted negatives."
- REASON: "Need a PASS anchor that demonstrates how to avoid 'same singer syndrome' without overloading the prompt."
- IMPACT: "Improves calibration and reuse for multi-voice tracks."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.CASE.GOOD.003

---

## 0) CASE RECORD
CASE_RECORD:
- CASE_ID: CASE-GOOD-003
- TYPE: GOOD
- CONTEXT:
  - FORMAT: FULL_SONG (~3:00)
  - LANGUAGE: RU
  - VOCAL_MODE: A/B roles + short call-response bridge
  - GENRE: electronic nu metal (primary) + industrial touch
- INPUT_INTENT (short):
  - Rap verses (Voice A) and melodic hook choruses (Voice B) must feel like different personas. Bridge uses call-response for contrast. Keep style stable and avoid repetition in verses.

---

## 1) PROMPT CONTRACT (GOOD EXAMPLE)
STYLE_BLOCK:
- electronic nu metal (PRIMARY, dominant)
- industrial rock touch (SECONDARY, subtle)
- ANCHORS:
  - rhythm feel: 94 bpm half-time stomp
  - guitar role: tight chug riffs + chorus lift
  - synth role: glitch accents (support)
  - drum tone: punchy hybrid kit + electronic hits (controlled)
  - texture direction: clean aggressive, tight low end

STRUCTURE_BLOCK:
- Intro (short)
- Verse 1 — Voice A lead (rap, percussive)
- Chorus — Voice B lead (melodic hook, sustained)
- Verse 2 — Voice A lead (new imagery, no repeated lines)
- Bridge — A/B call-response (short, punchy exchange)
- Final Chorus — Voice B lead + optional Voice A adlibs
- Outro (short)

VOCAL_INTENT_BLOCK (STRONG):
- ROLE OWNERSHIP:
  - Voice A owns verses
  - Voice B owns choruses
  - Bridge uses A/B call-response
- Voice A (Verses):
  - delivery: tight rhythmic rap, clipped phrasing
  - timbre principle: darker/rougher
  - range principle: lower/mid
- Voice B (Chorus):
  - delivery: melodic, sustained notes, open vowels
  - timbre principle: brighter/cleaner
  - range principle: mid/higher
- CONTRAST RULE:
  - chorus lead must clearly differ from verse lead (timbre + delivery)

NEGATIVE_SPEC_BLOCK:
- avoid identical vocal timbre across sections
- avoid same delivery mode for verse and chorus
- avoid chorus sounding like verse
- avoid repeating the same lines/phrases in verses
- avoid recycling chorus lines into verses
- avoid muddy low end / uncontrolled sub
- avoid genre drift; keep primary style consistent

CONSTRAINTS_BLOCK:
- full song ~3 minutes
- hook chorus should be clear and appear early
- repetition allowed mainly in chorus; verses must be novel
- clean aggressive mix intent; tight low end (principle)

---

## 2) EXPECTED GATE RESULTS (UID-ONLY)
EXPECTED_GATE_RESULTS:
- UE.KB.SPC.GATE.PROMPT_CONTRACT_CLARITY.001 -> PASS
- UE.KB.SPC.GATE.VOICE_DIVERSITY_INTENT.001 -> PASS
- UE.KB.SPC.GATE.REPETITION_CONTROL_INTENT.001 -> PASS
- UE.KB.SPC.GATE.STYLE_FINGERPRINT_STABILITY.001 -> PASS
- UE.KB.SPC.GATE.ONE_AXIS_DISCIPLINE.001 -> N/A (no iteration log)

---

## 3) WHY THIS IS GOOD (CALIBRATION NOTES)
WHY_GOOD:
- Voice plan has explicit role ownership per section (V1 PASS).
- Contrast levers are compact (delivery + timbre + range) (V2 PASS) without overload.
- Call-response in bridge adds a strong audible contrast cue without adding many lines.
- Targeted voice negatives reduce same singer risk and enforce chorus ≠ verse.
- Repetition policy and verse novelty are explicit.
- Style anchors are 3–6 and dominance is implicit (primary + touch) with no genre soup.

---

## 4) TRACE
TRACE:
- MEMORY_REUSE: NO
- WEB_LOOKUP_USED: NO

--- END.
