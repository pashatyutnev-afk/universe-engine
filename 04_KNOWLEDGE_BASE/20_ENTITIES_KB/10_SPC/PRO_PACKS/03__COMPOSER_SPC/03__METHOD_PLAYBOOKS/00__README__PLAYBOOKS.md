# 00__README__PLAYBOOKS — COMPOSER_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/03__COMPOSER_SPC/03__METHOD_PLAYBOOKS/00__README__PLAYBOOKS.md
SCOPE: KB — SPC Pro Pack — Composer — Method Playbooks (README)
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS / 03__METHOD_PLAYBOOKS
DOC_TYPE: README
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.COMPOSER.PLAYBOOKS.README.001
OWNER: SPC (Composer)
ROLE: Explains playbook set, order, and routing for composer outputs (motif/harmony/melody plan) with deterministic validation.

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Playbooks README initialized for Composer SPC pack."
- REASON: "Make composition workflow runnable without guessing."
- IMPACT: "Defines deterministic playbook routing for composer decisions."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.COMPOSER.PB.README.001

---

## PURPOSE (LAW)
Playbooks = "как делать композицию" в виде повторяемого процесса.
Этот набор:
- фиксирует композиционные решения (мотив, гармония, мелодия, форма на уровне музыки),
- задаёт проверяемые критерии (узнаваемость мотива, устойчивость тональности, контраст),
- не лезет в инженерные настройки и не забирает чужие роли.

---

## PLAYBOOK SET (THIS PACK)
- PB-01: CORE_WORKFLOW
  - FILE: 01__PLAYBOOK__CORE_WORKFLOW.md
  - UID: UE.KB.SPC.PACK.COMPOSER.PB.CORE.001
- PB-02: DIAGNOSE_AND_REWORK
  - FILE: 02__PLAYBOOK__DIAGNOSE_AND_REWORK.md
  - UID: UE.KB.SPC.PACK.COMPOSER.PB.DIAG_REWORK.001
- PB-03: QUALITY_POLISH
  - FILE: 03__PLAYBOOK__QUALITY_POLISH.md
  - UID: UE.KB.SPC.PACK.COMPOSER.PB.QUALITY_POLISH.001

---

## REQUIRED ORDER (DEFAULT)
1) PB-01 CORE → produce O1/O2 (+O3 optional)
2) Run CHECKLISTS (Readiness → Quality → Compliance)
3) Run GATES (Core Output Quality → Consistency → Edge optional)
4) If REWORK/FAIL → PB-02 (one-axis) → rerun minimum set
5) Optional polish → PB-03 → rerun regression guard

---

## OUTPUTS (COMPOSER)
### Required
- O1: COMPOSER_TASK_CARD
- O2: COMPOSITION_EXEC_PLAN

### Optional (task-driven)
- O3: MOTIF_LIBRARY (hooks/leitmotifs, 2–4 options)
- O4: HARMONY_MAP (progression logic + cadences)
- O5: MELODY_GUIDE (range/contour/targets, decision-level)

Rule:
- Optional outputs only when explicitly required by task or platform intent.

---

## WHEN TO USE WHICH PLAYBOOK

### PB-01 CORE_WORKFLOW
Use when:
- нужно придумать и стабилизировать музыкальную основу трека
- нужен хук как музыкальный мотив (а не только текст)
- нужна гармоническая логика и контраст

### PB-02 DIAGNOSE_AND_REWORK
Use when:
- gate/checklist FAIL/REWORK
- мотив не узнаётся, мелодия расплывчатая
- гармония конфликтует с mood/жанром
- появились противоречия (тональность, темп-ощущение, “слишком похоже”)

Strict rule:
- one-axis repair per loop.

### PB-03 QUALITY_POLISH
Use when:
- PASS есть, но хочется добить до 9–10
- усилить узнаваемость мотива, контраст, “запоминаемость”
- сделать план более исполнимым и читабельным

---

## NON-NEGOTIABLE RULES
- No engineering recipes (EQ/LUFS/компрессия/лимитер) — это не сюда.
- No final prompt takeover (если есть Prompt Architect).
- Composer changes are decision-level only:
  - motif/harmony/melody/rhythm-feel decisions, not mix knobs.
- UID-only references in runtime integrations.

---

## REQUIRED UID REFERENCES
- CHECKLISTS:
  - UE.KB.SPC.PACK.COMPOSER.CHK.READINESS.001
  - UE.KB.SPC.PACK.COMPOSER.CHK.QUALITY.001
  - UE.KB.SPC.PACK.COMPOSER.CHK.COMPLIANCE.001
- GATES:
  - UE.KB.SPC.PACK.COMPOSER.GATE.CORE_QUALITY.001
  - UE.KB.SPC.PACK.COMPOSER.GATE.CONSISTENCY.001
  - UE.KB.SPC.PACK.COMPOSER.GATE.EDGE_CASES.001
- PLAYBOOKS:
  - UE.KB.SPC.PACK.COMPOSER.PB.CORE.001
  - UE.KB.SPC.PACK.COMPOSER.PB.DIAG_REWORK.001
  - UE.KB.SPC.PACK.COMPOSER.PB.QUALITY_POLISH.001

---
END
