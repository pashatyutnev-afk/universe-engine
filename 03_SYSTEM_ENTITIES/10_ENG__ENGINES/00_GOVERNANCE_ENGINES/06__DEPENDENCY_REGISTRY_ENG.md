# Dependency Registry Engine
FILE: 06__DEPENDENCY_REGISTRY_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 00_GOVERNANCE_ENGINES
LEVEL: L1
STATUS: ACTIVE
VERSION: 1.0
ROLE: Canonical registry of dependencies between entities, indexes, rules, and projects

---

## PURPOSE

Создаёт и поддерживает **единый реестр зависимостей** системы:
- какие сущности зависят от каких
- какие индексы обязаны быть обновлены при изменениях
- какие правила/форматы (STANDARDS) обязаны соблюдаться
- какие проекты используют какие движки/сущности

Главная цель: **ни одно изменение не должно ломать цепочку**, даже если переименовали папку.

---

## DEFINITIONS

- Dependency — отношение "A требует B" (A cannot function without B).
- Dependent — тот, кто зависит (A).
- Provider — тот, от кого зависят (B).
- Dependency Type:
  - structural (paths, indexes, naming, numbering)
  - semantic (meaning/contract)
  - operational (process gates)
  - reference (links, xrefs)
  - production (output used by another)
- Dependency Strength:
  - hard (обязательная)
  - soft (желательная)
- Break — нарушение зависимости.

---

## INPUTS

- индексы (GLOBAL/FAMILY)
- README/REALM файлы семейств
- правила нумерации и именования
- решения (Decision Records)
- факты изменений (diff/commit)
- список проектов/пайплайнов (если привязка используется)

---

## OUTPUTS

- Dependency Records (структурированные записи)
- Impact Requirements:
  - "если меняешь X — обязан обновить Y"
- Break Alerts:
  - список нарушений
- Migration Guidance:
  - как переехать без поломки

---

## DEPENDENCY RECORD FORMAT

Минимальный формат записи (логический, можно хранить где угодно — важно содержимое):

- dependent_id / dependent_path
- provider_id / provider_path
- type: structural|semantic|operational|reference|production
- strength: hard|soft
- rationale: почему зависимость существует
- break_condition: что считается поломкой
- repair_action: как чинить

---

## MECHANICS (HOW IT WORKS)

1) Любая сущность/индекс может объявить зависимости.
2) При change package строится graph:
   - какие nodes затронуты
   - какие edges могут сломаться
3) Если ломается hard dependency → change blocked (см. CHANGE_CONTROL_ENG).
4) Если ломается soft dependency → warning, требуется план фикса.
5) Для move/rename обязательна запись dependency типа reference + XREF mapping.

---

## RULES

- D1: Индекс является provider для всех сущностей, которые он регистрирует.
- D2: README/REALM является provider для правил семейства.
- D3: STANDARDS является provider для формата документов.
- D4: Любая ссылка на raw/github path создаёт reference dependency.
- D5: Любое переименование папки создаёт structural dependency break risk.
- D6: Для крупных переездов обязателен migration plan:
  - mapping from → to
  - список индексов на апдейт
  - список ссылок на апдейт
  - валидация консистентности после

---

## FAILURE MODES

- F1: "Переезд" без зависимостей → волна битых ссылок.
- F2: "Не обновили индекс" → сироты/фантомы.
- F3: "Семантика поменялась" без фикса downstream → неверные результаты.

---

## INTEGRATION

- With CHANGE_CONTROL_ENG: dependency breaks участвуют в блокировке.
- With CONSISTENCY_ENG: зависимости помогают находить orphan/phantom и broken refs.
- With SCOPE_IMPACT_ENG: dependency graph повышает impact score.
- With XREF__CROSSREF: хранит mapping и поддерживает continuity.

---

## CHANGE POLICY

- Любая правка dependency policy требует Decision Approval.
- Для новых классов сущностей должен быть описан dependency baseline:
  - какие индексы обязательны
  - какие ссылки допустимы
  - какие правила формата обязательны

---
OWNER: Universe Engine
STATUS: FIXED
