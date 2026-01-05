# ENG FAMILY README — META_EVOLUTION_ENGINES (TEMPLATE v2)
FILE: 00__TEMPLATE__README__META_EVOLUTION_ENGINES.md

SCOPE: Universe Engine
LAYER: ENG
DOC_TYPE: TEMPLATE
ENTITY_KIND: META
PROJECT_SCOPE: GLOBAL
OUTPUT_LEVEL: N/A
ID: ENG.TPL.FAMILY.META_EVOLUTION.README
STATUS: ACTIVE
VERSION: 2.0
ROLE: Realm law + role map + interfaces + required REG/XREF + canon order for META_EVOLUTION family.

---

## 0) PURPOSE (REALM LAW)

Этот README — закон семейства **META_EVOLUTION_ENGINES**.
Семейство отвечает за развитие системы поверх всех слоёв:
- обучение на результатах (Learning)
- извлечение паттернов (Pattern Extraction)
- оптимизация процессов и качества (Optimization)
- креативные мутации (Creative Mutation)
- прогноз и планирование будущих веток (Future Projection)

### EXISTENCE RULE (META)
> Meta-движки не создают канон напрямую.  
> Они создают предложения/обоснования/планы улучшений, которые проходят governance pipeline.

---

## 1) FAMILY IDENTITY (MANDATORY)

FAMILY_NAME: META_EVOLUTION_ENGINES  
FAMILY_CODE: MET  
FAMILY_CLASS: META  
FAMILY_LEVEL: L4  

FAMILY_PATH: `10_ENG__ENGINES/10_META_EVOLUTION_ENGINES/`  
README_FILE: `00__README__META_EVOLUTION_ENGINES.md`

---

## 2) OWNERSHIP BOUNDARIES (ANTI-DUPLICATION)

### 2.1 OWNS
- meta-процессы улучшения: сбор сигналов, выводы, рекомендации
- выявление противоречий и “узких мест”
- предложения рефакторинга: движки/шаблоны/реестры/xref
- roadmap эволюции системы

### 2.2 DOES NOT OWN (hard boundaries)
- утверждение изменений канона → Governance (Change Control / Canon Authority)
- правки конкретных domain-документов без approval → запрещено
- создание новых сущностей без регистрации → запрещено

Boundary rule:
> Meta генерирует Change Proposals (CP). Governance утверждает. Потом изменения применяются в слоях.

---

## 3) ROLE MAP (MANDATORY)

- FOUNDATION — learning/pattern extraction как база сигналов
- BUILDER — optimization/mutation как генератор решений
- VALIDATOR — future projection как проверка устойчивости и roadmap
- OUTPUT — change proposal packs + evolution roadmap

### 3.1 Canonical role map table
| Engine NN | Engine Name | ROLE_IN_FAMILY | PIPELINE_STAGE |
|---|---|---|---|
| 01 | Learning Engine | FOUNDATION | DEFINE |
| 02 | Pattern Extraction Engine | FOUNDATION | DEFINE |
| 03 | Optimization Engine | BUILDER | BUILD |
| 04 | Creative Mutation Engine | BUILDER | BUILD |
| 05 | Future Projection Engine | VALIDATOR | CHECK |

---

## 4) CHANGE PROPOSAL STANDARD (MANDATORY)

Любой meta-output обязан быть оформлен как Change Proposal (CP):
- CP_ID
- TARGET_SCOPE (ENG templates / family rules / registries / xref / governance rules / project pipelines)
- PROBLEM (что болит)
- EVIDENCE (на чём основано)
- PROPOSED_CHANGE (что меняем)
- IMPACT (кто сломается / кто выиграет)
- MIGRATION_PLAN (как перейти)
- RISK (что может пойти не так)
- REQUIRED_APPROVALS (governance engines)
- STATUS (DRAFT/PROPOSED/APPROVED/REJECTED)

Rule:
> Если нет MIGRATION_PLAN и IMPACT — это не proposal, а мнение.

---

## 5) FAMILY OUTPUT POLICY (WORKSHOP L0–L3) — MANDATORY

DEFAULT_PROJECT_OUTPUT_ROOT:
- `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/`

Primary categories:
- `99_META/`
  - `01_SIGNALS/`
  - `02_PROPOSALS/`
  - `03_MIGRATIONS/`
  - `04_ROADMAP/`

Recommended:
- L0: сигналы/наблюдения
- L1: паттерны/инсайты
- L2: proposals canon (после approval)
- L3: migration packs / roadmap packs

---

## 6) REQUIRED REGISTRIES (MANDATORY)

REQUIRED_REGISTRIES (project-scoped or system-scoped):
- `REG.PRJ.<PROJECT_ID>.META_PROPOSALS`
- `REG.SYS.META_PROPOSALS` (если общесистемно)

---

## 7) REQUIRED XREF INDEXES (MANDATORY)

REQUIRED_XREF:
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CHANGES.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__PROVENANCE.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__DEPENDENCIES.md`

Hard rule:
> Каждое CP обязано ссылаться на затронутые файлы (CANON_REF) и зависимости (DEPENDS_ON).

---

## 8) INTERFACES (INPUT / OUTPUT ARTIFACT TYPES)

### 8.1 INPUT TYPES
- AUDIT_LOG (Governance 01)
- CONSISTENCY REPORTS (Governance 05)
- DEPENDENCY REGISTRY snapshots (Governance 06)
- QA outputs
- project outcomes (L3 outputs performance/feedback)

### 8.2 OUTPUT TYPES
- SIGNAL_REPORT
- PATTERN_REPORT
- OPTIMIZATION_PROPOSAL (CP)
- MUTATION_PROPOSAL (CP)
- EVOLUTION_ROADMAP
- MIGRATION_PACK

---

## 9) TEMPLATES (MANDATORY BLOCK)

Base templates:
- FAMILY README TEMPLATE (base) — `10_ENG__ENGINES/00__TEMPLATE__README__FAMILY__ENG.md`
- ENGINE TEMPLATE (base) — `10_ENG__ENGINES/00__TEMPLATE__ENGINE__ENG.md`

Family overlays:
- README TEMPLATE (this file) — `10_ENG__ENGINES/10_META_EVOLUTION_ENGINES/00__TEMPLATE__README__META_EVOLUTION_ENGINES.md`
- ENGINE TEMPLATE (family) — `10_ENG__ENGINES/10_META_EVOLUTION_ENGINES/00__TEMPLATE__ENGINE__META_EVOLUTION_ENGINES.md`

---

## 10) CANON ORDER (MANDATORY)

00 — README (Realm)  
01 — Learning Engine  
02 — Pattern Extraction Engine  
03 — Optimization Engine  
04 — Creative Mutation Engine  
05 — Future Projection Engine  

---

## FINAL RULE (LOCK)

> Meta family produces proposals, not canon changes.  
> Implementation must go through Governance change control.

OWNER: Universe Engine  
LOCK: FIXED
