# 03__CASE__BORDERLINE — MUSIC_SUPERVISOR_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/01__MUSIC_SUPERVISOR_SPC/06__CASE_LIBRARY/03__CASE__BORDERLINE.md
SCOPE: KB — SPC Pro Pack — Music Supervisor — Case: BORDERLINE
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS
DOC_TYPE: CASE
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.MUSIC_SUPERVISOR.CASE.BORDERLINE.001
OWNER: SPC (Music Supervisor)
ROLE: Borderline exemplar (decision rule: REWORK vs PASS).

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Borderline case initialized for Music Supervisor SPC pack."
- REASON: "Calibrate decision boundaries for REWORK."
- IMPACT: "Teaches one-axis repair vs accept."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.MSUP.CASE.BORDER.001

---

## CASE_ID
- ID: CASE-BL-001
- TYPE: BORDERLINE

---

## CONTEXT
Output is broadly usable but has one quality defect that should trigger REWORK (not FAIL).

---

## INPUTS_SUMMARY (MIN)
- TASK_ID: <...>
- GOAL: <what to deliver>
- FORMAT/PLATFORM: <...>
- CONSTRAINTS: <...>
- PRIMARY_OUTPUTS: <output_1>, <output_2>

---

## OUTPUT_SUMMARY (ACTUAL)
- Good parts:
  - <what is already acceptable>
- Defect:
  - <one clear defect: ambiguity OR minor incompleteness OR minor structure>
- Why it matters:
  - <impact>

---

## DECISION RULE (THE WHOLE POINT)
Choose one and justify:

### RULE A — REWORK (preferred)
Trigger REWORK if:
- defect can be fixed with ONE axis patch in <N> minutes/steps
- and fixing does not change scope

### RULE B — PASS (rare)
Allow PASS only if:
- defect does not affect any decisions/usage
- and does not propagate into downstream artifacts

---

## VALIDATION RESULT (UID-ONLY)
- CHECKLISTS:
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.CHK.QUALITY.001: REWORK
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.CHK.COMPLIANCE.001: PASS
- GATES:
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.GATE.CORE_QUALITY.001: REWORK
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.GATE.CONSISTENCY.001: PASS

---

## FIX PATH (PB-02 ONE-AXIS)
- PLAYBOOK: PB-02
- AXIS: <clarity|structure|completeness|consistency>
- PATCH:
  - <1–3 bullets minimal change>
- VALIDATE_AFTER:
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.CHK.QUALITY.001
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.GATE.CORE_QUALITY.001

---

## NOTES
- This case calibrates “REWORK, not FAIL”.
- Attach to rubric anchors as 4–6 example.

---
END
