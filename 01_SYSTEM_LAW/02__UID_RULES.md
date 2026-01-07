# UID RULES — SYSTEM IDENTIFICATION LANGUAGE (CANON)
FILE: 01_SYSTEM_LAW/02__UID_RULES.md

SCOPE: Universe Engine
LAYER: 01_SYSTEM_LAW
DOC_TYPE: LAW
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.LAW.UID.002
OWNER: SYSTEM
ROLE: Defines UID as the canonical system identification language, including format, namespaces, stability rules, and usage in registries and cross-references.

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MINOR
- SUMMARY: "Единый формат UID + области (namespace) + мост для локальных ID + правила XREF/REL"
- REASON: "Устранение коллизий ID/UID и обеспечение однозначной навигации"
- IMPACT: "Все слои, реестры, артефакты, пайплайны"

---

## 0) PRIME LAW (ABSOLUTE)
UID — единственный канонический язык идентификации системы Universe Engine.

UID обязателен для:
- любых канонических документов (LAW/STANDARDS/KB governance и т.п.)
- любых INDEX/REGISTRY
- артефакт-типов и схем
- пайплайнов
- системных сущностей (entities) и их паспортов
- кросс-ссылок между объектами системы (REL/XREF)

---

## 1) UID FORMAT (CANON)
### 1.1 Canonical UID syntax
UID — строка в формате UPPERCASE_TOKENS, разделённых точками:

`<NS>.<CLASS>.<SUBCLASS>.<NAME>.<NNN>`

Где:
- `<NS>` — корневой namespace (UE)
- `<CLASS>` — область системы (LAW / STD / KB / ART / ENT / PIPE / IDX / REG / TPL / PRJ / OUT)
- `<SUBCLASS>` — подтип/контекст (например CORE, SPEC, MODULE, REALM, GOV, TYPE, SCHEMA)
- `<NAME>` — смысловой идентификатор (A–Z, 0–9, `_`)
- `<NNN>` — числовой хвост (обычно 3 цифры) для уникальности/серийности

Примеры (валидные):
- `UE.LAW.CORE.SYSTEM.000`
- `UE.LAW.NAMING.RULES.001`
- `UE.LAW.UID.RULES.002`
- `UE.IDX.LAW.MASTER.000`
- `UE.IDX.KB.MASTER.000`
- `UE.STD.SPEC.UID_MARKING.001`
- `UE.KB.REALM.CHARACTER_CRAFT.002`

### 1.2 Allowed characters
Только:
- `A–Z`
- `0–9`
- `_`
- `.`
Запрещено:
- пробелы
- `: / \ -` (в UID запрещены)
- кириллица

---

## 2) UID SCOPE (NAMESPACES / AREAS)
### 2.1 Canonical classes (recommended set)
- `LAW` — законы системы
- `STD` — стандарты (SoT / SPEC / MODULE)
- `KB` — knowledge base (governance/realms/entities)
- `ART` — артефакты (конкретные экземпляры, если нужны)
- `ENT` — системные сущности (entity model)
- `PIPE` — пайплайны
- `IDX` — master-index слоёв
- `REG` — реестры (registry tables)
- `TPL` — шаблоны
- `PRJ` — проектные контейнеры/пространства (если используется)
- `OUT` — выходные сборки/экспорты (если используется)

### 2.2 Stable vs Local contexts
UID всегда **GLOBAL** внутри Universe Engine (не зависит от папки/времени/ветки).
Если объект локальный (внутри проекта/сцены) — он может иметь local id, но UID остаётся системой (см. раздел 6).

---

## 3) UID ASSIGNMENT RULES
### 3.1 Кто получает UID (обязательно)
UID обязателен для:
- любого файла, зарегистрированного в master-index
- любого INDEX/REGISTRY
- любого документа уровня L0/L1 (особенно CORE и master indexes)
- любой схемы артефакта в `ARTIFACT_SCHEMA_REGISTRY`
- любой сущности, которая используется в REL/XREF за пределами локального контекста

### 3.2 Кто может не иметь UID (временно / non-canon)
- черновики (`LOCK: OPEN`) до регистрации
- личные заметки вне канона
- временные файлы миграции (но они НЕ должны быть зарегистрированы в индексах)

---

## 4) UID STABILITY (IMMUTABILITY)
### 4.1 UID неизменяем
UID нельзя менять без Canon Protocol.
Если смысл объекта меняется настолько, что это другой объект — создаётся новый UID.

### 4.2 Переименование файла не меняет UID
Имя файла/путь может меняться (по Naming Rules), но UID остаётся прежним.

### 4.3 Один UID — один объект
Запрещено использовать один UID для разных смыслов/файлов.
Запрещено дублировать UID в двух разных файлах.

---

## 5) UID IN DOCUMENT HEADER (MANDATORY)
Каждый канонический документ обязан иметь в шапке:
- `UID: ...`
и этот UID является единственным источником истины для идентификации документа.

Запрещено:
- дублировать UID внизу файла как отдельную “вторую шапку”
- иметь два UID в одном документе

---

## 6) LOCAL ID BRIDGE (UID vs PROJECT IDs)
### 6.1 Local IDs разрешены
Local IDs (например: сцены, шоты, внутренние элементы) разрешены внутри ограниченного контекста.

### 6.2 Local IDs НЕ заменяют UID
Local ID не может:
- использоваться как идентификатор в system registries
- выступать как SoT идентификатор для объектов вне локального контекста
- использоваться как единственная ссылка в REL/XREF между слоями

### 6.3 Bridge rule (обязательный мост)
Если local id должен быть использован в системной навигации/ссылках — нужен мост:

`LOCAL_ID -> UID`

Мост фиксируется одним из способов:
- Entity Passport (рекомендуется)
- Registry (таблица соответствий)
- Explicit mapping block в документе (если это описательный документ)

---

## 7) CROSS-REFERENCES (REL / XREF) — UID FIRST
### 7.1 Rule
Любая междокументная/межслойная ссылка должна использовать UID как первичный идентификатор.

### 7.2 Minimal XREF record (format)
Рекомендуемый минимальный формат записи:

- `XREF: <UID_TARGET> | <REL_TYPE> | <WHY> | <PATH_OR_RAW(optional)>`

Пример:
- `XREF: UE.LAW.NAMING.RULES.001 | governs | Naming constraints for KB realms | 01_SYSTEM_LAW/01__NAMING_RULES.md`

### 7.3 REL types (minimal set)
- `defines` — определяет сущность/правило
- `governs` — управляет/регулирует
- `depends_on` — зависит от
- `extends` — расширяет (module -> SoT)
- `implements` — реализует (protocol/pipeline)
- `references` — справочная ссылка
- `deprecated_by` — заменён/устарел из-за

---

## 8) ENFORCEMENT (VALIDATION)
UID нарушение = документ неканоничен, пока не исправлен:
- нет UID в шапке у зарегистрированного файла
- UID меняют без Canon Protocol
- два разных файла имеют одинаковый UID
- UID содержит запрещённые символы
- REL/XREF используют local id как единственную межслойную ссылку

---

## FINAL RULE (LOCK)
UID — фундаментальный закон идентификации системы.
Любая правка — изменение канона и проходит Canon Protocol.
--- END.
