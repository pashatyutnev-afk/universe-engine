# 05__ARTIFACT_SCHEMA_REGISTRY

FILE: 01_SYSTEM_LAW/05__ARTIFACT_SCHEMA_REGISTRY.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 01_SYSTEM_LAW
DOC_TYPE: REGISTRY (LAW)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.LAW.ARTIFACT.REG.001
OWNER: SYSTEM
ROLE: Canonical registry of artifact document types and their minimum schemas. Defines what outputs are allowed and what sections are mandatory.

CHANGE_NOTE:
- DATE: 2026-01-19
- TYPE: MINOR
- SUMMARY: "Registry is now populated with canonical artifact types + minimum schemas + UID/CHANGE_ID expectations + mandatory sections. Enables Output Artifact Rule to be enforceable."
- REASON: "Without a filled registry the system cannot enforce artifact packaging deterministically."
- IMPACT: "Any output can be validated against a declared artifact schema."

---

## 0) PURPOSE (LAW)
Этот реестр фиксирует **какие артефакты существуют** в системе и **какую минимальную структуру** обязан иметь каждый артефакт-документ.

### 0.1 OUTPUT ARTIFACT RULE (ABSOLUTE)
Система не имеет права выпускать “голый контент”.
Любой результат = **артефакт-документ**, который:
- имеет DOC_CONTROL шапку (минимум: FILE, SCOPE, DOC_TYPE, STATUS, LOCK, VERSION, UID, OWNER);
- соответствует **одной записи** из этого реестра;
- проходит через цепочку контроля: CTL → VAL → QA → DOC CONTROL signoff (в рантайме).

Если артефакт не подходит ни под один тип — это GAP:
- система обязана предложить **новый artifact type** и добавить его в этот реестр через change management.

---

## 1) DEFINITIONS (MINIMUM)
- **Artifact Type** — канонический тип результата (пример: TRACK_CARD, KB_MODULE, ORC_PIPELINE).
- **Minimum Schema** — минимально обязательные секции для данного типа.
- **Optional Sections** — секции по желанию (но не могут заменять обязательные).
- **Schema UID** — UID записи схемы (в этом документе).
- **Artifact UID** — UID конкретного созданного артефакта.

---

## 2) REGISTRY FORMAT (HOW TO READ)
Каждая запись содержит:
- ARTIFACT_TYPE: каноническое имя типа
- ARTIFACT_CLASS: (DOC / ENTITY / PIPELINE / RECORD / PACK)
- OUTPUT_INTENT: что это даёт системе/пользователю
- MIN_SCHEMA: список обязательных секций
- OPTIONAL: опциональные секции
- REQUIRED_MARKERS: маркеры/ключи, которые должны присутствовать
- UID_RULE: ожидание по UID (формат определяется UID_RULES, здесь фиксируется назначение)
- CHANGE_ID_RULE: когда обязателен CHANGE_ID

---

## 3) CANONICAL ARTIFACT TYPES (REGISTRY)

### 3.1 GOVERNANCE & NAVIGATION

#### A01 — ROOT_INDEX_SNAPSHOT
- ARTIFACT_TYPE: ROOT_INDEX_SNAPSHOT
- ARTIFACT_CLASS: DOC
- OUTPUT_INTENT: “Снимок базы RAW-ссылок”, без выполнения задач.
- MIN_SCHEMA:
  - Header (DOC_CONTROL)
  - LINK BASE SNAPSHOT POLICY (LAW)
  - TASK ENTRYPOINT LAW
  - LIST OF RAW LINKS (organized)
- REQUIRED_MARKERS:
  - "LINK BASE SNAPSHOT POLICY"
  - "TASK ENTRYPOINT LAW"
- UID_RULE: Artifact UID обязателен.
- CHANGE_ID_RULE: обязателен при изменении списка ссылок.

