# Audit Log Engine
FILE: 01__AUDIT_LOG_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 00_GOVERNANCE_ENGINES
LEVEL: L1
STATUS: ACTIVE
VERSION: 1.0
ROLE: Canonical audit trail for all structural/content changes across the repository

---

## PURPOSE

Фиксирует **историю изменений** как неизменяемый след (audit trail):
- кто/что/когда изменил
- что именно изменилось (до/после или ссылка на diff)
- почему изменилось (причина/тикет/решение)
- к чему привязано (scope, entity, index)

---

## DEFINITIONS

- Audit Event — атомарная запись изменения.
- Actor — инициатор изменения (человек/роль/процесс).
- Target — объект изменения (файл/папка/индекс/сущность).
- Change Type — тип изменения (create/update/delete/move/rename).
- Evidence — доказательство (diff/link/commit/ref).
- Decision Ref — ссылка на решение (если требуется approval).

---

## INPUTS

- Change Proposal / Change Request (явный или implicit через commit)
- Diff / Commit reference
- Target identifiers (путь, entity_id, index_id)
- Optional: Decision Ref (из DECISION_APPROVAL_ENG)

---

## OUTPUTS

- Audit Event Record (структурированная запись)
- Audit Index pointers (где хранится событие и как найти)
- Severity marker (informational / controlled / critical)

---

## MECHANICS (HOW IT WORKS)

1) На каждое изменение создаётся **Audit Event**.
2) Event должен ссылаться на:
   - actor
   - target (точный путь + тип объекта)
   - change_type
   - timestamp
   - evidence (diff/commit)
   - rationale (кратко “зачем”)
3) Если изменение затрагивает “protected zones” (см. RULES) —
   требуется Decision Ref.
4) Audit записи **не редактируются**: только дополняются новыми событиями.

---

## RULES

- R1: Нет изменения без Audit Event (минимум — commit ref + rationale).
- R2: Audit Event immutable: запрещено “править историю” задним числом.
- R3: Для protected zones обязателен Decision Ref:
  - SYSTEM_LAW, STANDARDS, SYSTEM_ENTITIES indexes, naming rules, numbering rules.
- R4: Audit должен указывать “impact tags”:
  - scope: ENG/ORC/SPC/CTL/VAL/QA/PROJECTS/KB/DB
  - impact: low/medium/high
- R5: Любое move/rename обязано содержать mapping “from → to”.

---

## FAILURE MODES

- F1: “Тихие изменения” без следа → система теряет воспроизводимость.
- F2: Неполный target → невозможна трассировка и проверка.
- F3: Редактирование старых записей → недоверие ко всему канону.

---

## INTEGRATION

- With CHANGE_CONTROL_ENG: audit обязателен при любом change flow.
- With RULE_HIERARCHY_ENG: protected zones определяются уровнем правил.
- With DECISION_APPROVAL_ENG: Decision Ref обязателен для high-impact changes.
- With VERSIONING_MEMORY_ENG: audit связывается с версией/релизом.

---

## CHANGE POLICY

- Менять формат Audit Event можно только через Decision Approval.
- Любая миграция формата должна иметь:
  - совместимость чтения старых событий
  - правила преобразования и контроль полноты

---
OWNER: Universe Engine
STATUS: FIXED
