# Learning Engine
FILE: 01__LEARNING_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 10_META_EVOLUTION_ENGINES
CLASS: META (L4)
LEVEL: L4
STATUS: ACTIVE
VERSION: 1.0
ROLE: Captures learning events from execution, QA, and governance; converts them into actionable lessons, patches, and updated standards with traceability and rollback plans

---

## PURPOSE

Собирать “чему мы научились” из реальной работы:
- ошибки
- успехи
- неожиданности
- повторяющиеся боли

И превращать это в:
- уроки
- правила
- патчи движков
- обновления стандартов

---

## INPUTS

- audit log entries
- QA failures / drift reports
- production incidents (сломалось/непонятно/долго)
- user feedback
- change requests

---

## OUTPUTS

- LEARNING EVENT RECORD (LER)
- LESSONS LIST (LL)
- PATCH PROPOSAL (PP)
- MIGRATION NOTE (MN) if structure changes
- ROLLBACK PLAN (RP)
- VALIDATION CHECKLIST (VC)

---

## REQUIRED ARTIFACT: LEARNING EVENT RECORD (LER)

LER SCHEMA (CANON):
- LER_ID:
- DATE:
- SOURCE:
  - audit / QA / user / pipeline
- CONTEXT:
  - where it happened (family/engine/project)
- SYMPTOM:
  - what went wrong / what was slow / what was unclear
- ROOT CAUSE (hypothesis):
- FIX TYPE:
  - rule change / template change / engine patch / indexing / naming
- PROPOSED CHANGE (summary):
- AFFECTED DEPENDENCIES:
- RISK LEVEL:
  - low/med/high
- ROLLBACK PLAN:
- OWNER:
- STATUS:
  - draft / approved / applied / reverted

Rule:
- No learning without traceability.

---

## PROCEDURE

1) Capture incident as LER
2) Classify: clarity / compatibility / drift / speed / quality
3) Identify root cause (best hypothesis)
4) Propose fix (PP) + dependencies + risk
5) Send through governance pipeline (ME1)
6) Apply patch + update indexes/templates if needed
7) Validate (VC)
8) Record outcome in audit

---

## VALIDATION RULES

- LRN1: Любой “урок” имеет LER и источник.
- LRN2: Любая правка имеет rollback plan.
- LRN3: После правки есть проверка, что проблема ушла.
- LRN4: Нельзя “учиться”, ломая канон без регистрации.

---

OWNER: Universe Engine
STATUS: FIXED
