# CASE — GOOD (MINIMAL BUT COMPLETE CONTRACT) (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/06__CASE_LIBRARY/16__CASE__GOOD_004.md

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
UID: UE.KB.SPC.CASE.PROMPT_ARCHITECT.GOOD.004
OWNER: SYSTEM
ROLE: GOOD case showing a minimal yet complete prompt contract: all core blocks present, stable style anchors (3–5), explicit chorus hook, balanced repetition policy, targeted negatives. Calibrates that “compact” can still PASS gates.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Added GOOD case #4: compact full-song contract that passes gates without overload."
- REASON: "Need a PASS anchor teaching minimalism: fewer words, more control."
- IMPACT: "Reduces prompt bloat and improves consistency."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.CASE.GOOD.004

---

## 0) CASE RECORD
CASE_RECORD:
- CASE_ID: CASE-GOOD-004
- TYPE: GOOD
- CONTEXT:
  - FORMAT: FULL_SONG (~3:00)
  - LANGUAGE: RU
  - VOCAL_MODE: single voice with delivery contrast (no A/B required)
  - GENRE: electronic rock (primary) + industrial touch
- INPUT_INTENT (short):
  - A clean, hook-forward rock/electronic track with minimal clutter, clear chorus, and no verse repetition. Keep it compact and controllable.

---

## 1) PROMPT CONTRACT (COMPACT PASS)
STYLE_BLOCK:
- PRIMARY: electronic rock
- SECONDARY: industrial touch (subtle)
- ANCHORS:
  - rhythm feel: steady half-time groove
  - guitar role: tight riff (lead)
  - synth role: short metallic accents (support)
  - texture direction: clean aggressive, tight low end

STRUCTURE_BLOCK:
- Intro (short)
- Verse 1 (new lines)
- Chorus (HOOK, repeats)
- Verse 2 (new lines; different phrasing from Verse 1)
- Bridge (short contrast)
- Final Chorus (HOOK)
- Outro (short)

VOCAL_INTENT_BLOCK (SIMPLE):
- Single vocalist:
  - verses: rhythmic, tighter delivery
  - choruses: more sustained, open delivery
- Contrast rule:
  - chorus delivery must differ from verse delivery

NEGATIVE_SPEC_BLOCK:
- avoid repeating identical lines in verses
- avoid recycling chorus lines into verses
- avoid muddy low end
- avoid genre drift / style soup
- avoid excessive edit glitches (keep groove stable)

CONSTRAINTS_BLOCK:
- full song ~3 minutes
- hook chorus must be clear and appear early
- repetition allowed mainly in chorus/hook; verses must be novel
- keep arrangement minimal (no clutter)

---

## 2) EXPECTED GATE RESULTS (UID-ONLY)
EXPECTED_GATE_RESULTS:
- UE.KB.SPC.GATE.PROMPT_CONTRACT_CLARITY.001 -> PASS
- UE.KB.SPC.GATE.REPETITION_CONTROL_INTENT.001 -> PASS
- UE.KB.SPC.GATE.STYLE_FINGERPRINT_STABILITY.001 -> PASS
- UE.KB.SPC.GATE.VOICE_DIVERSITY_INTENT.001 -> PASS
  NOTE: single-voice mode passes via delivery contrast mechanics (no A/B ownership needed)

- UE.KB.SPC.GATE.ONE_AXIS_DISCIPLINE.001 -> N/A

---

## 3) WHY THIS IS GOOD (CALIBRATION NOTES)
WHY_GOOD:
- All required blocks exist, but each is compact (clarity without bloat).
- Style anchors are 4 and role-based (no inventory).
- Chorus is explicitly labeled as hook and repeats there (structure protects hook).
- Verse novelty is explicit + targeted repetition negatives (balanced policy).
- Vocal contrast is minimal and actionable (verse vs chorus delivery), avoiding overload.

---

## 4) TRACE
TRACE:
- MEMORY_REUSE: NO
- WEB_LOOKUP_USED: NO

--- END.