#### A02 — START_ENTRYPOINT_RUNBOOK
- ARTIFACT_TYPE: START_ENTRYPOINT_RUNBOOK
- ARTIFACT_CLASS: DOC
- OUTPUT_INTENT: Единственная точка запуска рантайма.
- MIN_SCHEMA:
  - Header (DOC_CONTROL)
  - PURPOSE (LAW)
  - INPUTS (MINIMUM)
  - ABSOLUTE RUNTIME LAWS
  - BOOT SEQUENCE (MANDATORY ORDER)
  - BOOT COMPLETE MARKER (REQUIRED)
  - TASK LIFECYCLE (DEFAULT PIPELINE)
  - CREATE MISSING ENTITY PROTOCOL
  - RUNTIME OUTPUT (CHAT CONTRACT)
- REQUIRED_MARKERS:
  - "BOOT SEQUENCE"
  - "BOOT COMPLETE MARKER"
  - "Stop conditions"
- UID_RULE: Artifact UID обязателен.
- CHANGE_ID_RULE: обязателен на любое изменение текста.

#### A03 — LAW_DOC
- ARTIFACT_TYPE: LAW_DOC
- ARTIFACT_CLASS: DOC
- OUTPUT_INTENT: Нормативный закон слоя/подсистемы.
- MIN_SCHEMA:
  - Header (DOC_CONTROL)
  - PURPOSE (LAW)
  - RULES (numbered)
  - ENFORCEMENT (who enforces: CTL/VAL/QA)
  - EXCEPTIONS (if any)
- OPTIONAL:
  - Examples
  - Appendix
- REQUIRED_MARKERS:
  - "PURPOSE (LAW)"
  - "ENFORCEMENT"
- UID_RULE: Artifact UID обязателен.
- CHANGE_ID_RULE: обязателен на любое изменение.

#### A04 — STANDARD_DOC
- ARTIFACT_TYPE: STANDARD_DOC
- ARTIFACT_CLASS: DOC
- OUTPUT_INTENT: Нормативный стандарт (как делать/оформлять/хранить).
- MIN_SCHEMA:
  - Header (DOC_CONTROL)
  - PURPOSE
  - SCOPE
  - DEFINITIONS
  - RULES / REQUIREMENTS
  - COMPLIANCE CHECKLIST
- REQUIRED_MARKERS:
  - "COMPLIANCE CHECKLIST"
- UID_RULE: Artifact UID обязателен.
- CHANGE_ID_RULE: обязателен на любое изменение.

#### A05 — TEMPLATE_DOC
- ARTIFACT_TYPE: TEMPLATE_DOC
- ARTIFACT_CLASS: DOC
- OUTPUT_INTENT: Шаблон документа (копируй-вставляй).
- MIN_SCHEMA:
  - Header (DOC_CONTROL)
  - TEMPLATE PURPOSE
  - REQUIRED FIELDS
  - REQUIRED SECTIONS
  - PLACEHOLDERS EXAMPLES
- REQUIRED_MARKERS:
  - "REQUIRED SECTIONS"
- UID_RULE: Artifact UID обязателен.
- CHANGE_ID_RULE: обязателен при изменении структуры шаблона.

---

### 3.2 SYSTEM ENTITIES (ROLES AS DOCS)

#### E01 — ENTITY_PASSPORT
- ARTIFACT_TYPE: ENTITY_PASSPORT
- ARTIFACT_CLASS: ENTITY
- OUTPUT_INTENT: Паспорт сущности (SPC/ORC/ENG/CTL/VAL/QA/XREF).
- MIN_SCHEMA:
  - Header (DOC_CONTROL)
  - IDENTITY (role, owner, status)
  - SCOPE (what it does / does not do)
  - INTERFACES (RAW ONLY)
  - KB SCOPE (inputs / outputs / boundaries + RAW refs)
  - LIMITS (hard constraints)
  - OUTPUTS (allowed artifact types)
  - GATES (what checks it must pass)
- REQUIRED_MARKERS:
  - "INTERFACES (RAW ONLY)"
  - "KB SCOPE"
  - "LIMITS"
- UID_RULE: Entity UID обязателен.
- CHANGE_ID_RULE: обязателен при изменении scope/limits/interfaces.

