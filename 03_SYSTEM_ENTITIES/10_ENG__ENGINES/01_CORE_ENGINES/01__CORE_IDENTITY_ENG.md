# Core Identity Engine
FILE: 01__CORE_IDENTITY_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 01_CORE_ENGINES
LEVEL: L1
STATUS: ACTIVE
VERSION: 1.0
ROLE: Defines the canonical identity contract for any system entity

---

## PURPOSE

Определяет **Identity Contract** — минимальный набор полей и правил,
который делает любую сущность системой распознаваемой, индексируемой и управляемой.

Если Identity невалиден — сущность считается **не существующей** для канона.

---

## IDENTITY CONTRACT (CANONICAL FIELDS)

Минимальные поля (должны быть либо в документе, либо выводимы однозначно):

### 1) Identity Core
- ID: уникальный идентификатор сущности (стабильный)
- TITLE: человеко-читаемое имя
- ENTITY_GROUP: ENG / ORC / SPC / CTL / VAL / QA / PROJECT / etc.
- TYPE: подтип внутри группы (например ENGINE, ORCHESTRATOR, SPECIALIST)
- LEVEL: L0..L? (иерархический уровень)
- STATUS: DRAFT|ACTIVE|DEPRECATED|ARCHIVED|BROKEN
- VERSION: semver или внутренний формат (например 1.0)

### 2) Location / Navigation
- CANONICAL_PATH: путь в репозитории (истина навигации)
- FAMILY: семейство (папка/реалм)
- INDEX_REFERENCE: какой индекс регистрирует сущность (если применимо)

### 3) Authority / Ownership
- OWNER: кто отвечает за сущность
- AUTHORITY_ZONE: какая зона правил на неё действует (если выделено)

### 4) Optional but Recommended
- TAGS: метки
- DESCRIPTION: 1–3 строки “что делает”
- DEPENDENCIES: ссылки на provider’ы (если есть)
- OUTPUTS/INPUTS: если сущность функциональная (движки/оркестраторы)

---

## ID FORMAT (RECOMMENDED)

ID должен быть:
- уникальным в пределах системы
- стабильным при переездах
- пригодным для ссылок

Рекомендация:
- `ENG-CORE-IDENTITY`
- либо `UE-<GROUP>-<FAMILY>-<NAME>`

Главное: **не завязывать ID на путь**, иначе любые rename ломают смысл.

---

## IDENTITY VALIDATION RULES

- I1: ID уникален.
- I2: CANONICAL_PATH существует и соответствует реальному расположению.
- I3: ENTITY_GROUP и FAMILY соответствуют папке (без “вранья”).
- I4: STATUS допустим и соответствует жизненному циклу.
- I5: VERSION задан и меняется по правилам (см. VERSIONING_MEMORY_ENG).
- I6: Если сущность объявлена в INDEX — она обязана существовать физически.
- I7: Если сущность существует физически — она обязана быть в INDEX (если это индексируемый класс).

---

## MECHANICS (HOW IT WORKS)

1) При создании сущности задаётся паспорт (Identity header).
2) Индексы регистрируют сущность по ID и пути.
3) Любые ссылки в системе должны опираться на:
   - ID (семантика)
   - PATH (навигация)
4) При move/rename:
   - ID не меняется (в идеале)
   - PATH обновляется
   - создаётся XREF mapping (from→to)

---

## FAILURE MODES

- F1: Два объекта с одинаковым ID → коллизия канона.
- F2: ID зависит от пути → переезд ломает историю и ссылки.
- F3: Нет OWNER → никто не отвечает, сущность “гниёт”.
- F4: Индекс говорит что есть, а файла нет → фантом.
- F5: Файл есть, а в индексе нет → сирота.

---

## INTEGRATION

- With CORE_STATE_ENG: статус часть identity, но правила статуса там.
- With CORE_LIFECYCLE_ENG: transitions и этапы жизни.
- With CONSISTENCY_ENG: ловит сирот/фантомов/конфликты.
- With DEPENDENCY_REGISTRY_ENG: dependencies часть контракта.
- With XREF__CROSSREF: хранит mapping при переездах.

---
OWNER: Universe Engine
STATUS: FIXED
