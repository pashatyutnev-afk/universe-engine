# ENG FAMILY README — CORE_ENGINES (TEMPLATE v2)
FILE: 00__TEMPLATE__README__CORE_ENGINES.md

SCOPE: Universe Engine
LAYER: ENG
DOC_TYPE: TEMPLATE
ENTITY_GROUP: ENGINES (ENG)
TEMPLATE_KIND: FAMILY_README_OVERLAY
LEVEL: L1
STATUS: ACTIVE
VERSION: 2.0
ROLE: Family overlay for CORE realm README. Compatible with base family template v2 and base engine template v2.

LOCK: FIXED
OWNER: Universe Engine

---

## 0) PURPOSE (REALM LAW)

Семейство **CORE_ENGINES** — базовая идентичность и “живое состояние” системы.
CORE задаёт фундаментальные ответы:
- кто/что является системой (identity)
- что сейчас считается “живым” и актуальным (state)
- как сущности рождаются/живут/умирают/фиксируются (lifecycle)

EXISTENCE RULE:
> Любая сущность/проект без CORE ID и состояния считается неинициализированной (не входит в активный канон).

---

## 1) FAMILY IDENTITY (MANDATORY)

FAMILY_NAME: CORE_ENGINES
FAMILY_CODE: CORE
FAMILY_CLASS: CORE
FAMILY_LEVEL: L1

FAMILY_PATH:
`03_SYSTEM_ENTITIES/10_ENG__ENGINES/01_CORE_ENGINES/`

README_FILE:
`00__README__CORE_ENGINES.md`

---

## 2) OWNERSHIP BOUNDARIES (ANTI-DUPLICATION)

### 2.1 OWNS
- Core Identity: минимальная модель “кто мы / где мы / что считается системой”
- Core State: актуальное состояние системы/проекта/сущностей (активно/архив/черновик/канон)
- Core Lifecycle: жизненный цикл сущностей и артефактов (создание → draft → canon → output → archive)

### 2.2 DOES NOT OWN (hard boundaries)
- сюжет/сцены/драматургия (Narrative)
- психология/мотивы персонажей (Character)
- законы мира/цивилизации (World)
- стиль/тон/атмосфера как художественный закон (Style)
- формат выпуска и deliverables (Format)
- производство медиа-артефактов (Production)
- глубокая музыка (Music)
- approvals и законность изменений (Governance)
Rule:
> CORE определяет “кто и в каком состоянии”, но не создаёт доменный контент.

---

## 3) ROLE MAP (MANDATORY)

- FOUNDATION: identity/state/lifecycle как базовая сетка всей системы
- VALIDATOR: проверка существования ID/state перед любыми L2/L3 операциями
- OUTPUT: core registries (system/project/entity)

### 3.1 Canonical role map table
| Engine NN | Engine Name | ROLE_IN_FAMILY | PIPELINE_STAGE |
|---|---|---|---|
| 01 | Core Identity Engine | FOUNDATION | DEFINE |
| 02 | Core State Engine | VALIDATOR | CHECK |
| 03 | Core Lifecycle Engine | OUTPUT | PRODUCE |

---

## 4) FAMILY OUTPUT POLICY (WORKSHOP L0–L3) — MANDATORY

CORE outputs live in two zones:

### A) SYSTEM scope (canonical)
- базовые core-laws и system registries:
  - `03_SYSTEM_ENTITIES/00_REG__REGISTRIES/REG.SYS.CORE.md` (если используете)
  - `03_SYSTEM_ENTITIES/` (core rules only; governance compatible)

### B) PROJECT / ENTITY scope (default operational)
- `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/<DOMAIN>/<ENTITY_ID>/<LEVEL_FOLDER>/`
- `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/03_PROJECT__L1/` etc (project-scope)

Rule:
> Перед созданием L2 canon и L3 outputs CORE State должен быть валиден (entity exists + status allowed).

---

## 5) REQUIRED REGISTRIES (MANDATORY)

Project-scoped (recommended minimum):
- `00_REG__REGISTRIES/REG.PRJ.<PROJECT_ID>.ENTITIES.md`
- `00_REG__REGISTRIES/REG.PRJ.<PROJECT_ID>.CANON_L2.md`
- `00_REG__REGISTRIES/REG.PRJ.<PROJECT_ID>.OUTPUT_L3.md`

System-scoped (optional if you maintain system-wide core):
- `00_REG__REGISTRIES/REG.SYS.ENTITIES.md`
- `00_REG__REGISTRIES/REG.SYS.CORE_STATE.md`
- `00_REG__REGISTRIES/REG.SYS.LIFECYCLE.md`

---

## 6) REQUIRED XREF INDEXES (MANDATORY)

Project-scoped:
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CANON_REFS.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__DEPENDENCIES.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__PROVENANCE.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__ENTITY_GRAPH.md`

System-scoped (optional):
- `90_XREF__CROSSREF/XREF__CANON_REFS.md`
- `90_XREF__CROSSREF/XREF__PROVENANCE.md`

---

## 7) TEMPLATES (MANDATORY BLOCK)

Base templates:
- ENGINE TEMPLATE (base) — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00__TEMPLATE__ENGINE__ENG.md
- FAMILY README TEMPLATE (base) — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00__TEMPLATE__README__FAMILY__ENG.md

Family overlays:
- ENGINE TEMPLATE (family) — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/01_CORE_ENGINES/00__TEMPLATE__ENGINE__CORE_ENGINES.md
- README TEMPLATE (family) — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/01_CORE_ENGINES/00__TEMPLATE__README__CORE_ENGINES.md

Rule:
> Family README must contain both base + overlay template links.

---

## 8) CANON ORDER (MANDATORY)

00 — README (Realm)  
01 — Core Identity Engine  
02 — Core State Engine  
03 — Core Lifecycle Engine  

---

## 9) GOVERNANCE COMPATIBILITY (MANDATORY)

Core rules and system registries are canon-sensitive.
Any changes must go through governance pipeline:
- Change Control
- Canon Authority
- Versioning & Memory
- Audit Log

---

## 10) RAW LINK (MANDATORY)

RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/01_CORE_ENGINES/00__TEMPLATE__README__CORE_ENGINES.md

---

## FINAL RULE (LOCK)

> CORE defines identity/state/lifecycle and must be consulted before producing L2 canon or L3 output.

LOCK: FIXED
