# Consistency Engine
FILE: 05__CONSISTENCY_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 00_GOVERNANCE_ENGINES
LEVEL: L1
STATUS: ACTIVE
VERSION: 1.0
ROLE: Defines invariants that keep the system coherent (indexes, naming, uniqueness, no-orphans)

---

## PURPOSE

Гарантирует **целостность системы** на уровне инвариантов:
- нет “сирот” (файлов без индекса)
- нет “фантомов” (индекс указывает на несуществующее)
- соблюдена нумерация/нейминг
- соблюдены границы семейств
- нет дубликатов идентичности

---

## DEFINITIONS

- Invariant — правило, которое всегда должно быть истинно.
- Orphan — сущность существует, но не зарегистрирована.
- Phantom — зарегистрирована, но фактически отсутствует.
- Collision — два объекта претендуют на одну идентичность.
- Broken Ref — ссылка ведёт в пустоту.

---

## INPUTS

- registries/index files
- filesystem structure (paths)
- naming/numbering rules
- cross references (links)
- change package info

---

## OUTPUTS

- Consistency Report:
  - OK / WARN / FAIL
  - список нарушений + указание источника
- Required Fix Actions:
  - update index
  - rename file
  - move entity
  - add xref mapping

---

## MECHANICS (HOW IT WORKS)

1) Проверяем “Index ↔ Reality”:
   - каждая запись индекса должна существовать (no phantoms)
   - каждый файл сущности должен быть в индексе (no orphans)
2) Проверяем “Naming/Numbering”:
   - номер в имени соответствует номеру в индексе
   - README/INDEX имеют фиксированные номера
3) Проверяем “Family Boundaries”:
   - сущность находится в правильной папке по группе
4) Проверяем “Identity Collisions”:
   - не существует двух сущностей с одинаковой canonical identity
5) Проверяем “References”:
   - ссылки на raw/github paths не битые
   - переезды сопровождаются mapping в XREF

---

## RULES (CORE INVARIANTS)

- I1: Если сущности нет в индексе — она не существует.
- I2: Индекс не может ссылаться на несуществующий файл.
- I3: Нумерация обязана совпадать: index_number == filename_number.
- I4: Любой move/rename требует XREF mapping.
- I5: Нельзя иметь два “главных” индекса для одной и той же области без явного закона.

---

## FAILURE MODES

- F1: Индексы врут → вся навигация рушится.
- F2: Дубликаты → конфликт источников истины.
- F3: Битые ссылки → система не может быть использована как машина.

---

## INTEGRATION

- With CHANGE_CONTROL_ENG: consistency check обязателен после структурных изменений.
- With DEPENDENCY_REGISTRY_ENG: учитывает зависимости (нельзя ломать требования).
- With VAL layer: валидаторы могут автоматизировать проверки инвариантов.
- With XREF: хранит переезды и обеспечивает непрерывность ссылок.

---

## CHANGE POLICY

- Инварианты можно менять только решением (Decision Approval), потому что это “кости” системы.
- Любое ослабление инварианта требует компенсирующей защиты (новое правило/валидатор/процесс).

---
OWNER: Universe Engine
STATUS: FIXED
