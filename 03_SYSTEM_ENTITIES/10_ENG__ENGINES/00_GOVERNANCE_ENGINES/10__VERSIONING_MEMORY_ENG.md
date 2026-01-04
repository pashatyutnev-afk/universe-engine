# Versioning & Memory Engine
FILE: 10__VERSIONING_MEMORY_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 00_GOVERNANCE_ENGINES
LEVEL: L1
STATUS: ACTIVE
VERSION: 1.1
ROLE: Canon version law + change memory — defines how ENG layer versions are assigned, recorded, and referenced

---

## MINI-CONTRACT (MANDATORY)
CONSUMES:
- Approved Change Decision (from Change Control)
- Audit reference (entry id / date / summary)
- List of affected files (paths)
- Dependency impact notes (optional)

PRODUCES:
- Canon version increment (LAYER / FAMILY / ENGINE)
- Changelog entry (structured)
- Memory anchors (references used by other docs)
- Release note stub (optional)

DEPENDS_ON:
- 01__AUDIT_LOG_ENG
- 02__CANON_AUTHORITY_ENG
- 04__CHANGE_CONTROL_ENG
- 05__CONSISTENCY_ENG

OUTPUT_TARGET:
- This file (Versioning Memory Registry)
- Affected docs: header VERSION update when required
- INDEX files when canon composition/order changes

---

## 0) PURPOSE (LAW)
Versioning & Memory Engine обеспечивает:
- **единые правила версий** для ENG слоя
- **память изменений** (что, когда, почему)
- **якоря ссылок** на изменения (чтобы другие документы могли ссылаться на точные версии)

> Любое каноническое изменение обязано оставить след в памяти версий.

---

## 1) VERSION SCOPES (3 LAYERS)
Версии бывают трёх уровней:

### 1.1 ENG LAYER VERSION
Главная версия слоя ENG (используется в индексах верхнего уровня).
Меняется когда затронут **состав/порядок/правила** всего слоя.

### 1.2 FAMILY VERSION
Версия конкретного семейства (папки), меняется когда:
- добавлен/удалён движок
- поменялся порядок
- изменился README realm семейства
- изменились правила/границы семейства

### 1.3 ENGINE VERSION
Версия конкретного движка, меняется когда:
- изменился mini-contract
- изменился алгоритм/процесс/выходы
- изменились зависимости
- изменились обязательные интерфейсы (inputs/outputs)

---

## 2) VERSION FORMAT (MANDATORY)
Формат: `MAJOR.MINOR`

### 2.1 MAJOR increment
MAJOR++ когда:
- ломается совместимость (rules breaking)
- меняется структура папок/именования
- меняется контракт движков так, что старые пайплайны невалидны
- меняются “законы” (law blocks) с обязательной миграцией

### 2.2 MINOR increment
MINOR++ когда:
- добавлены новые движки/поля/пояснения без ломки совместимости
- уточнение/расширение без изменения смысла (но добавляет норму)
- исправления, повышающие консистентность

### 2.3 C0 Cosmetic note
Если правка чисто косметическая (C0) и **не меняет смысл**, допускается:
- НЕ повышать версию файла,
- НО всё равно добавить запись в память как “C0 note” (см. раздел 4).

---

## 3) WHAT REQUIRES VERSION BUMP (TABLE)
### 3.1 ENG LAYER bump
- новый Family
- удаление/слияние Family
- изменение order семейств
- изменение “existence rule”, naming rules, link rules

### 3.2 FAMILY bump
- добавление/удаление engine внутри семейства
- смена нумерации
- изменение family README realm, влияющее на правила/границы

### 3.3 ENGINE bump
- изменение CONSUMES/PRODUCES/DEPENDS_ON/OUTPUT_TARGET
- изменение алгоритма/шагов/выходного формата
- изменение статуса/lock при фиксации канона (OPEN→FIXED)

---

## 4) MEMORY LOG (CANON CHANGELOG)
Все записи делаются в формате:

- DATE: YYYY-MM-DD
- SCOPE: LAYER / FAMILY:<name> / ENGINE:<name>
- TYPE: C0/C1/C2/C3/C4
- VERSION: old → new (или “no bump” для C0)
- CHANGE: 1–3 строки что изменено
- WHY: 1 строка зачем
- FILES:
  - list of canonical paths
- LINKS:
  - Audit entry (raw link or reference)

---

## 5) REQUIRED HEADER FIELDS (CONSISTENCY)
В каждом документе ENG допускается поле VERSION в шапке.

Правило:
- Если документ участвует в каноне (INDEX/README/ENGINE) — VERSION обязателен.
- VERSION внизу файла запрещён (только в шапке).

---

## 6) RELEASE ANCHORS (REFERENCE LAW)
Когда в других местах нужно сослаться на изменение, используется “anchor”:

Формат:
`ENG@<layer_version> / <family>@<family_version> / <engine>@<engine_version>`

Пример:
`ENG@4.0 / 02_DOMAIN_NARRATIVE_ENGINES@1.2 / 05__PACING_RHYTHM_ENG@1.1`

---

## 7) CURRENT CANON VERSIONS (REGISTRY)

### 7.1 ENG LAYER
- ENG_LAYER_VERSION: 4.0
- CURRENT_INDEX: 02__INDEX_ALL_ENGINES.md

### 7.2 FAMILY VERSIONS
- 00_GOVERNANCE_ENGINES: 1.0
- 01_CORE_ENGINES: 1.0
- 02_DOMAIN_NARRATIVE_ENGINES: 1.0
- 03_DOMAIN_CHARACTER_ENGINES: 1.0
- 04_DOMAIN_WORLD_ENGINES: 1.0
- 05_EXPRESSION_ENGINES: 1.0
- 06_GENRE_STYLE_ENGINES: 1.0
- 07_PRODUCTION_FORMAT_ENGINES: 1.0
- 08_KNOWLEDGE_PRODUCTION_ENGINES: 1.0
- 09_SOUND_MUSIC_ENGINES: 1.0
- 10_META_EVOLUTION_ENGINES: 1.0

### 7.3 ENGINE VERSIONS (OPTIONAL REGISTRY)
Этот реестр заполняется постепенно.
Правило: если движок открыт/в разработке — можно не фиксировать здесь.
Если движок LOCK: FIXED — рекомендуется добавить в этот список.

---

## 8) MEMORY LOG (ENTRIES)

### ENTRY 0001
DATE: 2026-01-05
SCOPE: LAYER
TYPE: C1
VERSION: 3.x → 4.0
CHANGE: Established global ENG index structure + family registry order + root links
WHY: Create single source of truth and canon navigation law
FILES:
- 03_SYSTEM_ENTITIES/10_ENG__ENGINES/02__INDEX_ALL_ENGINES.md
LINKS:
- Audit: (to be linked)

---

OWNER: Universe Engine  
LOCK: FIXED
