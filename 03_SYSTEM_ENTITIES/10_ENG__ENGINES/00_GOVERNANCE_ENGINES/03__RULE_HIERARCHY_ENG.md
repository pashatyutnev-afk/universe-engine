# Rule Hierarchy Engine
FILE: 03__RULE_HIERARCHY_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 00_GOVERNANCE_ENGINES
LEVEL: L1
STATUS: ACTIVE
VERSION: 1.0
ROLE: Defines rule levels and conflict resolution across the system

---

## PURPOSE

Задаёт **иерархию правил** и алгоритм разрешения конфликтов:
- какие правила сильнее
- как обнаруживать противоречия
- как решать “если два правила говорят разное”

---

## DEFINITIONS

- Rule — норматив, ограничивающий структуру/содержание/процессы.
- Rule Level — уровень силы правила (L0..Ln).
- Conflict — два правила не могут быть истинны одновременно.
- Override — осознанное исключение (разрешено только по policy).

---

## INPUTS

- SYSTEM_LAW rules
- STANDARDS rules
- registries/indexes constraints
- family realm constraints
- entity-level rules (локальные)

---

## OUTPUTS

- Rule Level Map (уровни и приоритеты)
- Conflict Resolution Algorithm
- Override Policy (когда можно нарушать)

---

## MECHANICS (HOW IT WORKS)

1) Каждое правило имеет:
   - уровень (LEVEL)
   - область действия (scope/path/entity_group)
   - тип (naming/numbering/structure/content/process)
2) Конфликт определяется, если два правила пересекаются по scope
   и дают несовместимые требования.
3) Разрешение:
   - выигрывает более высокий уровень
   - если уровни равны → нужен Decision Approval
   - если один из конфликтующих — локальный (family/entity), он уступает глобальному.

---

## RULES (LEVELS)

L0: SYSTEM_LAW (абсолютный закон)
L1: STANDARDS (обязательные стандарты)
L2: GLOBAL REGISTRIES / GLOBAL INDEXES
L3: FAMILY REALM / README constraints
L4: ENTITY LOCAL rules (внутри документа)
L5: NOTES / optional guidance

Overrides:
- OV1: Override возможен только “вверх по лестнице” через Decision Approval.
- OV2: Override обязан быть задокументирован ссылкой на решение + rationale.
- OV3: Временные overrides обязаны иметь срок или условие снятия.

---

## FAILURE MODES

- F1: Правила без уровней → вечные споры “кто прав”.
- F2: Override без решения → скрытые дырки в каноне.
- F3: Локальные правила ломают глобальные → распад целостности.

---

## INTEGRATION

- With CANON_AUTHORITY_ENG: источники авторитета задают уровни.
- With CONSISTENCY_ENG: консистентность проверяет конфликты правил в фактах.
- With CHANGE_CONTROL_ENG: change flow обязан учитывать уровень затронутых правил.
- With VAL layer: валидаторы могут реализовывать автоматическую проверку конфликтов.

---

## CHANGE POLICY

- Добавление нового уровня требует Decision Approval.
- Любое изменение алгоритма разрешения конфликтов требует:
  - описание миграции поведения
  - список “breaking changes”
  - апрув

---
OWNER: Universe Engine
STATUS: FIXED
