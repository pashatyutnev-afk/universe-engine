# CASE — GOOD (ONE-AXIS PASS: FROZEN BASELINE + TINY DELTA + DECISION) (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/06__CASE_LIBRARY/19__CASE__GOOD_005.md

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
UID: UE.KB.SPC.CASE.PROMPT_ARCHITECT.GOOD.005
OWNER: SYSTEM
ROLE: GOOD case calibrating Gate 05 PASS: baseline frozen, one axis declared, minimal delta (1–2 lines), expected effect stated, and decision recorded. Demonstrates reproducible iteration discipline.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Added GOOD case #5: one-axis discipline PASS example with minimal patch and decision record."
- REASON: "Need a positive anchor for Gate 05 demonstrating correct iteration logs."
- IMPACT: "Improves reproducibility and learning across prompt iterations."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.CASE.GOOD.005

---

## 0) CASE RECORD
CASE_RECORD:
- CASE_ID: CASE-GOOD-005
- TYPE: GOOD
- CONTEXT:
  - FORMAT: rework iteration (post-fail)
  - LANGUAGE: RU
  - PIPELINE: patching after QA feedback
- INPUT_INTENT (short):
  - Reduce verse repetition without changing style, structure, or vocals.

---

## 1) BASELINE (FROZEN)
BASELINE_PROMPT_ID: BASE_V0
BASELINE_FREEZE: YES
BASELINE_HASH (optional label): BASEV0-EXACT-COPY

Baseline relevant lines:
- "Repetition allowed mainly in chorus/hook."
- "Verses should be novel."

---

## 2) PATCH LOG (GOOD EXAMPLE)
PATCH_LABEL: PATCH_V1
AXIS_DECLARED: repetition
EXPECTED_EFFECT:
- "Less repeated lines in verses; chorus hook repetition preserved."

DELTA (TINY / 1–2 LINES):
- Change/append exactly these lines in CONSTRAINTS_BLOCK:
  - add: "Avoid repeating identical lines/phrases in verses."
  - add: "Avoid recycling chorus lines into verses."

NOT CHANGED:
- STYLE_BLOCK unchanged
- STRUCTURE_BLOCK unchanged
- VOCAL_INTENT_BLOCK unchanged
- BPM/feel unchanged

DECISION RECORD (AFTER RUN):
- RESULT: PASS
- DECISION: KEEP PATCH_V1
- NOTE: "Verse repetition reduced; hook intact."

LOOP COUNT:
- 1

---

## 3) EXPECTED GATE RESULTS (UID-ONLY)
EXPECTED_GATE_RESULTS:
- UE.KB.SPC.GATE.ONE_AXIS_DISCIPLINE.001 -> PASS
  WHY: baseline frozen, axis declared, minimal delta, expected effect stated, decision recorded

Other gates:
- not primary; assumed unchanged because only repetition constraints changed

---

## 4) WHY THIS IS GOOD (CALIBRATION NOTES)
WHY_GOOD:
- Single axis only (repetition).
- Delta is minimal and localized (1–2 lines).
- Baseline is frozen, so comparison is valid.
- Expected effect and decision are recorded, enabling learning.

---

## 5) TRACE
TRACE:
- MEMORY_REUSE: NO
- WEB_LOOKUP_USED: NO

--- END.
