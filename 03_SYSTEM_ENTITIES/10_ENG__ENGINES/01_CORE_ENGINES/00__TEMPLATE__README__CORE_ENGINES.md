# ENG FAMILY README — CORE_ENGINES (TEMPLATE v2)
FILE: 00__TEMPLATE__README__CORE_ENGINES.md

SCOPE: Universe Engine
LAYER: ENG
DOC_TYPE: TEMPLATE
ENTITY_KIND: GENERIC
PROJECT_SCOPE: GLOBAL
OUTPUT_LEVEL: N/A
ID: ENG.TPL.FAMILY.CORE.README
STATUS: ACTIVE
VERSION: 2.0
ROLE: Realm law + role map + interfaces + required REG/XREF + canon order for CORE family.

---

## 0) PURPOSE (REALM LAW)

Этот README — закон семейства **CORE_ENGINES**.
CORE отвечает за “базовую сущность системы”:
- кто мы / где мы / что живо
- как устроено состояние, идентичность и жизненный цикл
- минимальная модель существования сущностей и их статусов (без доменных деталей)

### EXISTENCE RULE (FAMILY)
> Любая сущность, не проходящая CORE-минимум (identity/state/lifecycle), считается incomplete для системы.

---

## 1) FAMILY IDENTITY (MANDATORY)

FAMILY_NAME: CORE_ENGINES  
FAMILY_CODE: CORE  
FAMILY_CLASS: CORE  
FAMILY_LEVEL: L1  

FAMILY_PATH: `10_ENG__ENGINES/01_CORE_ENGINES/`  
README_FILE: `00__README__CORE_ENGINES.md`

---

## 2) OWNERSHIP BOUNDARIES (ANTI-DUPLICATION)

### 2.1 OWNS (this family owns)
- Минимальная модель сущности: ID, kind, owner, status, lock, version
- Core Identity: “кто/что это” в системе (без лора/характера/мира)
- Core State: текущее состояние сущности (alive/dead/active/archived/etc.)
- Core Lifecycle: переходы состояния, правила жизненного цикла
- Базовые свойства трассируемости (provenance hooks), но не конкретные XREF записи (это governance/xref)

### 2.2 DOES NOT OWN (belongs elsewhere)
- Лор, смысл, сюжет, темы → DOMAIN_NARRATIVE / EXPRESSION
- Психология, мотивация, речь → DOMAIN_CHARACTER
- Законы мира, цивилизации, экономика → DOMAIN_WORLD
- Жанр/тон/символизм → GENRE_STYLE
- Формат выпуска (книга/сериал) → PRODUCTION_FORMAT
- Продакшн визуал/монтаж/звук → KNOWLEDGE_PRODUCTION
- Глубокая музыка → SOUND_MUSIC
- Решения “что канон” и change control → GOVERNANCE

Rule:
> CORE задаёт “скелет существования”, но не наполняет смыслом/историей.

---

## 3) ROLE MAP (MANDATORY)

Роли движков внутри CORE:

- FOUNDATION — модель идентичности/сущности
- BUILDER — формирует представление “state snapshot”
- VALIDATOR — проверяет корректность переходов и обязательных полей
- BRIDGE — связывает core-слой с domain-слоями (минимально)
- OUTPUT — выдаёт core-card/manifest сущности как основу для других движков

### 3.1 Role completeness rule
> CORE обязан иметь FOUNDATION и OUTPUT.  
> VALIDATOR обязателен для контроля состояния/переходов.

### 3.2 Role map table (canonical for this family)
| Engine NN | Engine Name | ROLE_IN_FAMILY | PIPELINE_STAGE |
|---|---|---|---|
| 01 | Core Identity Engine | FOUNDATION | DEFINE |
| 02 | Core State Engine | BUILDER | BUILD |
| 03 | Core Lifecycle Engine | VALIDATOR | CHECK |

Примечание:
> OUTPUT для CORE проявляется как produced artifact “CORE_CARD / CORE_MANIFEST” каждым движком по необходимости (см. интерфейсы).

---

## 4) FAMILY OUTPUT POLICY (WORKSHOP L0–L3) — MANDATORY

CORE работает **на сущностях** всех видов, поэтому по умолчанию пишет внутрь entity folders.

