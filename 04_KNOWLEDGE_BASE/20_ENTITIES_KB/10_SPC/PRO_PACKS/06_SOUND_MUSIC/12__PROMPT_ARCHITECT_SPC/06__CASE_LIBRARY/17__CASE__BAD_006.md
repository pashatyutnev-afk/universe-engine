# CASE — BAD (ONE-AXIS VIOLATION / MULTI-AXIS PATCH) (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/06__CASE_LIBRARY/17__CASE__BAD_006.md

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
UID: UE.KB.SPC.CASE.PROMPT_ARCHITECT.BAD.006
OWNER: SYSTEM
ROLE: BAD case calibrating Gate 05 (one-axis change discipline) FAIL: a supposed “minimal patch” changes multiple axes at once (style + vocals + structure/tempo), and baseline is not frozen. Demonstrates why learning collapses and how to fix (split variants).

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Added BAD case #6: multi-axis patch + no baseline freeze → Gate 05 FAIL anchor."
- REASON: "Need a dedicated FAIL anchor for iteration discipline and reproducibility."
- IMPACT: "Enforces correct A/B iteration and reduces chaotic rework."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.CASE.BAD.006

---

## 0) CASE RECORD
CASE_RECORD:
- CASE_ID: CASE-BAD-006
- TYPE: BAD
- CONTEXT:
  - FORMAT: any (iteration case)
  - LANGUAGE: RU
  - VOCAL_MODE: any
  - PIPELINE: rework after failure
- INPUT_INTENT (short):
  - User wants to “fix everything” in one patch; result becomes untraceable and non-reproducible.

---

## 1) BASELINE (REFERENCE)
BASELINE_PROMPT_ID: BASE_V0
BASELINE_SUMMARY (short):
- style: electronic nu metal + industrial touch
- structure: verse/chorus full song
- vocals: A rap verses / B melodic chorus
- repetition policy: chorus repeats, verses novel

---

## 2) PATCH LOG (BAD EXAMPLE)
PATCH_LABEL: "MINIMAL PATCH" (claimed)
AXIS_DECLARED: "make it better" (not an axis)

CHANGES (MULTI-AXIS):
- Style axis changed:
  - add synthwave + dnb + trap elements
  - change texture to lo-fi gritty
- Tempo axis changed:
  - change 94 bpm half-time to fast dnb tempo
- Vocal axis changed:
  - remove A/B roles, make single vocalist only
- Structure axis changed:
  - remove bridge, add pre-chorus, rearrange sections
- Negatives axis changed:
  - add 25 new negatives (spam)

DELTA SIZE:
- large rewrite (many blocks changed)

EXPECTED EFFECT:
- none stated

DECISION RECORD:
- none

BASELINE FREEZE:
- baseline text not included; unknown what changed exactly

---

## 3) EXPECTED GATE RESULTS (UID-ONLY)
EXPECTED_GATE_RESULTS:
- UE.KB.SPC.GATE.ONE_AXIS_DISCIPLINE.001 -> FAIL
  WHY: baseline not frozen (O1), axis not declared (O2), multiple axes changed (O3), delta not minimal (O4), no expected effect (O5), no decision log (O6)

Other gates:
- Gate 01/02/03/04: not primary; may fail depending on resulting chaos, but discipline gate fails first.

---

## 4) WHY THIS IS BAD (CALIBRATION NOTES)
WHY_BAD:
- Multi-axis changes prevent diagnosing what helped.
- “Minimal patch” is mislabeled; it is a rewrite.
- Missing baseline freeze makes it impossible to reproduce or compare results.

---

## 5) FIX PATH (WHAT TO DO)
Fix steps:
1) Freeze baseline:
   - copy baseline prompt as BASE_V0 (exact text)
2) Declare one axis only (choose):
   - vocals OR repetition OR style OR hook OR tempo
3) Split into variants:
   - Variant A: change only vocals
   - Variant B: change only repetition policy
   - Variant C: change only style anchors
4) Keep deltas minimal (≤ 1–3 lines per variant)
5) Add expected effect and record decision after results

Playbook mapping:
- PB-02 ONE-AXIS VARIANTS
- PB-04 PATCH MIN (only after selecting one axis)

---

## 6) TRACE
TRACE:
- MEMORY_REUSE: NO
- WEB_LOOKUP_USED: NO

--- END.
