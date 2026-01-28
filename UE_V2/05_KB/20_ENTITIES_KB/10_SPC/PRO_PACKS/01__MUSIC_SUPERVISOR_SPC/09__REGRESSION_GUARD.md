# 09__REGRESSION_GUARD — MUSIC_SUPERVISOR_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/01__MUSIC_SUPERVISOR_SPC/09__REGRESSION_GUARD.md
SCOPE: KB — SPC Pro Pack — Music Supervisor — Regression Guard
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS
DOC_TYPE: REGRESSION_GUARD
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.MUSIC_SUPERVISOR.REGRESSION_GUARD.001
OWNER: SPC (Music Supervisor)
ROLE: Defines mandatory post-change checks to prevent quality regressions (one-axis discipline + guard gates).

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Regression guard initialized for Music Supervisor SPC pack."
- REASON: "Prevent hidden breakage after repairs/edits."
- IMPACT: "Defines minimal rerun set after any patch."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.MSUP.REGR.001

---

## PURPOSE (LAW)
Любая правка может незаметно:
- вернуть противоречие,
- сломать ясность,
- добавить out-of-scope,
- испортить структуру.

Regression Guard фиксирует:
- что обязательно перепроверять,
- какой минимальный “rerun set”,
- как вести patch log.

---

## WHAT COUNTS AS A CHANGE
Change event считается, если:
- изменён текст deliverable (любой PRIMARY/OPTIONAL output)
- применён PB-02 repair
- добавлен/удалён блок, меняющий смысл/структуру
- переименованы термины/правила

---

## ONE-AXIS RULE (HARD)
- За один change event разрешено менять только одну ось:
  - clarity | structure | completeness | consistency | compliance | edge
- Если нужно больше:
  - делай второй change event (второй прогон PB-02)

---

## MINIMUM RERUN SET (MANDATORY)
После любого change event:

1) Re-run FAILED/REWORK item (the original trigger)
2) Then run at least ONE guard:
   - if axis != consistency → run CONSISTENCY gate
   - if axis == consistency → run CORE_OUTPUT_QUALITY gate

### Guard default mapping
- Axis: clarity → guard = CONSISTENCY
- Axis: structure → guard = CORE_OUTPUT_QUALITY
- Axis: completeness → guard = CORE_OUTPUT_QUALITY
- Axis: consistency → guard = CORE_OUTPUT_QUALITY
- Axis: compliance → guard = CONSISTENCY + COMPLIANCE checklist
- Axis: edge → guard = CONSISTENCY + EDGE gate (if enabled)

---

## REGRESSION SIGNALS (STOP CONDITIONS)
Stop and escalate if:
- contradictions reappear after 2 repair loops
- scope creep returns repeatedly
- fixing one axis breaks another axis every time (“ping-pong”)
- same failure mode repeats across tasks (needs pack update)

---

## PATCH LOG FORMAT (MANDATORY)
Каждая правка обязана фиксировать:

- CHANGE_ID: <...>
- AXIS_CHANGED: <one axis>
- BEFORE (1–3 bullets): <what was wrong>
- PATCH (1–5 bullets): <what changed>
- AFTER (1–3 bullets): <what improved>
- RERUN:
  - <UID>: <PASS|REWORK|FAIL>
  - <UID>: <PASS|REWORK|FAIL>
- DECISION:
  - <CONTINUE|STOP|READY>

---

## CALIBRATION ANCHORS (CASES)
Use case library as anchors:
- PASS reference:
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.CASE.GOOD.001
- FAIL reference:
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.CASE.BAD.001
- Borderline reference:
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.CASE.BORDERLINE.001

---

## REQUIRED UID REFERENCES
- CHECKLISTS:
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.CHK.QUALITY.001
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.CHK.COMPLIANCE.001
- GATES:
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.GATE.CORE_QUALITY.001
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.GATE.CONSISTENCY.001
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.GATE.EDGE_CASES.001
- PRINCIPLES:
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.PRINCIPLES.001

---
END
