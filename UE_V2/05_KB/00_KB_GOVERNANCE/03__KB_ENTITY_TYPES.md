# KB ENTITY TYPES — CANONICAL TYPE SYSTEM (KB)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/03__KB_ENTITY_TYPES.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: SPEC
INDEX_TYPE: ENTITY_TYPE_REGISTRY (KB)
LEVEL: L1
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPEC.ENTITY_TYPES.001
OWNER: SYSTEM
ROLE: Define canonical KB unit types and mandatory fields; enables deterministic authoring and source-locked usage by entities

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created KB entity type system: universal KB modules + libraries + entity connectors + maps; mandatory fields and usage intent."
- REASON: "KB must be universal professional library; entities must know what they can consume and how."
- IMPACT: "All KB content becomes typed, checkable, and enforceable by KB usage gate."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TYPES.001

---

## 0) PURPOSE (LAW)
Этот документ фиксирует **типы KB-единиц** (что именно является “единицей знания/актива/карты”).
Цель:
- устранить хаос (“что это за файл?”),
- обеспечить единый формат,
- дать сущностям понятный “контракт потребления” (что читать и как применять).

Это не NAV/EXISTENCE индекс. Существование файлов фиксирует только KB master-index.

---

## 1) ABSOLUTE RULES
### 1.1 Typed-only rule (mandatory)
Любой KB файл должен быть однозначно классифицирован как один из типов ниже.

### 1.2 Source-lock compatibility
Каждый тип должен быть пригоден для source-locked применения:
- однозначные правила
- чеклисты/рубрики
- примеры PASS/FAIL
- связанные ссылки (PATH/RAW)

### 1.3 No duplication
Типы не дублируют друг друга:
- фундамент → PILLAR
- атомарное знание → TOPIC
- актив качества → LIBRARY_ITEM
- подключение сущностей → ENTITY_CONNECTOR / PRO_PACK
- маршруты/связи → MAP

---

## 2) TYPE GROUP A — FOUNDATION KNOWLEDGE
### A1) PILLAR (FOUNDATION TOME)
**Что это:** фундаментальный том домена (широкая область).  
**Где лежит:** `01_PILLARS/` (см. KB storage map).  
**Для кого:** SPC/ENG/ORC и любые сущности как базовая “книга”.  
**Обязательные секции (minimum):**
- PURPOSE
- PRINCIPLES (core)
- STANDARD PROCEDURES (high level)
- COMMON FAILURES (high level)
- REFERENCES (PATH/RAW на TOPICS/LIBRARIES)

**Запрещено:** превращать PILLAR в свалку “всё подряд”. Детали — в TOPICS.

---

## 3) TYPE GROUP B — ATOMIC KNOWLEDGE
### B1) TOPIC (ATOMIC MODULE)
**Что это:** один метод/правило/техника/понятие.  
**Где лежит:** `10_TOPICS/<DOMAIN>/TOPIC__*.md`  
**Для кого:** все сущности как “кирпичик”.  
**Обязательные поля/секции (minimum):**
- PURPOSE
- WHEN TO USE / WHEN NOT TO USE
- PROCEDURE / CHECKLIST (или формальная формулировка)
- EXAMPLES: PASS / FAIL (+ EDGE если применимо)
- RELATED: REL/XREF (PATH only)

**Запрещено:** делать TOPIC без применения и примеров.

---

## 4) TYPE GROUP C — QUALITY ASSETS (SHARED LIBRARIES)
### C0) LIBRARY_ITEM (GENERAL)
LIBRARY_ITEM — переиспользуемый актив качества. Хранится в `30_SHARED_LIBRARIES/`.

Общие minimum секции:
- PURPOSE
- USAGE (как применять)
- EXAMPLES (если применимо)
- RELATED (PATH)

#### C1) CHECKLIST (CL__)
**Назначение:** decision/checklist контроль.  
**Must contain:** checklist steps + pass criteria.

#### C2) RUBRIC (RUBRIC__)
**Назначение:** оценка качества PASS/FAIL/REWORK.  
**Must contain:** шкала, критерии, пороги, примеры.

#### C3) TEMPLATE (TPL__)
**Назначение:** формат выходного артефакта (output contract).  
**Must contain:** поля/разделы + правила заполнения + пример мини-выхода.

#### C4) PATTERN (PATTERN__)
**Назначение:** успешная конструкция/паттерн.  
**Must contain:** когда применять, структура, примеры.

#### C5) ANTI-PATTERN (ANTI__)
**Назначение:** типовая ошибка/запрещённый подход.  
**Must contain:** почему плохо, симптомы, как исправлять.

#### C6) EXAMPLE (EXAMPLE__)
**Назначение:** эталонные примеры PASS/FAIL паков.  
**Must contain:** вход → выход → пояснение → ссылки на нормы.

#### C7) PROMPT_LIB (PROMPT__)
**Назначение:** переиспользуемые промпт-блоки/ограничения.  
**Must contain:** контекст применения + негативные ограничения (если есть) + примеры.

---

## 5) TYPE GROUP D — ENTITY INTEGRATION (ENTITIES_KB)
### D1) ENTITY_CONNECTOR_STANDARD (README)
**Что это:** стандарт коннектора для класса сущностей (SPC/ENG/ORC/CTL/VAL/QA/XREF).  
**Где лежит:** `20_ENTITIES_KB/<CLASS>/00__README__*_KB_CONNECTOR_STANDARD.md`  
**Назначение:** объяснить обязательные файлы/структуру/гейты.

### D2) ENTITY_CONNECTOR_PACK (for a specific entity)
**Что это:** пакет документов, описывающий как конкретная сущность подключается к KB.  
**Must contain (general):**
- KB_SOURCES (REQUIRED/OPTIONAL)
- KB_GATES (mandatory)
- OUTPUT CONTRACT (template path)
- STOP CONDITIONS

### D3) SPC_PRO_PACK (special case, mandatory for every SPC)
**Что это:** пакет профессиональных знаний для SPC (не знания “внутри сущности”, а KB-пакет специалиста).  
**Must contain:** минимум файлов, заданных SPC PRO PACK standard:
- passport, skill tree, golden principles, playbooks, checklists, patterns/anti, case library, evaluation rubric, sources, gates.

### D4) COVERAGE / STATUS MAPS
**Что это:** файлы контроля покрытия:
- кто из сущностей имеет KB-pack
- кто из SPC достиг уровня “proficiency”
Это не knowledge modules и не templates.

---

## 6) TYPE GROUP E — MAPS (RELATION / ROUTING / XREF)
### E1) TASK_TO_SCOPE_MAP
**Назначение:** “задача → какие KB модули/рубрики обязательны”.  
**Must contain:** таблица задач и минимальный scope.

### E2) REL_GRAPH / XREF_MAPS
**Назначение:** карты связей (не знание).  
**Must contain:** rel/xref правила + “куда смотреть дальше”.

### E3) CANON TERMS LIST
**Назначение:** канонические термины и определения (если требуется единая терминология).  
**Must contain:** термин → определение → ссылки на источники.

---

## 7) TYPE MINIMUM CHECK (FAST)
KB файл проходит минимум-чек, если:
- тип определён и соответствует placement (storage map),
- есть секции minimum для типа,
- есть примеры (если тип требует),
- нет фантазии: всё source-locked/Memory-OK без искажений.

--- END.
