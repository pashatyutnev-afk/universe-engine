# KB RULES (GOVERNANCE LAW) (CANON)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: LAW
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.KB.GOV.RULES.011
OWNER: SYSTEM
ROLE: Governance law for Knowledge Base: defines how KB entities and knowledge are created, registered, linked, validated, and changed without duplication.

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MINOR
- SUMMARY: "Нормализован KB Rules: registry-first, UID-first, no-dup, различие KB сущности vs KB знание, deprecation/migration"
- REASON: "KB должен быть управляемым и каноническим слоем"
- IMPACT: "All KB creation, registries, passports, realms"

---

## XREF (UID-first)
XREF: UE.KB.IDX.MASTER.001 | governs | KB existence by master-index | 04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md
XREF: UE.STD.SPEC.REL_XREF.104 | depends_on | UID-first linking | 02_STANDARDS/01_SPECIFICATIONS/04__REL_POLICY_XREF_STANDARD.md
XREF: UE.LAW.CANON.PROTOCOL.004 | depends_on | canon changes flow | 01_SYSTEM_LAW/04__CANON_PROTOCOL.md
XREF: UE.LAW.VERSIONING.003 | depends_on | SemVer policy | 01_SYSTEM_LAW/03__VERSIONING_CHANGE_POLICY.md
XREF: UE.KB.GOV.REGISTRY.012 | depends_on | KB Global Registry rules | 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/02__INDEX__KB_GLOBAL_REGISTRY.md
XREF: UE.KB.GOV.ENTITY_TYPES.013 | depends_on | entity typing | 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/03__INDEX__KB_ENTITY_TYPES.md
XREF: UE.KB.GOV.STORAGE_MAP.014 | depends_on | storage placement | 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/04__KB_STORAGE_MAP.md
XREF: UE.KB.TPL.ENTITY_PASSPORT.015 | depends_on | passport template | 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/05__TEMPLATE__KB_ENTITY_PASSPORT.md
XREF: UE.KB.GOV.CREATE_FLOW.016 | references | operational steps | 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/06__KB_CREATE_FLOW.md

---

## 0) PURPOSE (LAW)
Этот документ — закон управления Knowledge Base.

Он определяет:
- что считается KB-каноном
- что такое KB сущность и что такое KB знание
- как создавать/регистрировать/связывать сущности
- как вносить знания в realm-файлы
- как предотвращать дубли (no-dup)
- как делать изменения (deprecation/migration) без ломания истории

---

## 1) DEFINITIONS (CONTROLLED)
### 1.1 KB Entity
KB Entity — объект мира/системы (персонаж, локация, предмет, событие, фракция, концепт, технология…),
который:
- имеет `ENTITY_UID`
- имеет паспорт сущности
- зарегистрирован в KB Global Registry

### 1.2 KB Knowledge (Realm Knowledge)
KB Knowledge — правило/методика/справочник/контекст внутри realm-файлов.
Это знание может ссылаться на сущности, но не заменяет их паспорта.

### 1.3 Canon (KB)
KB-каноном считается только то, что:
- существует по master-index слоя KB
- и (для сущностей) зарегистрировано в KB Global Registry

---

## 2) PRIME RULES (ABSOLUTE)
### 2.1 Registry-first for entities
Новая сущность не считается существующей, пока не зарегистрирована в KB Global Registry.

### 2.2 UID-first everywhere
Все внутренние связи:
- только через UID-first (XREF)

### 2.3 No-dup (one meaning → one entity)
Запрещено создавать вторую сущность с тем же смыслом.
Если обнаружен дубль:
- выбирается каноническая сущность
- дубли → DEPRECATED и переводятся в alias/migration (см. раздел 6)

### 2.4 Separation of concerns
- Паспорт сущности = truth about entity
- Realm-файл = knowledge / methods / rules / patterns
Realm не должен становиться “свалкой паспортов”.

---

## 3) ENTITY CREATION RULES (MANDATORY)
Чтобы создать сущность:

1) Определи `ENTITY_TYPE` по `KB Entity Types`
2) Присвой `ENTITY_UID`
3) Создай паспорт по шаблону `KB Entity Passport`
4) Заполни минимум:
   - identity (uid/name/type)
   - one-line summary
   - ключевые attributes (если есть)
   - XREF связи (если есть)
5) Добавь запись в KB Global Registry:
   - ENTITY_UID
   - NAME
   - TYPE
   - STATUS (entity-status)
   - PASSPORT_PATH
6) (опционально) добавь упоминания/секции в realm-файлах с XREF на UID

---

## 4) KNOWLEDGE ADD RULES (REALM CONTENT)
Если добавляешь знание в realm:
- оно должно быть:
  - структурированным (разделы/подразделы)
  - привязанным к сущностям через XREF (если это про конкретные сущности)
- нельзя:
  - описывать “новую сущность” только текстом без паспорта
  - создавать второй SoT смысл в другом realm без XREF

---

## 5) VALIDATION (QUALITY GATES)
### 5.1 Entity validation
Сущность считается валидной, если:
- ENTITY_UID существует и уникален
- паспорт существует и соответствует шаблону
- запись есть в Global Registry
- тип соответствует Entity Types

### 5.2 Knowledge validation
Знание считается валидным, если:
- не противоречит governance/законам
- не дублирует смысл другого realm без явной причины + XREF
- использует UID-first для внутренних ссылок

---

## 6) CHANGE / DEPRECATION / MIGRATION
### 6.1 Updating an entity
Любая правка паспорта сущности:
- фиксируется через Change Note в header паспорта (если паспорт канонический документ)
- не удаляет историю “молчанием”

### 6.2 Deprecating an entity
Если сущность заменяется/сливается:
- каноническая сущность остаётся ACTIVE
- дубль ставится `ENTITY_STATUS: deprecated`
- в паспорте дубля:
  - `DEPRECATED_BY_ENTITY_UID: <ENTITY_UID_CANON>`
  - XREF: `deprecated_by` → канон

### 6.3 Renaming an entity
Переименование не меняет UID.
Меняется только `ENTITY_NAME`.

### 6.4 Major changes
Если изменение ломает структуру шаблонов/реестров:
- проходит Canon Protocol (system-level)
- и требует SemVer bump

---

## 7) COLLISION RULES (CRITICAL)
### 7.1 File collisions
Если в KB появляются “дубликаты индексов/ридми”:
- канонический entrypoint только один (master-index)
- остальные файлы становятся legacy alias pointers и НЕ регистрируются как канон

### 7.2 Number collisions
Запрещено иметь одинаковые `NN` значения для разных сущностей в одном scope, если это ломает навигацию.
(Например `02__KB_TAGS.md` и `02_CHARACTER_CRAFT.md`.)

Решение:
- system-файлы KB переводятся в отдельный неймспейс/номер (например 90+)
или
- переносятся в governance папку как SoT-справочники.

---

## 8) ENFORCEMENT (WHAT IS IGNORED)
Игнорируется (non-canon):
- сущности без регистрации
- сущности без паспортов
- знания “вне master-index”
- ссылки на внутренние объекты без UID (path-only)

---

## FINAL RULE (LOCK)
Этот документ — закон управления KB.
Любая правка, меняющая правила существования сущностей/реестров = изменение канона.
--- END.
