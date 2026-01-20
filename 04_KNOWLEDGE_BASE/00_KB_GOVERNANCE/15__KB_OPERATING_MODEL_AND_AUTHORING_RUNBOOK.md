# KB OPERATING MODEL + AUTHORING RUNBOOK (CANON)

FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/15__KB_OPERATING_MODEL_AND_AUTHORING_RUNBOOK.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 04_KNOWLEDGE_BASE
REALM: 00_KB_GOVERNANCE
DOC_TYPE: RUNBOOK (KB_GOVERNANCE)
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.RUNBOOK.OPERATING_MODEL.015
OWNER: SYSTEM
ROLE: Single operational description of how KB is structured, how links/relations are formed, how entities consume KB, and how KB must be created/updated to keep the whole system deterministic and audit-safe.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: CREATE
- SUMMARY: "Created KB operating model + authoring runbook: structure, link model, provenance, state, consumption, and update discipline."
- REASON: "Prevent KB drift and rework; enforce deterministic usage across entities and pipelines."
- IMPACT: "KB creation/updates become repeatable; runtime consumption becomes audit-ready."
- CHANGE_ID: UE.CHG.2026-01-20.KB.RUNBOOK.015

---

## 0) PURPOSE (LAW)
Этот документ отвечает на вопросы:
- как KB устроена (слои/реалмы/типы объектов),
- как формируются связи (NAV/REL/XREF),
- как сущности используют KB без фантазии,
- как добавлять/обновлять KB так, чтобы система работала без переделок.

KB — не “копилка текста”. KB — плоскость качества и происхождения (quality + provenance), пригодная для CTL/VAL/QA.

---

## 1) ABSOLUTE LAWS (MUST ALWAYS HOLD)
L1 — ONE-INDEX / EXISTENCE  
- Оперативное существование KB определяется только `04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md`.
- Любой KB файл вне master-index считается NON-CANON для операций.

L2 — RAW-ONLY NAVIGATION  
- Открытие/доступ к KB объектам происходит только через RAW ссылки из master-index.
- Запрещено угадывать пути/файлы.

L3 — SOURCE LOCK / NO FANTASY  
- Любой non-user контент запрещён, пока не представлен как KB-tracked source с provenance markers и статусом разрешения.

L4 — DETERMINISTIC CONSUMPTION  
- Сущности выбирают KB scope по карте задачи, затем загружают минимальный набор модулей по правилам загрузки, затем применяют gates/checklists, и фиксируют evidence в output.

L5 — CHANGE DISCIPLINE  
- Никаких “тихих правок”: change note + запись в KB_CHANGELOG + синхронизация master-index при добавлениях/rename/move.

---

## 2) KB ARCHITECTURE (WHAT LIVES WHERE)
KB разделена на “реалмы действий” (не вторые индексы, а назначение):

A) 00_KB_GOVERNANCE  
- законы, правила, форматы, provenance, states, doc control, обязательные templates.

B) 01_PILLARS  
- крупные фундаментальные “тома” знаний (base craft).

C) 10_TOPICS  
- атомарные модули знаний (малые темы, применимые как building blocks).

D) 20_ENTITIES_KB  
- правила подключения KB к сущностям и PRO PACK (компетенции и гейты для SPC/и т.п.).

E) 30_SHARED_LIBRARIES  
- переиспользуемые активы качества: CHECKLISTS / RUBRICS / TEMPLATES / PATTERNS / EXAMPLES / PROMPT_LIB.

F) 40_RELATION_XREF  
- карты соответствий (task→scope, scope→modules, gate→modules, pipeline→scope, etc.).

---

## 3) KB OBJECT MODEL (TYPES)
KB содержит два базовых семейства объектов:

### 3.1 KB MODULE (правило/метод/гейт/тема)
Использовать TEMPLATE: `20__TEMPLATE__KB_MODULE`.
Минимальная обязанность модуля: быть actionable (procedure/checklist/rubric/template) + иметь PASS/FAIL примеры.

### 3.2 KB LIBRARY ITEM (переиспользуемый актив качества)
Использовать TEMPLATE: `21__TEMPLATE__KB_LIBRARY_ITEM`.
Подходит для: чеклистов, рубрик, шаблонов, паттернов, анти-паттернов, промпт-либы, примеров.

### 3.3 KB-TRACKED SOURCE (источник внешнего контента)
Это KB объект (module/item/record), который содержит provenance markers и статусы разрешения.
Используется для corpus/поэзии/цитат/внешних фактов/таблиц/любой “не-user” информации.

---

## 4) LINK MODEL (HOW CONNECTIONS ARE FORMED)
В системе ровно 3 механизма связей, у каждого своя роль.

### 4.1 NAV/EXISTENCE (RAW-only, via master-index)
- Только master-index даёт право “существовать” и открывать RAW.
- Внутренние документы не должны заменять master-index вторыми entrypoint.

