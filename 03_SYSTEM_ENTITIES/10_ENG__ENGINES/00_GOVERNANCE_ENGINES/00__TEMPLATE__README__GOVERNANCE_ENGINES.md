# ENG FAMILY README — GOVERNANCE_ENGINES (TEMPLATE v2)
FILE: 00__TEMPLATE__README__GOVERNANCE_ENGINES.md

SCOPE: Universe Engine
LAYER: ENG
DOC_TYPE: TEMPLATE
ENTITY_KIND: GENERIC
PROJECT_SCOPE: GLOBAL
OUTPUT_LEVEL: N/A
ID: ENG.TPL.FAMILY.GOVERNANCE.README
STATUS: ACTIVE
VERSION: 2.0
ROLE: Realm law + role map + interfaces + required REG/XREF + canon order for GOVERNANCE family.

---

## 0) PURPOSE (REALM LAW)

Этот README — закон семейства **GOVERNANCE_ENGINES**.
Он фиксирует:
- границы ответственности governance
- роли движков внутри семьи (FOUNDATION/BUILDER/VALIDATOR/BRIDGE/OUTPUT)
- обязательные REG/XREF связи (чтобы не было hidden dependencies)
- правила вывода в WORKSHOP L0–L3 (как governance живёт в проектах)
- канонический порядок движков

### EXISTENCE RULE (FAMILY)
> Движок, не внесённый в CANON ORDER этой семьи + общий ENG INDEX — считается non-canon.

---

## 1) FAMILY IDENTITY (MANDATORY)

FAMILY_NAME: GOVERNANCE_ENGINES  
FAMILY_CODE: GOV  
FAMILY_CLASS: GOVERNANCE  
FAMILY_LEVEL: L1  

FAMILY_PATH: `10_ENG__ENGINES/00_GOVERNANCE_ENGINES/`  
README_FILE: `00__README__GOVERNANCE_ENGINES.md`

---

## 2) OWNERSHIP BOUNDARIES (ANTI-DUPLICATION)

### 2.1 OWNS (this family owns)
- Канон власти: кто имеет право фиксировать канон и правила системы
- Иерархия правил: какие документы “старше/младше”
- Контроль изменений: как вносить изменения в канон/шаблоны/пайплайны
- Audit trail: как фиксируются решения, изменения и причины (WHY)
- Dependency law: отсутствие скрытых зависимостей (no hidden deps)
- Risk & Safety: оценка рисков изменений и безопасность системы
- Versioning & memory: память версий, замены, миграции, обратная совместимость

### 2.2 DOES NOT OWN (belongs elsewhere)
- Создание контента сущностей (CHR/LOC/OBJ/...) → CORE/DOMAIN families
- Продакшн-выходы медиа (монтаж, звук, визуал) → PRODUCTION families
- Художественные/жанровые решения → STYLE families
- Глубокая музыка → SOUND families

Rule:
> Governance управляет **законом и контролем**, но не создаёт сюжет/персонажей/мир напрямую.

---

## 3) ROLE MAP (MANDATORY)

Каждый движок семьи обязан иметь роль:

- FOUNDATION — базовые законы (власть канона, иерархия правил)
- BUILDER — оформляет изменения/версии/память системы
- VALIDATOR — проверяет консистентность/риски/безопасность
- BRIDGE — проводит решения и их утверждение через пайплайн
- OUTPUT — делает “след”: журнал, отчёты, публичный слой фиксации

### 3.1 Role completeness rule
> В семье должны быть: минимум 1 FOUNDATION и 1 OUTPUT.  
> VALIDATOR обязателен, потому что governance влияет на все слои.

### 3.2 Role map table (canonical for this family)
| Engine NN | Engine Name | ROLE_IN_FAMILY | PIPELINE_STAGE |
|---|---|---|---|
| 01 | Audit Log Engine | OUTPUT | PRODUCE |
| 02 | Canon Authority Engine | FOUNDATION | DEFINE |
| 03 | Rule Hierarchy Engine | FOUNDATION | DEFINE |
| 04 | Change Control Engine | BUILDER | BUILD |
| 05 | Consistency Engine | VALIDATOR | CHECK |
| 06 | Dependency Registry Engine | BUILDER | BUILD |
| 07 | Decision Approval Engine | BRIDGE | PACKAGE |
| 08 | Scope Impact Engine | VALIDATOR | CHECK |
| 09 | Risk Safety Engine | VALIDATOR | CHECK |
| 10 | Versioning & Memory Engine | BUILDER | BUILD |

