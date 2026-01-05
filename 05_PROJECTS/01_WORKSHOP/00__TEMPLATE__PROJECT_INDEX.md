# PROJECT INDEX TEMPLATE — WORKSHOP NAV + SYSTEM HUB
FILE: 00__TEMPLATE__PROJECT_INDEX.md

SCOPE: Projects Workshop
LAYER: PRJ
DOC_TYPE: TEMPLATE
ENTITY_KIND: GENERIC
PROJECT_SCOPE: PROJECT_ONLY
OUTPUT_LEVEL: N/A
ID: PRJ.WORKSHOP.TEMPLATE.PROJECT_INDEX
STATUS: ACTIVE
VERSION: 2.0
ROLE: Universal project index template for Workshop. Central hub linking registries, xref indexes, orchestrators, gates, entities, canon, and outputs across L0→L3.

---

## 0) PURPOSE (LAW)

Project Index — единая точка входа в проект:
- где лежат сущности и артефакты
- какие реестры являются “существованием”
- где хранятся связи (XREF)
- какими пайплайнами проект производится (ORC)
- какие законы enforce’ят (CTL) и кто проверяет (VAL/QA)
- где лежит канон (L2) и выход (L3)

### PROJECT SINGLE SOURCE RULE
> Любая навигация в проекте начинается с этого INDEX.  
> Всё важное обязано иметь ссылки здесь (или через дочерние индексы).

---

## 1) PROJECT IDENTITY (MANDATORY)

PROJECT_NAME: <human readable>
PROJECT_ID: <PROJECT_ID>

PROJECT_ROOT: `05_PROJECTS/<PROJECT_ID>/`
WORKSHOP_ROOT: `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/`

OWNER: <project owner>
LOCK: OPEN

---

## 2) WORKSHOP MAP (MANDATORY)

### 2.1 Categories (standard)
- 01_CHARACTERS/
- 02_LOCATIONS/
- 03_OBJECTS/
- 04_SYSTEMS/
- 05_FACTIONS/
- 06_EVENTS/
- 07_CONCEPTS/
- 08_RELATIONSHIPS/
- 09_ARCS/
- 10_STYLES/
- 11_EXPERIMENTS/
- 05_PROJECT__L3/     (outputs that are project-level, not entity-level)

### 2.2 Level system (standard)
- L0 intake: `01_INTAKE_L0/`
- L1 draft: `02_DRAFT_L1/`
- L2 canon: `03_CANON_L2/`
- L3 output: `04_OUTPUT_L3/`

---

## 3) PROJECT REGISTRIES (MANDATORY)

Declare concrete registry files used by this project.

REGISTRIES:
- Entities Registry:
  - ID/PATH: <REG.PRJ.<PROJECT_ID>.ENTITIES.md>
- Canon Artifacts Registry (L2):
  - ID/PATH: <REG.PRJ.<PROJECT_ID>.CANON_L2.md>
- Output Artifacts Registry (L3):
  - ID/PATH: <REG.PRJ.<PROJECT_ID>.OUTPUT_L3.md>
Optional:
- Assets Registry:
  - ID/PATH: <REG.PRJ.<PROJECT_ID>.ASSETS.md>

Rule:
> Any entity root folder must be in Entities Registry.  
> Any L2/L3 artifact must be registered.

---

## 4) PROJECT XREF INDEXES (MANDATORY)

XREF INDEXES:
- Dependency Graph:
  - PATH: `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__DEPENDENCIES.md`
- Provenance / Derivation:
  - PATH: `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__PROVENANCE.md`
- Canon References:
  - PATH: `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CANON_REFS.md`
- Entity Graph:
  - PATH: `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__ENTITY_GRAPH.md`
- Changes / Replacement:
  - PATH: `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CHANGES.md`
Optional:
- Conflicts / Duplicates:
  - PATH: `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CONFLICTS.md`

Rule:
> L3 outputs must have CANON_REF in XREF__CANON_REFS.  
> L2 canon must have provenance in XREF__PROVENANCE.

