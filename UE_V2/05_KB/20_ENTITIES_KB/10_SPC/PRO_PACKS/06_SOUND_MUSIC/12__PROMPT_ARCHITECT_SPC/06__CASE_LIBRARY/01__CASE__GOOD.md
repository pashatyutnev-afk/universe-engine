# CASE — GOOD (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/06__CASE_LIBRARY/01__CASE__GOOD.md

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
UID: UE.KB.SPC.CASE.PROMPT_ARCHITECT.GOOD.001
OWNER: SYSTEM
ROLE: A "good" prompt contract example that should PASS core prompt-level gates: contract clarity, vocal diversity intent, repetition control intent, and style stability. Used to calibrate gates.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Added GOOD case for PROMPT_ARCHITECT: clear contract, controlled style anchors, explicit vocal roles, repetition policy."
- REASON: "Need a concrete PASS anchor for gates calibration."
- IMPACT: "Reduces subjective judgments and speeds up prompt authoring."
- CHANGE_ID: UE.CHG.2026-01-14.KB.SPC.CASE.GOOD.001

---

## 0) CASE RECORD
CASE_RECORD:
- CASE_ID: CASE-GOOD-001
- TYPE: GOOD
- CONTEXT:
  - FORMAT: FULL_SONG (~3:00)
  - LANGUAGE: RU
  - VOCAL_MODE: A/B roles (rap verses + melodic choruses)
  - GENRE: electronic nu metal / industrial rock touch (primary + touch)
- INPUT_INTENT (short):
  - Heavy guitars + glitchy synth accents, half-time stomp feel, clear hook chorus, distinct rap vs melodic vocal roles, minimal repetition outside chorus.

---

## 1) PROMPT CONTRACT (EXAMPLE)
STYLE_BLOCK:
- electronic nu metal (PRIMARY, dominant)
- industrial rock touch (SECONDARY, subtle)
- ANCHORS:
  - rhythm feel: 94 bpm half-time stomp, heavy downbeat
  - guitar role: tight chug riffs + punchy chorus lifts
  - synth role: glitchy lead accents (supporting, not constant lead)
  - drum tone: hybrid kit + electronic hits (controlled, not chaotic)
  - texture direction: clean aggressive, tight low end

STRUCTURE_BLOCK:
- Intro (short, tension build) — instrumental
- Verse 1 (Voice A: rap, percussive) — new imagery, no repeated lines
- Chorus (Voice B: melodic hook, sustained) — hook repeats here
- Verse 2 (Voice A: rap) — different phrasing/imagery vs Verse 1
- Bridge (A/B call-response) — short contrast, then lift
- Final Chorus (Voice B lead + Voice A adlibs optional) — strongest hook
- Outro (short)

VOCAL_INTENT_BLOCK:
- Voice A (Verses): rap delivery, tight rhythm, clipped phrasing; darker timbre principle; sits lower/mid
- Voice B (Chorus): melodic, sustained notes, open vowels; brighter/cleaner timbre principle; sits mid/higher
- CONTRAST RULE: chorus lead must clearly differ from verse lead; A owns verses, B owns choruses
- Optional: call/response in bridge for extra contrast

NEGATIVE_SPEC_BLOCK:
- avoid identical vocal timbre across sections
- avoid same delivery mode for verse and chorus
- avoid repeating the same lines/phrases in verses
- avoid recycling chorus lines into verses
- avoid muddy low end / uncontrolled sub
- avoid genre soup; keep primary style consistent
- avoid excessive stutter edits that break groove

CONSTRAINTS_BLOCK:
- full song ~3 minutes
- hook chorus should be clear and appear early
- repetition allowed mainly in chorus/hook; verses must be novel
- clean aggressive mix, tight low end (principle), controlled dynamics

---

## 2) EXPECTED GATE RESULTS (UID-ONLY)
EXPECTED_GATE_RESULTS:
- UE.KB.SPC.GATE.PROMPT_CONTRACT_CLARITY.001 -> PASS
- UE.KB.SPC.GATE.VOICE_DIVERSITY_INTENT.001 -> PASS
- UE.KB.SPC.GATE.REPETITION_CONTROL_INTENT.001 -> PASS
- UE.KB.SPC.GATE.STYLE_FINGERPRINT_STABILITY.001 -> PASS
- UE.KB.SPC.GATE.ONE_AXIS_DISCIPLINE.001 -> N/A (no iteration log in this single example)

---

## 3) WHY THIS IS GOOD (CALIBRATION NOTES)
WHY_GOOD:
- All core blocks exist (style/structure/vocals/negatives/constraints) → clarity gate PASS.
- Style has “primary + touch” dominance and 5 anchors (roles, not inventory) → stable fingerprint.
- Vocal roles are explicit per section + 2–3 contrast levers + targeted voice negatives → reduces same singer risk.
- Repetition policy is explicit; verse novelty enforced; chorus repetition allowed → avoids contradictions.
- Negatives are targeted (7 items) and not spam → control without killing quality.
- No internal contradictions (clean aggressive vs muddy; dominance resolves blend).

---

## 4) OPTIONAL FIX PATH (IF IT FAILS IN PRACTICE)
If output still shows:
- same singer syndrome → apply PB-05 VOCAL DIVERSITY BOOST (increase role ownership + call/response)
- repetition in verses → apply PB-06 ANTI-REPETITION FIX (add verse novelty constraints)
- style drift → apply PB-07 STYLE STABILIZER (reduce anchors to 3–4)

---

## 5) TRACE
TRACE:
- MEMORY_REUSE: NO
- WEB_LOOKUP_USED: NO

--- END.
