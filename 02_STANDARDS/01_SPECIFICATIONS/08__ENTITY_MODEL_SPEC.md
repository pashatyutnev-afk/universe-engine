# ENTITY MODEL SPEC (SoT)
FILE: 02_STANDARDS/01_SPECIFICATIONS/08__ENTITY_MODEL_SPEC.md

SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: SPEC
SPEC_TYPE: ENTITY_MODEL
LEVEL: L2
STATUS: DRAFT
LOCK: OPEN
VERSION: 0.1.0
UID: UE.STD.SPEC.ENTITY_MODEL.001
OWNER: SYSTEM
ROLE: Single source of truth for the universal entity model (types, fields, relationships, lifecycle hooks) used across system entities, KB, and projects

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Нормализация legacy-spec: добавлен Doc Control, SemVer, UID и каноническое имя с номером"
- REASON: "Файл без номера запрещён; нужен фундаментальный SoT по модели сущностей"
- IMPACT: "Все слои, где есть сущности: SYSTEM_ENTITIES, KB, PROJECTS, DATABASES"

---

## 0) PURPOSE
Этот документ фиксирует **универсальную модель сущности** Universe Engine:
- какие поля обязательны для сущностей
- какие типы сущностей существуют (в терминах модели)
- как описываются связи (REL/XREF)
- какие “контракты” обязаны быть одинаковыми в разных слоях

---

## 1) SCOPE (BOUNDARIES)
### IN
- модель “карточки сущности” (passport/record)
- универсальные поля (UID, статус, версия, слой и т.д.)
- универсальные связи REL/XREF
- минимальный жизненный цикл (создание → активность → депрекация → архив)

### OUT
- конкретные деревья хранения (это Storage Map)
- конкретные правила naming (это Naming Rules)
- конкретные пайплайны производства (это Pipeline Registry)

---

## 2) CORE CONCEPTS (MODEL)
### 2.1 Entity
Entity — абстрактный объект системы, имеющий:
- идентичность (UID)
- тип (ENTITY_TYPE)
- состояние (STATUS/LOCK)
- версию (SemVer)
- связи (REL/XREF)
- место в хранении (PATH)

### 2.2 Passport
Passport — канонический файл-описание сущности по единому шаблону.

### 2.3 Registry record
Registry record — запись учёта (минимальная карточка в реестре), не обязательно полный паспорт.

---

## 3) REQUIRED FIELDS (MINIMUM)
Любая сущность (passport/record) обязана иметь:

### 3.1 Identity
- UID (stable)
- NAME (canonical)
- LAYER
- ENTITY_TYPE
- OWNER
- ROLE (1-line purpose)

### 3.2 Control
- STATUS: DRAFT | ACTIVE | DEPRECATED | ARCHIVED
- LOCK: OPEN | FIXED
- VERSION: X.Y.Z

### 3.3 Location
- FILE: canonical path (для документов)
- STORAGE_TARGET (если сущность не документ, но имеет target)

---

## 4) ENTITY TYPES (MODEL LEVEL)
Модель описывает типы на уровне “класса”, не конкретного слоя.

Минимальный набор классов:
- DOC (documents: law/standard/index/template/spec/etc.)
- ENTITY (system entities: ENG/ORC/SPC/CTL/VAL/QA)
- KB (knowledge realm entities / KB passports)
- PRJ (project entities / project artifacts)
- AST (assets)
- DB (databases / tables)

Примечание:
Конкретные перечисления типов живут в реестрах:
- `08_DATABASES/DB__ENTITY_TYPES.md`
- индексы слоёв (master-index)

---

## 5) RELATIONSHIPS (REL / XREF)
### 5.1 REL (Entity-to-Entity)
Формат записи связи (норматив):
`REL: <REL_TYPE> -> <TARGET_UID> | WHY:<short> | TYPE:<HARD|SOFT>`

Примеры REL_TYPE:
- DEPENDS_ON
- PRODUCES
- CONSUMES
- DEPRECATES
- REPLACES
- PART_OF

### 5.2 XREF (Doc-to-Doc pointers)
Формат:
`XREF: <DOC_UID or PATH>#<section> | WHY:<short>`

---

## 6) LIFECYCLE (MINIMUM)
Сущность проходит состояния:
1) DRAFT (LOCK: OPEN)
2) ACTIVE (LOCK: FIXED)
3) DEPRECATED (LOCK: FIXED) + ссылка на замену
4) ARCHIVED (LOCK: FIXED) (история, не участвует в производстве)

Правила:
- ACTIVE → DEPRECATED требует указать REPLACED_BY (UID)
- DEPRECATED не может быть снова ACTIVE без MAJOR-пересоздания сущности

---

## 7) VALIDATION RULES (MODEL GATES)
Сущность считается валидной, если:
- UID присутствует и уникален
- VERSION в формате X.Y.Z
- STATUS/LOCK входят в допустимый набор
- NAME и FILE соответствуют naming rules
- нет дублирования SoT по смыслу (проверка через registries)

---

## 8) OPEN ITEMS (DRAFT TODO)
- синхронизировать REL_TYPES с DB__ACTION_LEX.md / DB__ENTITY_TYPES.md
- закрепить полный список обязательных полей для каждого класса (DOC/ENG/KB/PRJ/AST)
- определить “минимальный паспорт” vs “расширенный паспорт”

---

## FINAL RULE
Этот spec является SoT по универсальной модели сущностей.
Пока STATUS: DRAFT — допускает правки.
--- END.
