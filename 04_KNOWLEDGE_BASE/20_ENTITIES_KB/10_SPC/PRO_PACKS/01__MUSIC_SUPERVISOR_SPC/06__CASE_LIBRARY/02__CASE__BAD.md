# 02__CASE__BAD — MUSIC_SUPERVISOR_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/01__MUSIC_SUPERVISOR_SPC/06__CASE_LIBRARY/02__CASE__BAD.md
SCOPE: KB — SPC Pro Pack — Music Supervisor — Case: BAD
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS
DOC_TYPE: CASE
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.MUSIC_SUPERVISOR.CASE.BAD.001
OWNER: SPC (Music Supervisor)
ROLE: Failure exemplar (must fail at least one core gate).

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Bad case initialized (template failure anchor) for Music Supervisor SPC pack."
- REASON: "Provide FAIL reference for gates and rubric."
- IMPACT: "Must fail core quality and/or consistency."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.MSUP.CASE.BAD.001

---

## CASE_ID
- ID: CASE-B-001
- TYPE: BAD

---

## CONTEXT
A task where output looks “long/complex” but fails core acceptance due to a hard, testable issue.

---

## INPUTS_SUMMARY (MIN)
- TASK_ID: <...>
- GOAL: <what to deliver>
- FORMAT/PLATFORM: <...>
- CONSTRAINTS: <...>
- PRIMARY_OUTPUTS: <output_1>, <output_2>

---

## EXPECTED_OUTPUT (SUMMARY)
- Should be clear, complete, consistent, and within scope.

---

## OUTPUT_SUMMARY (ACTUAL — WHAT WENT WRONG)
- Symptoms:
  - <symptom_1: ambiguity that changes decisions>
  - <symptom_2: contradiction between sections>
  - <symptom_3: missing core section>
- Net effect:
  - output cannot be used without guessing OR contains conflicting guidance.

---

## WHY THIS IS BAD (FAIL ANCHORS)
Pick at least one (document it clearly):
- Core intent unclear (fails clarity)
- Missing required parts (fails completeness)
- Contradiction (fails consistency)
- Constraints broken in a way that requires rewrite

---

## FAILED VALIDATIONS (UID-ONLY)
- CHECKLISTS:
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.CHK.QUALITY.001: FAIL
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.CHK.COMPLIANCE.001: <PASS|REWORK|FAIL>
- GATES:
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.GATE.CORE_QUALITY.001: FAIL
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.GATE.CONSISTENCY.001: <PASS|REWORK|FAIL>

---

## ROOT CAUSE (ONE SENTENCE)
- <e.g., "Output mixes two incompatible rulesets, causing contradictions that break acceptance.">

---

## FIX PATH (PB-02 ONE-AXIS)
- PLAYBOOK: PB-02 DIAGNOSE_AND_REWORK
- AXIS: <clarity|consistency|completeness|structure>
- MINIMUM FIX:
  - <1–3 bullets describing the minimal change>
- VALIDATE_AFTER:
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.CHK.QUALITY.001
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.GATE.CORE_QUALITY.001
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.GATE.CONSISTENCY.001 (if relevant)

---

## NOTES
- Use this case as the anchor for:
  - Rubric 0–3 examples (clarity/consistency)
  - Gate FAIL calibration

---
END
