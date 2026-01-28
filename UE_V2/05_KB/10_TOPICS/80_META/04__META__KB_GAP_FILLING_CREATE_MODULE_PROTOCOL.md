# TOPIC — KB GAP FILLING: CREATE MODULE PROTOCOL (META / OPERATIONAL)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/80_META/04__META__KB_GAP_FILLING_CREATE_MODULE_PROTOCOL.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TOPIC
INDEX_TYPE: META_PROTOCOL
LEVEL: L2
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.TOPIC.META.GAP_FILL.004
OWNER: SYSTEM
ROLE: Protocol for handling missing knowledge modules: detect KB gaps, decide create vs stop, create atomic modules with correct headers, register in master index, and run QA gates; prevents “improvisation without KB”

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created KB gap filling protocol: when KB lacks a method, create an atomic module first or hard stop; includes creation checklist and registry steps."
- REASON: "KB is the quality backbone; gap handling must be deterministic to prevent fantasy and drift."
- IMPACT: "Entities can expand KB safely while preserving navigation and auditability."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPIC.META.004

---

TYPE: type_topic
STATE: UNREAD
TAGS:
- domain_meta
- knowledge_base
- gap_filling
- create_module
- atomic_kb
- nav_registry
- maturity_seed

---

## 1) PURPOSE
Если нужного метода нет в KB:
- **не импровизировать**,
- либо создать атомарный модуль,
- либо сделать HARD STOP,
с обязательной регистрацией в master-index.

---

## 2) GAP TRIGGERS (WHEN A GAP EXISTS)
Gap существует, если:
- G1: задача требует метод/правило, но модуля нет
- G2: есть модуль, но он не покрывает важный случай
- G3: модуль устарел/противоречив
- G4: сущность вынуждена “додумывать”

---

## 3) DECISION: CREATE VS STOP
### Option A — CREATE (preferred)
Создавать модуль, если:
- задача повторяемая,
- это фундамент качества,
- метод можно описать атомарно (L3 topic).

### Option B — HARD STOP
Остановиться, если:
- нужен специфический факт без источников,
- риск высокий (high-stakes),
- неизвестны требования/входы.

Правило:
- запрещено “временно сделать без KB”.

---

## 4) CREATE FLOW (DETERMINISTIC)
Step 1 — Choose domain folder
- 10_NARRATIVE / 20_CHARACTER / 50_SOUND_MUSIC / 60_PRODUCTION / 70_MARKETING / 80_META / etc.

Step 2 — Choose next index number (NN)
- уникальный в домене (или по правилам папки).

Step 3 — Create atomic module (TOPIC)
Модуль должен иметь:
- стандартную шапку (как в остальных KB)
- PURPOSE, WHEN TO USE, DEFINITIONS
- INPUTS/OUTPUTS
- PROCEDURE (step-by-step)
- TEMPLATES (copy)
- QA gates (PASS/REWORK/FAIL)
- RELATED (PATH ONLY)
- COMPLIANCE

Step 4 — Add UID
- уникальный UID в стиле UE.KB.TOPIC.<DOMAIN>.<NAME>.<###>

Step 5 — Register in KB master-index
- добавить PATH + RAW

Step 6 — Run QA
- см. §6

---

## 5) ATOMICITY RULE (DO NOT MIX)
Один модуль = одна функция.
Запрет:
- делать “энциклопедию в одном файле”
- смешивать разные задачи без явной необходимости

---

## 6) QA GATES (PASS/FAIL)
PASS IF:
- модуль атомарный (1 роль)
- есть INPUTS/OUTPUTS
- есть процедура и шаблон
- есть QA гейты
- UID уникален и логичен
- модуль зарегистрирован в master-index

REWORK IF:
- модуль полезен, но слишком общий или нет шаблона

FAIL IF:
- модуль не зарегистрирован
- модуль требует внешних фактов без источников
- модуль содержит “советы из головы” без закрепления как метод

---

## 7) CREATE MODULE CHECKLIST (COPY)
[ ] Domain folder chosen
[ ] File name follows pattern NN__DOMAIN__TOPIC.md
[ ] Header complete (scope/layer/doc_type/index_type/level/status/lock/version/uid/owner/role)
[ ] TYPE/STATE/TAGS block present
[ ] Purpose + When to use
[ ] Definitions
[ ] Inputs/Outputs
[ ] Procedure
[ ] Templates
[ ] QA gates
[ ] Related (PATH only)
[ ] Compliance
[ ] Registered in master-index (PATH + RAW)

---

## 8) EXAMPLES (MANDATORY)
### 8.1 PASS example
Нужна “hook engineering” — модуля нет → создаём атомарный topic:
- процедура + hook card + QA tests
→ регистрируем в master-index.
WHY PASS:
- метод повторяемый, качество растёт.

### 8.2 FAIL example
Нет модуля и мы “просто делаем как умеем”.
WHY FAIL:
- gap ignored → drift.

---

## 9) RELATED (PATH ONLY)
REL:
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/80_META/01__META__KNOWLEDGE_BASE_USAGE_PROTOCOL.md
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/80_META/03__META__KB_EXCERPTING_AND_MEMORY_REUSE_RULES.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/80_META/02__META__KB_INDEX_NAVIGATION_STANDARD.md

---

## 10) COMPLIANCE
- NO_IMPROVISATION: absolute
- CREATE_OR_STOP: mandatory
- REGISTER_MASTER_INDEX: mandatory
- ATOMICITY: strict

--- END.
