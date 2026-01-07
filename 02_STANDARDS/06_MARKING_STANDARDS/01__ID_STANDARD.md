# ID STANDARD (MARKING MODULE) (CANON)
FILE: 02_STANDARDS/06_MARKING_STANDARDS/01__ID_STANDARD.md

SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: MODULE
MODULE_TYPE: MARKING
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.STD.MOD.MARKING.ID.601
OWNER: SYSTEM
ROLE: Marking module that details ID/UID usage rules: local ids, human-readable ids, and identity fields across documents. Extends UID & Marking SoT without duplicating it.

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MINOR
- SUMMARY: "Модуль ID: различие UID vs Local ID vs Human ID, правила формирования, запрет подмены UID, формат ссылок"
- REASON: "Убрать путаницу идентификаторов и сделать единый контракт применения"
- IMPACT: "All layers, KB passports, registries, scene/event artifacts"

---

## XREF (UID-first)
XREF: UE.STD.SPEC.UID_MARKING.101 | extends | this module details ID rules | 02_STANDARDS/01_SPECIFICATIONS/01__UID_AND_MARKING_STANDARD.md
XREF: UE.LAW.UID.002 | depends_on | UID primary rules | 01_SYSTEM_LAW/02__UID_RULES.md
XREF: UE.STD.SPEC.DOC_CONTROL.103 | depends_on | header fields usage | 02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md
XREF: UE.STD.SPEC.REL_XREF.104 | depends_on | UID-first linking | 02_STANDARDS/01_SPECIFICATIONS/04__REL_POLICY_XREF_STANDARD.md

---

## 0) PURPOSE
Этот модуль уточняет правила идентификаторов:
- чем UID отличается от любых “локальных id”
- где допускаются Local IDs (внутри документа)
- как писать Human-readable IDs (если нужны)
- как ссылаться на объекты системы без ломания UID-first

---

## 1) ID TYPES (CONTROLLED DEFINITIONS)
### 1.1 UID (ABSOLUTE)
- глобальный системный идентификатор
- уникальный и стабильный
- primary ключ для ссылок

UID обязателен:
- в Doc Control header (для канонического документа)
- в XREF/REL связях (UID-first)

### 1.2 LOCAL_ID (ALLOWED)
Local ID — идентификатор внутри одного документа/контейнера:
- используется для удобства чтения
- НЕ является глобальной ссылкой
- может быть не уникален глобально

Примеры Local ID:
- `E10` (event внутри сцены)
- `SHOT_03`
- `RULE_A`

Правило:
- Local ID нельзя использовать как единственный идентификатор в междокументных ссылках.

### 1.3 HUMAN_ID (OPTIONAL)
Human ID — “человеческая метка”, например:
- `SCENE_01_INTRO`
- `ARC_A1_CH03`
- `CHAR_MAIN_001`

Правила:
- Human ID не заменяет UID
- если используется, то пишется рядом с UID (как label)

---

## 2) WHERE IDS LIVE (PLACEMENT)
### 2.1 Document header
- `UID` — обязателен для канона
- другие ID в header не обязательны

### 2.2 Inside content (allowed)
Local IDs разрешены внутри:
- Scene Pack events
- Track events
- tables/registries
- lists of entities

---

## 3) CANONICAL REFERENCE FORMAT (UID-FIRST)
### 3.1 Minimal reference
- `UID: <UID>`

### 3.2 Reference with label/path
- `UID: <UID> | LABEL: <HUMAN_ID optional> | PATH: <path optional>`

### 3.3 Prohibited reference
Нельзя:
- ссылаться “только по пути”
- ссылаться “только по local id”
- ссылаться “по имени без UID” (если это внутренняя сущность системы)

---

## 4) LOCAL ID RULES (WHEN ALLOWED)
Local ID разрешён только если:
- объект не должен быть адресуемым вне контейнера
- либо у него есть UID, а local id — только alias

Рекомендуемый формат:
- uppercase + digits/underscore: `E10`, `SHOT_03`, `R_02`
- без пробелов
- стабильность внутри документа (не менять без необходимости)

---

## 5) HUMAN ID RULES (OPTIONAL)
Если вводится Human ID:
- он должен быть детерминированным и читаемым
- не должен конфликтовать по смыслу с UID
- не используется как ключ системы

Рекомендуемый формат:
- `DOMAIN_PREFIX + "_" + descriptor`
Пример:
- `SCENE_INTRO_01`
- `CHAR_VIKTOR_01`

---

## 6) ID COLLISION RULES
### 6.1 UID collisions (FORBIDDEN)
Два объекта не могут иметь одинаковый UID.

### 6.2 Local ID collisions (ALLOWED WITH RULE)
В одном контейнере local id должен быть уникальным.
Если есть группы:
- используй вложенные namespace: `SHOT_01_A`, `SHOT_01_B`

---

## 7) MIGRATION NOTES
S0:
- во всех документах, где есть “id/номер”, явно различить: UID vs local id
- привести ссылки к UID-first формату

---

## FINAL RULE (LOCK)
Этот модуль расширяет SoT UID & Marking и не может противоречить ему.
Любая правка, меняющая базовые определения UID/Local/Human = MAJOR по умолчанию.
--- END.
