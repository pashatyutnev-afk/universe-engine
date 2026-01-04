# Canon Authority Engine
FILE: 02__CANON_AUTHORITY_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 00_GOVERNANCE_ENGINES
LEVEL: L1
STATUS: ACTIVE
VERSION: 1.0
ROLE: Defines who/what is authoritative and how canon decisions are legitimized

---

## PURPOSE

Определяет **источники канона** и их приоритет:
- что считается “истиной системы”
- какие документы имеют власть над какими
- кто может утверждать изменения и на каких условиях

---

## DEFINITIONS

- Authority Source — источник авторитета (документ/индекс/решение).
- Canon Zone — область канона (структура, правила, контент, проекты).
- Owner — владелец зоны (роль или фиксированный документ-источник).
- Protected Zone — зона, требующая апрува.

---

## INPUTS

- ссылки на системные индексы (00_INDEX*)
- документы уровня SYSTEM_LAW / STANDARDS
- decision records (если есть)
- фактические изменения (commit/diff)

---

## OUTPUTS

- Authority Map (логика приоритетов источников)
- Ownership Rules (кто может менять что)
- Protected Zones List (что требует approval)

---

## MECHANICS (HOW IT WORKS)

1) Система принимает, что **INDEX-файлы и LAW/STD** — источники высшего приоритета.
2) Любая сущность “существует” только если:
   - она находится в правильной зоне (папка)
   - она присутствует в соответствующем реестре (index)
3) При конфликте двух утверждений:
   - побеждает источник с более высоким приоритетом (см. RULES).
4) Изменения protected zones требуют Decision Approval.

---

## RULES (AUTHORITY ORDER)

- A1 (Highest): SYSTEM_LAW (законы системы)
- A2: STANDARDS (форматы/шаблоны/правила оформления)
- A3: SYSTEM_ENTITIES indexes (реестры сущностей)
- A4: Family READMEs/REALM (границы семейств)
- A5: Individual entity docs (движки/оркестраторы/спецы и т.д.)
- A6 (Lowest): NOTES / drafts / experiments

Ownership:
- O1: Owner зоны фиксируется в law/registry/index.
- O2: Если owner не определён — owner считается “repository owner” (по умолчанию) и любые high-impact изменения требуют approval.

---

## FAILURE MODES

- F1: “Сущность без индекса” → фантомы и распад навигации.
- F2: “Непонятно кто главный” → конфликты правок и дубли.
- F3: “Слабый источник побеждает сильный” → разрушение канона.

---

## INTEGRATION

- With RULE_HIERARCHY_ENG: использует уровни и правила разрешения конфликтов.
- With CHANGE_CONTROL_ENG: определяет, какие изменения требуют approval.
- With AUDIT_LOG_ENG: authority decisions должны быть трассируемы.
- With DECISION_APPROVAL_ENG: формализует апрув для protected zones.

---

## CHANGE POLICY

- Изменение порядка Authority Order — только через Decision Approval.
- Любое добавление новой Canon Zone требует:
  - явного owner
  - явного registry/index
  - правил protected zones

---
OWNER: Universe Engine
STATUS: FIXED