DEFAULT_ENTITY_KIND: GENERIC (настраивается per entity)
DEFAULT_OUTPUT_LEVEL: L1_DRAFT (по умолчанию)

DEFAULT_PROJECT_OUTPUT_ROOT:
- `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/`

DEFAULT_CATEGORY_PATH:
- зависит от ENTITY_KIND (CHR/LOC/OBJ/...)

DEFAULT_FILES (recommended):
- L0: `01_INTAKE_L0/00__CORE_INTAKE.md`
- L1: `02_DRAFT_L1/00__CORE_DRAFT.md`
- L2: `03_CANON_L2/00__CORE_CANON.md` (или включить как секцию в `00__CANON.md`)
- L3: `04_OUTPUT_L3/00__CORE_MANIFEST.md` (если нужно)

### 4.1 Level routing rules
- L0: сырьё/наброски core данных
- L1: структурный черновик “кто/что это” + state snapshot
- L2: утверждённый core-card (минимальный канон существования)
- L3: manifest для продакшна/инструментов (если нужно)

---

## 5) REQUIRED REGISTRIES (MANDATORY)

CORE требует регистрации сущностей в проекте.

REQUIRED_REGISTRIES (project-scoped):
- Entities Registry:
  - `REG.PRJ.<PROJECT_ID>.ENTITIES`

Optional:
- Canon artifacts registry (если core фиксируется отдельным файлом в L2):
  - `REG.PRJ.<PROJECT_ID>.CANON_L2`

Rule:
> Любая сущность обязана быть в Entities Registry.  
> Любой отдельный core canon file в L2 должен быть зарегистрирован как canon artifact.

---

## 6) REQUIRED XREF INDEXES (MANDATORY)

CORE обязателен к связям “сущность существует / связана / произошла из”.

REQUIRED_XREF (project-scoped):
- Entity graph:
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__ENTITY_GRAPH.md`
- Provenance:
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__PROVENANCE.md`
- Canon refs (если L3 outputs ссылаются на core canon):
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CANON_REFS.md`

Hard rule:
> Если core выводит отдельный L2 файл — provenance обязателен (DERIVED_FROM).

---

## 7) INTERFACES (INPUT / OUTPUT ARTIFACT TYPES)

### 7.1 INPUT ARTIFACT TYPES
- ENTITY_INTAKE (raw)
- ENTITY_METADATA
- PROJECT_CONTEXT
- EXISTING_ENTITY_REG_ENTRY (if exists)

### 7.2 OUTPUT ARTIFACT TYPES
- CORE_CARD (identity)
- STATE_SNAPSHOT (state)
- LIFECYCLE_RULESET (transitions)
- CORE_MANIFEST (optional L3)

---

## 8) TEMPLATES (MANDATORY BLOCK)

Base templates:
- FAMILY README TEMPLATE (base) — `10_ENG__ENGINES/00__TEMPLATE__README__FAMILY__ENG.md`
- ENGINE TEMPLATE (base) — `10_ENG__ENGINES/00__TEMPLATE__ENGINE__ENG.md`

Family overlays:
- README TEMPLATE (this file) — `10_ENG__ENGINES/01_CORE_ENGINES/00__TEMPLATE__README__CORE_ENGINES.md`
- ENGINE TEMPLATE (family) — `10_ENG__ENGINES/01_CORE_ENGINES/00__TEMPLATE__ENGINE__CORE_ENGINES.md`

---

## 9) CANON ORDER (MANDATORY)

00 — README (Realm)  
01 — Core Identity Engine  
02 — Core State Engine  
03 — Core Lifecycle Engine  

Rule:
> Номер в списке = номер в имени файла.

---

## 10) GOVERNANCE COMPATIBILITY (MANDATORY)

Изменения core-модели (обязательные поля, статусы, переходы) считаются системным изменением:
- через change control
- с audit log записью WHY
- с versioning/memory фиксацией

---

## FINAL RULE (LOCK)

> CORE — минимальная “конституция существования” для сущностей проекта.  
> Без core identity/state/lifecycle сущность не может стать L2_CANON.

OWNER: Universe Engine  
LOCK: FIXED