---

## 5) PROJECT PIPELINES (ORC) (MANDATORY)

List orchestrators used in this project.

ORCHESTRATORS:
- Narrative pipeline: <ORC.* id/path>
- Character pipeline: <ORC.* id/path>
- World pipeline: <ORC.* id/path>
- Production pipeline: <ORC.* id/path>
- Music pipeline: <ORC.* id/path>

Rule:
> Pipelines define allowed promotion steps and gate points.

---

## 6) ENFORCEMENT + GATES (MANDATORY)

### 6.1 Controllers (CTL)
CONTROLLERS:
- Path enforcement: <CTL.*>
- Level/promotion enforcement: <CTL.*>
- Registry enforcement: <CTL.*>
- XREF enforcement: <CTL.*>
- Hidden dependency enforcement: <CTL.*>

### 6.2 Validators (VAL)
VALIDATORS:
- Schema validator: <VAL.*>
- Registry integrity validator: <VAL.*>
- Xref consistency validator: <VAL.*>
- Canon conflict validator: <VAL.*>

### 6.3 QA checks
QA_CHECKS:
- Readability & completeness: <QA.*>
- Anti-stub gate: <QA.*>
- Link integrity: <QA.*>

---

## 7) CANON + OUTPUT ENTRYPOINTS (MANDATORY)

### 7.1 Canon entrypoints (L2)
- Canon overview: `01_WORKSHOP/__CANON_OVERVIEW_L2.md` (optional)
- Canon packs:
  - Characters canon index: <path>
  - World canon index: <path>

### 7.2 Output entrypoints (L3)
- Output overview: `01_WORKSHOP/__OUTPUT_OVERVIEW_L3.md` (optional)
- Project-level outputs: `01_WORKSHOP/05_PROJECT__L3/`

---

## 8) ENTITY NAVIGATION (MANDATORY)

### 8.1 Quick entity list (fill)
(Only list top-level entities or keep an index per category.)

- Characters:
  - CHR_<NAME> → `01_WORKSHOP/01_CHARACTERS/CHR_<NAME>/00__ENTITY_OVERVIEW.md`
- Locations:
  - LOC_<NAME> → `01_WORKSHOP/02_LOCATIONS/LOC_<NAME>/00__ENTITY_OVERVIEW.md`
...

### 8.2 Rule
> Каждая сущность обязана иметь `00__ENTITY_OVERVIEW.md` как навигационный хаб.

---

## 9) CHANGE CONTROL (MANDATORY)

Changes to:
- registries
- xref indexes
- pipelines
- canon L2
must be logged:
- governance audit log entry
- replacement/move recorded in XREF__CHANGES when relevant

---

## 10) SYSTEM INTERFACE (MANDATORY)

## SYSTEM INTERFACE
- INPUTS:
  - artifacts: [all workshop artifacts]
  - sources: [project goals, engines, orc pipelines]
- OUTPUTS:
  - artifacts: [project canon + outputs]
  - target_path: `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/`
- REGISTRY_UPDATES:
  - required: YES
  - registries: [project registries listed in section 3]
  - entries_to_add: [new entities, new L2/L3 artifacts]
- XREF_UPDATES:
  - required: YES
  - record_types: [DEPENDS_ON, DERIVED_FROM, CANON_REF, ENTITY_LINK, REPLACED_BY, CONFLICTS_WITH]
  - xref_targets: [project xref indexes listed in section 4]
- GATES:
  - validators: [project validators listed in section 6]
  - qa_checks: [project QA checks listed in section 6]
- ORCHESTRATION:
  - orc_owner: [project orchestrators listed in section 5]
  - ctl_enforcers: [project controllers listed in section 6]

---

## FINAL RULE (LOCK)

> Этот индекс — главный навигационный и системный хаб проекта.  
> Без него проект считается неинициализированным в системе.

OWNER: <project owner>  
LOCK: OPEN
