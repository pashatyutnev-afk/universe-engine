# CASE — EDGE (SECTION COLLAPSE: VERSE BECOMES CHORUS) (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/06__CASE_LIBRARY/14__CASE__EDGE_004.md

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
UID: UE.KB.SPC.CASE.PROMPT_ARCHITECT.EDGE.004
OWNER: SYSTEM
ROLE: Edge-case calibrating “section collapse” failure mode: verses blur into chorus/hook due to unclear section roles and missing repetition policy. Should trigger REWORK on Gate 01 (section clarity) and Gate 03 (structure protects repetition policy). Includes minimal fix.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Added EDGE case #4: section collapse (verse behaves like chorus) → Gate01/03 REWORK; fix via explicit role labels + repetition policy."
- REASON: "Common generator failure: chorus lines leak into verses or verses repeat like choruses."
- IMPACT: "More consistent structure prompts and fewer accidental chorus/verse merges."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.CASE.EDGE.004

---

## 0) CASE RECORD
CASE_RECORD:
- CASE_ID: CASE-EDGE-004
- TYPE: EDGE
- CONTEXT:
  - FORMAT: FULL_SONG (~3:00)
  - LANGUAGE: RU
  - VOCAL_MODE: any
  - GENRE: any (not focus)
- INPUT_INTENT (short):
  - Song needs a clear chorus hook, but the prompt accidentally encourages repeating hook lines in verses (section collapse risk).

---

## 1) PROMPT CONTRACT (EDGE — STRUCTURE BLUR)
STYLE_BLOCK:
- (ok; not focus)

STRUCTURE_BLOCK (PROBLEM):
- "Verse 1 and Verse 2 should be as catchy as chorus and repeat the hook"
- "Chorus is a hook but also verses use the same hook line"
- (chorus not clearly separated; roles blurred)
- (no explicit “verses develop new content” rule)

NEGATIVE_SPEC_BLOCK:
- avoid too much repetition (vague)

CONSTRAINTS_BLOCK:
- hook should repeat and be memorable
- (no policy stating where repetition is allowed)

---

## 2) EXPECTED GATE RESULTS (UID-ONLY)
EXPECTED_GATE_RESULTS:
- UE.KB.SPC.GATE.PROMPT_CONTRACT_CLARITY.001 -> REWORK
  WHY: section clarity (C2) and role separation are weak; chorus label may exist but verses are instructed to reuse hook

- UE.KB.SPC.GATE.REPETITION_CONTROL_INTENT.001 -> REWORK
  WHY: structure does not protect policy (R3); repetition instruction leaks into verses; novelty constraint missing

Other gates:
- voice/style: N/A
- one-axis: N/A

---

## 3) WHY THIS IS EDGE (CALIBRATION NOTES)
WHY_EDGE:
- This is not “missing structure completely”; it is a subtle structure bug:
  - explicit instruction causes chorus→verse leakage
- REWORK (not FAIL) is correct if we can fix with a minimal role clarification.

---

## 4) MINIMAL FIX (TO REACH PASS)
PATCH_PROMPT (MINIMAL CHANGE):
- Keep everything else unchanged.
- Rewrite STRUCTURE_BLOCK roles:
  - Chorus/hook repeats
  - Verses develop new content; do NOT reuse hook lines
  - Bridge optional for contrast
- Add repetition policy line:
  - "Repetition allowed mainly in chorus/hook; verses must be novel."
- Add 1 targeted negative:
  - "avoid recycling chorus lines into verses"

Expected after patch:
- Gate 01 -> PASS (C2 clarified)
- Gate 03 -> PASS (policy protected by structure)

Playbook mapping:
- PB-04 PATCH MIN (axis: structure/repetition)
- PB-06 ANTI-REPETITION FIX (if leakage persists)

---

## 5) TRACE
TRACE:
- MEMORY_REUSE: NO
- WEB_LOOKUP_USED: NO

--- END.
