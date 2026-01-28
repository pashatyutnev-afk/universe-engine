# 09__REGRESSION_GUARD — MUSIC_PRODUCER_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/02__MUSIC_PRODUCER_SPC/09__REGRESSION_GUARD.md
SCOPE: KB — SPC Pro Pack — Music Producer — Regression Guard
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS
DOC_TYPE: REGRESSION_GUARD
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.MUSIC_PRODUCER.REGRESSION_GUARD.001
OWNER: SPC (Music Producer)
ROLE: Mandatory post-change checks to prevent regressions in producer plans and direction notes.

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Regression guard initialized for Music Producer SPC pack."
- REASON: "Prevent hidden breakage after revisions."
- IMPACT: "Defines minimal rerun set + one-axis discipline."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.MPROD.REGR.001

---

## PURPOSE (LAW)
Любая правка может:
- нарушить связность плана,
- сломать структуру/сканируемость,
- вернуть противоречия,
- добавить out-of-scope,
- разрушить “identity anchors” при вариантах.

Regression Guard фиксирует:
- что перепроверять после изменений,
- какой минимальный rerun set,
- как вести patch log.

---

## WHAT COUNTS AS A CHANGE
Change event считается, если:
- изменён любой блок O1/O2/O3 deliverables
- применён PB-02 repair
- изменена структура секций/динамика/seat plan
- менялись термины/правила/критерии приёма

---

## ONE-AXIS RULE (HARD)
Один change event = одна ось:
- clarity | structure | completeness | consistency | compliance | variants | edge

Если нужно несколько:
- делай несколько событий по очереди.

---

## MINIMUM RERUN SET (MANDATORY)
После каждого change event:

1) Re-run original failed/rework trigger (check/gate)
2) Run at least one guard:
   - default guard = CONSISTENCY gate
   - if change touched structure/completeness heavily → CORE_QUALITY gate too
   - if change touched variants → CONSISTENCY + (EDGE if enabled)

### Guard mapping
- clarity → guard: CONSISTENCY
- structure → guard: CORE_QUALITY + CONSISTENCY
- completeness → guard: CORE_QUALITY
- consistency → guard: CORE_QUALITY
- compliance → guard: COMPLIANCE checklist + CONSISTENCY
- variants → guard: CONSISTENCY (+ EDGE if enabled)
- edge → guard: EDGE (+ CONSISTENCY)

---

## REGRESSION SIGNALS (STOP CONDITIONS)
Stop and escalate if:
- repairs ping-pong (fix A breaks B repeatedly)
- contradictions reappear after 2 loops
- variants drift identity every time
- same failure repeats across multiple tasks (pack needs update)

---

## PATCH LOG FORMAT (MANDATORY)
- CHANGE_ID: <...>
- AXIS_CHANGED: <one axis>
- BEFORE (1–3 bullets):
- PATCH (1–5 bullets):
- AFTER (1–3 bullets):
- RERUN:
  - <UID>: <PASS|REWORK|FAIL>
  - <UID>: <PASS|REWORK|FAIL>
- DECISION: <CONTINUE|STOP|READY>

---

## CALIBRATION ANCHORS (CASES)
- UE.KB.SPC.PACK.MUSIC_PRODUCER.CASE.GOOD.001
- UE.KB.SPC.PACK.MUSIC_PRODUCER.CASE.BAD.001
- UE.KB.SPC.PACK.MUSIC_PRODUCER.CASE.BORDERLINE.001
- UE.KB.SPC.PACK.MUSIC_PRODUCER.CASE.EDGE.001

---

## REQUIRED UID REFERENCES
- CHECKLISTS:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.CHK.QUALITY.001
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.CHK.COMPLIANCE.001
- GATES:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.CORE_QUALITY.001
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.CONSISTENCY.001
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.EDGE_CASES.001
- PRINCIPLES:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.PRINCIPLES.001

---
END