### 4.2 REL (semantic relations between KB units)
REL отвечает на вопрос “почему связано”.
- Используются только канонические rel types (depends_on, reinforces, conflicts_with, …).
- REL не является навигацией: он не открывает файлы, он описывает смысл связи.

### 4.3 XREF / MAPS (deterministic routing)
XREF/MAPS отвечают на вопрос “что обязано применяться”.
Типовые карты:
- task → KB scope
- scope → module loading rules
- pipeline → required scopes/modules/gates
- entity → required KB sources + gates (через connector)

---

## 5) PROVENANCE MODEL (NO-FANTASY EXECUTION)
Если KB объект содержит или использует non-user content, он обязан иметь маркеры:

MANDATORY PROVENANCE MARKERS:
- KB_SOURCE_RAW: (raw ссылка на KB объект-источник)
- SOURCE_STATUS: PD_CONFIRMED | LICENSE_CONFIRMED
- SOURCE_NOTE: что это и почему допустимо
- FULL_TEXT_ALLOWED: YES|NO (YES только если реально разрешено и нужно)

Boundary rule:
- Если задача требует non-user content, а provenance markers нет → STOP: marker not confirmed.

---

## 6) STATE + MEMORY SAFETY
KB управляет “операционным состоянием” модулей:
- UNREAD
- READ_ONCE
- VERIFIED
- DEPRECATED

Memory-OK разрешён только для VERIFIED.
Любое изменение VERIFIED модуля требует пересмотра state (обычно VERIFIED → READ_ONCE до перепроверки).

---

## 7) ENTITY ↔ KB CONNECTION (HOW ENTITIES CONSUME KB)
Любая сущность, которая принимает решения/делает output, обязана иметь KB-connector по шаблону `23__TEMPLATE__ENTITY_KB_CONNECTOR`.

Connector фиксирует:
- KB_SOURCES (обязательные/опциональные)
- KB_GATES (обязательные проверки)
- output contract (какой тип артефакта и по какому шаблону)
- stop triggers
- evidence block requirement

### 7.1 Runtime evidence requirement (mandatory)
Любой output artifact, который использует KB, обязан содержать:
- KB_SOURCES_USED: (что реально было загружено/использовано)
- KB_GATES_APPLIED: (что реально проверено)
- KB_SCOPE_RAW: (если пайплайн/контент относится к выбранному scope и реально потреблял KB)

Если evidence отсутствует → FAIL (KB usage gate violation).

---

## 8) DETERMINISTIC KB INTAKE (HOW A RUN SELECTS MODULES)
Схема всегда одинаковая:

Step A — classify task (task class)  
Step B — select REQUIRED scopes (task→scope map)  
Step C — load minimal modules in deterministic order (scope→module loading rules)  
Step D — apply gates/checklists/rubrics required  
Step E — emit trace (KB_SOURCES_USED + KB_GATES_APPLIED + provenance if needed)

Запрещено:
- грузить “всё подряд”
- применять память, когда state не VERIFIED
- подменять provenance “по ощущениям”

---

## 9) AUTHORING WORKFLOWS (CREATE / UPDATE WITHOUT REWORK)

### 9.1 CREATE: new KB module
1) Choose correct realm (PILLARS / TOPICS / SHARED_LIBRARIES / RELATION_XREF / GOVERNANCE).
2) Create file using correct template (KB_MODULE or KB_LIBRARY_ITEM).
3) Assign doc control fields + UID + version + status/lock.
4) If module contains external content: add provenance markers + status.
5) Register file in KB master-index (existence).
6) Add entry in KB_CHANGELOG with impact + required actions.
7) If module must be used by entities: update relevant entity KB connectors or scope maps.
8) Run validation checklists (XREF/REL if you added links).

### 9.2 UPDATE: existing KB module
1) Change note must be present (no silent drift).
2) Update KB_CHANGELOG entry with IMPACT + REQUIRED_ACTIONS.
3) If module was VERIFIED: downgrade state until revalidated.
4) If rename/move: update KB master-index + all references (maps/connectors).
5) Re-run gates or exemplars that depend on the module.

### 9.3 DEPRECATE
1) Status → DEPRECATED
2) Provide replacement (what to use instead)
3) Update maps/connectors to stop requiring deprecated module
4) Log change (impact + actions)

---

## 10) MINIMUM QUALITY CHECKS (BEFORE ACCEPTING KB CHANGE)
- Existence: file is registered in KB master-index.
- Source lock: if external content exists, provenance markers exist.
- State: no Memory-OK use unless VERIFIED.
- Determinism: maps/connectors specify REQUIRED vs OPTIONAL (no vague words).
- Trace: outputs include KB_SOURCES_USED + KB_GATES_APPLIED when KB consumed.

---

END.
