# CORE STATE ENGINE (CANON)
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/01_CORE_ENGINES/02__CORE_STATE_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 01_CORE_ENGINES
DOC_TYPE: ENGINE
LEVEL: L1
STATUS: ACTIVE
VERSION: 1.0.0
UID: UE.ENG.CORE.STATE.001
OWNER: SYSTEM
ROLE: Defines and enforces canonical system state model + produces authoritative state snapshots and drift reports

---

## 0) ENGINE HEADER (REQUIRED)

ENGINE_NAME: 02__CORE_STATE_ENG
ENGINE_CLASS: CORE
ENGINE_FAMILY: 01_CORE_ENGINES
ENGINE_NUMBER: 02
ENGINE_UID: UE.ENG.CORE.STATE.001
ENGINE_STATUS: ACTIVE

---

## 1) PURPOSE (WHAT THIS ENGINE SOLVES)

Этот движок определяет **каноническое состояние системы “прямо сейчас”** и правила, как оно фиксируется.

Он отвечает за:
- что считается “текущим состоянием” (не история, а факт на данный момент)
- какие параметры состояния обязаны быть явными (канон, версии, блокировки, активные слои, индексы, реестры)
- как выявлять **state drift** (когда фактическая структура/индексы/статусы расходятся с каноном)
- как формировать **state snapshot** — один понятный “слепок” для контроля совместимости

Результат: можно жить и развивать систему без неожиданностей — ты всегда знаешь, “что сейчас реально считается каноном”.

---

## 2) SCOPE & BOUNDARIES (ANTI-CONFLICT)

### IN SCOPE
- Каноническая модель “System State”
- State Snapshot как артефакт (обязательная структура)
- Список “активных” компонентов системы (слои/семейства/ключевые реестры)
- Статусы/локи критических файлов и индексов
- Drift detection: конфликты индексов, битые ссылки, несогласованные версии, лишние “точки истины”

### OUT OF SCOPE
- Определение “кто мы” (это `01__CORE_IDENTITY_ENG`)
- Полный жизненный цикл (рождение→активация→деприкация→архив) — это `03__CORE_LIFECYCLE_ENG`
- Принятие решений о каноне — это governance (Canon Authority / Decision Approval)
- Валидация содержания (язык/факты/научность) — это VAL/QA

---

## 3) MINI-CONTRACT (MANDATORY)

CONSUMES:
- SYS_IDENTITY (из Core Identity Engine / root index section)
- CANON_INDEX_SET (набор канонических индексов по слоям)
- REGISTRY_SET (ключевые реестры/БД-реестры типов/доков)
- REPO_TREE_SNAPSHOT (фактическая структура путей)

PRODUCES:
- SYS_STATE_MODEL (определение “что такое состояние” + поля)
- SYS_STATE_SNAPSHOT (слепок текущего состояния системы)
- SYS_STATE_DRIFT_REPORT (отчёт о расхождениях/ошибках/блокерах)

DEPENDS_ON:
- 01_CORE_ENGINES/01__CORE_IDENTITY_ENG (HARD)
- 00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG (HARD)
- 00_GOVERNANCE_ENGINES/03__RULE_HIERARCHY_ENG (HARD)
- 00_GOVERNANCE_ENGINES/05__CONSISTENCY_ENG (HARD)
- 00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG (SOFT)
- 00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG (SOFT)

OUTPUT_TARGET:
- 00_INDEX/00__ROOT_INDEX.md (раздел SYSTEM_STATE)
- 08_DATABASES/DB__RELEASE_LOG.md (state snapshot pointer + compatibility line)
- 99_LOGS/LOG__AUDIT.md (обязательная запись о state snapshot / drift)

---

## 4) STATE MODEL (CANONICAL DEFINITION)

### 4.1 What is “System State”
System State = **наблюдаемое текущее каноническое положение** системы, определённое:
- каноническими индексами (existence via index)
- статусами и блокировками критических документов
- активными семействами сущностей (ENG/ORC/SPC/CTL/VAL/QA/KB/PRJ/AST/DB/LOG)
- актуальными версиями ключевых реестров

State не равен “истории”. История живёт в LOGS и governance.

### 4.2 State Layers (min)
- STATE.CANON: корневой канон + master indexes
- STATE.STRUCTURE: слои/папки/канонические пути
- STATE.REGISTRIES: DB/registries (doc/entity/artifact/track types)
- STATE.ENTITIES: какие классы сущностей активны (ENG/ORC/…)
- STATE.PROJECTS: активные правила проектов (PRJ governance)
- STATE.ASSETS: активные правила ассетов (AST governance)
- STATE.LOGGING: аудит/изменения и доступность логов

