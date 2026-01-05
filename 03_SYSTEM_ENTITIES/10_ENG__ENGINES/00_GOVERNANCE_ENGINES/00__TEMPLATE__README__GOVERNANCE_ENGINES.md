# ENG FAMILY README — GOVERNANCE_ENGINES (TEMPLATE v2)
FILE: 00__TEMPLATE__README__GOVERNANCE_ENGINES.md

SCOPE: Universe Engine
LAYER: ENG
DOC_TYPE: TEMPLATE
ENTITY_GROUP: ENGINES (ENG)
TEMPLATE_KIND: FAMILY_README_OVERLAY
LEVEL: L1
STATUS: ACTIVE
VERSION: 2.0
ROLE: Family overlay for GOVERNANCE realm README. Must be compatible with base family template v2 and base engine template v2.

LOCK: FIXED
OWNER: Universe Engine

---

## 0) PURPOSE (REALM LAW)

Семейство **GOVERNANCE_ENGINES** — это слой законов, контроля изменений и памяти системы.

GOVERNANCE:
- определяет, что считается каноном
- фиксирует правила и иерархию правил
- управляет изменениями (change control)
- обеспечивает консистентность
- ведёт реестр зависимостей
- управляет approvals/решениями
- оценивает влияние и риски
- ведёт журнал аудита
- ведёт versioning + memory

EXISTENCE RULE:
> Любая правка канона без governance pipeline — недействительна.

---

## 1) FAMILY IDENTITY (MANDATORY)

FAMILY_NAME: GOVERNANCE_ENGINES
FAMILY_CODE: GOV
FAMILY_CLASS: GOVERNANCE
FAMILY_LEVEL: L1

FAMILY_PATH:
`03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/`

README_FILE:
`00__README__GOVERNANCE_ENGINES.md`

---

## 2) OWNERSHIP BOUNDARIES (ANTI-DUPLICATION)

### 2.1 OWNS
- каноническая власть (что является каноном и как фиксируется)
- контроль изменений (порядок, approvals, миграции)
- аудит-лог (история решений и правок)
- иерархия правил (какие правила старше/младше)
- консистентность (детект конфликтов и policy решения)
- registry зависимостей (явные DEPENDS_ON)
- оценка влияния (scope impact)
- риск/безопасность (risk safety)
- память системы (версионирование, immutable записи)

### 2.2 DOES NOT OWN (hard boundaries)
- создание контента мира/персонажей/сюжета как фактов
- создание медиа-артефактов (видео/картинки/монтаж)
- создание музыки как произведения
Rule:
> Governance управляет правилами и изменениями, но не “пишет историю” и не производит медиа.

---

## 3) ROLE MAP (MANDATORY)

- FOUNDATION: аудит/иерархия/authority
- BUILDER: change control + registry зависимостей
- VALIDATOR: консистентность + риск/влияние
- OUTPUT: versioning/memory + approvals

### 3.1 Canonical role map table
| Engine NN | Engine Name | ROLE_IN_FAMILY | PIPELINE_STAGE |
|---|---|---|---|
| 01 | Audit Log Engine | FOUNDATION | PRODUCE |
| 02 | Canon Authority Engine | FOUNDATION | DEFINE |
| 03 | Rule Hierarchy Engine | FOUNDATION | DEFINE |
| 04 | Change Control Engine | BUILDER | PACKAGE |
| 05 | Consistency Engine | VALIDATOR | CHECK |
| 06 | Dependency Registry Engine | BUILDER | PACKAGE |
| 07 | Decision Approval Engine | OUTPUT | PRODUCE |
| 08 | Scope Impact Engine | VALIDATOR | CHECK |
| 09 | Risk Safety Engine | VALIDATOR | CHECK |
| 10 | Versioning & Memory Engine | OUTPUT | PRODUCE |

---

## 4) FAMILY OUTPUT POLICY (WORKSHOP L0–L3) — MANDATORY

Governance outputs are primarily SYSTEM-level artifacts.

Allowed targets:
- SYSTEM scope (canonical):
  - `03_SYSTEM_ENTITIES/<...>` (laws/templates)
  - `00_REG__REGISTRIES/` (system registries)
  - `90_XREF__CROSSREF/` (system crossrefs)
- PROJECT scope (when governance is applied per-project):
  - `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/99_META/<...>/`

Rule:
> Governance engines are the exception: SYSTEM scope is allowed by design.

---

## 5) REQUIRED REGISTRIES (MANDATORY)

System-scoped (core):
- `00_REG__REGISTRIES/REG.SYS.AUDIT_LOG.md`
- `00_REG__REGISTRIES/REG.SYS.DECISIONS.md`
- `00_REG__REGISTRIES/REG.SYS.DEPENDENCIES.md`
- `00_REG__REGISTRIES/REG.SYS.CANON_AUTHORITY.md`
- `00_REG__REGISTRIES/REG.SYS.VERSIONING_MEMORY.md`
- `00_REG__REGISTRIES/REG.SYS.CHANGE_CONTROL.md`

Project-scoped (optional if used):
- `00_REG__REGISTRIES/REG.PRJ.<PROJECT_ID>.META_PROPOSALS.md`

---

## 6) REQUIRED XREF INDEXES (MANDATORY)

System-scoped:
- `90_XREF__CROSSREF/XREF__DEPENDENCIES.md`
- `90_XREF__CROSSREF/XREF__CHANGES.md`
- `90_XREF__CROSSREF/XREF__PROVENANCE.md`
- `90_XREF__CROSSREF/XREF__CANON_REFS.md` (if system canon refs tracked)

Project-scoped (optional):
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CHANGES.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__PROVENANCE.md`

---

## 7) TEMPLATES (MANDATORY BLOCK)

Base templates:
- ENGINE TEMPLATE (base) — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00__TEMPLATE__ENGINE__ENG.md
- FAMILY README TEMPLATE (base) — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00__TEMPLATE__README__FAMILY__ENG.md

Family overlays:
- ENGINE TEMPLATE (family) — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/00__TEMPLATE__ENGINE__GOVERNANCE_ENGINES.md
- README TEMPLATE (family) — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/00__TEMPLATE__README__GOVERNANCE_ENGINES.md

Rule:
> Family README must contain both base + overlay template links.

---

## 8) CANON ORDER (MANDATORY)

00 — README (Realm)  
01 — Audit Log Engine  
02 — Canon Authority Engine  
03 — Rule Hierarchy Engine  
04 — Change Control Engine  
05 — Consistency Engine  
06 — Dependency Registry Engine  
07 — Decision Approval Engine  
08 — Scope Impact Engine  
09 — Risk Safety Engine  
10 — Versioning & Memory Engine  

Rule:
> Engine NN in list must match file NN.

---

## 9) GOVERNANCE PIPELINE (MANDATORY)

Any change in canon, templates, registries, xref structure must go through:
- 04 Change Control
- 02 Canon Authority
- 10 Versioning & Memory
- 01 Audit Log

---

## 10) RAW LINK (MANDATORY)

RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/00__TEMPLATE__README__GOVERNANCE_ENGINES.md

---

## FINAL RULE (LOCK)

> Governance defines legality of canon changes and keeps the system consistent.

LOCK: FIXED
