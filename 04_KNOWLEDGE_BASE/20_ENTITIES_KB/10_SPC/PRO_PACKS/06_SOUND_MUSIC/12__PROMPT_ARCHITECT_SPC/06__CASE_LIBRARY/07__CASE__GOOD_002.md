# CASE — GOOD (UGC/SHORT LOOP PASS ANCHOR) (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/06__CASE_LIBRARY/07__CASE__GOOD_002.md

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
UID: UE.KB.SPC.CASE.PROMPT_ARCHITECT.GOOD.002
OWNER: SYSTEM
ROLE: GOOD case for UGC/SHORT loop format (15–30s). Calibrates a PASS-quality prompt contract that is loopable, hook-forward, minimal-clutter, and has explicit repetition policy suitable for UGC clips.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Added GOOD case #2: UGC/SHORT loop PASS anchor with explicit loop structure and repetition policy."
- REASON: "Need a second PASS anchor beyond full-song: short/UGC mode should pass clarity and repetition gates without full-song structure."
- IMPACT: "Better calibration of loop/UGC workflows and fewer false failures."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.CASE.GOOD.002

---

## 0) CASE RECORD
CASE_RECORD:
- CASE_ID: CASE-GOOD-002
- TYPE: GOOD
- CONTEXT:
  - FORMAT: LOOP / UGC SHORT (15–30s)
  - LANGUAGE: RU (optional hook phrase) OR instrumental (allowed)
  - VOCAL_MODE: optional (simple hook/chant only)
  - GENRE: industrial electronic rock touch (primary compact identity)
- INPUT_INTENT (short):
  - A loopable 20s hook segment with tight half-time groove, chug riff anchor, minimal glitch accents, immediate recognition, and explicit loop repetition policy.

---

## 1) PROMPT CONTRACT (GOOD UGC/LOOP)
STYLE_BLOCK:
- electronic rock / rap rock vibe (PRIMARY, dominant for short)
- industrial rock touch (SECONDARY, subtle)
- ANCHORS:
  - rhythm feel: half-time stomp groove (stable)
  - guitar role: tight chug riff as loop anchor
  - drum tone: punchy kit + controlled electronic hits
  - synth role: short glitch accents (sparingly, not constant)
  - texture direction: clean aggressive, tight low end

STRUCTURE_BLOCK (LOOP MODE):
- LOOP SEGMENT (15–30s):
  - A) riff + groove foundation (dominant)
  - B) hook phrase/chant (short, repeatable) OR hook melody motif (instrumental)
  - C) 1–2 glitch accents per loop (support only)
- NOTE:
  - No verse/chorus required; this is a loopable clip segment for UGC.

VOCAL_INTENT_BLOCK (OPTIONAL):
- If vocals used:
  - short hook phrase/chant, punchy rhythmic delivery
  - keep it simple (no multi-role map needed)
- If instrumental:
  - hook motif carried by riff/synth accent (state explicitly)

NEGATIVE_SPEC_BLOCK:
- avoid clutter/overlayering (keep minimal)
- avoid long verse-like sections (stay loop segment)
- avoid muddy low end / uncontrolled sub
- avoid excessive stutter edits that break groove
- avoid genre drift; keep primary identity consistent

CONSTRAINTS_BLOCK:
- duration: 15–30 seconds loopable segment
- hook must be clear immediately (first seconds)
- repetition allowed (loop), but keep hook short and clean
- stable groove; clear edit points / cut-friendly phrasing (UGC-ready)

---

## 2) EXPECTED GATE RESULTS (UID-ONLY)
EXPECTED_GATE_RESULTS:
- UE.KB.SPC.GATE.PROMPT_CONTRACT_CLARITY.001 -> PASS
  NOTE: loop structure is explicit and valid (no verse/chorus requirement)

- UE.KB.SPC.GATE.REPETITION_CONTROL_INTENT.001 -> PASS
  NOTE: repetition is explicitly allowed for loop, with constraint “short hook”

- UE.KB.SPC.GATE.STYLE_FINGERPRINT_STABILITY.001 -> PASS

- UE.KB.SPC.GATE.VOICE_DIVERSITY_INTENT.001 -> PASS/N/A
  NOTE: depends on whether vocals are used; if instrumental, treat as N/A

- UE.KB.SPC.GATE.ONE_AXIS_DISCIPLINE.001 -> N/A (no iteration log)

---

## 3) WHY THIS IS GOOD (CALIBRATION NOTES)
WHY_GOOD:
- Contract is complete and non-contradictory; loop structure is explicit.
- Style has stable anchors (roles) and avoids genre soup.
- Repetition policy is correct for loop: allowed, but constrained to short hook.
- Negatives are targeted (5) and prevent clutter without killing identity.
- UGC-readiness is encoded as principles (clear edit points, early recognition).

---

## 4) TRACE
TRACE:
- MEMORY_REUSE: NO
- WEB_LOOKUP_USED: NO

--- END.