---

## 5) INPUTS (STRICT)

### 5.1 Required inputs
- SYS_IDENTITY  
  WHY: state невозможен без identity (что считать системой).
- CANON_INDEX_SET  
  WHY: existence via index определяет состав канона.
- REGISTRY_SET  
  WHY: типы/реестры задают допустимые сущности и документы.
- REPO_TREE_SNAPSHOT  
  WHY: нужен факт структуры для drift detection.

### 5.2 Optional inputs
- VERSION_MEMORY (если ведётся отдельно)  
  WHEN: нужна сверка “какая версия считалась текущей”.
- MIGRATION_NOTES / LEGACY_MAP  
  WHEN: идут переименования/сдвиги путей.

### 5.3 Forbidden inputs
- Любые списки “как было раньше” без фиксации в логах  
  WHY: state ≠ история.
- “Сторонние индексы” не зарегистрированные в каноне  
  WHY: создают ложное состояние.

---

## 6) OUTPUTS (STRICT)

### 6.1 SYS_STATE_MODEL
- TYPE: SYSTEM_SPEC
- MIN_FIELDS:
  - STATE_FIELDS (полный список полей)
  - SEVERITY_SCALE (OK|WARN|BLOCK)
  - SOURCE_OF_TRUTH (индексы)
  - UPDATE_RULES (как обновлять state snapshot)
- FORMAT: Markdown, sectioned

### 6.2 SYS_STATE_SNAPSHOT
- TYPE: SYSTEM_SNAPSHOT
- MIN_FIELDS:
  - TIMESTAMP
  - CANON_ROOT
  - ACTIVE_INDEXES (list)
  - ACTIVE_LAYERS (list)
  - CRITICAL_FILES_STATUS (status/lock/version)
  - REGISTRIES_VERSIONS (list)
  - COMPATIBILITY_TAG (например: “STATE_OK”)
- FORMAT: Markdown record (строгие ключи)
- STORAGE:
  - Root index section `SYSTEM_STATE`
  - pointer в release log

### 6.3 SYS_STATE_DRIFT_REPORT
- TYPE: SYSTEM_REPORT
- MIN_FIELDS:
  - TIMESTAMP
  - DRIFTS (list)
  - SEVERITY
  - BLOCKERS (list)
  - FIX_ACTIONS (list)
- STORAGE:
  - LOG__AUDIT (обязательно)
  - при необходимости отдельный отчётный файл

---

## 7) OPERATION (ALGORITHM / STEPS)

1) **Load SYS_IDENTITY**
   - взять CANON_ROOT, existence rule, base paths, law hierarchy

2) **Resolve Canon Index Set**
   - собрать список канонических индексов слоёв:
     - root index
     - master registries/indexes (ENG/ORC/SPC/CTL/VAL/QA/KB/PRJ/AST/DB)
   - убедиться: каждый “существующий компонент” присутствует в своём индексе

3) **Extract Critical File State**
   - для каждого критического файла: STATUS, LOCK, VERSION, UID (если обязателен)
   - проверить “anti-duplication” по статусам/локам (не два раза в документе)

4) **Registry & DB health**
   - сверить наличие ключевых DB файлов:
     - doc registry / entity types / artifact types / track types / release log
   - сопоставить версии/ссылки (если ведутся)

5) **Detect Drift**
   - DRIFT TYPES:
     - D1: index references missing file (broken canon)
     - D2: file exists but not in index (non-canon stray)
     - D3: duplicate canon root claim
     - D4: status/lock illegal value
     - D5: conflicting versions across critical registries
   - присвоить severity: OK/WARN/BLOCK

6) **Emit Snapshot**
   - сформировать SYS_STATE_SNAPSHOT
   - сформировать SYS_STATE_DRIFT_REPORT

7) **Governance logging**
   - запись в audit log обязательно:
     - snapshot created/updated
     - drift findings (если есть)
   - если BLOCK: инициировать canon authority / change control

Return:
- OK: можно продолжать разработку без стопов
- WARN: можно продолжать, но есть “долги”
- BLOCK: нельзя продолжать, канон сломан (лечить через governance)

---

## 8) CONSTRAINTS (MUST ALWAYS HOLD)

- S1 (HARD): **Identity must exist**  
  Без SYS_IDENTITY state не считается.
