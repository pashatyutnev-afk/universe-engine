# SPC PRO PACK — CASE LIBRARY (README) (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/06__CASE_LIBRARY/00__README__CASES.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: README
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.1
UID: UE.KB.SPC.PACK.PROMPT_ARCHITECT.CASES.README.DRAFT.001
OWNER: SYSTEM
ROLE: Case library map for PROMPT_ARCHITECT: what case types exist, how cases calibrate gates, and how to expand the library (good/bad/borderline/edge). Not navigation authority.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: PATCH
- SUMMARY: "Case library reached >=25 cases. Updated distribution notes and case map."
- REASON: "L3 readiness target requires >=25 calibrated cases."
- IMPACT: "Stronger calibration coverage across gates and compliance."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.PROMPT.CASES.README.002

---

## 0) PURPOSE
Case library provides concrete examples to:
- calibrate gates (PASS / FAIL / REWORK / BORDERLINE)
- teach what “good” looks like
- speed up diagnosis and rework selection

Rule:
- Every key gate should have at least:
  - 1 good, 1 bad, 1 borderline case.

---

## 1) CASE TYPES (CANON)
CASE_TYPES:
- GOOD:
  - prompt contract that passes gates (clean, controllable)

- BAD:
  - prompt contract that fails a gate clearly (missing blocks, contradictions, overload)

- BORDERLINE:
  - near-pass that needs a small patch (teaches thresholds)

- EDGE:
  - special situations:
    - loop/short format corner cases
    - fusion/dominance edge
    - multi-voice overload edge
    - compliance boundary cases

---

## 2) GATE CALIBRATION LINKS (UID-ONLY)
Cases must state which gate(s) they calibrate:

GATES_IN_THIS_PACK (UID-ONLY):
- UE.KB.SPC.GATE.PROMPT_CONTRACT_CLARITY.001
- UE.KB.SPC.GATE.VOICE_DIVERSITY_INTENT.001
- UE.KB.SPC.GATE.REPETITION_CONTROL_INTENT.001
- UE.KB.SPC.GATE.STYLE_FINGERPRINT_STABILITY.001
- UE.KB.SPC.GATE.ONE_AXIS_DISCIPLINE.001

Rule:
- Each case must list:
  - VALIDATED_BY (gate UIDs)
  - expected result per gate (PASS/REWORK/FAIL)

---

## 3) CURRENT COVERAGE SNAPSHOT (NOW)
TOTAL_CASES: 25 (TARGET >=25 REACHED)

Approx distribution (by file set):
- GOOD: 7
- BAD: 8
- BORDERLINE: 5
- EDGE: 5

Notes:
- This distribution is acceptable for L3 calibration.
- Continue adding when new failure modes appear.

---

## 4) CASE FILE STRUCTURE (REQUIRED FIELDS)
Each case file must include:

CASE_RECORD:
- CASE_ID:
- TYPE: GOOD/BAD/BORDERLINE/EDGE
- CONTEXT:
  - format (full/loop/short)
  - language
  - vocal mode
- INPUT_INTENT (short):
- PROMPT_CONTRACT (excerpt or full if short):
- EXPECTED_GATE_RESULTS (UID-ONLY):
  - <gate uid> -> PASS/REWORK/FAIL
- WHY (explain in 3–6 bullets):
- FIX (if BORDERLINE or BAD):
  - which playbook to use + minimal patch idea
- TRACE:
  - MEMORY_REUSE: YES/NO
  - WEB_LOOKUP_USED: YES/NO

---

## 5) CASE MAP (FILES 01..25)
GOOD:
- 01__CASE__GOOD.md
- 07__CASE__GOOD_002.md
- 10__CASE__GOOD_003.md
- 16__CASE__GOOD_004.md
- 19__CASE__GOOD_005.md
- 23__CASE__GOOD_006.md
- 25__CASE__GOOD_007.md

BAD:
- 02__CASE__BAD.md
- 05__CASE__BAD_002.md
- 09__CASE__BAD_003.md
- 12__CASE__BAD_004.md
- 15__CASE__BAD_005.md
- 17__CASE__BAD_006.md
- 21__CASE__BAD_007.md
- 24__CASE__BAD_008.md

BORDERLINE:
- 03__CASE__BORDERLINE.md
- 06__CASE__BORDERLINE_002.md
- 13__CASE__BORDERLINE_003.md
- 18__CASE__BORDERLINE_004.md
- 22__CASE__BORDERLINE_005.md

EDGE:
- 04__CASE__EDGE_001.md
- 08__CASE__EDGE_002.md
- 11__CASE__EDGE_003.md
- 14__CASE__EDGE_004.md
- 20__CASE__EDGE_005.md

---

## 6) EXPANSION RULES (BEYOND L3)
Add cases when:
- a new failure mode appears
- a gate threshold is unclear (create BORDERLINE)
- a playbook fix pattern repeats (document it)

---

## 7) HARD FAIL CONDITIONS
FAIL IF:
- a case does not map to gate results (no calibration)
- a case claims PASS/FAIL without specifying which gate(s)
- a case includes external links as “authority” instead of UID

---

## 8) RELATED (UID-ONLY)
XREF:
- UE.KB.SPC.PACK.PROMPT_ARCHITECT.GATES.README.DRAFT.001 | WHY: gate list and run order
- UE.KB.SPC.PACK.PROMPT_ARCHITECT.PLAYBOOKS.README.DRAFT.001 | WHY: playbook selection for fixes
- UE.KB.SPC.PACK.PROMPT_ARCHITECT.REGRESSION.DRAFT.001 | WHY: regression anchors reference these cases

--- END.
