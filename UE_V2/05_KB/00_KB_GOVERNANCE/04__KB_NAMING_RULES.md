# KB NAMING RULES — FILE/FOLDER NAMING STANDARD (KB)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/04__KB_NAMING_RULES.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: SPEC
INDEX_TYPE: NAMING_RULES (KB)
LEVEL: L1
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPEC.NAMING.001
OWNER: SYSTEM
ROLE: Define deterministic naming rules for all KB files/folders; supports scaling, searchability, and prevents drift/duplication

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created KB naming rules for all realms: governance, pillars, topics, libraries, entities_kb, relation_xref."
- REASON: "KB must be universal professional library; names must be predictable for one-index navigation and Ctrl+F."
- IMPACT: "All KB objects get stable predictable names; duplicate/ambiguous names become violations."
- CHANGE_ID: UE.CHG.2026-01-14.KB.NAMING.001

---

## 0) PURPOSE (LAW)
Эти правила задают единый стандарт именования файлов и папок в `04_KNOWLEDGE_BASE`.
Цель:
- детерминированный поиск (Ctrl+F) в master-index,
- отсутствие коллизий и дублей,
- стабильные пути для ссылок (PATH/RAW),
- масштабирование без хаоса.

Это не индекс существования. Существование фиксирует только master-index.

---

## 1) GLOBAL RULES (ABSOLUTE)
### 1.1 Case & separators
- Используется `UPPER_SNAKE_CASE` для смысловых частей.
- Разделитель — `_` (underscore).
- Никаких пробелов в именах файлов/папок.

### 1.2 Numeric ordering
- Везде, где есть порядок, используется префикс `NN__` (две цифры + двойное подчёркивание).
- Папки доменов в TOPICS: `10_...`, `20_...`, `30_...` и т.д.

### 1.3 README rule
- README файл realm/домена всегда `00__README__...md`

### 1.4 Template rule
- Шаблон всегда содержит `TEMPLATE` и идёт отдельной нумерацией:
  - `20__TEMPLATE__...md`, `21__TEMPLATE__...md` и т.д.

### 1.5 No drift rule
- Нельзя создавать “почти такое же имя” как у существующего файла (коллизия смыслов).
- Любое переименование требует синхронизации master-index (иначе файл “исчезает оперативно”).

---

## 2) REALM-SPECIFIC NAMING (CANON)
### 2.1 00_KB_GOVERNANCE
Форматы:
- `NN__README__...md`
- `NN__RULES__...md`
- `NN__KB_<THING>.md`
- `NN__TEMPLATE__<THING>.md`

Примеры:
- `00__README__KB_REALM.md`
- `01__RULES__KB.md`
- `10__KB_QUALITY_LAWS.md`
- `12__KB_SOURCE_LOCK_NO_FANTASY.md`
- `20__TEMPLATE__KB_MODULE.md`

---

### 2.2 01_PILLARS
Формат:
- `NN__PILLAR__<DOMAIN_NAME>.md`

Примеры:
- `01__PILLAR__NARRATIVE_CRAFT.md`
- `05__PILLAR__SOUND_MUSIC.md`

Правило:
- PILLAR — это “том”, не тема. Не дробим его именем на слишком узкие куски.

---

### 2.3 10_TOPICS
TOPIC формат (файл):
- `TOPIC__<NAME>.md`

Доменные папки (фиксированный набор, можно расширять только через KB change control):
- `10_NARRATIVE/`
- `20_CHARACTER/`
- `30_WORLD/`
- `40_VISUAL/`
- `50_SOUND_MUSIC/`
- `60_PRODUCTION/`
- `70_MARKETING/`
- `90_REFERENCE/`

README домена:
- `00__README__TOPICS_<DOMAIN>.md`

Пример пути:
- `04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/TOPIC__HOOK_TIMING.md`

---

### 2.4 30_SHARED_LIBRARIES
Каждый тип библиотеки имеет свой префикс:

- CHECKLISTS → `CL__<NAME>.md`
- RUBRICS → `RUBRIC__<NAME>.md`
- TEMPLATES → `TPL__<NAME>.md`
- PATTERNS → `PATTERN__<NAME>.md`
- ANTI-PATTERNS → `ANTI__<NAME>.md`
- EXAMPLES → `EXAMPLE__<NAME>.md`
- PROMPT_LIB → `PROMPT__<NAME>.md`

README в каждой подпапке:
- `00__README__<TYPE>.md`

---

### 2.5 20_ENTITIES_KB
Этот realm хранит стандарты коннекторов и PRO PACK.

#### A) Connector standard readme (per class)
- `00__README__<CLASS>_KB_CONNECTOR_STANDARD.md`
Где `<CLASS>` один из: `SPC`, `ENG`, `ORC`, `CTL`, `VAL`, `QA`, `XREF`.

#### B) Template folders (per class)
- `<CLASS>__TEMPLATE/` (папка)
- внутри файлы имеют `NN__...` формат как в вашем каркасе.

#### C) SPC PRO PACK folders
Папка конкретного специалиста:
- `SPC__<SPC_NAME>/`

Файлы внутри SPC PRO PACK:
- `00__KB_PASSPORT.md`
- `01__SKILL_TREE.md`
- `02__GOLDEN_PRINCIPLES.md`
- `03__PLAYBOOKS.md`
- `04__CHECKLISTS.md`
- `05__PATTERNS_ANTI_PATTERNS.md`
- `06__CASE_LIBRARY.md`
- `07__EVALUATION_RUBRIC.md`
- `90__KB_SOURCES.md`
- `91__KB_GATES.md`

---

### 2.6 40_RELATION_XREF
Формат:
- `NN__<MAP_NAME>.md`

Примеры:
- `01__TASK_TO_KB_SCOPE_MAP.md`
- `02__KB_REL_GRAPH.md`
- `03__KB_XREF_MAPS.md`

---

## 3) COLLISION RULES (ABSOLUTE)
Коллизии запрещены:
- одинаковые `<NAME>` в одном и том же типе (например два `TOPIC__HOOK_TIMING.md`)
- разные файлы с одинаковым смыслом под разными именами
- “alias файлы” как вторые entrypoints (кроме специально разрешённых POINTER файлов без правил)

Если нужен alias:
- делается только как POINTER (пустышка-ссылка), без новых правил и без дублирования содержания.

---

## 4) RENAMING / MOVING RULE (MANDATORY)
Любое переименование/перемещение KB файла требует:
1) Обновить master-index KB (CANON MAP RAW).
2) Обновить все ссылки PATH/RAW, которые на него ссылаются (KB_SOURCES/RELATED).
3) Зафиксировать изменение в KB_CHANGELOG с impact note.

Если этого нет — файл считается “потерянным” для оперативной системы.

--- END.