PIPELINE_STAGE standard: DEFINE / BUILD / CHECK / PACKAGE / PRODUCE

---

## 4) FAMILY OUTPUT POLICY (WORKSHOP L0–L3) — MANDATORY

Governance тоже живёт в проектах, но как **управленческий контур**, а не “сюжет”.

DEFAULT_ENTITY_KIND: GENERIC  
DEFAULT_OUTPUT_LEVEL: L1_DRAFT (по умолчанию)  

DEFAULT_PROJECT_OUTPUT_ROOT:
- `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/`

DEFAULT_CATEGORY_PATH:
- `11_EXPERIMENTS/`   (временный стабильный контейнер для governance в проекте)

DEFAULT_ENTITY_FOLDER:
- `GENERIC_GOVERNANCE/` (один governance-root на проект)

### 4.1 Level routing rules (strict)
- L0_INTAKE: заявки/идеи/сырьё изменений (change requests)
- L1_DRAFT: проекты решений, черновики правил, черновые зависимости
- L2_CANON: утверждённые решения/изменения, канон-фиксации
- L3_OUTPUT: release notes / canon packs / публичные сводки изменений

---

## 5) REQUIRED REGISTRIES (MANDATORY)

Governance обязана регистрировать свои управленческие артефакты в проектах.

REQUIRED_REGISTRIES (project-scoped placeholders):
- `REG.PRJ.<PROJECT_ID>.GOV.CHANGES`
- `REG.PRJ.<PROJECT_ID>.GOV.DECISIONS`
- `REG.PRJ.<PROJECT_ID>.GOV.VERSIONS`

Rule:
> Любое L2_CANON governance-решение и любой L3_OUTPUT governance-пакет обязаны быть в REG.

---

## 6) REQUIRED XREF INDEXES (MANDATORY)

Governance обязана фиксировать связи, чтобы не было скрытых причин и зависимостей.

REQUIRED_XREF (project-scoped placeholders):
- Dependency graph:
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__DEPENDENCIES.md`
- Changes / replacement / movement:
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CHANGES.md`
- Conflicts / duplicates:
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CONFLICTS.md`
- Canon references (если governance выпускает пакеты, ссылающиеся на канон):
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CANON_REFS.md`

Hard rule:
> Любое DEPENDS_ON из mini-contract движков должно быть отражено в XREF__DEPENDENCIES.

---

## 7) INTERFACES (INPUT / OUTPUT ARTIFACT TYPES)

### 7.1 INPUT ARTIFACT TYPES (common)
- CHANGE_REQUEST (L0)
- DECISION_PROPOSAL (L1)
- DEPENDENCY_DECLARATION (L1)
- CONFLICT_REPORT (L1)
- RISK_NOTE (L1)
- VERSION_NOTE (L1)

### 7.2 OUTPUT ARTIFACT TYPES (common)
- APPROVED_DECISION (L2)
- AUDIT_LOG_ENTRY (L2/L3)
- DEPENDENCY_REGISTRY_UPDATE (L2)
- VERSION_RECORD (L2)
- RELEASE_NOTES / CANON_CHANGELOG (L3)

---

## 8) TEMPLATES (MANDATORY BLOCK)

- FAMILY README TEMPLATE (base) — `10_ENG__ENGINES/00__TEMPLATE__README__FAMILY__ENG.md`
- ENGINE TEMPLATE (base) — `10_ENG__ENGINES/00__TEMPLATE__ENGINE__ENG.md`

Family overlays:
- README TEMPLATE (this file) — `10_ENG__ENGINES/00_GOVERNANCE_ENGINES/00__TEMPLATE__README__GOVERNANCE_ENGINES.md`
- ENGINE TEMPLATE (family) — `10_ENG__ENGINES/00_GOVERNANCE_ENGINES/00__TEMPLATE__ENGINE__GOVERNANCE_ENGINES.md`

---

## 9) CANON ORDER (MANDATORY)

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
> Номер в списке = номер в имени файла.

---

## 10) GOVERNANCE COMPATIBILITY (MANDATORY)

Изменения в этой семье = изменения закона системы.
Обязательны:
- Audit log запись (WHY + что менялось)
- Change control решение
- Version/memory обновление
- XREF изменения (REPLACED_BY/MOVED_TO/RENAMED_TO, если применимо)

---

## FINAL RULE (LOCK)

> Этот README — закон семейства GOVERNANCE_ENGINES.  
> Несоответствие роли/границам/обязательным REG/XREF = non-canon.

OWNER: Universe Engine  
LOCK: FIXED
