# CORE LIFECYCLE ENGINE (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/01_CORE_ENGINES/03__CORE_LIFECYCLE_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: ENGINE
FAMILY: 01_CORE_ENGINES
CLASS: CORE (L1)
LEVEL: L1
STATUS: ACTIVE
LOCK: OPEN
VERSION: 0.1.0
UID: UE.ENG.CORE.LIFECYCLE.001
OWNER: SYSTEM
ROLE: Defines the canonical lifecycle model for canon artifacts and system entities: allowed states, transitions, required records, and blockers. Prevents “half-born” canon and silent deprecations.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Lifecycle model standardized: states, transition law, deprecation/archival protocol, minimal lifecycle records, and S0 blockers."
- REASON: "Stop unmanaged renames/deletes, orphan artifacts, and drifting status/lock semantics."
- IMPACT: "Every canon object gets a traceable birth → active → change → deprecate → archive path."
- CHANGE_ID: UE.CHG.2026-01-08.CORE.LC.001

---

## 0) PURPOSE (LAW)

Core Lifecycle Engine — закон “как живут объекты” в системе.

Он фиксирует:
- допустимые **состояния жизненного цикла** (lifecycle states)
- допустимые **переходы** (transitions) и что для них обязательно
- **минимальный набор записей**, без которых переход недействителен
- правила **deprecate/archive/migration**, чтобы канон не ломался

Ключевая мысль:
> **STATUS/LOCK** — это *метаданные документа*,  
> а **LIFECYCLE** — это *жизненный цикл объекта/артефакта/сущности* как единицы канона.

---

## 1) SCOPE (WHAT THIS ENGINE GOVERNS)

Governs (in-scope):
- Canon artifacts: LAW / STANDARD / INDEX / REGISTRY / ENGINE / TEMPLATE / XREF maps
- System entities (ENG/ORC/SPC/CTL/VAL/QA) как объекты канона
- Project artifacts (PRJ L0–L3 outputs) — только на уровне правил переходов и записей

Out-of-scope (non-goals):
- “кто главный” и приоритет правил (Rule Hierarchy)
- “что есть канон” (Canon Authority)
- проверка структуры/имен/UID (Consistency делает; Lifecycle требует прохождения)
- текущее здоровье системы (Core State Engine)
- факт- и качество-проверки (VAL/QA)

---

## 2) MINI-CONTRACT (MANDATORY)

CONSUMES:
- CANON_OBJECT (path + UID + declared role)
- CURRENT_METADATA (STATUS/LOCK/VERSION header snapshot)
- STATE_SNAPSHOT (from Core State Engine, optional but recommended)
- CHANGE_PACKAGE? (required if transition touches FIXED/INDEX/LAW or is MIGRATION)
- IMPACT_REPORT? (required for MAJOR/MIGRATION)
- RISK_REPORT? (required for risky transitions)
- DEPENDENCY_CONTEXT? (if object has downstream dependents)

PRODUCES:
- LIFECYCLE_STATE (LC_STATE)
- LIFECYCLE_EVENT (LC_EVENT record)
- TRANSITION_PLAN (LC_PLAN)
- MIGRATION_MAP? (if rename/move/delete)
- AUDIT_LOG_ENTRY (required for canon transitions)
- VERSION_MEMORY_ENTRY? (required if versions/paths changed)

DEPENDS_ON:
- 01_CORE_ENGINES/01__CORE_IDENTITY_ENG
- 01_CORE_ENGINES/02__CORE_STATE_ENG
- 00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG
- 00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG
- 00_GOVERNANCE_ENGINES/03__RULE_HIERARCHY_ENG
- 00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG
- 00_GOVERNANCE_ENGINES/05__CONSISTENCY_ENG
- 00_GOVERNANCE_ENGINES/06__DEPENDENCY_REGISTRY_ENG
- 00_GOVERNANCE_ENGINES/10__VERSIONING_MEMORY_ENG

OUTPUT_TARGET:
MANDATORY:
- 99_LOGS/LOG__AUDIT.md (LC_EVENT + summary)
- 99_LOGS/LOG__CHANGES.md (if transition came from change package)
OPTIONAL:
- 08_DATABASES/DB__RELEASE_LOG.md (release markers)
- Entity passport (if entity-type supports passport storage)

