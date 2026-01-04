# Decision Approval Engine
FILE: 07__DECISION_APPROVAL_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 00_GOVERNANCE_ENGINES
LEVEL: L1
STATUS: ACTIVE
VERSION: 1.0
ROLE: Defines how decisions are made, recorded, approved, and referenced in canon

---

## PURPOSE

Формализует **решения** как канонические артефакты:
- когда требуется решение
- кто имеет право утверждать
- как выглядит решение (структура)
- как ссылка на решение встроена в изменения/индексы/правила

---

## DEFINITIONS

- Decision Record (DR) — документ решения (что решили и почему).
- Approval — подтверждение решения владельцем зоны.
- Decision Scope — область действия решения.
- Decision Class:
  - policy (правила/уровни/иерархии)
  - structural (переезды/нумерация/индексы)
  - semantic (смена смысла контрактов)
  - safety (риски/ограничения)
- Gate — обязательность решения для merge.

---

## WHEN DECISION IS REQUIRED

Decision обязателен если:
- меняем SYSTEM_LAW / STANDARDS
- меняем глобальные реестры/индексы
- делаем массовые rename/move
- меняем naming/numbering rules
- вводим новый класс сущностей или новый “уровень правил”
- ломаем обратную совместимость или меняем семантику контрактов

---

## INPUTS

- change package (diff)
- impact classification (SCOPE_IMPACT_ENG)
- authority (CANON_AUTHORITY_ENG)
- dependency graph (DEPENDENCY_REGISTRY_ENG)
- risk analysis (RISK_SAFETY_ENG)

---

## OUTPUTS

- Decision Record (approved/declined)
- Decision Reference ID
- Required Follow-ups:
  - migration steps
  - updates to indexes
  - updates to crossrefs

---

## DECISION RECORD STRUCTURE (MIN)

DR должен содержать:

- ID: DR-YYYYMMDD-XXX (уникальный)
- Title
- Status: proposed | approved | rejected | superseded
- Scope: paths/entity_groups affected
- Context: проблема/ситуация
- Decision: что делаем
- Rationale: почему так
- Alternatives: что рассматривали
- Impact: what breaks / what changes
- Migration Plan: steps + mapping
- Validation: как проверим (consistency/xref)
- Owner/Approver: кто утверждает
- References: ссылки на diff/commits/index changes

---

## MECHANICS (HOW IT WORKS)

1) Change Control отмечает необходимость Decision.
2) Создаётся DR в статусе proposed.
3) Owner зоны подтверждает (approved) или отклоняет.
4) Любой merge, который требует approval, обязан ссылаться на DR:
   - в commit message / audit event / index note
5) DR может быть superseded новым DR, но не удаляется.

---

## RULES

- DA1: Без DR запрещено менять protected zones.
- DA2: DR immutable после approval (только supersede новым DR).
- DA3: DR обязателен ссылочный: должен быть указан в AUDIT_LOG_ENG.
- DA4: Все breaking changes обязаны иметь migration plan.
- DA5: Влияние на проекты/пайплайны обязано быть отражено (если есть связь).

---

## FAILURE MODES

- F1: “Сделали по-тихому” → канон недоверяем.
- F2: DR без миграции → система ломается после merge.
- F3: DR без scope → непонятно где действует, возникают конфликты.

---

## INTEGRATION

- With CHANGE_CONTROL_ENG: gatekeeper для high/critical.
- With AUDIT_LOG_ENG: DR обязателен как reference.
- With RULE_HIERARCHY_ENG: DR нужен для overrides/level changes.
- With VERSIONING_MEMORY_ENG: DR привязывается к релизам/версиям.

---

## CHANGE POLICY

- Изменение структуры DR — только через Decision Approval (мета-решение).
- Изменение требований “когда нужен DR” — только через approval.

---
OWNER: Universe Engine
STATUS: FIXED
