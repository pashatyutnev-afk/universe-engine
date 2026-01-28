# TOPIC — KB QA & AUDIT CHECKS (META / QUALITY LAW)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/80_META/05__META__KB_QA_AUDIT_CHECKS.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TOPIC
INDEX_TYPE: META_QUALITY_STANDARD
LEVEL: L2
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.TOPIC.META.QA_AUDIT.005
OWNER: SYSTEM
ROLE: Define quality and audit checks for Knowledge Base modules: completeness, atomicity, nav registration, traceability, anti-drift, consistency, and deprecation handling; includes audit checklist and pass/fail gates

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created KB QA/Audit standard: checks for module quality, nav registry completeness, consistency, and drift prevention."
- REASON: "KB must be ideal; without audit rules it accumulates duplicates, vague modules, and conflicting guidance."
- IMPACT: "KB remains deterministic, scalable, and entity-usable with stable quality over time."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPIC.META.005

---

TYPE: type_topic
STATE: UNREAD
TAGS:
- domain_meta
- knowledge_base
- qa
- audit
- anti_drift
- registry_integrity
- maturity_seed

---

## 1) PURPOSE
KB должна быть идеальной и проверяемой:
- каждый модуль полноценный,
- атомарный,
- зарегистрирован в master-index,
- не противоречит соседним,
- не плодит дубликаты,
- не заставляет сущности “додумывать”.

---

## 2) AUDIT LEVELS
- L-A: Module-level audit (1 файл)
- L-B: Folder-level audit (папка темы)
- L-C: KB-wide audit (master-index + слои)

---

## 3) MODULE-LEVEL QA (L-A)
### A1 — Header completeness
Есть ли:
- FILE/SCOPE/LAYER/DOC_TYPE/INDEX_TYPE/LEVEL/STATUS/LOCK/VERSION/UID/OWNER/ROLE
- CHANGE_NOTE
- TYPE/STATE/TAGS

### A2 — Atomicity
- один модуль = одна функция
- нет “энциклопедии”

### A3 — Operability
- Inputs/Outputs
- Procedure (step-by-step)
- Templates (copy)
- QA gates (PASS/REWORK/FAIL)

### A4 — No invention
- модуль не подменяет отсутствующие факты “из головы”
- правила сформулированы как метод, не как фантазия

### A5 — Trace & relations
- RELATED (PATH only) есть
- нет RAW размазанного по подпапкам (RAW в master-index)

Result:
- PASS / REWORK / FAIL

---

## 4) FOLDER-LEVEL QA (L-B)
### B1 — Coverage map
- все ключевые темы домена представлены (нет дыр)

### B2 — Numbering consistency
- NN идут по порядку, нет хаоса/дубликатов

### B3 — Sub-index role
- если есть подпапочный индекс, он “карта/ориентир”, не реестр существования

### B4 — Duplicate detection
- нет 2 модулей с одной функцией (если есть — должен быть DEPRECATION)

Result:
- PASS / REWORK / FAIL

---

## 5) KB-WIDE QA (L-C)
### C1 — Master-index integrity
- содержит RAW ссылки на каждый KB файл
- existence rule соблюдён

### C2 — No extra entrypoints
- нет вторых “главных” индексов

### C3 — Consistency across domains
- общие принципы (RAW-only, trace, no-fantasy) соблюдены везде

### C4 — Deprecation handling
- устаревшие модули помечены и не используются

Result:
- PASS / REWORK / FAIL

---

## 6) DEPRECATION STANDARD (WHEN MODULES CONFLICT)
Если найден конфликт/дубликат:
- выбрать canonical module
- другой пометить как DEPRECATED (status + note)
- добавить POINTER на канон
- обновить master-index (если нужно)

Запрет:
- держать два равноправных модуля на одну роль.

---

## 7) AUDIT CHECKLIST (COPY)
KB AUDIT CHECKLIST:
L-A Module:
- [ ] Header complete
- [ ] Atomic
- [ ] Inputs/Outputs present
- [ ] Procedure present
- [ ] Templates present
- [ ] QA gates present
- [ ] Related present (PATH only)
- [ ] No invention
- [ ] Ready to use by entities

L-B Folder:
- [ ] Coverage ok
- [ ] Numbering consistent
- [ ] No duplicates or deprecated handled
- [ ] Sub-index used as map only

L-C KB-wide:
- [ ] Master-index contains all RAW
- [ ] Existence rule enforced
- [ ] No duplicate entrypoints
- [ ] Deprecation policy applied

Result: PASS/REWORK/FAIL

---

## 8) HARD FAIL CONDITIONS
FAIL IF:
- модуль не зарегистрирован в master-index
- модуль без процедуры/шаблона/QA gates
- модуль смешивает 3 разных темы
- дубликаты без deprecation
- master-index неполный

---

## 9) EXAMPLES (MANDATORY)
### 9.1 PASS example
Модуль “hook engineering”:
- есть процедура + hook card + QA tests
- зарегистрирован в master-index
WHY PASS:
- операционен и повторяем.

### 9.2 FAIL example
Файл “размышления про маркетинг” без шаблонов и гейтов.
WHY FAIL:
- неоперационен, вызывает drift.

---

## 10) RELATED (PATH ONLY)
REL:
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/80_META/04__META__KB_GAP_FILLING_CREATE_MODULE_PROTOCOL.md
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/80_META/02__META__KB_INDEX_NAVIGATION_STANDARD.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/80_META/03__META__KB_EXCERPTING_AND_MEMORY_REUSE_RULES.md

---

## 11) COMPLIANCE
- AUDIT_REQUIRED: yes (periodic)
- MASTER_INDEX_SOT: absolute
- NO_DUPLICATES: strict
- NO_INVENTION: absolute

--- END.