---

## 3) CORE DEFINITIONS

- **Canon Object** — единица канона, которая обязана быть управляемой индексами/правилами.
- **Lifecycle State** — состояние объекта в процессе жизни (не путать с STATUS документа).
- **Transition** — допустимый переход между lifecycle states.
- **Gate** — обязательная проверка/условие перед переходом.
- **Downstream** — объекты, зависящие от данного (dependency registry).

---

## 4) LIFECYCLE STATES (STRICT SET)

LC_STATE:
- `BIRTH`        — объект создан/зарегистрирован, ещё не введён в эксплуатацию
- `ACTIVE`       — объект используется как часть канона/пайплайна
- `MAINTENANCE`  — объект активен, но допускает корректировки/улучшения
- `FROZEN`       — объект активен, но запрещены смысловые изменения (только patch/clarity)
- `DEPRECATED`   — объект заменён, использование запрещено/не рекомендуется, но ещё нужен для совместимости
- `ARCHIVED`     — объект выведен из обращения и хранится только как история
- `RETIRED`      — объект удалён из актуальной структуры (оставлен только через ссылки на архив/историю)

Правило:
> Canon object не может “исчезнуть” без перехода через `DEPRECATED`/`ARCHIVED`/`RETIRED` и записей.

---

## 5) TRANSITIONS (ALLOWED GRAPH)

Allowed transitions:
- BIRTH → ACTIVE
- ACTIVE → MAINTENANCE
- MAINTENANCE → ACTIVE
- ACTIVE/MAINTENANCE → FROZEN
- FROZEN → MAINTENANCE (только через approval, если FIXED-семантика нарушена)
- ACTIVE/MAINTENANCE/FROZEN → DEPRECATED
- DEPRECATED → ARCHIVED
- ARCHIVED → RETIRED (только если допускается удаление физического файла или вынос в history storage)

Forbidden (invalid):
- BIRTH → DEPRECATED (нельзя “родить и сразу похоронить” — значит ошибочная регистрация)
- ACTIVE → RETIRED (нельзя удалять активный объект без deprecate+archive path)
- Любой переход, если Core State = BLOCK (см. раздел 9)

---

## 6) TRANSITION GATES (MANDATORY ORDER)

G0 — Identity Gate (always)
- объект должен иметь корректный путь/UID/роль (baseline invariants)

G1 — Existence Gate (always)
- объект обязан быть зарегистрирован в каноническом индексе (если он канон)
- иначе: либо это non-canon (не управляем), либо ошибка (stop)

G2 — Consistency Gate (always for canon)
- naming/UID/version header legality (Consistency Engine)

G3 — Dependency Gate (conditional)
- если есть downstream dependents:
  - нужен план совместимости
  - запись в dependency registry обязательна

G4 — Change Control Gate (conditional)
- если затрагиваем FIXED/LAW/INDEX или делаем MIGRATION:
  - нужен CHANGE_PACKAGE (CHG) и прохождение pipeline

G5 — Authority/Approval Gate (conditional)
- если переход меняет поведение, ломает совместимость, или трогает FIXED:
  - требуется approval (Decision Approval + Canon Authority)

G6 — Audit + Memory Gate (always for canon transitions)
- LC_EVENT обязателен
- если менялись версии/пути: VERSION_MEMORY_ENTRY обязателен

Ни один gate нельзя “перепрыгнуть”.

---

## 7) REQUIRED RECORDS (MINIMUM SCHEMAS)

### 7.1 LIFECYCLE_EVENT (LC_EVENT) — mandatory for any canon transition
LC_EVENT:
- DATE:
- OBJECT_PATH:
- OBJECT_UID:
- FROM_STATE:
- TO_STATE:
- TYPE: PATCH | MINOR | MAJOR | MIGRATION | EMERGENCY
- REASON:
- IMPACT: short
- COMPATIBILITY: backward|breaking|mixed|n/a
- DEPENDENTS: none|listed
- REQUIRED_GATES: [list]
- LINKS: [indexes/records]
- APPROVAL_REF?: (if required)
- CHG_REF?: (if change package exists)

