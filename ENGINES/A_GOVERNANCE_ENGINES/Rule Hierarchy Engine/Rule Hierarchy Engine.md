# Rule Hierarchy Engine
## Движок Иерархии Правил

---

## 1) Identity / Идентификация

- Engine ID: RHE-A2-002
- Class: Governance Engine
- Level: A2 (Rule Hierarchy Core)
- Status: Active
- Owner: Universe Engine

---

## 2) Purpose / Назначение

### EN
Defines the hierarchy, priority, and override rules between all system rules.
Controls which rules dominate in case of conflict across engines and layers.

### RU
Определяет иерархию, приоритеты и правила переопределения всех правил системы.
Управляет тем, какие правила доминируют при конфликтах между движками и слоями.

---

## 3) Responsibilities / Ответственность

Responsible for:
- Rule priority levels
- Cross-layer rule ordering
- Override permissions
- Conflict resolution precedence
- Rule inheritance logic

Отвечает за:
- Уровни приоритетов правил
- Порядок правил между слоями
- Права на переопределение
- Приоритеты разрешения конфликтов
- Логику наследования правил

---

## 4) Domains / Entities

- Rule
- Rule Level
- Priority Tier
- Override Permission
- Inheritance Chain
- Conflict Precedence
- Rule Scope

---

## 5) Inputs / Входные данные

Receives:
- Canon rules
- Engine constraints
- Change requests
- Dependency graphs
- Conflict reports

---

## 6) Outputs / Выходные данные

Produces:
- Rule hierarchy maps
- Priority resolutions
- Override validations
- Conflict precedence decisions
- Rule inheritance structures

---

## 7) Operating Logic / Логика работы

1. Register rules and scopes
2. Assign priority tiers
3. Validate override permissions
4. Resolve rule conflicts by hierarchy
5. Enforce inheritance logic
6. Publish rule precedence state

---

## 8) Constraints / Ограничения

This engine must NOT:
- Create new rules autonomously
- Modify canon directly
- Bypass Canon Authority decisions
- Interpret narrative meaning
- Ignore locked priorities

---

## 9) Integration / Интеграция

Used by:
- Canon Authority Engine
- Change Control Engine
- Consistency Engine
- All Engines requiring rule resolution

Uses:
- Dependency Registry Engine
- Audit Log Engine

---

## 10) Canon Status / Канонический статус

- Governance Core Engine
- Rule hierarchy is canon-bound
- Mandatory for conflict resolution

---

## 11) Versioning / Версии

- v1.0 — Base rule hierarchy framework

---

## 12) Notes / Заметки

Rules do not compete.
Rules are ordered.
Order prevents collapse.
