# 00__PACK_PASSPORT — MUSIC_PRODUCER_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/02__MUSIC_PRODUCER_SPC/00__PACK_PASSPORT.md
SCOPE: KB — SPC Pro Pack — Music Producer
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS
DOC_TYPE: PACK_PASSPORT
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.MUSIC_PRODUCER.PASSPORT.001
OWNER: SPC (Music Producer)
ROLE: Canonical passport for Music Producer SPC competence pack. Defines scope, outputs, gates, and runtime bindings.

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Music Producer SPC Pro Pack passport initialized."
- REASON: "Create single authoritative entrypoint for producer pack usage."
- IMPACT: "Defines pack contract, outputs, and gating."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.MPROD.PASSPORT.001

---

## PURPOSE
Этот PACK описывает, как сущность **MUSIC_PRODUCER_SPC** работает в рантайме:
- превращает композиторское/креативное намерение в продюсерский план трека
- фиксирует аранжировку, слои, динамику, энергию, плотность, смены секций
- обеспечивает дисциплину вариантов (one-axis) и стабильность “идентичности трека”
- даёт routing на Mix/Master/Prompt roles без захвата их зоны

---

## SCOPE (WHAT THIS PACK COVERS)

### IN SCOPE (Producer decisions)
- arrangement blueprint (слои/инструменты/роли слоёв)
- energy curve (плотность/динамика по секциям)
- hook support (подводка, место, подчёркивание)
- contrast & transitions (переходы, разрежение/уплотнение, drop/lift)
- groove/rhythm decisions (ударные роли, паттерн-логика, swing/straight intent)
- texture palette (тембровая идея без “эквалайзера и цифр”)
- variant discipline (one lever change)
- delivery handoff blocks (что передать Prompt Architect / Mix Engineer)

### OUT OF SCOPE (must route)
- numeric mixing/mastering settings (LUFS/EQ/comp values)
- plugin chains and step-by-step engineering
- rights/legal certainty
- final prompt takeover (если есть Prompt Architect)
- вокальная постановка как техника (это Vocal Director)

---

## RUNTIME ROLE (HOW IT FUNCTIONS)
MUSIC_PRODUCER_SPC = “производственный архитектор трека”:
- принимает Composer intent (мотив/форма/гармония) + задачу платформы
- собирает аранжировку и динамику в runnable план
- обеспечивает читаемость и “первый зацеп”
- отдаёт дальнейшие роли по контракту (без захвата)

---

## INPUT CONTRACT (MIN)
Required:
- TASK_GOAL
- PLATFORM_INTENT (shorts/full/clip)
- CONSTRAINTS (1–7 bullets)
Optional:
- composer outputs (motif/form anchors)
- vocals required (yes/no)
- variants request (yes/no)

If required inputs missing → STOP (readiness rework).

---

## OUTPUT CONTRACT

### Mandatory outputs
- O1: PRODUCER_TASK_CARD
- O2: ARRANGEMENT_EXEC_PLAN

### Optional outputs (task-driven)
- O3: LAYER_STACK_MAP (слои по секциям)
- O4: TRANSITION_PLAN (переходы + приёмы)
- O5: VARIANT_SET (если нужно 2–4 версии)

Rule:
- Optional outputs only when the task requires them.

---

## QUALITY CONTROL STACK

### Checklists (order)
- UE.KB.SPC.PACK.MUSIC_PRODUCER.CHK.READINESS.001
- UE.KB.SPC.PACK.MUSIC_PRODUCER.CHK.QUALITY.001
- UE.KB.SPC.PACK.MUSIC_PRODUCER.CHK.COMPLIANCE.001

### Gates (order)
- UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.CORE_QUALITY.001
- UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.CONSISTENCY.001
- UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.EDGE_CASES.001 (conditional)

### Repair discipline
- One-axis repair loop:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.PB.DIAG_REWORK.001
- Polish (post-pass):
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.PB.QUALITY_POLISH.001

---

## PACK CONTENT MAP (FILES)

### METHOD PLAYBOOKS
- UE.KB.SPC.PACK.MUSIC_PRODUCER.PLAYBOOKS.README.001
- UE.KB.SPC.PACK.MUSIC_PRODUCER.PB.CORE.001
- UE.KB.SPC.PACK.MUSIC_PRODUCER.PB.DIAG_REWORK.001
- UE.KB.SPC.PACK.MUSIC_PRODUCER.PB.QUALITY_POLISH.001

### CHECKLISTS
- UE.KB.SPC.PACK.MUSIC_PRODUCER.CHK.README.001
- UE.KB.SPC.PACK.MUSIC_PRODUCER.CHK.READINESS.001
- UE.KB.SPC.PACK.MUSIC_PRODUCER.CHK.QUALITY.001
- UE.KB.SPC.PACK.MUSIC_PRODUCER.CHK.COMPLIANCE.001

### GATES
- UE.KB.SPC.PACK.MUSIC_PRODUCER.GATES.README.001
- UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.CORE_QUALITY.001
- UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.CONSISTENCY.001
- UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.EDGE_CASES.001

### CASE LIBRARY
- UE.KB.SPC.PACK.MUSIC_PRODUCER.CASES.README.001
- UE.KB.SPC.PACK.MUSIC_PRODUCER.CASE.GOOD.001
- UE.KB.SPC.PACK.MUSIC_PRODUCER.CASE.BAD.001
- UE.KB.SPC.PACK.MUSIC_PRODUCER.CASE.BORDERLINE.001
- UE.KB.SPC.PACK.MUSIC_PRODUCER.CASE.EDGE.001

### PACK CORE
- UE.KB.SPC.PACK.MUSIC_PRODUCER.SCOPE.001
- UE.KB.SPC.PACK.MUSIC_PRODUCER.PRINCIPLES.001
- UE.KB.SPC.PACK.MUSIC_PRODUCER.RUBRIC.001
- UE.KB.SPC.PACK.MUSIC_PRODUCER.KB_SOURCES.001
- UE.KB.SPC.PACK.MUSIC_PRODUCER.REGRESSION_GUARD.001
- UE.KB.SPC.PACK.MUSIC_PRODUCER.TOPIC_BINDINGS.001

---

## ENTITY INTEROP (HIGH LEVEL)
- COMPOSER_SPC: provides anchors (motif/form/harmony intent) if available
- PROMPT_ARCHITECT_SPC: receives handoff block (arrangement + stack + constraints)
- MIX_ENGINEER_SPC: receives intent tests (no numbers)
- VOCAL_DIRECTOR_SPC: receives vocal needs (density, register intent) if vocals are required
- ORC: pipeline step consumes O1/O2 and routes to downstream roles

---

## DEFAULT RUN TRACE (MIN)
- INPUTS_RECEIVED: <yes/no>
- OUTPUTS_EMITTED: O1, O2, (optional)
- CHECKLISTS_RUN: <uids + results>
- GATES_RUN: <uids + results>
- NEXT_ACTION: <pass / rework axis / stop>

---
END