#### E02 — REALM_README
- ARTIFACT_TYPE: REALM_README
- ARTIFACT_CLASS: DOC
- OUTPUT_INTENT: README для реестра сущностей (realm).
- MIN_SCHEMA:
  - Header (DOC_CONTROL)
  - PURPOSE
  - WHO IS IN THIS REALM
  - HOW TO USE (navigation)
  - CREATE FLOW (if any)
  - RELATED REGISTRIES (RAW ONLY)
- REQUIRED_MARKERS:
  - "HOW TO USE"
- UID_RULE: Artifact UID обязателен.
- CHANGE_ID_RULE: обязателен при изменении состава/правил.

#### E03 — REALM_INDEX
- ARTIFACT_TYPE: REALM_INDEX
- ARTIFACT_CLASS: DOC
- OUTPUT_INTENT: Индекс сущностей realm (список).
- MIN_SCHEMA:
  - Header (DOC_CONTROL)
  - INDEX SCOPE
  - ENTRIES (UID → RAW link)
  - UPDATE POLICY
- REQUIRED_MARKERS:
  - "UPDATE POLICY"
- UID_RULE: Artifact UID обязателен.
- CHANGE_ID_RULE: обязателен при изменении списка.

---

### 3.3 PIPELINES & EXECUTION

#### P01 — ORC_PIPELINE
- ARTIFACT_TYPE: ORC_PIPELINE
- ARTIFACT_CLASS: PIPELINE
- OUTPUT_INTENT: Канонический пайплайн (шаги + handoffs + gates).
- MIN_SCHEMA:
  - Header (DOC_CONTROL)
  - PURPOSE
  - INPUTS (minimum)
  - PIPELINE STEPS (ordered)
  - HANDOFFS (who receives what)
  - GATES PLACEMENT (CTL/VAL/QA order)
  - FAILOVER (missing entity protocol hook)
  - OUTPUTS (artifact types)
- REQUIRED_MARKERS:
  - "PIPELINE STEPS"
  - "GATES PLACEMENT"
  - "FAILOVER"
- UID_RULE: Artifact UID обязателен.
- CHANGE_ID_RULE: обязателен при изменении шагов/гейтов.

#### P02 — ORC_STEP_CONTRACT
- ARTIFACT_TYPE: ORC_STEP_CONTRACT
- ARTIFACT_CLASS: RECORD
- OUTPUT_INTENT: Контракт конкретного шага пайплайна.
- MIN_SCHEMA:
  - Header (DOC_CONTROL)
  - STEP ID + NAME
  - INPUTS → OUTPUTS
  - CONSTRAINTS (links to CTL)
  - VALIDATION (links to VAL/QA)
  - HANDOFF TARGET
- REQUIRED_MARKERS:
  - "INPUTS"
  - "OUTPUTS"
  - "HANDOFF"
- UID_RULE: Artifact UID обязателен.
- CHANGE_ID_RULE: обязателен при изменении входов/выходов.

---

### 3.4 CONTROL / VALIDATION / QA

#### C01 — CTL_POLICY
- ARTIFACT_TYPE: CTL_POLICY
- ARTIFACT_CLASS: DOC
- OUTPUT_INTENT: Политика/лимиты/блокировки для домена.
- MIN_SCHEMA:
  - Header (DOC_CONTROL)
  - POLICY PURPOSE
  - LIMITS & THRESHOLDS
  - BLOCK CONDITIONS
  - EXAMPLES (allowed / blocked)
- REQUIRED_MARKERS:
  - "LIMITS & THRESHOLDS"
  - "BLOCK CONDITIONS"
- UID_RULE: Artifact UID обязателен.
- CHANGE_ID_RULE: обязателен при изменении лимитов.

#### V01 — VAL_CHECK_RULE
- ARTIFACT_TYPE: VAL_CHECK_RULE
- ARTIFACT_CLASS: DOC
- OUTPUT_INTENT: Правило валидации (что проверять).
- MIN_SCHEMA:
  - Header (DOC_CONTROL)
  - CHECK PURPOSE
  - CHECK LOGIC (human-readable)
  - VIOLATION FORMAT (what to record)
  - FIX GUIDE (how to resolve)
  - TEST CASES
