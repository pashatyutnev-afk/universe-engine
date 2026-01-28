# CASE — BORDERLINE (ONE-AXIS OK, DELTA TOO BIG) (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/06__CASE_LIBRARY/18__CASE__BORDERLINE_004.md

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
UID: UE.KB.SPC.CASE.PROMPT_ARCHITECT.BORDERLINE.004
OWNER: SYSTEM
ROLE: Borderline case calibrating Gate 05 REWORK threshold: baseline is frozen and axis is declared, but the “patch” delta is too large (rewrites a block) instead of a 1–3 line change. Should be REWORK, fixable by shrinking delta.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Added BORDERLINE case #4: one-axis declared but delta too big → Gate 05 REWORK; fix by reducing to minimal patch."
- REASON: "Need calibration between PASS and FAIL for iteration discipline: large delta is often fixable."
- IMPACT: "Improves minimal patch practice and reproducibility."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.CASE.BORDERLINE.004

---

## 0) CASE RECORD
CASE_RECORD:
- CASE_ID: CASE-BL-004
- TYPE: BORDERLINE
- CONTEXT:
  - FORMAT: rework iteration
  - LANGUAGE: RU
  - PIPELINE: post-fail patching
- INPUT_INTENT (short):
  - Change one axis (repetition), but patch rewrites too much; must be reduced.

---

## 1) BASELINE (FROZEN)
BASELINE_PROMPT_ID: BASE_V0
BASELINE_FREEZE: YES

Baseline snippet (relevant):
- CONSTRAINTS:
  - "hook chorus repeats"
  - "verses should be novel"

---

## 2) PATCH (BORDERLINE EXAMPLE)
PATCH_LABEL: PATCH_V1
AXIS_DECLARED: repetition
EXPECTED_EFFECT:
- “reduce repeated lines in verses while keeping chorus hook repetition”

CHANGES (TOO BIG):
- Rewrites the entire NEGATIVE_SPEC_BLOCK (adds 18 new items)
- Rewrites the STRUCTURE_BLOCK (adds pre-chorus, changes sections) (unintended second axis)
- Adds multiple extra constraints

Delta summary:
- more than 3 lines changed and touches multiple blocks

Decision record:
- missing

---

## 3) EXPECTED GATE RESULTS (UID-ONLY)
EXPECTED_GATE_RESULTS:
- UE.KB.SPC.GATE.ONE_AXIS_DISCIPLINE.001 -> REWORK
  WHY: O4 delta size too large; may also violate O3 if structure changed; decision record missing (O6)

Other gates:
- not primary for this calibration case

---

## 4) WHY THIS IS BORDERLINE
WHY_BORDERLINE:
- Baseline freeze exists and axis is declared (good).
- Intended change is valid (repetition).
- But the patch is not minimal and touches extra blocks.
→ REWORK is correct: we can reduce delta to a minimal patch and keep one axis.

---

## 5) MINIMAL FIX (SHRINK DELTA TO PASS)
Fix steps:
1) Revert patch to baseline.
2) Apply minimal edits only (1–3 lines):
   - Add/replace exactly these lines:
     - "Repetition allowed mainly in chorus/hook."
     - "Verses must be novel; avoid repeating identical lines/phrases in verses."
   - Add 1 targeted negative:
     - "avoid recycling chorus lines into verses"
3) Do NOT change structure sections (no pre-chorus edits) in this patch.
4) Record decision after results (winner/keeper/loser).

Expected after fix:
- UE.KB.SPC.GATE.ONE_AXIS_DISCIPLINE.001 -> PASS

Playbook mapping:
- PB-04 PATCH MIN (axis: repetition)
- PB-02 ONE-AXIS VARIANTS if multiple improvements needed

---

## 6) TRACE
TRACE:
- MEMORY_REUSE: NO
- WEB_LOOKUP_USED: NO

--- END.
