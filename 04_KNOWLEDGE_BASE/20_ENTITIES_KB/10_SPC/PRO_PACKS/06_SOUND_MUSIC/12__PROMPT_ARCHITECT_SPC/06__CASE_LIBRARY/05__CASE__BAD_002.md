# CASE — BAD (NEGATIVE SPAM / OVER-BANNING) (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/06__CASE_LIBRARY/05__CASE__BAD_002.md

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
UID: UE.KB.SPC.CASE.PROMPT_ARCHITECT.BAD.002
OWNER: SYSTEM
ROLE: BAD case calibrating “negative spam” and “over-banning” failure mode: too many negatives, contradictions that forbid hook repetition and core style elements. Should trigger REWORK/FAIL primarily on Gate 01 and Gate 03.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Added BAD case: negative spam + over-banning causes contradictions and kills hook/clarity."
- REASON: "Need a dedicated calibration case for negative overload and repetition-policy contradictions."
- IMPACT: "Prevents 'wall of negatives' prompts and improves fix selection."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.CASE.BAD.002

---

## 0) CASE RECORD
CASE_RECORD:
- CASE_ID: CASE-BAD-002
- TYPE: BAD
- CONTEXT:
  - FORMAT: FULL_SONG (~3:00)
  - LANGUAGE: RU
  - VOCAL_MODE: A/B intended
  - GENRE: electronic nu metal (primary)
- INPUT_INTENT (short):
  - "Make a catchy hook song but also ban almost everything; add huge negative list to force quality."

---

## 1) PROMPT CONTRACT (BAD EXAMPLE)
STYLE_BLOCK:
- electronic nu metal (PRIMARY)
- industrial rock touch (SECONDARY)
- ANCHORS:
  - rhythm feel: half-time stomp
  - guitar role: heavy chug riffs
  - synth role: glitch accents (light)

STRUCTURE_BLOCK:
- Intro
- Verse 1 (rap)
- Chorus (hook)
- Verse 2
- Bridge
- Final chorus
- Outro

VOCAL_INTENT_BLOCK:
- A verses rap, B chorus melodic (stated)
- (no real contrast levers)

NEGATIVE_SPEC_BLOCK (NEGATIVE SPAM):
- 25–40 negatives, including:
  - "no repetition anywhere"
  - "no repeating hook"
  - "no chorus repeats"
  - "no guitars" (contradicts heavy guitars)
  - "no synth" (contradicts glitch accents)
  - "no distortion" (contradicts nu metal)
  - "no aggressive vocals" (contradicts genre intent)
  - "no loud drums" (kills stomp feel)
  - plus many vague items: "no bad mixing", "no boring parts", "no generic"

CONSTRAINTS_BLOCK:
- "hook must be catchy and repeatable"
- "chorus must repeat" (contradiction with negatives)
- "avoid repetition everywhere" (hard contradiction)

---

## 2) EXPECTED GATE RESULTS (UID-ONLY)
EXPECTED_GATE_RESULTS:
- UE.KB.SPC.GATE.PROMPT_CONTRACT_CLARITY.001 -> REWORK/FAIL
  WHY: contradictions + overload in negatives

- UE.KB.SPC.GATE.REPETITION_CONTROL_INTENT.001 -> FAIL
  WHY: policy contradiction (hook repeats vs ban repetition everywhere)

- UE.KB.SPC.GATE.STYLE_FINGERPRINT_STABILITY.001 -> REWORK
  WHY: anchors exist but negatives forbid core style elements

- UE.KB.SPC.GATE.VOICE_DIVERSITY_INTENT.001 -> REWORK
  WHY: vocal intent present but weak mechanics (not primary failure)

- UE.KB.SPC.GATE.ONE_AXIS_DISCIPLINE.001 -> N/A

---

## 3) WHY THIS IS BAD (CALIBRATION NOTES)
WHY_BAD:
- Negative list is too long and includes vague “no bad stuff” style bans → overload risk.
- Over-banning creates direct contradictions:
  - hook repetition required but forbidden everywhere.
- Negatives forbid core identity elements (guitars, distortion, synth) → style cannot manifest.
- This case teaches that “more negatives” is not “more control”.

---

## 4) FIX PATH (WHAT TO DO)
Fix steps (minimal, deterministic):
1) Run Gate 01 and prune negatives:
   - cap negatives to 8–12
   - remove vague bans (“no boring”, “no bad mix”)
2) Run Gate 03 and define repetition policy:
   - allow repetition in chorus/hook
   - forbid repetition mainly in verses
3) Ensure negatives do not ban core anchors (guitars/distortion/synth role)
4) Use PB-04 PATCH MINIMAL CHANGE if baseline is otherwise good:
   - edit only NEGATIVE_SPEC_BLOCK + repetition policy line(s)
5) If still failing, use PB-06 ANTI-REPETITION FIX (balanced policy + novelty constraints)

---

## 5) TRACE
TRACE:
- MEMORY_REUSE: NO
- WEB_LOOKUP_USED: NO

--- END.
