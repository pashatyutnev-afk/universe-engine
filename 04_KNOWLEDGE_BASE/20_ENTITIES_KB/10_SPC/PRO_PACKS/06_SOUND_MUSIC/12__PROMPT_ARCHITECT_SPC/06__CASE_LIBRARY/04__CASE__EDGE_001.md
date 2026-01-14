# CASE — EDGE (LOOP/SHORT FORMAT) (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/06__CASE_LIBRARY/04__CASE__EDGE_001.md

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
UID: UE.KB.SPC.CASE.PROMPT_ARCHITECT.EDGE.001
OWNER: SYSTEM
ROLE: Edge-case prompt contract for LOOP/SHORT format (15–30s). Calibrates how gates interpret structure, repetition policy, and hook clarity when the output is intentionally loopable and compact.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Added EDGE case for PROMPT_ARCHITECT: loop/short format with proper hook + repetition policy and minimal structure."
- REASON: "Loop format breaks full-song assumptions; needs explicit calibration for gates."
- IMPACT: "Prevents false FAIL decisions and improves loop-ready prompting."
- CHANGE_ID: UE.CHG.2026-01-14.KB.SPC.CASE.EDGE.001

---

## 0) CASE RECORD
CASE_RECORD:
- CASE_ID: CASE-EDGE-001
- TYPE: EDGE
- CONTEXT:
  - FORMAT: LOOP (15–30s)
  - LANGUAGE: RU (optional vocals; can be chant/hook only)
  - VOCAL_MODE: single voice OR simple A/B (optional)
  - GENRE: industrial electronic rock touch (compact)
- INPUT_INTENT (short):
  - Make a loopable, hook-forward 20s segment with tight groove, minimal clutter, controlled glitch accents; repetition is allowed but must be purposeful.

---

## 1) PROMPT CONTRACT (EDGE EXAMPLE)
STYLE_BLOCK:
- industrial rock touch (SECONDARY)
- electronic rock / rap rock vibe (PRIMARY, dominant for loop)
- ANCHORS:
  - rhythm feel: half-time stomp groove
  - guitar role: tight chug riff (loop anchor)
  - synth role: short glitch accents (sparingly)
  - texture direction: clean aggressive, tight low end

STRUCTURE_BLOCK (LOOP MODE):
- LOOP SEGMENT: "hook loop" (15–30s)
- COMPONENTS:
  - A) riff + beat groove (foundation)
  - B) hook line / chant (repeatable)
  - C) short glitch accent (1–2 hits per loop)
- NOTE:
  - No full verse/chorus structure required; this is a loopable segment.

VOCAL_INTENT_BLOCK (optional for loop):
- Single vocal mode:
  - short hook/chant line, clear and repeatable
  - delivery: punchy, rhythmic
- If vocals present:
  - keep it simple; no multi-section role map required

NEGATIVE_SPEC_BLOCK:
- avoid clutter/overlayering (keep minimal)
- avoid long verse-like sections (stay loop segment)
- avoid muddy low end / uncontrolled sub
- avoid excessive stutter edits that break loop groove
- avoid random genre drift

CONSTRAINTS_BLOCK:
- duration: 15–30 seconds loopable segment
- hook must be clear immediately (first seconds)
- repetition allowed (loop), but keep wording short and clean
- tight groove, stable fingerprint

---

## 2) EXPECTED GATE RESULTS (UID-ONLY)
EXPECTED_GATE_RESULTS:
- UE.KB.SPC.GATE.PROMPT_CONTRACT_CLARITY.001 -> PASS
  NOTE: structure check should accept LOOP structure (no verse/chorus required)

- UE.KB.SPC.GATE.STYLE_FINGERPRINT_STABILITY.001 -> PASS

- UE.KB.SPC.GATE.REPETITION_CONTROL_INTENT.001 -> PASS
  NOTE: repetition policy must allow loop repetition explicitly

- UE.KB.SPC.GATE.VOICE_DIVERSITY_INTENT.001 -> PASS/REWORK (depends on whether vocals are used)
  NOTE: if single simple vocal, must have delivery intent; no A/B map required

- UE.KB.SPC.GATE.ONE_AXIS_DISCIPLINE.001 -> N/A (no iteration log)

---

## 3) WHY THIS IS EDGE (CALIBRATION NOTES)
WHY_EDGE:
- LOOP format intentionally violates “full song” assumptions.
- STRUCTURE_BLOCK must define loop segment components instead of verse/chorus.
- Repetition is allowed and required for loopability, but must be constrained:
  - short hook line, not verse-length repeated text.
- Gate 01 must treat LOOP mode as valid structure if loop segment is explicit.
- Gate 03 must treat repetition as allowed when policy says so (no contradiction).

---

## 4) COMMON FAILS IN LOOP MODE → FIX PATH
If hook not immediate:
- strengthen “hook appears immediately” constraint; remove extra components.

If loop feels cluttered:
- reduce anchors; remove glitch density; keep one riff + one hook.

If repetition becomes annoying:
- shorten hook line; reduce word count; allow micro-variation (optional).

Playbook mapping:
- PB-01 CORE WORKFLOW (loop variant) or PB-04 PATCH MIN
- PB-07 STYLE STABILIZER if drift occurs

---

## 5) TRACE
TRACE:
- MEMORY_REUSE: NO
- WEB_LOOKUP_USED: NO

--- END.
