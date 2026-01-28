# KB XREF RULES — CROSS-REFERENCE MAP STANDARD (KB)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/07__KB_XREF_RULES.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: SPEC
INDEX_TYPE: XREF_RULESET (KB)
LEVEL: L1
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPEC.XREF.001
OWNER: SYSTEM
ROLE: Define canonical XREF map rules for KB; enables deterministic task routing, scope maps, and audit-friendly cross-references (PATH-only)

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created KB XREF rules: map types, formats, and required tables; PATH-only and audit-safe."
- REASON: "KB must support deterministic navigation of actions: task→scope, pipeline→modules, validation→checks without invention."
- IMPACT: "Crossref maps become consistent; entities can select required KB scope deterministically."
- CHANGE_ID: UE.CHG.2026-01-14.KB.XREF.001

---

## 0) PURPOSE (LAW)
XREF — это **карты маршрутов и соответствий**, которые позволяют быстро отвечать:
- какие KB-модули обязательны для задачи (task→scope),
- какие проверки (VAL/QA) привязаны к пайплайну/домену,
- какие политики/рубрики применяются,
- где лежат маршруты “что читать и что применять”.

XREF НЕ:
- не является NAV/EXISTENCE индексом (это делает master-index),
- не заменяет REL (семантические связи между двумя модулями).

---

## 1) ABSOLUTE RULES
### 1.1 PATH-only (ABSOLUTE)
Все ссылки в XREF картах фиксируются в виде PATH.
RAW можно добавлять вторичной строкой, но canonical идентификатор всегда PATH.

### 1.2 Deterministic mapping (no poetry)
XREF карты должны быть однозначными таблицами.
Запрещены размытые формулировки (“часто”, “примерно”, “иногда”) без гейтов.

### 1.3 Minimal but complete
XREF карта должна быть минимальной, но покрывать обязательные маршруты.
Если карта становится “архивом всего” — это нарушение.

### 1.4 Update discipline
Любое изменение XREF карты:
- фиксируется в KB_CHANGELOG,
- имеет impact note (какие сущности/пайплайны затронуты).

---

## 2) CANON XREF MAP TYPES (KB)
### X1) TASK_TO_SCOPE_MAP
**Вопрос:** “для задачи X какие KB-модули обязательны?”  
**Тип файла:** `type_scope_map`  
**Рекомендуемое место:** `04_KNOWLEDGE_BASE/40_RELATION_XREF/01__TASK_TO_KB_SCOPE_MAP.md`

---

### X2) PIPELINE_TO_SCOPE_MAP
**Вопрос:** “для пайплайна P какие модули и гейты обязательны?”  
**Используется:** ORC pipelines / release packs / production flows.

---

### X3) VALIDATION_MATRIX
**Вопрос:** “какие валидаторы/QA гейты применяются к типу результата?”  
**Используется:** VAL/QA подключение к доменам и артефактам.

---

### X4) POLICY_APPLICATION_MAP
**Вопрос:** “какие CTL политики обязательны для домена/задачи?”  
**Используется:** enforcement и governance.

---

### X5) ENTITY_TO_KB_SCOPE_MAP
**Вопрос:** “какой минимальный KB scope обязателен для сущности/класса сущностей?”  
**Рекомендуемое место:** `04_KNOWLEDGE_BASE/20_ENTITIES_KB/02__ENTITY_TO_KB_SCOPE_MAP.md`

---

### X6) TEMPLATE_USAGE_MAP
**Вопрос:** “какой шаблон (output contract) обязателен для типа результата?”  
**Используется:** output contract enforcement.

---

## 3) REQUIRED FORMAT (MANDATORY TABLES)
### 3.1 XREF header block (recommended)
Каждая XREF карта должна начинаться с:
- PURPOSE (что карта отвечает)
- SCOPE (что покрывает / что не покрывает)
- UPDATE RULE (как обновлять)

### 3.2 Table format (mandatory)
Таблицы пишутся в markdown table.

#### A) TASK_TO_SCOPE_MAP — mandatory columns
| TASK_ID | TASK_NAME | DOMAIN | REQUIRED_KB_MODULES (PATH list) | REQUIRED_GATES (PATH list) | OUTPUT_TEMPLATE (PATH) | NOTES |
|---|---|---|---|---|---|---|

Правила:
- REQUIRED_KB_MODULES: список PATH через `; `
- REQUIRED_GATES: список PATH через `; `
- OUTPUT_TEMPLATE: один PATH (или `N/A`)
- Если задача имеет варианты — отдельные строки (TASK_ID suffix)

#### B) VALIDATION_MATRIX — mandatory columns
| ARTIFACT_TYPE | DOMAIN | REQUIRED_VAL (PATH list) | REQUIRED_QA (PATH list) | OPTIONAL_CHECKS (PATH list) | FAIL_POLICY (PATH) |
|---|---|---|---|---|---|

#### C) ENTITY_TO_KB_SCOPE_MAP — mandatory columns
| ENTITY_CLASS | ENTITY_NAME_OR_PATTERN | REQUIRED_PILLARS (PATH list) | REQUIRED_TOPICS (PATH list) | REQUIRED_LIBS (PATH list) | REQUIRED_GATES (PATH list) |
|---|---|---|---|---|---|

---

## 4) LINKING RULES (XREF vs REL)
### 4.1 When to use REL
REL используется в модуле, чтобы объяснить связь “этот модуль зависит от того”.

### 4.2 When to use XREF
XREF используется, когда нужно:
- таблица соответствий,
- маршрут по задаче/пайплайну,
- матрица проверок,
- выбор обязательного scope.

---

## 5) ANTI-PATTERNS (FORBIDDEN)
Запрещено:
- использовать XREF как “второй master-index” (перечислять все файлы слоя)
- хранить в XREF “контент знаний” (это TOPICS/PILLARS/LIBRARIES)
- писать “ссылки без назначения” (каждая строка должна отвечать вопросу карты)
- размытые требования без gate/порога

---

## 6) MINIMUM COMPLIANCE CHECK
XREF карта считается корректной, если:
- тип карты определён (из X1..X6),
- все ссылки в PATH формате,
- таблицы имеют обязательные колонки,
- карта отвечает на свой вопрос однозначно,
- изменения контролируются (changelog + impact note).

--- END.
