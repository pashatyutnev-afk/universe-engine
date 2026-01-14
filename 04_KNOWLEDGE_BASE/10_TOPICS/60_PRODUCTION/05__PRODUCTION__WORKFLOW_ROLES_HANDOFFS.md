# TOPIC — WORKFLOW, ROLES & HANDOFFS (PRODUCTION / ATOMIC MODULE)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/60_PRODUCTION/05__PRODUCTION__WORKFLOW_ROLES_HANDOFFS.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TOPIC
INDEX_TYPE: ATOMIC_KB_MODULE
LEVEL: L3
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.TOPIC.PROD.WORKFLOW_HANDOFFS.001
OWNER: SYSTEM
ROLE: Atomic method to run production as a deterministic workflow with explicit roles, handoffs, and quality gates; includes Workflow Blueprint, Handoff Contract template, and pass/fail checks

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created production workflow standard: role-based steps, input/output contracts, handoff fields, and QA gates."
- REASON: "Production scales only with deterministic handoffs; without contracts quality drifts and ownership becomes unclear."
- IMPACT: "Entities/teams can coordinate reliably; each step produces auditable outputs and can be re-run."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPIC.PROD.005

---

TYPE: type_topic
STATE: UNREAD
TAGS:
- domain_production
- type_topic
- workflow
- handoffs
- roles
- gates
- maturity_seed

---

## 1) PURPOSE
Описать производство как конвейер:
- роли (кто делает),
- шаги (что делаем),
- handoffs (что передаём дальше),
- gates (как проверяем качество),
чтобы результат был стабильным и повторяемым.

---

## 2) WHEN TO USE
- Много релизов и вариантов.
- Несколько участников или “сущности” выполняют разные функции.
- Часто возникают ошибки из-за “не договорились, что сдаём”.
- Нужно ускорить производство без потери качества.

## 3) WHEN NOT TO USE
- Разовый эксперимент без повторного использования.

---

## 4) DEFINITIONS (STRICT)
### Role
Ответственность за шаг и качество выхода.

### Step
Операционный этап производства с чёткими входами/выходами.

### Handoff
Передача результата следующему шагу с контрактом полей.

### Gate
PASS/REWORK/FAIL проверка качества на границе.

---

## 5) CORE WORKFLOW (GENERIC)
Универсальная цепочка (можно укоротить, но порядок сохранять):

S0 — Brief / Goal  
S1 — Outline / Plan  
S2 — Draft Build (content)  
S3 — Quality Pass (structure)  
S4 — Polish Pass (style/finish)  
S5 — Release Pack Assembly  
S6 — Publish / Archive

---

## 6) ROLES (GENERIC SET)
Минимальный набор ролей (можно маппить на сущности/людей):
- R1: Producer / Coordinator (владение процессом)
- R2: Creator (текст/музыка/сцены)
- R3: Editor (структура/ясность/сжатие)
- R4: QA (гейты и баги)
- R5: Publisher (релиз пак, метадата, варианты)

---

## 7) HANDOFF CONTRACT (MANDATORY)
Каждая передача должна иметь:
- INPUTS (что пришло)
- OUTPUTS (что сдаём)
- REQUIRED FIELDS (минимум полей)
- ACCEPTANCE CRITERIA (PASS)
- REWORK CONDITIONS
- OWNER (кто отвечает)

---

## 8) PROCEDURE (BUILD A WORKFLOW BLUEPRINT)
### Step 1 — Choose artifact type
- track / episode / chapter / pack

### Step 2 — Select steps (S0..S6)
- какие шаги нужны
- какие можно объединить (но gate сохраняем)

### Step 3 — Assign owners (roles)
- каждый шаг имеет одного владельца (owner)

### Step 4 — Define handoff fields
Для каждого шага определить обязательные поля:
Пример:
- S2 output: draft_text, notes, open_questions
- S3 output: structure_fixes, cuts, gaps
- S5 output: release_pack_files, metadata, credits, rights, changelog

### Step 5 — Define gates per step
Минимум:
- Gate A: Structure PASS
- Gate B: QA PASS
- Gate C: Release pack PASS

### Step 6 — Run a dry-run checklist
Проверить:
- можно ли выполнить шаги без “вопросов в воздух”
- понятны ли acceptance criteria

---

## 9) WORKFLOW BLUEPRINT TEMPLATE (COPY)
WORKFLOW BLUEPRINT:
- ARTIFACT TYPE:
- STEPS:
  - S0 Brief:
    - Owner role:
    - Inputs:
    - Outputs:
    - Gate:
  - S1 Outline:
    - Owner role:
    - Inputs:
    - Outputs:
    - Gate:
  - S2 Draft Build:
    - Owner role:
    - Inputs:
    - Outputs:
    - Gate:
  - S3 Quality Pass:
    - Owner role:
    - Inputs:
    - Outputs:
    - Gate:
  - S4 Polish Pass:
    - Owner role:
    - Inputs:
    - Outputs:
    - Gate:
  - S5 Release Pack:
    - Owner role:
    - Inputs:
    - Outputs:
    - Gate:
  - S6 Publish/Archive:
    - Owner role:
    - Inputs:
    - Outputs:
    - Gate:

HANDOFF CONTRACT (per step):
- FROM STEP:
- TO STEP:
- REQUIRED FIELDS (minimum):
- ACCEPTANCE CRITERIA (PASS):
- REWORK CONDITIONS:
- OWNER:

---

## 10) QUICK CHECKLIST (PASS/FAIL)
- [ ] выбран artifact type
- [ ] шаги определены и идут в порядке
- [ ] у каждого шага есть owner
- [ ] у каждого шага определены inputs/outputs
- [ ] handoff contract заполнен (минимум поля)
- [ ] есть gates (PASS/REWORK/FAIL)
- [ ] release pack шаг присутствует перед публикацией

PASS IF:
- всё заполнено и нет “дыр” в ответственности

REWORK IF:
- есть шаги, но не хватает полей/гейтов

FAIL IF:
- нет owner или нет gates (качество неконтролируемо)

---

## 11) EXAMPLES (MANDATORY)
### 11.1 PASS EXAMPLE (track workflow)
S0: Brief (Producer) → S1: Outline (Creator) → S2: Draft (Creator)
→ S3: Quality (Editor) → S4: Polish (Editor) → S5: Release Pack (Publisher) → S6: Publish (Producer)

Handoff S2→S3 fields:
- lyrics_draft, bpm, mood, hook_line, issues_list
Gate:
- PASS если есть хук + структура + нет “дыр” по смыслу.

### 11.2 FAIL EXAMPLE
“Сделали трек”, но:
- нет release pack, нет credits, нет QA, никто не ответственный.
WHY FAIL:
- выпуск не повторяем и рискованный.

---

## 12) RELATED (PATH ONLY)
REL:
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/60_PRODUCTION/03__PRODUCTION__RELEASE_PACK_CHECKLIST.md
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/60_PRODUCTION/04__PRODUCTION__VERSIONING_DELIVERY_NAMING.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/60_PRODUCTION/02__PRODUCTION__ADAPTATION_PIPELINE.md

XREF:
- XREF: entity_mapping -> PATH: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/02__ENTITY_TO_KB_SCOPE_MAP.md
- XREF: task_to_scope -> PATH: 04_KNOWLEDGE_BASE/40_RELATION_XREF/01__TASK_TO_KB_SCOPE_MAP.md

---

## 13) COMPLIANCE
- SOURCE_LOCK: required (no step without owner; no publish without release pack + gates)
- MEMORY: allowed only if meaning unchanged
- KB_USAGE_GATE: reference this topic via PATH in KB_SOURCES when used

--- END.
