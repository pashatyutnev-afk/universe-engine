# SPC PRO PACK — CASE LIBRARY (README) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/06__CASE_LIBRARY/00__README__CASES.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: README
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.CASES.README.DRAFT.001
OWNER: SYSTEM
ROLE: Case library map for VOCAL_DIRECTOR: what case types exist, how cases calibrate gates (G1..G9), and how to expand the library with GOOD/BAD/BORDERLINE/EDGE anchors. Not navigation authority.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created VOCAL_DIRECTOR case library README with gate calibration map and planned 25-case skeleton."
- REASON: "L3 readiness requires calibrated thresholds and repeatable examples for failures and fixes."
- IMPACT: "Faster diagnosis, deterministic rework selection, and stable quality across runs."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.VOCAL_DIRECTOR.CASES.001

---

## 0) PURPOSE
Case library provides concrete examples to:
- calibrate gates (PASS / REWORK / FAIL)
- teach “what good looks like”
- speed up diagnosis and playbook selection

Rule:
- Every key gate should have at least:
  - 1 GOOD case, 1 BAD case, 1 BORDERLINE threshold case.

---

## 1) CASE TYPES (CANON)
CASE_TYPES:
- GOOD:
  - direction pack that passes gates (clear, executable, repeatable)

- BAD:
  - direction pack that fails a gate clearly (missing targets, contradictions, scope violations)

- BORDERLINE:
  - near-pass that needs a small patch (teaches thresholds)

- EDGE:
  - special situations:
    - fast density/breath trap
    - extreme delivery mode masking consonants
    - stacking masking P0
    - arc lift conflicts with intelligibility
    - ownership/compliance boundary cases

---

## 2) GATE CALIBRATION MAP (UID-ONLY)
Cases must state which gate(s) they calibrate:

GATE_UIDS (VOCAL_DIRECTOR):
- G1: UE.KB.SPC.GATE.VOCAL_DIRECTOR.INPUT_READINESS.001
- G2: UE.KB.SPC.GATE.VOCAL_DIRECTOR.MUST_HEAR.001
- G3: UE.KB.SPC.GATE.VOCAL_DIRECTOR.INTELLIGIBILITY.001
- G4: UE.KB.SPC.GATE.VOCAL_DIRECTOR.DELIVERY_COHERENCE.001
- G5: UE.KB.SPC.GATE.VOCAL_DIRECTOR.ARC_CONTRAST.001
- G6: UE.KB.SPC.GATE.VOCAL_DIRECTOR.BREATH_SINGABILITY.001
- G7: UE.KB.SPC.GATE.VOCAL_DIRECTOR.STACKING_SAFE.001
- G8: UE.KB.SPC.GATE.VOCAL_DIRECTOR.TAKE_PACK.001
- G9: UE.KB.SPC.GATE.VOCAL_DIRECTOR.SCOPE_COMPLIANCE.001

Rule:
- Each case must list:
  - VALIDATED_BY (gate UIDs)
  - expected result per gate (PASS/REWORK/FAIL)

---

## 3) CASE FILE STRUCTURE (REQUIRED FIELDS)
Each case file must include:

CASE_RECORD:
- CASE_ID:
- TYPE: GOOD/BAD/BORDERLINE/EDGE
- CONTEXT:
  - format (full/loop/short)
  - language
  - vocal mode (rap/sing/mixed/aggressive/clean)
  - tempo feel (if known)
- INPUTS (minimal):
  - lyric excerpt (hook + 1 verse fragment)
  - structure labels
  - must-hear targets (P0)
- BASELINE_DIRECTION_PACK (short):
  - delivery profile (principles)
  - arc levers (1–3)
  - breath policy (allowed/forbidden)
  - stacking plan (or N/A)
  - take goals + QC hard fails
- EXPECTED_GATE_RESULTS (UID-ONLY):
  - <gate uid> -> PASS/REWORK/FAIL
- WHY (3–8 bullets):
  - why this passes/fails which gate
- FIX ROUTE:
  - which playbook(s) fix it (PB-01..PB-08)
  - minimal patch idea (1–3 changes)
