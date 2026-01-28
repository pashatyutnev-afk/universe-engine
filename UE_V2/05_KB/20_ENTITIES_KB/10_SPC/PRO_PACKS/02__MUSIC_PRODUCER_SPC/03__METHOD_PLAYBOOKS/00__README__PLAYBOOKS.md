# 00__README__PLAYBOOKS — MUSIC_PRODUCER_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/02__MUSIC_PRODUCER_SPC/03__METHOD_PLAYBOOKS/00__README__PLAYBOOKS.md
SCOPE: KB — SPC Pro Pack — Music Producer — Method Playbooks (README)
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS / 03__METHOD_PLAYBOOKS
DOC_TYPE: README
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.MUSIC_PRODUCER.PLAYBOOKS.README.001
OWNER: SPC (Music Producer)
ROLE: Explains playbook set, when to use each, required order, and how it binds to checklists/gates.

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Playbooks README initialized for Music Producer SPC pack."
- REASON: "Make method runnable and prevent random actions."
- IMPACT: "Defines deterministic playbook routing."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.MPROD.PB.README.001

---

## PURPOSE (LAW)
Playbooks — это “как работать”, а не “что такое”.
Они управляют:
- порядком действий,
- точками проверки,
- ремонтом (one-axis),
- полировкой результата.

---

## PLAYBOOK SET (THIS PACK)
- PB-01: CORE_WORKFLOW
  - FILE: 01__PLAYBOOK__CORE_WORKFLOW.md
  - UID: UE.KB.SPC.PACK.MUSIC_PRODUCER.PB.CORE.001
- PB-02: DIAGNOSE_AND_REWORK
  - FILE: 02__PLAYBOOK__DIAGNOSE_AND_REWORK.md
  - UID: UE.KB.SPC.PACK.MUSIC_PRODUCER.PB.DIAG_REWORK.001
- PB-03: QUALITY_POLISH
  - FILE: 03__PLAYBOOK__QUALITY_POLISH.md
  - UID: UE.KB.SPC.PACK.MUSIC_PRODUCER.PB.QUALITY_POLISH.001

---

## REQUIRED ORDER (DEFAULT)
1) PB-01 CORE → produce O1/O2 (+O3 optional)
2) Run CHECKLISTS (Readiness → Quality → Compliance)
3) Run GATES (Core Output Quality → Consistency → Edge optional)
4) If any REWORK/FAIL → PB-02 (one-axis) → rerun minimum set
5) If PASS but want sharper result → PB-03 polish → rerun regression guard

---

## WHEN TO USE WHICH PLAYBOOK

### PB-01 CORE_WORKFLOW
Use when:
- you have enough inputs to plan structure/arrangement and acceptance
Outputs:
- O1 PRODUCER_TASK_CARD
- O2 PRODUCTION_EXEC_PLAN
- O3 VARIANTS_PLAN (only if requested)

### PB-02 DIAGNOSE_AND_REWORK
Use when:
- a checklist/gate fails
- contradictions appear
- output feels vague/unactionable
Rule:
- one-axis change per loop + patch log + rerun.

### PB-03 QUALITY_POLISH
Use when:
- output passes, but needs upgrade to 9–10
- want better scanability, stronger acceptance tests, better contrast notes
Rule:
- polish cannot introduce new scope; only improve clarity/structure/consistency.

---

## NON-NEGOTIABLE RULES
- One-axis repair discipline:
  - see REGRESSION_GUARD and PRINCIPLES docs.
- No engineering recipes:
  - producer gives decision-level direction only.
- UID-only references when binding to checks/gates/topics.

---

## REQUIRED UID REFERENCES
- PRINCIPLES:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.PRINCIPLES.001
- REGRESSION GUARD:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.REGRESSION_GUARD.001
- CHECKLISTS:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.CHK.READINESS.001
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.CHK.QUALITY.001
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.CHK.COMPLIANCE.001
- GATES:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.CORE_QUALITY.001
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.CONSISTENCY.001
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.EDGE_CASES.001

---
END
