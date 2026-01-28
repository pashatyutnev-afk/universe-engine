# SPC PRO PACK — CASE (BAD-001) — MISSING INPUTS (G1 FAIL / STOP-GAP) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/06__CASE_LIBRARY/02__CASE__BAD_001.md

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
UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.CASE.BAD.001.DRAFT.001
OWNER: SYSTEM
ROLE: BAD case anchor for calibrating G1 INPUT READINESS as FAIL(STOP/GAP). Demonstrates exact missing-field reporting and prohibition on proceeding without minimum inputs.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created BAD-001 anchor case: missing minimum inputs triggers G1 FAIL (STOP/GAP)."
- REASON: "Pack must never guess; this case teaches strict intake requirements."
- IMPACT: "Prevents invalid runs and vague outputs when lyrics/structure/language are absent."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.VOCAL_DIRECTOR.CASE.BAD001.001

---

## 0) CASE_RECORD
CASE_RECORD:
- CASE_ID: BAD-001
- TYPE: BAD
- CONTEXT:
  - format: unknown (not provided)
  - language: unknown (missing)
  - vocal_mode: unknown (missing)
  - tempo_feel: unknown (missing)
  - note: This case intentionally lacks minimum inputs.

---

## 1) INPUTS (MINIMAL) — INTENTIONALLY INCOMPLETE
Provided input (bad):
- "Сделай вокал мощнее и чтобы припев прям цеплял."

Missing:
- LYRIC_DRAFT: missing
- SECTION STRUCTURE / LOOP PROFILE: missing
- LANGUAGE: missing

No must-hear targets can be defined without lyrics/hook.

---

## 2) BASELINE_DIRECTION_PACK
NOT APPLICABLE (STOP/GAP).
Reason:
- Without minimum inputs, any “direction pack” would be guessing (forbidden).

---

## 3) EXPECTED_GATE_RESULTS (UID-ONLY)
VALIDATED_BY:
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.INPUT_READINESS.001

EXPECTED_GATE_RESULTS:
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.INPUT_READINESS.001 -> FAIL (STOP/GAP)

---

## 4) WHY (WHY THIS FAILS)
- Missing ALL minimum inputs required by G1:
  - I1 LYRIC_DRAFT missing
  - I2 SECTION STRUCTURE/LOOP missing
  - I3 LANGUAGE missing
- Therefore:
  - MUST stop and request missing fields explicitly.
  - Must not run G2..G9.

---

## 5) REQUIRED MISSING-FIELDS REPORT (ANCHOR FORMAT)
G1_RESULT (expected):
- VERDICT: FAIL(STOP/GAP)
- EVIDENCE_BLOCK:
  - LYRIC_DRAFT_PRESENT: NO
  - SECTION_STRUCTURE_PRESENT: NO
  - LANGUAGE_PRESENT: NO
  - HOOK_SECTION_IDENTIFIABLE: NO
  - MISSING_FIELDS:
    - I1 LYRIC_DRAFT
    - I2 SECTION STRUCTURE or LOOP PROFILE
    - I3 LANGUAGE
- NEXT_STEP:
  - "Request missing minimum inputs and stop."

---

## 6) FIX ROUTE
- Apply PB-01 intake step:
  - request: lyric draft (hook lines minimum)
  - request: section structure list or loop profile
  - request: language label + pronunciation risks
- Only after G1 PASS proceed to PB-02/G2.

---

## 7) TRACE
TRACE:
- MEMORY_REUSE: NO
- WEB_LOOKUP_USED: NO

--- END.
