# CASE — BAD (STYLE DRIFT / GENRE SOUP / ANCHOR CONFLICT) (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/06__CASE_LIBRARY/12__CASE__BAD_004.md

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
UID: UE.KB.SPC.CASE.PROMPT_ARCHITECT.BAD.004
OWNER: SYSTEM
ROLE: BAD case calibrating Gate 04 (style fingerprint stability) FAIL: genre soup + conflicting anchors + contradictory texture directions causing inevitable style drift. Distinct from “fusion missing dominance” edge case; here the spec is overloaded and internally conflicting.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Added BAD case #4: genre soup + conflicting anchors → style drift; Gate 04 should FAIL."
- REASON: "Need a clear FAIL anchor for drift caused by overload/contradiction, not just missing dominance."
- IMPACT: "Improves Gate 04 strictness and correct fix selection (prune + unify)."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.CASE.BAD.004

---

## 0) CASE RECORD
CASE_RECORD:
- CASE_ID: CASE-BAD-004
- TYPE: BAD
- CONTEXT:
  - FORMAT: FULL_SONG (~3:00)
  - LANGUAGE: RU (optional)
  - VOCAL_MODE: irrelevant
  - STYLE: genre soup + conflicting anchor roles
- INPUT_INTENT (short):
  - User piles many genres and contradictory texture intents; output drifts unpredictably.

---

## 1) PROMPT CONTRACT (BAD EXAMPLE)
STYLE_BLOCK (PROBLEM):
- genres listed:
  - nu metal + trap + dnb + synthwave + industrial + ambient + orchestral + hardstyle
- texture direction contradictions:
  - clean aggressive mix AND lo-fi cassette hiss AND super muddy room vibe
- anchor conflicts:
  - “minimal sparse arrangement” AND “dense wall of layers”
  - “glitchy stutter edits everywhere” AND “smooth steady groove”
  - “big synth lead dominates” AND “guitars dominate always” (two dominants)
- no dominance rule
- too many anchors (>10) and multiple “lead” roles

STRUCTURE_BLOCK:
- verse/chorus exists (not the main issue)

NEGATIVE_SPEC_BLOCK:
- “avoid genre drift”
- (but style spec itself guarantees drift)

CONSTRAINTS_BLOCK:
- none that restricts style; just “make it awesome”

---

## 2) EXPECTED GATE RESULTS (UID-ONLY)
EXPECTED_GATE_RESULTS:
- UE.KB.SPC.GATE.STYLE_FINGERPRINT_STABILITY.001 -> FAIL
  WHY: severe genre soup + contradictions + multiple lead roles + no dominance

- UE.KB.SPC.GATE.PROMPT_CONTRACT_CLARITY.001 -> FAIL/REWORK
  WHY: contradictions and overload likely trip clarity gate

Other gates:
- voice/repetition: N/A
- one-axis: N/A

---

## 3) WHY THIS IS BAD (CALIBRATION NOTES)
WHY_BAD:
- Too many genres is not “fusion”; it is genre soup.
- Conflicting anchors and texture directions make the target undefined.
- Even with “avoid genre drift” negative, the positive specs force drift.
- This case teaches: Gate 04 must FAIL when the fingerprint cannot be stabilized by a small patch.

---

## 4) FIX PATH (WHAT TO DO)
Fix steps:
1) Choose one primary identity (one label) + optional touch (one label max).
2) Prune anchors to 3–6 roles:
   - pick ONE rhythm feel
   - pick ONE lead role (guitar OR synth, not both)
   - pick ONE texture direction (clean OR lo-fi, not both)
3) Add dominance rule if touch is used.
4) Use PB-07 STYLE FINGERPRINT STABILIZER + rerun Gate 04 and Gate 01.

Minimal fix direction:
- convert “genre soup” into:
  - PRIMARY: nu metal
  - SECONDARY: industrial touch
  - anchors: rhythm feel + guitar role + synth accent + drum tone + mix direction

---

## 5) TRACE
TRACE:
- MEMORY_REUSE: NO
- WEB_LOOKUP_USED: NO

--- END.