### 7.2 TRANSITION_PLAN (LC_PLAN) — mandatory for MAJOR/MIGRATION/DEPRECATION
LC_PLAN:
- TARGET_STATE:
- STEPS: [ordered]
- AFFECTED_INDEXES: [list]
- DEPENDENCY_UPDATES: [list]
- MIGRATION_MAP?: (if rename/move/delete)
- ROLLBACK_PLAN?: (if hard/breaking)
- OWNER:

### 7.3 MIGRATION_MAP — mandatory for rename/move/delete
MIGRATION_MAP:
- OLD_PATH:
- NEW_PATH: (or RETIRED/DELETED)
- OLD_UID:
- NEW_UID: (usually same; change requires justification)
- WHY:
- REFERENCES_TO_UPDATE: [indexes/xrefs/registries]
- MEMORY_REF: required

---

## 8) STATUS/LOCK vs LIFECYCLE (NO CONFUSION LAW)

- `STATUS` и `LOCK` — свойства **файла документа** (header).
- `LC_STATE` — состояние **канонического объекта** (может быть документом, но смысл шире).

Пример:
- Документ может иметь `STATUS: ACTIVE`, но объект может быть `LC_STATE: MAINTENANCE`.
- Документ может быть `LOCK: FIXED`, но объект может быть `LC_STATE: FROZEN` (жёстко).

Rule:
> Нельзя использовать STATUS вместо LIFECYCLE, иначе всё начнёт “гулять”.

---

## 9) SYSTEM STATE PRECONDITION (HARD)

Если `Core State Engine` выдаёт `SEVERITY: BLOCK`:
- любые lifecycle transitions для канона **запрещены**
- допускается только emergency fix (по Change Control emergency path)

Если `WARN`:
- transitions разрешены, но LC_EVENT обязан отметить WARN.

---

## 10) DEPRECATION LAW (NO SILENT DEATH)

DEPRECATED означает:
- есть **замена** (successor) или причина, почему замены нет
- индекс существования обновлён так, чтобы:
  - старый объект либо остаётся как deprecated, либо переезжает в архив, но не пропадает
- есть migration mapping (если переезд)
- dependents либо мигрированы, либо явно закреплены на deprecated объекте (временно)

Required fields on deprecate:
- SUCCESSOR_PATH? (если есть)
- MIGRATION_WINDOW (если используется)
- COMPATIBILITY_NOTE

---

## 11) ARCHIVE / RETIRE LAW

ARCHIVED:
- объект больше не используется пайплайнами
- остаётся доступным для истории и ссылок (raw-links, если требуется)

RETIRED:
- допускается только если:
  - ссылки закрыты/переведены
  - migration map записан
  - индексы не содержат ссылок на retired путь
  - memory содержит mapping, чтобы навигация не ломалась

---

## 12) S0 BLOCKERS (ABSOLUTE)

S0-1: Canon object не зарегистрирован в каноническом индексе, но объявлен каноном
S0-2: Переход выполнен без LC_EVENT
S0-3: Rename/move/delete без MIGRATION_MAP + memory entry
S0-4: Есть downstream dependents, но нет dependency updates
S0-5: Core State = BLOCK, но transition выполнен (policy breach)
S0-6: Два объекта конкурируют за одну роль “single source of truth” без решения authority

Если S0 → STOP / REVERT / EMERGENCY only.

---

## 13) HOW THIS ENGINE FITS THE SYSTEM (INTEGRATION)

- Core Identity: задаёт инварианты и базовую идентичность системы
- Core State: говорит “можно ли сейчас менять”
- Change Control: задаёт pipeline для опасных/канон-правок
- Consistency: проверяет легальность структуры/шапок/UID/версий
- Dependency Registry: фиксирует downstream и миграции зависимостей
- Audit Log + Versioning Memory: делает жизнь объекта трассируемой

Lifecycle — это **единый закон управления жизнью**, чтобы канон не превращался в кладбище без табличек.

---

## 14) REFERENCES (RAW ONLY)

CORE:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/01_CORE_ENGINES/01__CORE_IDENTITY_ENG.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/01_CORE_ENGINES/02__CORE_STATE_ENG.md

GOVERNANCE:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/05__CONSISTENCY_ENG.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/06__DEPENDENCY_REGISTRY_ENG.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/10__VERSIONING_MEMORY_ENG.md

STANDARDS / LAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/04__CANON_PROTOCOL.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md

--- END.
