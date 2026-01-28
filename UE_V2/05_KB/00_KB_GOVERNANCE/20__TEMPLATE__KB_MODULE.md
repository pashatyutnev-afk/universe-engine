# TEMPLATE — KB MODULE (UNIVERSAL / ACTIONABLE)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/20__TEMPLATE__KB_MODULE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TEMPLATE
INDEX_TYPE: KB_MODULE_TEMPLATE
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.TPL.MODULE.001
OWNER: SYSTEM
ROLE: Copy template for any KB module (TOPIC / CHECKLIST / RUBRIC / TEMPLATE / PATTERN / EXAMPLE / PROMPT_LIB) with mandatory actionable structure, examples, and PATH-only relations

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created universal KB module template: mandatory purpose, use rules, actionable procedure, PASS/FAIL examples, and PATH-only REL/XREF."
- REASON: "KB must drive quality; modules must be usable by entities without invention."
- IMPACT: "All KB modules become consistent, auditable, and gate-compatible."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TPL.MODULE.001

---

## 0) HEADER FIELDS (FILL THESE)
TYPE: <type_topic | type_checklist | type_rubric | type_template | type_pattern | type_anti_pattern | type_example | type_prompt_lib | type_scope_map | type_rel_map | type_xref_map>
STATE: <UNREAD | READ_ONCE | VERIFIED | DEPRECATED>
TAGS:
- <domain_*>
- <type_*>
- <optional skill_*/gate_*/maturity_*>

---

## 1) PURPOSE
(1–3 строки: что это и зачем. Без воды.)

---

## 2) WHEN TO USE
- (конкретные условия, триггеры)

## 3) WHEN NOT TO USE
- (явные анти-условия, запреты)

---

## 4) INPUTS (IF APPLICABLE)
- (какие входные данные нужны, минимальный набор)

## 5) OUTPUTS (IF APPLICABLE)
- (что должен дать модуль: артефакт/решение/формат)

---

## 6) PROCEDURE / CHECKLIST / RUBRIC (MANDATORY)
Выбери ОДИН формат и заполни:

### A) PROCEDURE (steps)
1)
2)
3)

### B) CHECKLIST (pass criteria)
- [ ] ...
- [ ] ...
PASS IF:
- ...

### C) RUBRIC (PASS/FAIL/REWORK)
CRITERIA:
- PASS: ...
- REWORK: ...
- FAIL: ...
NOTES:
- ...

### D) TEMPLATE (output contract)
REQUIRED SECTIONS:
- ...
FILL RULES:
- ...
MINI EXAMPLE:
- ...

---

## 7) CONSTRAINTS / POLICIES (IF APPLICABLE)
- (пороги, ограничения, запреты)
- (если есть thresholds — указать явно)

---

## 8) EXAMPLES (MANDATORY)
### 8.1 PASS EXAMPLE
INPUT:
- ...
OUTPUT:
- ...
WHY PASS:
- (ссылка на правило/критерий внутри модуля)

### 8.2 FAIL EXAMPLE
INPUT:
- ...
OUTPUT:
- ...
WHY FAIL:
- ...

### 8.3 EDGE EXAMPLE (IF APPLICABLE)
INPUT:
- ...
OUTPUT:
- ...
WHY EDGE:
- ...

---

## 9) COMMON FAILURE MODES (RECOMMENDED)
- Failure: ...
  Fix: ...
- Failure: ...
  Fix: ...

---

## 10) RELATED (PATH ONLY) (MANDATORY IF DEPENDENCIES EXIST)
REL:
- REL: depends_on -> PATH: ...
- REL: reinforces -> PATH: ...
- REL: complements -> PATH: ...
- REL: conflicts_with -> PATH: ...   # if used, link to policy resolution
- REL: supersedes -> PATH: ...       # if deprecating

XREF:
- XREF: task_to_scope -> PATH: ...
- XREF: validation_matrix -> PATH: ...
- XREF: pipeline_to_scope -> PATH: ...

---

## 11) COMPLIANCE (MANDATORY)
- SOURCE_LOCK: required (no invention)
- KB_USAGE_GATE: this module must be referenceable via PATH in KB_SOURCES
- MEMORY: allowed only if STATE=VERIFIED (no meaning changes)

--- END.
