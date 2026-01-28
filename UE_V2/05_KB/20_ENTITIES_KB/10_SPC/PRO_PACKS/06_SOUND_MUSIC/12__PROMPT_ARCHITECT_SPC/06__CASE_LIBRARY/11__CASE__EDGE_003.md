# CASE — EDGE (MULTI-VOICE OVERLOAD: TOO MANY LEVERS/ROLES) (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/06__CASE_LIBRARY/11__CASE__EDGE_003.md

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
UID: UE.KB.SPC.CASE.PROMPT_ARCHITECT.EDGE.003
OWNER: SYSTEM
ROLE: Edge-case calibrating Gate 02 REWORK threshold for voice intent overload: too many vocal roles/levers and overly complex instructions reduce controllability. Shows minimal pruning fix to restore PASS.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Added EDGE case #3: multi-voice overload (>4 levers/roles) should trigger Gate 02 REWORK; fix by pruning to 2–4 levers and 2 roles."
- REASON: "Users often over-specify vocals; gate must enforce simplicity for controllability."
- IMPACT: "More consistent Gate 02 thresholds and cleaner vocal prompts."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.CASE.EDGE.003

---

## 0) CASE RECORD
CASE_RECORD:
- CASE_ID: CASE-EDGE-003
- TYPE: EDGE
- CONTEXT:
  - FORMAT: FULL_SONG (~3:00)
  - LANGUAGE: RU
  - VOCAL_MODE: attempted 3–4 roles + many levers (overload)
  - GENRE: rock/electronic hybrid
- INPUT_INTENT (short):
  - Want strong vocal contrast, but the plan becomes too complex and risks collapsing into chaos or sameness.

---

## 1) PROMPT CONTRACT (EDGE — OVERLOADED VOICE PLAN)
STYLE_BLOCK:
- electronic rock / nu metal touch
- (not the focus)

STRUCTURE_BLOCK:
- Verse / Chorus / Verse / Bridge / Final Chorus (present)

VOCAL_INTENT_BLOCK (PROBLEM: OVERLOAD):
- Roles:
  - Voice A (rap verse)
  - Voice B (melodic chorus)
  - Voice C (screams on pre-chorus)
  - Voice D (whisper adlibs)
- Levers (too many):
  - delivery contrast
  - range separation
  - timbre contrast
  - accent/phoneme rules
  - section-specific FX rules
  - gender-like hints (should be avoided as model claims)
  - doubling + harmonies + stacked choirs
- Additional constraints:
  - “every section must have different voice”
  - “no voice should repeat”
  - “make it all super clear”
- Negatives:
  - long voice negative list + long general negatives (overload)

---

## 2) EXPECTED GATE RESULTS (UID-ONLY)
EXPECTED_GATE_RESULTS:
- UE.KB.SPC.GATE.VOICE_DIVERSITY_INTENT.001 -> REWORK
  WHY: V2 overload (>4 levers) + too many roles + control density too high

- UE.KB.SPC.GATE.PROMPT_CONTRACT_CLARITY.001 -> REWORK
  WHY: control density/overload risk (may trip clarity gate’s overload heuristic)

Other gates:
- style/repetition: N/A (not the focus)
- one-axis: N/A

---

## 3) WHY THIS IS EDGE (CALIBRATION NOTES)
WHY_EDGE:
- More vocal rules ≠ more control; too many roles and levers:
  - increase contradictions
  - create untestable requirements
  - often collapse into generic output
- Gate 02 should not FAIL immediately if it’s fixable by pruning:
  - REWORK is correct result.

Threshold taught:
- 2–4 contrast levers max
- 2 roles (A/B) preferred; 3 roles only if necessary

---

## 4) MINIMAL FIX (PRUNE TO PASS)
PATCH_PROMPT (MINIMAL CHANGE):
- Keep everything else unchanged.
- Reduce roles to A/B only:
  - A owns verses (rap)
  - B owns choruses (melodic)
  - Bridge uses brief A/B call-response (optional) — no new “Voice C/D”
- Reduce levers to 3 max:
  - delivery contrast (A rap vs B melodic)
  - timbre principle contrast (darker vs brighter)
  - range principle separation (lower vs higher)
- Remove “no voice should repeat” requirement (contradiction with identity).
- Keep 1–3 targeted voice negatives only.

Expected after patch:
- UE.KB.SPC.GATE.VOICE_DIVERSITY_INTENT.001 -> PASS

Playbook mapping:
- PB-05 VOCAL DIVERSITY BOOST (but with pruning emphasis)
- PB-04 PATCH MIN (axis: vocals)

---

## 5) TRACE
TRACE:
- MEMORY_REUSE: NO
- WEB_LOOKUP_USED: NO

--- END.
