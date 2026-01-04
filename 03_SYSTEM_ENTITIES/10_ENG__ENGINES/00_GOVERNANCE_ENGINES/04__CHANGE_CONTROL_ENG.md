# Change Control Engine
FILE: 04__CHANGE_CONTROL_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 00_GOVERNANCE_ENGINES
LEVEL: L1
STATUS: ACTIVE
VERSION: 1.0
ROLE: Defines how system changes are proposed, evaluated, approved, and merged

---

## PURPOSE

Определяет **канонический контроль изменений**:
- классификация изменений по риску и влиянию
- обязательные артефакты (audit, decision, index updates)
- правила принятия/отклонения изменений

---

## DEFINITIONS

- Change — любое создание/правка/удаление/перемещение.
- Change Package — набор изменений как одна операция.
- Impact Level — low/medium/high/critical.
- Protected Zone — зоны, где без апрува нельзя.
- Gate — условие, которое должно быть выполнено.

---

## INPUTS

- proposed diff/commit
- target scope & paths
- authority & hierarchy constraints
- optional: decision record

---

## OUTPUTS

- Change Classification (impact + required gates)
- Required Artifacts List
- Merge Eligibility (allowed / blocked / needs approval)

---

## MECHANICS (HOW IT WORKS)

1) Классифицируем изменение по типу:
   - create/update/delete
   - move/rename
   - structural (индексы/папки) vs content (текст/смысл)
2) Определяем Impact Level:
   - low: правка текста без изменения смысла/структуры
   - medium: смысловая правка одного документа
   - high: изменение индексов/структуры/нумерации/правил семейства
   - critical: изменение SYSTEM_LAW / STANDARDS / глобальных реестров
3) Назначаем Gates:
   - всегда: audit event
   - для medium+: обновить соответствующий index/registry если требуется
   - для high/critical: decision approval
4) Если gates не выполнены → change blocked.

---

## RULES

- C1: Любое изменение обязано иметь audit (см. AUDIT_LOG_ENG).
- C2: Любое изменение, которое создаёт/перемещает сущность, обязано обновить индекс.
- C3: Любое rename/move обязано содержать mapping + проверку ссылок (XREF).
- C4: Изменения protected zones требуют Decision Approval.
- C5: Запрещены “ломающие” изменения без migration plan:
  - изменение форматов, нумерации, путей без планов переезда и обновления ссылок.

---

## FAILURE MODES

- F1: Переезд без индексов → система “теряет” сущности.
- F2: Правки законов без апрува → разрушение доверия.
- F3: Rename без XREF → битые ссылки везде.

---

## INTEGRATION

- With AUDIT_LOG_ENG: обязательно на каждом change.
- With DECISION_APPROVAL_ENG: approval для high/critical.
- With SCOPE_IMPACT_ENG: impact вычисление.
- With CONSISTENCY_ENG: пост-проверка инвариантов.
- With XREF layer: проверка ссылок и обновление путей.

---

## CHANGE POLICY

- Изменение классификации impact или gates — только через approval.
- Любое послабление protected zones запрещено без явного решения.

---
OWNER: Universe Engine
STATUS: FIXED
