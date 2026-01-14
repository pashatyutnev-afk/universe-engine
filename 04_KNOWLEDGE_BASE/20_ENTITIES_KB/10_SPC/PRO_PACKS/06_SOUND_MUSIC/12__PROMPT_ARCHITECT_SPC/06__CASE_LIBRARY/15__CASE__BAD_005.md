# CASE — BAD (FULL SONG WITHOUT STRUCTURE / NO CHORUS LABEL) (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/06__CASE_LIBRARY/15__CASE__BAD_005.md

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
UID: UE.KB.SPC.CASE.PROMPT_ARCHITECT.BAD.005
OWNER: SYSTEM
ROLE: BAD case calibrating Gate 01 FAIL for full-song runs: prompt claims “full song” but provides no explicit structure and no chorus/hook labeling. Distinct from genre-soup cases; this is a structural absence failure.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Added BAD case #5: full-song without explicit structure/chorus label → Gate 01 FAIL."
- REASON: "Need a clean structural FAIL anchor separate from style/negative overload cases."
- IMPACT: "Prevents wasting generations on undefined song structure."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.CASE.BAD.005

---

## 0) CASE RECORD
CASE_RECORD:
- CASE_ID: CASE-BAD-005
- TYPE: BAD
- CONTEXT:
  - FORMAT: FULL_SONG (~3:00)
  - LANGUAGE: RU
  - VOCAL_MODE: any
  - STYLE: any (not focus)
- INPUT_INTENT (short):
  - User wants a full song with a hook but does not specify verse/chorus/bridge structure at all.

---

## 1) PROMPT CONTRACT (BAD EXAMPLE)
STYLE_BLOCK:
- "rock with some electronics" (fine)

STRUCTURE_BLOCK (MISSING / VAGUE):
- "make a full song with intro and then stuff happens"
- "make it catchy"
- (no Verse/Chorus sections)
- (no explicit chorus/hook label)
- (no plan for where hook appears)

VOCAL_INTENT_BLOCK:
- optional / vague

NEGATIVE_SPEC_BLOCK:
- minimal / not relevant

CONSTRAINTS_BLOCK:
- full song ~3 minutes
- (no structure constraints beyond length)

---

## 2) EXPECTED GATE RESULTS (UID-ONLY)
EXPECTED_GATE_RESULTS:
- UE.KB.SPC.GATE.PROMPT_CONTRACT_CLARITY.001 -> FAIL
  WHY: full-song requires explicit structure; C2 fails (no verse/chorus, no chorus/hook label)

Other gates:
- repetition/style/voice: N/A because clarity gate fails first
- one-axis: N/A

---

## 3) WHY THIS IS BAD (CALIBRATION NOTES)
WHY_BAD:
- For full-song mode, structure is a core contract element:
  - without verse/chorus separation, generator tends to produce random form
  - hook timing cannot be enforced
- This should be FAIL, not REWORK, because the missing structure is foundational.

---

## 4) FIX PATH (WHAT TO DO)
Fix steps:
- Use PB-01 CORE WORKFLOW:
  - define explicit sections: Intro / Verse / Chorus (hook) / Verse / Bridge / Final Chorus / Outro
  - label chorus as hook
  - state hook timing (early)
- Then rerun Gate 01.

Minimal patch is usually insufficient if structure is absent; rebuild is required.

---

## 5) TRACE
TRACE:
- MEMORY_REUSE: NO
- WEB_LOOKUP_USED: NO

--- END.
