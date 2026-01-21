# 06__CASE_LIBRARY — SPC PRO PACK (TEMPLATE)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/SPC__TEMPLATE/06__CASE_LIBRARY.md
SCOPE: Knowledge Base — Entities KB — SPC — Pro Pack Template
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
DOC_TYPE: TEMPLATE
TEMPLATE_FOR: SPC_PRO_PACK (case library)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.TPL.SPC.PRO_PACK.CASES.001
OWNER: SYSTEM
ROLE: Canonical case library template (good/bad/borderline/edge) used to calibrate gates and scoring.

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Initial case library template for SPC Pro Packs."
- REASON: "Provide exemplars for validation gates and training-by-example."
- IMPACT: "Real packs should include at least 1 good + 1 bad case."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.TPL.CASES.001

---

## PURPOSE (LAW)
Кейсы нужны не “для красоты”, а для:
- калибровки гейтов (что значит PASS/REWORK/FAIL),
- обучения быстрым диагнозам,
- фиксации типовых ошибок и edge-ситуаций.

> RULE: Кейсы должны ссылаться на validation (UID-only) и на outcomes из skill tree.

---

## BINDINGS (MUST MATCH PASSPORT)
- PACK_UID: <PACK_UID>
- SPC_ENTITY_UID: <SPC_ENTITY_UID>
- TARGET_PROFICIENCY_LEVEL: <L1|L2|L3|L4>

---

## CASE CONTRACT (MUST USE THIS SHAPE)
### FIELDS
- CASE_ID
- CASE_TYPE: GOOD | BAD | BORDERLINE | EDGE
- TITLE
- CONTEXT
- INPUTS (minimal)
- EXPECTED OUTPUT (summary)
- ACTUAL OUTPUT (snippet/summary)
- WHY (why good/bad)
- RELATED SKILLS/OUTCOMES
- VALIDATION RESULT (UID-only)
- FIX PATH (playbook + one-axis)
- NOTES

---

## CASE INDEX (README)
### GOOD
- CASE-G-001: <title>

### BAD
- CASE-B-001: <title>

### BORDERLINE
- CASE-BL-001: <title>

### EDGE
- CASE-E-001: <title>

---

## CASES

### CASE-G-001
- CASE_ID: CASE-G-001
- CASE_TYPE: GOOD
- TITLE: <short title>
- CONTEXT: <what situation/task this represents>
- INPUTS (MIN):
  - <input_1>
- EXPECTED OUTPUT (SUMMARY):
  - <what should be produced>
- ACTUAL OUTPUT (SUMMARY):
  - <what was produced>
- WHY GOOD:
  - <reason_1>
  - <reason_2>
- RELATED SKILLS/OUTCOMES:
  - <A1 / O-A1-1>
- VALIDATION RESULT (UID-ONLY):
  - PASSED: <CHK_UID_02>, <GATE_UID_CLARITY>
- FIX PATH:
  - Not needed
- NOTES:
  - <optional>

---

### CASE-B-001
- CASE_ID: CASE-B-001
- CASE_TYPE: BAD
- TITLE: <short title>
- CONTEXT: <...>
- INPUTS (MIN):
  - <...>
- EXPECTED OUTPUT (SUMMARY):
  - <...>
- ACTUAL OUTPUT (SUMMARY):
  - <...>
- WHY BAD:
  - Violations:
    - <hard limit violated or scope drift>
  - Failure modes:
    - <FM-xxx>
- RELATED SKILLS/OUTCOMES:
  - <...>
- VALIDATION RESULT (UID-ONLY):
  - FAILED: <CHK_UID_03>, <GATE_UID_SCOPE_COMPLIANCE>
- FIX PATH:
  - PB-03 (DIAGNOSE_AND_REWORK)
  - PB-02 (ONE_AXIS_PATCH_LOOP) — AXIS: <axis>
- NOTES:
  - <...>

---

### CASE-BL-001
- CASE_ID: CASE-BL-001
- CASE_TYPE: BORDERLINE
- TITLE: <short title>
- CONTEXT: <...>
- INPUTS (MIN): <...>
- EXPECTED OUTPUT: <...>
- ACTUAL OUTPUT: <...>
- WHY BORDERLINE:
  - What passes:
    - <...>
  - What is risky:
    - <...>
  - Decision rule:
    - If <condition> → PASS
    - Else → REWORK
- RELATED SKILLS/OUTCOMES: <...>
- VALIDATION RESULT (UID-ONLY):
  - REWORK: <CHK_UID_02> (or gate)
- FIX PATH:
  - PB-02 — AXIS: <axis>
- NOTES: <...>

---

### CASE-E-001
- CASE_ID: CASE-E-001
- CASE_TYPE: EDGE
- TITLE: <edge condition title>
- CONTEXT: <edge scenario>
- INPUTS (MIN): <...>
- EXPECTED OUTPUT: <...>
- ACTUAL OUTPUT: <...>
- EDGE CONDITION:
  - <what makes it special>
- MAIN RISK:
  - <risk>
- HANDLING STEPS:
  1) <step>
  2) <step>
- RELATED SKILLS/OUTCOMES: <...>
- VALIDATION RESULT (UID-ONLY):
  - MUST PASS: <GATE_UID_EDGE_HANDLING> (or checklist)
- FIX PATH:
  - PB-03 / PB-05 (if routing)
- NOTES: <...>

---

## CASE MAINTENANCE RULES
- Every new gate should have at least one supporting case (GOOD or EDGE).
- Every recurring fail mode should eventually have a BAD case.
- Cases must not include large external copyrighted text; keep summaries/snippets minimal.

---
END
