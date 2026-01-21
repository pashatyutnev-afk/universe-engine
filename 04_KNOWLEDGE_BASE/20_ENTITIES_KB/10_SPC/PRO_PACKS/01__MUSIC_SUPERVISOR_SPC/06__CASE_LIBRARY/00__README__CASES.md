# 00__README__CASES — MUSIC_SUPERVISOR_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/01__MUSIC_SUPERVISOR_SPC/06__CASE_LIBRARY/00__README__CASES.md
SCOPE: KB — SPC Pro Pack — Music Supervisor — Case Library
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS
DOC_TYPE: README
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.MUSIC_SUPERVISOR.CASES.README.001
OWNER: SPC (Music Supervisor)
ROLE: Entry point for case library; defines case types and how they bind to gates/rubric.

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Case library README initialized for Music Supervisor SPC pack."
- REASON: "Calibrate gates and rubric with concrete exemplars."
- IMPACT: "Defines minimum required case set."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.MSUP.CASES.README.001

---

## PURPOSE (LAW)
Кейсы — это калибровка реальностью:
- что считается PASS,
- что считается FAIL,
- что borderline,
- какие edge-условия должны выдерживаться.

---

## MINIMUM REQUIRED SET (FOR A REAL PACK)
- 1x GOOD case (acceptance anchor)
- 1x BAD case (failure anchor)
- Optional:
  - BORDERLINE (decision rule example)
  - EDGE (robustness example)

---

## CASE TYPES
- GOOD:
  - пример результата, который проходит базовые гейты
- BAD:
  - пример результата, который должен проваливать хотя бы один core gate
- BORDERLINE:
  - пример “на грани” с явным правилом решения PASS vs REWORK
- EDGE:
  - пример нестандартных входов/констрейнтов с корректной обработкой

---

## BINDINGS (MUST MATCH PACK PASSPORT)
- PACK_UID: <PACK_UID>
- SPC_ENTITY_UID: <SPC_ENTITY_UID>
- TARGET_PROFICIENCY_LEVEL: <L1|L2|L3|L4>

---

## CASE INDEX
- GOOD:
  - 01__CASE__GOOD.md
- BAD:
  - 02__CASE__BAD.md
- BORDERLINE:
  - 03__CASE__BORDERLINE.md
- EDGE:
  - 04__CASE__EDGE_001.md
  - 05__CASE__BAD_002.md (optional expansion)

---

## BINDINGS TO GATES
- GOOD must PASS:
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.GATE.CORE_QUALITY.001
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.GATE.CONSISTENCY.001
- BAD must FAIL at least one of:
  - CORE_QUALITY or CONSISTENCY (document exactly which and why)
- EDGE (if used) must PASS:
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.GATE.EDGE_CASES.001

---

## HOW TO WRITE CASES (RULES)
- Keep content compact: summary over full transcripts.
- Record:
  - inputs summary
  - expected vs actual
  - why pass/fail
  - which gate/check triggered
  - recommended fix path (PB-02 one-axis)

---

## EVIDENCE STANDARD
Каждый кейс обязан содержать:
- CASE_ID
- CASE_TYPE
- CONTEXT
- INPUTS_SUMMARY
- OUTPUT_SUMMARY
- VALIDATION_RESULT (UID-only)
- FIX_PATH (PB + axis)

---
END
