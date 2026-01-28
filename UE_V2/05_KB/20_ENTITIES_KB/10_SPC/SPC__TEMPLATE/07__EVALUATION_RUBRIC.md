# 07__EVALUATION_RUBRIC — SPC PRO PACK (TEMPLATE)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/SPC__TEMPLATE/07__EVALUATION_RUBRIC.md
SCOPE: Knowledge Base — Entities KB — SPC — Pro Pack Template
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
DOC_TYPE: TEMPLATE
TEMPLATE_FOR: SPC_PRO_PACK (evaluation rubric)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.TPL.SPC.PRO_PACK.RUBRIC.001
OWNER: SYSTEM
ROLE: Canonical scoring rubric template (axes + anchors + thresholds + gate override).

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Initial evaluation rubric template for SPC Pro Packs."
- REASON: "Enable consistent scoring and readiness decisions."
- IMPACT: "Rubric must be aligned with gates and outputs."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.TPL.RUBRIC.001

---

## PURPOSE (LAW)
Рубрика нужна, чтобы:
- оценивать качество результата по понятным осям,
- принимать решение “готово/на доработку”,
- калибровать ожидания между SPC/ORC/QA.

> RULE: Рубрика НЕ отменяет гейты. Если ключевой гейт провален — результат не принимается.

---

## BINDINGS (MUST MATCH PASSPORT)
- PACK_UID: <PACK_UID>
- SPC_ENTITY_UID: <SPC_ENTITY_UID>
- TARGET_PROFICIENCY_LEVEL: <L1|L2|L3|L4>
- PRIMARY_OUTPUTS:
  - <output_1>
  - <output_2>

---

## GATE OVERRIDE RULE (ABSOLUTE)
### HARD OVERRIDE
- If any of these gates FAIL → FINAL_DECISION = FAIL (no score compensation):
  - <GATE_UID_SCOPE_COMPLIANCE>
  - <GATE_UID_HARD_LIMITS>
  - <GATE_UID_MIN_READINESS>

### SOFT OVERRIDE
- If these gates FAIL → FINAL_DECISION = REWORK (even if avg score is high):
  - <GATE_UID_CLARITY>
  - <GATE_UID_CONSISTENCY>

---

## SCORING MODEL
- SCALE: 0..10 per axis
- AVG_SCORE: mean of axes (or weighted mean)
- READY_THRESHOLD:
  - L1: <min_avg>
  - L2: <min_avg>
  - L3: <min_avg>
  - L4: <min_avg>
- WEIGHTS (optional):
  - <axis>: <weight>

> Default: equal weights unless the pack declares otherwise.

---

## AXES (0..10)
> 5–9 осей. Каждая ось: definition + what “10” means + what “0” means + anchors.

### AX-01 — CLARITY
- DEFINITION: Output is easy to read, unambiguous, and actionable.
- 0 ANCHOR: unreadable / ambiguous / missing key info
- 3 ANCHOR: partially clear, requires guessing, weak structure
- 6 ANCHOR: mostly clear, minor ambiguity, usable with small edits
- 8 ANCHOR: clear and consistent, minimal friction
- 10 ANCHOR: crystal clear, self-contained, no ambiguity
- RELATED VALIDATION (UID-ONLY):
  - <CHK-02> / <GATE_UID_CLARITY>

### AX-02 — COMPLETENESS
- DEFINITION: All required sections/outputs are present.
- ANCHORS: 0 / 3 / 6 / 8 / 10 as above
- RELATED VALIDATION:
  - <CHK-02>

### AX-03 — CONSISTENCY
- DEFINITION: No contradictions; formatting and terms stable.
- RELATED VALIDATION:
  - <GATE_UID_CONSISTENCY>

### AX-04 — SCOPE DISCIPLINE
- DEFINITION: No scope creep; respects COVERS/EXCLUDES.
- RELATED VALIDATION:
  - <GATE_UID_SCOPE_COMPLIANCE>

### AX-05 — REPEATABILITY
- DEFINITION: Another operator could reproduce the result with the same inputs.
- RELATED VALIDATION:
  - <CHK-01> / PB-01 trace

(…add more axes if needed: safety, efficiency, elegance, edge-case handling…)

---

## SCORING PROCEDURE
1) Verify HARD OVERRIDE gates.
2) If passed → score each axis 0..10 with anchors.
3) Compute AVG_SCORE.
4) Apply SOFT OVERRIDE gates.
5) Output FINAL_DECISION:
   - READY (publish/use)
   - REWORK (patch loop)
   - FAIL (stop/escalate)

---

## EXEMPLARS (LINK TO CASE LIBRARY)
> Привязка к кейсам для калибровки оценки.

- AX-01 CLARITY:
  - 8–10 examples: CASE-G-001
  - 0–3 examples: CASE-B-001
- AX-04 SCOPE:
  - FAIL example: CASE-B-001
  - Edge handling: CASE-E-001

---

## OUTPUT: RUBRIC REPORT (TEMPLATE)
- DATE: <yyyy-mm-dd>
- PACK_UID: <...>
- DECISION: <READY|REWORK|FAIL>
- HARD_GATES:
  - <gate_uid>: <PASS|FAIL>
- SOFT_GATES:
  - <gate_uid>: <PASS|FAIL>
- SCORES:
  - CLARITY: <0..10>
  - COMPLETENESS: <0..10>
  - CONSISTENCY: <0..10>
  - SCOPE: <0..10>
  - REPEATABILITY: <0..10>
- AVG_SCORE: <...>
- ONE-AXIS NEXT STEP (if REWORK):
  - AXIS: <...>
  - ACTION: <...>

---
END
