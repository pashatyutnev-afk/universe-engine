# 00__README__GATES — COMPOSER_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/03__COMPOSER_SPC/05__KB_GATES/00__README__GATES.md
SCOPE: KB — SPC Pro Pack — Composer — KB Gates (README)
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS / 05__KB_GATES
DOC_TYPE: README
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.COMPOSER.GATES.README.001
OWNER: SPC (Composer)
ROLE: Defines gate set, order, decision rules, and calibration via cases + rubric for composer outputs.

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Gates README initialized for Composer SPC pack."
- REASON: "Make composition quality enforcement deterministic after checklists."
- IMPACT: "Defines gate order, thresholds, and repair routing."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.COMPOSER.GATES.README.001

---

## PURPOSE (LAW)
GATES — строгие рубежи качества.
Они принимают решение:
- PASS / REWORK / FAIL
и определяют маршрут PB-02 ремонта (one-axis).

---

## REQUIRED PREREQUISITE
Before any gate:
- run checklists in order:
  - CHK-READINESS → CHK-QUALITY → CHK-COMPLIANCE
If any REWORK/FAIL → STOP and repair first.

---

## GATE SET (THIS PACK)
- GATE-01: CORE OUTPUT QUALITY
  - FILE: 01__GATE__CORE_OUTPUT_QUALITY.md
  - UID: UE.KB.SPC.PACK.COMPOSER.GATE.CORE_QUALITY.001
- GATE-02: CONSISTENCY
  - FILE: 02__GATE__CONSISTENCY.md
  - UID: UE.KB.SPC.PACK.COMPOSER.GATE.CONSISTENCY.001
- GATE-03: EDGE CASES (optional)
  - FILE: 03__GATE__EDGE_CASES.md
  - UID: UE.KB.SPC.PACK.COMPOSER.GATE.EDGE_CASES.001

---

## REQUIRED ORDER
Default:
1) GATE-CORE_OUTPUT_QUALITY
2) GATE-CONSISTENCY
Optional:
3) GATE-EDGE_CASES (only when conflicts/variants/high risk)

---

## DECISION RULES (GLOBAL)
- PASS:
  - thresholds met and no hard-fail triggers
- REWORK:
  - fixable issues with one-axis patch
- FAIL:
  - compliance hard limits present
  - repeated contradictions after 2 repair loops
  - output fundamentally non-actionable

---

## CALIBRATION SOURCES
- RUBRIC:
  - UE.KB.SPC.PACK.COMPOSER.RUBRIC.001
- CASES:
  - GOOD / BAD / BORDERLINE / EDGE (see case library)
- REGRESSION GUARD:
  - UE.KB.SPC.PACK.COMPOSER.REGRESSION_GUARD.001

---

## OUTPUT OF ANY GATE (TRACE)
Every gate must output:
- GATE_UID
- DECISION: PASS|REWORK|FAIL
- FAIL_REASONS: <list>
- AXIS_RECOMMENDATION: <one axis for PB-02>
- RERUN_SET: <uids to rerun after patch>

---

## REQUIRED UID REFERENCES
- CHECKLISTS:
  - UE.KB.SPC.PACK.COMPOSER.CHK.READINESS.001
  - UE.KB.SPC.PACK.COMPOSER.CHK.QUALITY.001
  - UE.KB.SPC.PACK.COMPOSER.CHK.COMPLIANCE.001
- PLAYBOOK (repair):
  - UE.KB.SPC.PACK.COMPOSER.PB.DIAG_REWORK.001
- RUBRIC:
  - UE.KB.SPC.PACK.COMPOSER.RUBRIC.001

---
END
