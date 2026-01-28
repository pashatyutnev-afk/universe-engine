# 02__GATE__CONSISTENCY — MUSIC_PRODUCER_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/02__MUSIC_PRODUCER_SPC/05__KB_GATES/02__GATE__CONSISTENCY.md
SCOPE: KB — SPC Pro Pack — Music Producer — Gate (Consistency)
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS / 05__KB_GATES
DOC_TYPE: GATE
GATE_TYPE: CONSISTENCY
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.CONSISTENCY.001
OWNER: SPC (Music Producer)
ROLE: Detect contradictions, term drift, scope drift, and identity-anchor violations across O1/O2/(O3).

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Consistency gate initialized for Music Producer SPC pack."
- REASON: "Prevent hidden contradictions and drift after edits/variants."
- IMPACT: "Defines consistency checks and rerun discipline."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.MPROD.GATE.CONSIST.001

---

## PREREQUISITE (MUST)
- Core gate should be PASS or output is at least structurally complete.
Recommended order:
- GATE.CORE_QUALITY first, then this gate.

---

## INPUTS
- O1 PRODUCER_TASK_CARD
- O2 PRODUCTION_EXEC_PLAN
- Optional O3 VARIANTS_PLAN
- Optional patch log (if PB-02 or PB-03 was used)

---

## CONSISTENCY CHECKS (MUST)

### C1 Constraint alignment
[ ] All constraints listed in O1 are respected or explicitly handled in O2.
[ ] No new “hidden constraints” appear in O2 that contradict O1.

### C2 Scope discipline
[ ] No engineering recipes appear anywhere.
[ ] No legal certainty claims appear.
[ ] If prompt role split exists: no prompt takeover.
[ ] Routing notes exist where needed.

### C3 Term stability
[ ] Key terms are used consistently (hook timing, must-hear, identity anchors, variants).
[ ] No “synonym drift” that changes meaning (e.g., hook <=10s vs hook “sometime early”)

### C4 Structure alignment
[ ] Section map timings match described arc/peaks.
[ ] If Hook B is referenced, “one lever change” is respected.

### C5 Identity anchors (if O3 exists)
[ ] Identity anchors are explicitly stated.
[ ] Variants do not change anchors.
[ ] Each variant changes at most one lever.

### C6 Patch safety (if patched)
[ ] Patch axis matches the change made (no multi-axis disguised changes).
[ ] Patch did not break previously passing items.

---

## DECISION RULES
- FAIL:
  - any hard-limit appears (scope breach)
  - direct contradiction that breaks executability
- REWORK:
  - minor contradictions, missing routing note, term drift fixable with one-axis patch
- PASS:
  - no contradictions, stable terms, anchors intact

Axis recommendation:
- compliance (scope breach)
- consistency (term drift/contradictions)
- variants (anchor drift)
- structure (map vs arc mismatch)

---

## OUTPUT (MANDATORY)
- GATE_UID: UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.CONSISTENCY.001
- DECISION: <PASS|REWORK|FAIL>
- FAIL_REASONS:
  - <list C# items that failed>
- AXIS_RECOMMENDATION (if REWORK):
  - <one axis>
- RERUN_SET (after patch):
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.CONSISTENCY.001
  - (plus any gate/checklist that was affected)

---

## CALIBRATION ANCHORS
- EDGE case:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.CASE.EDGE.001
- BAD case (scope drift):
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.CASE.BAD.001

---

## REQUIRED UID REFERENCES
- PLAYBOOK (repair):
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.PB.DIAG_REWORK.001
- COMPLIANCE CHECKLIST:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.CHK.COMPLIANCE.001

---
END
