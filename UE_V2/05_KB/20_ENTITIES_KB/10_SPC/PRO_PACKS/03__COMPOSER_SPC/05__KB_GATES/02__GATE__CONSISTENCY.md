# 02__GATE__CONSISTENCY — COMPOSER_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/03__COMPOSER_SPC/05__KB_GATES/02__GATE__CONSISTENCY.md
SCOPE: KB — SPC Pro Pack — Composer — Gate (Consistency)
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS / 05__KB_GATES
DOC_TYPE: GATE
GATE_TYPE: CONSISTENCY
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.COMPOSER.GATE.CONSISTENCY.001
OWNER: SPC (Composer)
ROLE: Detect contradictions, term drift, scope drift, and identity-anchor violations across O1/O2/(O3+).

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Consistency gate initialized for Composer SPC pack."
- REASON: "Prevent hidden contradictions and drift after edits/variants."
- IMPACT: "Defines checks and rerun discipline."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.COMPOSER.GATE.CONSIST.001

---

## PREREQUISITE (MUST)
Recommended order:
- Run CORE_OUTPUT_QUALITY first, then this gate.

---

## INPUTS
- O1 COMPOSER_TASK_CARD
- O2 COMPOSITION_EXEC_PLAN
- Optional O3/O4/O5 (motif/harmony/melody add-ons)
- Optional patch log (if PB-02 was used)

---

## CONSISTENCY CHECKS (MUST)

### C1 Constraint alignment
[ ] All constraints listed in O1 are respected or explicitly handled in O2.
[ ] No new “hidden constraints” appear that contradict O1.

### C2 Scope discipline
[ ] No engineering recipes appear anywhere.
[ ] No legal certainty claims appear.
[ ] If prompt role split exists: no prompt takeover.
[ ] Routing notes exist where needed.

### C3 Term stability (composition terms)
[ ] Hook placement window stable (<=10–12s or stated otherwise)
[ ] Motif fingerprint wording consistent (contour/rhythm cell)
[ ] Tonal center/modal color consistent unless intentional shift is declared
[ ] “One lever change” stable across variants

### C4 Form alignment
[ ] Form map timings match described arc/contrast
[ ] Contrast points align with harmonic/melodic intent
[ ] Repetition control rules do not contradict motif identity

### C5 Identity anchors (if variants exist)
[ ] Identity anchors explicitly stated
[ ] Variants do not change anchors
[ ] Each variant changes at most one lever

### C6 Patch safety (if patched)
[ ] Patch axis matches the change made (no multi-axis drift)
[ ] Patch did not break previously passing items

---

## DECISION RULES
- FAIL:
  - any hard-limit appears (scope breach)
  - direct contradiction that breaks executability (tonal center vs plan, hook window broken)
- REWORK:
  - minor contradictions / term drift fixable with one-axis patch
  - missing routing note / anchor statement
- PASS:
  - no contradictions, stable terms, anchors intact

Axis recommendation:
- compliance (scope breach)
- consistency (term drift/contradictions)
- motif / harmony / melody (if core drift originates there)
- structure (form mismatch)

---

## OUTPUT (MANDATORY)
- GATE_UID: UE.KB.SPC.PACK.COMPOSER.GATE.CONSISTENCY.001
- DECISION: <PASS|REWORK|FAIL>
- FAIL_REASONS:
  - <list C# items that failed>
- AXIS_RECOMMENDATION (if REWORK):
  - <one axis>
- RERUN_SET (after patch):
  - UE.KB.SPC.PACK.COMPOSER.GATE.CONSISTENCY.001
  - (plus any gate/checklist affected)

---

## CALIBRATION ANCHORS
- EDGE: UE.KB.SPC.PACK.COMPOSER.CASE.EDGE.001
- BAD: UE.KB.SPC.PACK.COMPOSER.CASE.BAD.001

---

## REQUIRED UID REFERENCES
- PLAYBOOK (repair):
  - UE.KB.SPC.PACK.COMPOSER.PB.DIAG_REWORK.001
- COMPLIANCE CHECKLIST:
  - UE.KB.SPC.PACK.COMPOSER.CHK.COMPLIANCE.001

---
END
