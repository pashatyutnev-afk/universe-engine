# CASE — BORDERLINE (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/06__CASE_LIBRARY/03__CASE__BORDERLINE.md

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
UID: UE.KB.SPC.CASE.PROMPT_ARCHITECT.BORDERLINE.001
OWNER: SYSTEM
ROLE: A borderline prompt contract example that is close to PASS but should trigger REWORK on one gate (vocal diversity intent) due to insufficient mechanics. Used to calibrate thresholds and minimal patch behavior.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Added BORDERLINE case for PROMPT_ARCHITECT: strong contract but vocal intent too vague → REWORK with minimal patch."
- REASON: "Need a near-pass case to teach threshold and minimal delta repair."
- IMPACT: "Improves consistency of REWORK decisions and patch selection."
- CHANGE_ID: UE.CHG.2026-01-14.KB.SPC.CASE.BORDERLINE.001

---

## 0) CASE RECORD
CASE_RECORD:
- CASE_ID: CASE-BL-001
- TYPE: BORDERLINE
- CONTEXT:
  - FORMAT: FULL_SONG (~3:00)
  - LANGUAGE: RU
  - VOCAL_MODE: A/B roles intended (but weakly specified)
  - GENRE: electronic nu metal (primary) + industrial touch
- INPUT_INTENT (short):
  - Controlled nu metal + glitch accents, clear hook chorus, rap vs melodic contrast intended, avoid repetition in verses.

---

## 1) PROMPT CONTRACT (BORDERLINE EXAMPLE)
STYLE_BLOCK:
- electronic nu metal (PRIMARY, dominant)
- industrial rock touch (SECONDARY, subtle)
- ANCHORS:
  - rhythm feel: 94 bpm half-time stomp
  - guitar role: tight chug riffs
  - synth role: glitchy accents (support)
  - texture direction: clean aggressive, tight low end

STRUCTURE_BLOCK:
- Intro (short)
- Verse 1 (rap feel)
- Chorus (hook)
- Verse 2 (rap feel, different wording)
- Bridge (short contrast)
- Final Chorus
- Outro

VOCAL_INTENT_BLOCK:
- “rap verses + melodic chorus”
- “make voices different”
- (no explicit role ownership per section)
- (no contrast levers like range/timbre/delivery specifics)
- (no targeted voice negatives)

NEGATIVE_SPEC_BLOCK:
- avoid repeating the same lines/phrases in verses
- avoid recycling chorus lines into verses
- avoid muddy low end
- avoid genre soup / style drift

CONSTRAINTS_BLOCK:
- full song ~3 minutes
- chorus hook should be clear and appear early
- repetition mainly in chorus; verses should be novel

---

## 2) EXPECTED GATE RESULTS (UID-ONLY)
EXPECTED_GATE_RESULTS:
- UE.KB.SPC.GATE.PROMPT_CONTRACT_CLARITY.001 -> PASS
- UE.KB.SPC.GATE.STYLE_FINGERPRINT_STABILITY.001 -> PASS
- UE.KB.SPC.GATE.REPETITION_CONTROL_INTENT.001 -> PASS
- UE.KB.SPC.GATE.VOICE_DIVERSITY_INTENT.001 -> REWORK
- UE.KB.SPC.GATE.ONE_AXIS_DISCIPLINE.001 -> N/A (no iteration log)

---

## 3) WHY THIS IS BORDERLINE
WHY_BORDERLINE:
- Contract is mostly complete and non-contradictory (clarity PASS).
- Style anchors and dominance are clear (stability PASS).
- Repetition policy + verse novelty are explicit (repeat PASS).
- Vocal intent is vibes-only:
  - no section role ownership
  - no contrast levers
  - no targeted negatives
→ should trigger REWORK (not FAIL), because a minimal patch can fix it without rewriting style/structure.

---

## 4) DECISION RULE
DECISION:
- Result should be REWORK (not FAIL).
- Minimal patch should target only VOCAL_INTENT_BLOCK (+ 1–3 voice negatives).

---

## 5) MINIMAL PATCH (TO REACH PASS)
PATCH_PROMPT (MINIMAL CHANGE):
- Keep everything else unchanged.
- Replace VOCAL_INTENT_BLOCK with:
  - Voice A (verses): rap, percussive, clipped phrasing; darker timbre principle; lower/mid range principle
  - Voice B (chorus): melodic, sustained notes; brighter/cleaner timbre principle; mid/higher range principle
  - Role ownership: A owns verses, B owns chorus
  - Contrast rule: chorus lead must clearly differ from verse lead
- Add negatives:
  - avoid identical vocal timbre across sections
  - avoid same delivery mode for verse and chorus

Expected after patch:
- UE.KB.SPC.GATE.VOICE_DIVERSITY_INTENT.001 -> PASS

---

## 6) TRACE
TRACE:
- MEMORY_REUSE: NO
- WEB_LOOKUP_USED: NO

--- END.