- S2 (HARD): **Existence via index**  
  Если сущность/компонент не зарегистрирован — он не часть состояния.
- S3 (HARD): **No duplicate canon roots**  
  Только один CANON_ROOT.
- S4 (HARD): **Critical indexes must be resolvable**  
  Критический индекс не может ссылаться на несуществующий файл.
- S5 (HARD): **Allowed STATUS/LOCK**  
  Только разрешённые значения.
- S6 (SOFT): **Version coherence**  
  Версии реестров должны быть согласованы (иначе WARN, при критичности BLOCK).

---

## 9) VALIDATION & QUALITY GATES

### Must-pass (BLOCK if fail)
- G1: SYS_IDENTITY present + CANON_ROOT resolvable
- G2: Root index asserts existence rule explicitly
- G3: All critical indexes in CANON_INDEX_SET exist
- G4: No second canonical entrypoint declared
- G5: STATUS/LOCK fields are from allowed sets

### Warnings
- W1: Non-canon files detected (exist but not indexed)
- W2: Version mismatches in registries, but non-breaking
- W3: Legacy paths referenced without legacy map note

---

## 10) FAILURE MODES (KNOWN RISKS)

- FM1: “Silent drift” после массовых правок  
  SYMPTOM: ссылки битые, но никто не заметил  
  FIX: запуск Consistency + State drift report, затем change control
- FM2: Удалили “посторонние индексы”, но остались ссылки на них  
  SYMPTOM: индекс ссылается на несуществующий файл  
  FIX: обновить канонический индекс, удалить ссылки, audit запись
- FM3: Дублирование “master registry” в нескольких местах  
  SYMPTOM: два файла объявляют себя точкой истины  
  FIX: Canon Authority decision + deprecate лишний

---

## 11) DEPENDENCIES & XREF (MANDATORY)

### Direct dependencies
- 01_CORE_ENGINES/01__CORE_IDENTITY_ENG -> TYPE:HARD -> WHY: state anchored to identity
- 00_GOVERNANCE_ENGINES/05__CONSISTENCY_ENG -> TYPE:HARD -> WHY: detects structural contradictions
- 00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG -> TYPE:HARD -> WHY: snapshot/drift must be recorded
- 00_GOVERNANCE_ENGINES/03__RULE_HIERARCHY_ENG -> TYPE:HARD -> WHY: state cannot violate law ordering

### Cross-layer stitches
- CTL readiness check consumes SYS_STATE_DRIFT_REPORT:
  - если severity=BLOCK -> стоп пайплайна
- ORC bootstrap pipeline:
  - Identity → State → Lifecycle (core chain)
- DB release log stores current snapshot pointer/compatibility tag
- VAL validators can use constraints S1–S6 for automated checks

---

## 12) RECORDS (AUDIT / CHANGE)

Обязательные записи в `LOG__AUDIT.md`:
- “SYS_STATE_SNAPSHOT created/updated” + timestamp
- “SYS_STATE_DRIFT_REPORT severity=...” (если не OK)
- при BLOCK:
  - ссылка на Canon Authority / Change Control action

---

## 13) VERSIONING POLICY

- Minor update (1.0.x):
  - уточнение полей snapshot, добавление warning checks
- Breaking update (1.x → 2.0):
  - смена смысла state model / severity rules / источников истины
- Любая смена источника истины (CANON_INDEX_SET definition) = breaking + governance запись

---

## 14) EXAMPLES (MINIMUM 1)

### Example A — OK state
INPUT:
- SYS_IDENTITY закреплён в root index
- Все master indexes существуют и актуальны

OUTPUT:
- SYS_STATE_SNAPSHOT:
  - SEVERITY: OK
  - ACTIVE_LAYERS: [SYSTEM_LAW, STANDARDS, SYSTEM_ENTITIES, KB, PROJECTS, ASSETS, DB, LOGS]
- SYS_STATE_DRIFT_REPORT:
  - DRIFTS: []
  - SEVERITY: OK

### Example B — BLOCK drift
INPUT:
- индекс ссылается на файл, которого больше нет (удалили/переименовали)

OUTPUT:
- DRIFT_REPORT:
  - DRIFTS: [D1 broken index reference]
  - SEVERITY: BLOCK
  - FIX_ACTIONS:
    - update canon index link
    - record audit entry
    - (если спор) canon authority decision

---

## FINAL RULE (LOCK)

LOCK: FIXED
