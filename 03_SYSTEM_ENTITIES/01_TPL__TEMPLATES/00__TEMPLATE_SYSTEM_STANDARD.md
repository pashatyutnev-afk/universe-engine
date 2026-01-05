# TEMPLATE SYSTEM STANDARD — UNIVERSAL LAW
FILE: 00__TEMPLATE_SYSTEM_STANDARD.md

SCOPE: Universe Engine Repository
LAYER: TPL
DOC_TYPE: STANDARD
LEVEL: L0
STATUS: ACTIVE
VERSION: 1.0
ROLE: Universal law that defines how ALL documents, templates, artifacts, registries, and crossrefs are written, linked, registered, and promoted across levels L0→L3.

---

## 0) PURPOSE (LAW)

Этот стандарт определяет единый формат и обязательные поля для всех файлов системы:
- ENG / ORC / CTL / VAL / QA / REG / XREF / PROJECTS
- сущностей (CHR/LOC/OBJ/...) и артефактов (canon/production)

### EXISTENCE RULE
> Любой артефакт, не зарегистрированный в REG и не связанный через XREF — считается **non-existent for the system**.

---

## 1) SYSTEM ROOTS (CANON PATHS)

- REG (existence registries): `00_REG__REGISTRIES/`
- TPL (templates): `01_TPL__TEMPLATES/`
- ENG (engines): `10_ENG__ENGINES/`
- ORC (orchestrators): `20_ORC__ORCHESTRATORS/`
- SPC (specialists): `30_SPC__SPECIALISTS/`
- CTL (controllers): `40_CTL__CONTROLLERS/`
- VAL (validators): `50_VAL__VALIDATORS/`
- QA (quality gates): `60_QA__QUALITY/`
- XREF (crossrefs): `90_XREF__CROSSREF/`
- PROJECTS (production workspace): `05_PROJECTS/`

---

## 2) UNIVERSAL HEADER (MANDATORY IN ALL DOCS)

Каждый файл системы обязан начинаться с универсальной шапки.

### 2.1 Required fields (strict)
- FILE: <exact filename>
- SCOPE: <Universe Engine | Project:<ID> | Workshop>
- LAYER: <REG|TPL|ENG|ORC|SPC|CTL|VAL|QA|XREF|PRJ>
- DOC_TYPE: <STANDARD|TEMPLATE|README|ENGINE|REGISTRY|XREF_RECORD|XREF_INDEX|ORCHESTRATOR|CONTROLLER|VALIDATOR|QA_CHECK|ENTITY|INDEX|LOG_ENTRY|CHANGE_REQUEST>
- ENTITY_KIND: <CHR|LOC|OBJ|SYS|FAC|EVT|CPT|REL|ARC|STY|EXP|GENERIC>
- PROJECT_SCOPE: <GLOBAL|PROJECT_ONLY>
- OUTPUT_LEVEL: <L0_INTAKE|L1_DRAFT|L2_CANON|L3_OUTPUT|N/A>
- ID: <canonical id string>
- STATUS: <DRAFT|ACTIVE|DEPRECATED|ARCHIVED>
- VERSION: <x.y>
- ROLE: <one-line purpose>

### 2.2 Lock policy (strict)
- LOCK: <OPEN|FIXED> MUST exist exactly once (recommended at bottom in FINAL RULE block)

---

## 3) CANONICAL ID STANDARD (MANDATORY)

### 3.1 Engines
Format:
- `ENG.<FAMILYCODE>.<NN>.<ENGINE_NAME>`
Examples:
- `ENG.GOV.04.CHANGE_CONTROL`
- `ENG.NARR.02.STORY_STRUCTURE`
- `ENG.MUS.13.MIX_MASTER`

### 3.2 Orchestrators / Controllers / Validators / QA
- `ORC.<DOMAIN>.<NN>.<NAME>`
- `CTL.<DOMAIN>.<NN>.<NAME>`
- `VAL.<DOMAIN>.<NN>.<NAME>`
- `QA.<DOMAIN>.<NN>.<NAME>`

### 3.3 Entities (Workshop)
- `CHR.<NAME>` / `LOC.<NAME>` / `OBJ.<NAME>` / ...
- Project-scoped variant:
  - `PRJ.<PROJECT_ID>.CHR.<NAME>`

### 3.4 Registries / Xref
- `REG.<DOMAIN>.<NAME>`
- `XREF.<DOMAIN>.<NAME>`

---

## 4) WORKSHOP LEVEL SYSTEM (L0→L3) — CANON LAW

### 4.1 Levels
- L0_INTAKE: raw inputs, notes, fragments
- L1_DRAFT: structured draft artifacts (not canon)
- L2_CANON: approved canon artifacts
- L3_OUTPUT: production outputs (ART/BOOK/FILM/GAME/MUSIC/SERIES)

### 4.2 Promotion rule (hard)
> Нельзя продвинуть артефакт вверх по уровням без обязательных gate-проверок и обновлений REG/XREF.

---

## 5) SYSTEM INTERFACE BLOCK (MANDATORY FOR ENGINES + ENTITIES + OUTPUTS)

Любой ENGINE/ENTITY/OUTPUT обязан содержать блок:

## SYSTEM INTERFACE
- INPUTS:
  - artifacts: [...]
  - sources: [...]
- OUTPUTS:
  - artifacts: [...]
  - target_path: <canonical path rule>
- REGISTRY_UPDATES:
  - required: <YES|NO>
  - registries: [<registry ids or paths>]
  - entries_to_add: [<short list>]
- XREF_UPDATES:
  - required: <YES|NO>
  - record_types: [<DEPENDS_ON|DERIVED_FROM|CANON_REF|PRODUCTION_REF|ENTITY_LINK|CONFLICTS_WITH>]
  - xref_targets: [<xref ids or paths>]
- GATES:
  - validators: [<VAL ids>]
  - qa_checks: [<QA ids>]
- ORCHESTRATION:
  - orc_owner: <ORC id or []>
  - ctl_enforcers: [<CTL ids>]

If SYSTEM INTERFACE is missing → artifact is **incomplete**.

---

## 6) REGISTRY RULE (EXISTENCE)

### 6.1 Registry update is mandatory when:
- New entity is created (CHR/LOC/OBJ/...)
- New canon artifact (L2) is created
- New output artifact (L3) is created
- Any template or engine is introduced as canon rule

### 6.2 Minimal registry entry fields
- ID
- PATH
- TYPE
- STATUS
- OWNER
- CREATED_BY (engine/orc)
- UPDATED_AT

---

## 7) XREF RULE (RELATIONSHIPS)

### 7.1 XREF update is mandatory when:
- A depends on B
- A derived from B
- Canon artifact references entity
- Output derived from canon
- Two artifacts conflict / replace

### 7.2 Minimal xref record format
`<A_ID> -> <B_ID> | TYPE:<...> | SCOPE:<GLOBAL|PRJ:<ID>> | WHY:<short> | BY:<engine/orc>`

---

## 8) FINAL RULE (LOCK)

> Этот стандарт является законом для всех шаблонов и документов системы.  
> Любая правка стандарта проходит governance pipeline и фиксируется в Audit Log.

OWNER: Universe Engine  
LOCK: FIXED
