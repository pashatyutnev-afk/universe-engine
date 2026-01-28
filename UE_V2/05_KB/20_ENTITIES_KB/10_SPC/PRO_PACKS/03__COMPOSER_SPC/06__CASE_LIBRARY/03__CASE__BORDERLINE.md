# 03__CASE__BORDERLINE — MUSIC_PRODUCER_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/02__MUSIC_PRODUCER_SPC/06__CASE_LIBRARY/03__CASE__BORDERLINE.md
SCOPE: KB — SPC Pro Pack — Music Producer — Case (BORDERLINE)
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: CASE
CASE_TYPE: BORDERLINE
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.MUSIC_PRODUCER.CASE.BORDERLINE.001
OWNER: SPC (Music Producer)
ROLE: Near-pass case where structure exists but hook spotlight and lead space are underdefined; fixable by one-axis patch.

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "BORDERLINE case initialized."
- REASON: "Provide rework anchor."
- IMPACT: "Defines minimal fix patterns."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.MPROD.CASE.BORDERLINE.001

---

## CONTEXT
Arrangement map exists, but hook readability protection is weak.

---

## INPUTS (MIN)
- TASK_GOAL: "Short-form track with strong hook."
- PLATFORM_INTENT: "shorts"
- CONSTRAINTS:
  - hook early
  - not too busy

---

## OUTPUTS (ABBREVIATED)
- O1:
  - has A1 (hook early)
  - missing explicit “lead space / no clutter” rule
- O2:
  - layer list exists but no hierarchy per section
  - transitions mentioned but not placed

---

## CHECKLIST / GATE OUTCOME
- CHK-READINESS: PASS
- CHK-QUALITY: REWORK (hook readability)
- CHK-COMPLIANCE: PASS
- GATE-CORE_OUTPUT_QUALITY: REWORK
- GATE-CONSISTENCY: PASS

---

## WHY BORDERLINE
- runnable, but risk that hook is masked by supports
- needs spotlight window + hierarchy

---

## AXIS (FOR REPAIR)
- hook spotlight / lead space (single-axis)

---

## MIN PATCH (ONE AXIS)
Axis=hook spotlight:
- add spotlight window (time range)
- define “lead space” rule for hook section
- add hierarchy line for hook section:
  - lead foreground, supports sparse, bed minimal
- add acceptance A2 “no clutter”

---

## RERUN SET
- UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.CORE_QUALITY.001
- UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.CONSISTENCY.001

---
END