- REQUIRED_MARKERS:
  - "VIOLATION FORMAT"
  - "FIX GUIDE"
- UID_RULE: Artifact UID обязателен.
- CHANGE_ID_RULE: обязателен при изменении логики.

#### V02 — VAL_VIOLATION_RECORD
- ARTIFACT_TYPE: VAL_VIOLATION_RECORD
- ARTIFACT_CLASS: RECORD
- OUTPUT_INTENT: Запись нарушения (runtime evidence).
- MIN_SCHEMA:
  - Header (DOC_CONTROL)
  - CONTEXT (task, artifact uid)
  - VIOLATION (rule, severity)
  - EVIDENCE (excerpt / pointer)
  - REQUIRED FIX
  - STATUS (open/closed)
- REQUIRED_MARKERS:
  - "EVIDENCE"
  - "STATUS"
- UID_RULE: Artifact UID обязателен.
- CHANGE_ID_RULE: не обязателен (это запись, не закон).

#### Q01 — QA_GATE
- ARTIFACT_TYPE: QA_GATE
- ARTIFACT_CLASS: DOC
- OUTPUT_INTENT: Гейт приемки (rubric + pass/fail).
- MIN_SCHEMA:
  - Header (DOC_CONTROL)
  - PURPOSE
  - RUBRIC (scoring or checklist)
  - EXEMPLARS (if any)
  - PASS CRITERIA
  - REGRESSION GUARD (if any)
- REQUIRED_MARKERS:
  - "PASS CRITERIA"
- UID_RULE: Artifact UID обязателен.
- CHANGE_ID_RULE: обязателен при изменении критериев.

#### Q02 — QA_ISSUE_RECORD
- ARTIFACT_TYPE: QA_ISSUE_RECORD
- ARTIFACT_CLASS: RECORD
- OUTPUT_INTENT: Запись QA-замечания.
- MIN_SCHEMA:
  - Header (DOC_CONTROL)
  - CONTEXT
  - ISSUE
  - IMPACT
  - FIX REQUEST
  - STATUS
- REQUIRED_MARKERS:
  - "STATUS"
- UID_RULE: Artifact UID обязателен.
- CHANGE_ID_RULE: не обязателен.

---

### 3.5 KNOWLEDGE BASE

#### K01 — KB_MODULE
- ARTIFACT_TYPE: KB_MODULE
- ARTIFACT_CLASS: DOC
- OUTPUT_INTENT: Атомарный модуль знаний.
- MIN_SCHEMA:
  - Header (DOC_CONTROL)
  - KB SCOPE (inputs/outputs/boundaries + RAW refs)
  - CORE CONTENT (rules/methods)
  - CHECKLISTS / GATES (if relevant)
  - XREF (UID-only)
- REQUIRED_MARKERS:
  - "KB SCOPE"
- UID_RULE: Artifact UID обязателен.
- CHANGE_ID_RULE: обязателен при изменении контента.

#### K02 — KB_LIBRARY_ITEM
- ARTIFACT_TYPE: KB_LIBRARY_ITEM
- ARTIFACT_CLASS: DOC
- OUTPUT_INTENT: Элемент библиотеки (пример/паттерн/чеклист/шаблон).
- MIN_SCHEMA:
  - Header (DOC_CONTROL)
  - PURPOSE
  - ITEM BODY
  - USAGE
  - LINKS (RAW only)
- REQUIRED_MARKERS:
  - "USAGE"
- UID_RULE: Artifact UID обязателен.
- CHANGE_ID_RULE: обязателен при изменении тела.

---

### 3.6 PROJECTS & OUTPUT

#### O01 — OUTPUT_PACK
- ARTIFACT_TYPE: OUTPUT_PACK
- ARTIFACT_CLASS: PACK
- OUTPUT_INTENT: Пакет выдачи пользователю (готов к применению).
- MIN_SCHEMA:
  - Header (DOC_CONTROL)
  - PURPOSE
  - CONTENT LIST (what is inside)
  - HOW TO USE (steps)
  - RISKS / LIMITS (if any)
  - VERSION NOTES