- TRACE:
  - MEMORY_REUSE: YES/NO
  - WEB_LOOKUP_USED: YES/NO

---

## 4) COVERAGE TARGET (L3)
TARGET:
- TOTAL_CASES >= 25
- distribution (recommended):
  - GOOD: 7
  - BAD: 8
  - BORDERLINE: 5
  - EDGE: 5

---

## 5) PLANNED CASE MAP (FILES 01..25)
NOTE:
- These filenames are placeholders for the skeleton.
- Each case must later be filled with real content + gate results.

GOOD (7):
- 01__CASE__GOOD_001.md  (G1..G3 pass anchor)
- 07__CASE__GOOD_002.md  (G4 delivery coherence anchor)
- 10__CASE__GOOD_003.md  (G5 arc/contrast anchor)
- 16__CASE__GOOD_004.md  (G6 breath-safe hook anchor)
- 19__CASE__GOOD_005.md  (G7 stacking safe anchor)
- 23__CASE__GOOD_006.md  (G8 take pack anchor)
- 25__CASE__GOOD_007.md  (full-stack pass: G1..G9)

BAD (8):
- 02__CASE__BAD_001.md   (missing inputs -> G1 FAIL)
- 05__CASE__BAD_002.md   (P0 missing / bloated -> G2 FAIL)
- 09__CASE__BAD_003.md   (no intelligibility checklist -> G3 FAIL)
- 12__CASE__BAD_004.md   (contradictory delivery profile -> G4 FAIL)
- 15__CASE__BAD_005.md   (flat arc, no lift -> G5 REWORK/FAIL)
- 17__CASE__BAD_006.md   (breath splits P0 -> G6 FAIL)
- 21__CASE__BAD_007.md   (stacking masks P0 -> G7 FAIL)
- 24__CASE__BAD_008.md   (scope violation: lyric rewrite / mix chain -> G9 FAIL)

BORDERLINE (5):
- 03__CASE__BORDERLINE_001.md (P0 too long -> G2 REWORK)
- 06__CASE__BORDERLINE_002.md (intelligibility ok but breath policy incomplete -> G6 REWORK)
- 13__CASE__BORDERLINE_003.md (arc levers too many -> G5 REWORK)
- 18__CASE__BORDERLINE_004.md (take goals too many -> G8 REWORK)
- 22__CASE__BORDERLINE_005.md (stacking map ok but protected zones weak -> G7 REWORK)

EDGE (5):
- 04__CASE__EDGE_001.md (fast rap density trap -> PB-04 escalation)
- 08__CASE__EDGE_002.md (aggressive delivery masks consonants -> PB-03/PB-08 A1/A4)
- 11__CASE__EDGE_003.md (chorus lift conflicts with intelligibility -> PB-05+PB-03)
- 14__CASE__EDGE_004.md (foreign name pronunciation risk -> PB-02 risk notes)
- 20__CASE__EDGE_005.md (arrangement seat conflict masking P0 -> escalation to Arranger/Producer)

---

## 6) EXPANSION RULES
Add cases when:
- a new failure mode appears
- a gate threshold is unclear (create BORDERLINE)
- a fix pattern repeats (document the minimal patch)

After adding a new case:
- update TOTAL_CASES and distribution
- ensure it calibrates at least one gate UID

---

## 7) HARD FAIL CONDITIONS
FAIL IF:
- a case does not map to gate results (no calibration)
- a case claims PASS/FAIL without specifying which gate(s)
- a case introduces new rules not present in pack docs
- a case includes out-of-scope prescriptions (mix chains, lyric rewrites)

---

## 8) RELATED (UID-ONLY)
XREF:
- UE.KB.SPC.PACK.VOCAL_DIRECTOR.GATES.README.DRAFT.001 | WHY: gate list and order
- UE.KB.SPC.PACK.VOCAL_DIRECTOR.PLAYBOOKS.README.DRAFT.001 | WHY: fix routing
- UE.KB.SPC.PACK.VOCAL_DIRECTOR.PRINCIPLES.DRAFT.001 | WHY: golden rules enforced by cases

--- END.
