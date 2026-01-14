# CASE — GOOD (CATALOG DIFFERENTIATION / COLLISION AVOIDANCE INTENT) (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/06__CASE_LIBRARY/25__CASE__GOOD_007.md

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
UID: UE.KB.SPC.CASE.PROMPT_ARCHITECT.GOOD.007
OWNER: SYSTEM
ROLE: GOOD case for catalog differentiation and collision avoidance intent: prompt contract encodes “do not repeat existing catalog fingerprint” using controlled uniqueness constraints (without genre soup). Calibrates repeat/collision avoidance behavior.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Added GOOD case #7 (25th case): catalog differentiation / collision avoidance intent with controlled uniqueness constraints."
- REASON: "L3 target requires ≥25 cases and needs a unique scenario beyond hook/voice/style basics."
- IMPACT: "Reduces internal catalog collisions while keeping prompts stable."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.CASE.GOOD.007

---

## 0) CASE RECORD
CASE_RECORD:
- CASE_ID: CASE-GOOD-007
- TYPE: GOOD
- CONTEXT:
  - FORMAT: FULL_SONG (~3:00)
  - LANGUAGE: RU
  - VOCAL_MODE: A/B optional
  - GOAL: differentiate from existing catalog to avoid collisions
- INPUT_INTENT (short):
  - Create a track in a stable primary style, but with a unique fingerprint relative to existing internal catalog patterns (avoid repeating the same hook phrase shapes, same riff rhythm, or same chorus contour).

---

## 1) PROMPT CONTRACT (GOOD DIFFERENTIATION)
STYLE_BLOCK:
- PRIMARY: electronic nu metal (dominant)
- SECONDARY: industrial touch (subtle)
- ANCHORS (5):
  - rhythm feel: half-time stomp groove
  - guitar role: tight chug riff (lead)
  - synth role: glitch accents (support)
  - drum tone: punchy hybrid kit + controlled electronic hits
  - texture direction: clean aggressive, tight low end

STRUCTURE_BLOCK:
- Intro (short)
- Verse 1
- Chorus (HOOK, repeats)
- Verse 2 (novel)
- Bridge (short contrast)
- Final Chorus (HOOK)
- Outro

VOCAL_INTENT_BLOCK (optional):
- If vocals:
  - A verses (rap), B choruses (melodic) with clear contrast rule
- If instrumental:
  - hook carried by riff contour + synth accent

NEGATIVE_SPEC_BLOCK (ANTI-COLLISION FOCUS):
- avoid reusing the same hook lines/phrases used in recent tracks (internal catalog)
- avoid reusing the same chorus cadence pattern (internal catalog)
- avoid repeating the same riff rhythm motif as recent tracks
- avoid muddy low end
- avoid genre drift / style soup

CONSTRAINTS_BLOCK:
- repetition allowed mainly in chorus/hook; verses must be novel
- uniqueness constraints (catalog-aware):
  - change hook contour pattern compared to recent tracks
  - change riff rhythmic motif compared to recent tracks
  - keep primary style stable (do not add extra genres to “force uniqueness”)
- keep prompt compact and controllable

---

## 2) EXPECTED GATE RESULTS (UID-ONLY)
EXPECTED_GATE_RESULTS:
- UE.KB.SPC.GATE.PROMPT_CONTRACT_CLARITY.001 -> PASS
- UE.KB.SPC.GATE.REPETITION_CONTROL_INTENT.001 -> PASS
- UE.KB.SPC.GATE.STYLE_FINGERPRINT_STABILITY.001 -> PASS
- UE.KB.SPC.GATE.VOICE_DIVERSITY_INTENT.001 -> PASS/N/A (depending on vocals)
- UE.KB.SPC.GATE.ONE_AXIS_DISCIPLINE.001 -> N/A

POLICY INTENT (UID-ONLY, NON-GATE):
- UE.CTL.MUS.CATALOG_MEMORY.001 -> SATISFIED (catalog-aware uniqueness constraints present)

---

## 3) WHY THIS IS GOOD (CALIBRATION NOTES)
WHY_GOOD:
- Uniqueness is encoded as constraints against internal motifs (hook contour / riff rhythm) rather than adding more genres.
- Style identity stays stable (no genre soup).
- Repetition is balanced: chorus repeats allowed; verses novel.
- Negatives are targeted and limited (anti-collision without “negative spam”).

---

## 4) TRACE
TRACE:
- MEMORY_REUSE: NO
- WEB_LOOKUP_USED: NO

--- END.