- REQUIRED_MARKERS:
  - "HOW TO USE"
- UID_RULE: Artifact UID обязателен.
- CHANGE_ID_RULE: обязателен при изменении состава/инструкций.

#### M01 — MUSIC_TRACK_CARD
- ARTIFACT_TYPE: MUSIC_TRACK_CARD
- ARTIFACT_CLASS: DOC
- OUTPUT_INTENT: Карточка трека (идентичность + цель).
- MIN_SCHEMA:
  - Header (DOC_CONTROL)
  - TRACK IDENTITY (title, order, group/album)
  - TARGET (mood/genre/usage)
  - LYRICS SOURCE (PD/own) + compliance note
  - QA TARGETS (hook timing / repeat guard intent)
  - LINKS (RAW only)
- REQUIRED_MARKERS:
  - "TRACK IDENTITY"
  - "QA TARGETS"
- UID_RULE: Artifact UID обязателен.
- CHANGE_ID_RULE: обязателен при изменении identity/targets.

#### M02 — MUSIC_TRACK_PROMPT
- ARTIFACT_TYPE: MUSIC_TRACK_PROMPT
- ARTIFACT_CLASS: DOC
- OUTPUT_INTENT: Готовый промпт(ы) для генерации.
- MIN_SCHEMA:
  - Header (DOC_CONTROL)
  - PROMPT CONTRACT (structured)
  - NEGATIVE SPEC (if used)
  - VARIANTS (one-axis)
  - COPY BLOCKS (prompt-only sections)
- REQUIRED_MARKERS:
  - "PROMPT CONTRACT"
  - "VARIANTS"
- UID_RULE: Artifact UID обязателен.
- CHANGE_ID_RULE: обязателен при изменении промпта.

#### M03 — MUSIC_TRACK_RELEASE
- ARTIFACT_TYPE: MUSIC_TRACK_RELEASE
- ARTIFACT_CLASS: DOC
- OUTPUT_INTENT: Метаданные релиза и пакет публикации.
- MIN_SCHEMA:
  - Header (DOC_CONTROL)
  - RELEASE METADATA
  - PLATFORM NAMING
  - CREDITS
  - FILE LIST
  - QA SIGNOFF SNAPSHOT (what gates passed)
- REQUIRED_MARKERS:
  - "RELEASE METADATA"
  - "QA SIGNOFF"
- UID_RULE: Artifact UID обязателен.
- CHANGE_ID_RULE: обязателен при изменении метаданных.

---

## 4) MANDATORY HEADER (DOC_CONTROL MINIMUM)
Для любого артефакта из реестра обязателен минимум:
- FILE:
- SCOPE:
- DOC_TYPE:
- STATUS:
- LOCK:
- VERSION:
- UID:
- OWNER:

Если это изменение существующего документа — обязателен CHANGE_NOTE блок с CHANGE_ID.

---

## 5) GAP PROTOCOL FOR NEW ARTIFACT TYPES
Если во время работы нужен новый тип:
1) Declare GAP: "Missing artifact type"
2) Propose new ARTIFACT_TYPE name
3) Provide MIN_SCHEMA + REQUIRED_MARKERS
4) Define UID_RULE + CHANGE_ID_RULE expectations
5) Add record here via change management (не молча)

---

## 6) ENFORCEMENT HOOKS
Этот реестр должен использоваться:
- CTL: чтобы блокировать выпуск артефактов без минимальной структуры
- VAL: чтобы фиксировать нарушение “artifact schema missing”
- QA: чтобы проверять готовность пакета и отсутствие “голого контента”

---

## 7) APPENDIX: RESERVED TYPES (FUTURE)
- ARTIFACT_TYPE: MUSIC_ALBUM_BLUEPRINT
- ARTIFACT_TYPE: MUSIC_GROUP_PASSPORT
- ARTIFACT_TYPE: BRAND_PASSPORT
- ARTIFACT_TYPE: CERT_RECORD
- ARTIFACT_TYPE: AUDIT_RECORD

(Пока зарезервировано, наполнение через change management)
