# CASE — BORDERLINE (REPETITION POLICY TOO VAGUE) (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/06__CASE_LIBRARY/06__CASE__BORDERLINE_002.md

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
UID: UE.KB.SPC.CASE.PROMPT_ARCHITECT.BORDERLINE.002
OWNER: SYSTEM
ROLE: Borderline case calibrating Gate 03 (repetition control intent): contract is solid, but repetition policy is too vague and verse novelty constraint is missing → REWORK should be triggered and fixed with a minimal patch.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Added BORDERLINE case #2: strong contract but repetition policy vague → REWORK on Gate 03 with minimal fix."
- REASON: "Need an additional threshold example for repetition intent: 'sounds right' is not enough without explicit policy."
- IMPACT: "Makes Gate 03 decisions consistent and patchable."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.CASE.BORDERLINE.002

---

## 0) CASE RECORD
CASE_RECORD:
- CASE_ID: CASE-BL-002
- TYPE: BORDERLINE
- CONTEXT:
  - FORMAT: FULL_SONG (~3:00)
  - LANGUAGE: RU
  - VOCAL_MODE: A/B roles
  - GENRE: electronic nu metal (primary) + industrial touch
- INPUT_INTENT (short):
  - Controlled nu metal + glitch accents, clear hook chorus, distinct rap vs melodic roles, avoid verse repetition (but policy not explicitly encoded).

---

## 1) PROMPT CONTRACT (BORDERLINE EXAMPLE)
STYLE_BLOCK:
- electronic nu metal (PRIMARY, dominant)
- industrial rock touch (SECONDARY, subtle)
- ANCHORS:
  - rhythm feel: 94 bpm half-time stomp
  - guitar role: tight chug riffs
  - synth role: glitch accents (support)
  - texture direction: clean aggressive, tight low end

STRUCTURE_BLOCK:
- Intro (short)
- Verse 1 (Voice A: rap)
- Chorus (Voice B: melodic hook)
- Verse 2 (Voice A: rap)
- Bridge (short contrast)
- Final Chorus
- Outro

VOCAL_INTENT_BLOCK:
- Voice A owns verses (rap percussive)
- Voice B owns choruses (melodic sustained)
- Contrast rule: chorus lead differs from verse lead
- (voice negatives included minimally)

NEGATIVE_SPEC_BLOCK:
- avoid identical vocal timbre across sections
- avoid same delivery mode for verse and chorus
- avoid muddy low end / uncontrolled sub
- avoid genre drift

CONSTRAINTS_BLOCK (PROBLEM):
- "avoid too much repetition"
- (no explicit policy: where repetition is allowed)
- (no explicit verse novelty constraint)

---

## 2) EXPECTED GATE RESULTS (UID-ONLY)
EXPECTED_GATE_RESULTS:
- UE.KB.SPC.GATE.PROMPT_CONTRACT_CLARITY.001 -> PASS
- UE.KB.SPC.GATE.VOICE_DIVERSITY_INTENT.001 -> PASS
- UE.KB.SPC.GATE.STYLE_FINGERPRINT_STABILITY.001 -> PASS
- UE.KB.SPC.GATE.REPETITION_CONTROL_INTENT.001 -> REWORK
  WHY: repetition policy is vague and verse novelty constraint is missing

- UE.KB.SPC.GATE.ONE_AXIS_DISCIPLINE.001 -> N/A

---

## 3) WHY THIS IS BORDERLINE
WHY_BORDERLINE:
- The contract is complete and consistent (Gate 01 PASS).
- Vocal roles are explicit (Gate 02 PASS).
- Style anchors are stable (Gate 04 PASS).
- Repetition intent is “vibes-only”:
  - “avoid too much repetition” does not specify where repetition is allowed
  - missing verse novelty constraint
→ Gate 03 should trigger REWORK (not FAIL), because a minimal patch fixes it without rewriting.

---

## 4) MINIMAL PATCH (TO REACH PASS ON GATE 03)
PATCH_PROMPT (MINIMAL CHANGE):
- Keep everything else unchanged.
- Update CONSTRAINTS_BLOCK by adding explicit repetition policy:
  - "Repetition allowed mainly in chorus/hook."
  - "Verses must be novel; avoid repeating identical lines/phrases in verses."
- Add 1–2 targeted negatives:
  - "avoid repeating the same lines/phrases in verses"
  - "avoid recycling chorus lines into verses"

Expected after patch:
- UE.KB.SPC.GATE.REPETITION_CONTROL_INTENT.001 -> PASS

Playbook mapping:
- PB-04 PATCH MINIMAL CHANGE (axis: repetition)
- PB-06 ANTI-REPETITION FIX if repeats persist in practice

---

## 5) TRACE
TRACE:
- MEMORY_REUSE: NO
- WEB_LOOKUP_USED: NO

--- END.
