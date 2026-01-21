# 00__README__PLAYBOOKS — MUSIC_SUPERVISOR_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/01__MUSIC_SUPERVISOR_SPC/03__METHOD_PLAYBOOKS/00__README__PLAYBOOKS.md
SCOPE: KB — SPC Pro Pack — Music Supervisor — Method Playbooks
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS
DOC_TYPE: README
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.MUSIC_SUPERVISOR.PLAYBOOKS.README.001
OWNER: SPC (Music Supervisor)
ROLE: Entry point for all playbooks; defines contracts, order, and how to use the playbooks.

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Playbooks README initialized for Music Supervisor SPC pack."
- REASON: "Deterministic workflow navigation."
- IMPACT: "Standardized usage for PB-01..PB-03."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.MSUP.PLAYBOOKS.README.001

---

## PURPOSE (LAW)
Этот README — точка входа в плейбуки пака Music Supervisor SPC.
Он описывает:
- какие плейбуки существуют,
- в каком порядке их использовать,
- какой контракт обязателен для каждого плейбука,
- как фиксировать результат (минимальный trace).

---

## PACK BINDINGS (MUST MATCH PACK PASSPORT)
- PACK_UID: <PACK_UID>
- SPC_ENTITY_UID: <SPC_ENTITY_UID>
- TARGET_PROFICIENCY_LEVEL: <L1|L2|L3|L4>
- PRIMARY_OUTPUTS (from passport):
  - <output_1>
  - <output_2>

---

## PLAYBOOK LIST
- 01__PLAYBOOK__CORE_WORKFLOW.md
  - ID: PB-01
  - GOAL: произвести PRIMARY_OUTPUTS по базовому стандарту
  - USE WHEN: старт любого задания в рамках компетенции

- 02__PLAYBOOK__DIAGNOSE_AND_REWORK.md
  - ID: PB-02
  - GOAL: диагностика провала гейтов/чеклистов и ремонт
  - USE WHEN: есть FAIL/REWORK после проверок

- 03__PLAYBOOK__QUALITY_POLISH.md
  - ID: PB-03
  - GOAL: довести результат до publish-ready уровня
  - USE WHEN: базовые гейты пройдены, нужен полиш и финальная приёмка

---

## REQUIRED PLAYBOOK CONTRACT (MUST USE)
Каждый плейбук обязан содержать следующие блоки:

1) PLAYBOOK_ID / GOAL  
2) REQUIRED_INPUTS / OPTIONAL_INPUTS  
3) OUTPUTS (что обязуется выдать)  
4) PRECHECK (readiness)  
5) STEPS (пошагово)  
6) CHECKPOINTS (с привязкой к validation UID-only)  
7) FAIL MODES + FIXES (желательно one-axis)  
8) STOP / ESCALATE RULES  
9) ARTIFACT TRACE (что зафиксировать в конце)

---

## DEFAULT USAGE ORDER (NORMAL RUN)
1) PB-01 CORE_WORKFLOW
2) Run checklists:
   - 04__CHECKLISTS/01__CHK__READINESS.md
   - 04__CHECKLISTS/02__CHK__QUALITY.md
   - 04__CHECKLISTS/03__CHK__COMPLIANCE.md
3) If any REWORK/FAIL:
   - PB-02 DIAGNOSE_AND_REWORK (one-axis repair loop)
4) When базовые гейты PASS:
   - PB-03 QUALITY_POLISH
5) Финальная приёмка через гейты:
   - 05__KB_GATES/01__GATE__CORE_OUTPUT_QUALITY.md
   - 05__KB_GATES/02__GATE__CONSISTENCY.md
   - 05__KB_GATES/03__GATE__EDGE_CASES.md (если применимо)

---

## MINIMUM TRACE (MANDATORY)
После выполнения любого плейбука фиксируй минимум:

- TASK_ID: <id or date>
- INPUTS_SUMMARY: <1–5 bullets>
- OUTPUTS_PRODUCED: <list>
- VALIDATIONS:
  - PASSED: <GATE_UIDs / CHK_UIDs>
  - FAILED/REWORK: <GATE_UIDs / CHK_UIDs>
- AXIS_CHANGED (if any): <one axis>
- NEXT_ACTION: <PB-xx or checklist or escalate>

---

## NOTE: UID AUTHORITY
- Внутри плейбуков привязки к валидации/топикам/правилам делай UID-only.
- RAW-ссылки допускаются только как NAV (для перехода).

---
END
