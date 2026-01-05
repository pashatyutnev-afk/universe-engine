# ORCHESTRATOR TEMPLATE — UNIVERSAL PIPELINE CONTROLLER
FILE: 00__TEMPLATE__ORCHESTRATOR.md

SCOPE: Universe Engine
LAYER: ORC
DOC_TYPE: TEMPLATE
ENTITY_KIND: GENERIC
PROJECT_SCOPE: GLOBAL
OUTPUT_LEVEL: N/A
ID: ORC.TEMPLATE.UNIVERSAL
STATUS: ACTIVE
VERSION: 2.0
ROLE: Universal template for ORC orchestrators. Defines execution pipelines across engines, level promotions (L0→L3), gate points (VAL/QA), and mandatory REG/XREF checkpoints.

---

## 0) PURPOSE (LAW)

Orchestrator — это “пайплайн-мозг”, который:
- запускает движки в правильном порядке
- управляет продвижением уровней L0→L1→L2→L3
- ставит gate points (VAL/QA)
- enforce’ит обновления REG/XREF как обязательные checkpoints
- запрещает “перепрыгивания” уровней и скрытые зависимости

### NO SKIP RULE
> Нельзя перейти к L2_CANON или L3_OUTPUT минуя gates и REG/XREF checkpoints.

---

## 1) ORCHESTRATOR IDENTITY (MANDATORY)

ORC_NAME: <UPPER_SNAKE_CASE>
ORC_ID: <ORC.<DOMAIN>.<NN>.<ORC_NAME>>

DOMAIN: <NARRATIVE|CHARACTER|WORLD|STYLE|FORMAT|PRODUCTION|MUSIC|META|GOV|GENERIC>
APPLIES_TO:
- ENTITY_KIND: <CHR|LOC|OBJ|SYS|FAC|EVT|CPT|REL|ARC|STY|EXP|GENERIC>
- SCOPE: <GLOBAL|PRJ:<PROJECT_ID>>
- DEFAULT_WORKSHOP_ROOT: `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/`

OWNER: Universe Engine
LOCK: OPEN

---

## 2) INPUT / OUTPUT CONTRACT (MANDATORY)

### 2.1 Inputs
INPUTS:
- triggers: [<event or manual call>]
- required_artifacts: [<ids/types>]
- required_registries: [<REG ids/paths>]
- required_xref_indexes: [<XREF ids/paths>]

### 2.2 Outputs
OUTPUTS:
- produces_levels: [<L0_INTAKE|L1_DRAFT|L2_CANON|L3_OUTPUT>]
- produced_artifacts: [<ids/types>]
- target_categories: [<01_CHARACTERS|...|05_PROJECT__L3>]

---

## 3) PIPELINE GRAPH (MANDATORY)

Define pipeline as ordered steps. Each step runs one engine (or sub-orchestrator).

### 3.1 Step format (strict)
STEP:
- STEP_ID: <ORC.<...>.S01 / S02 ...>
- NAME: <short>
- RUN: <ENG.* id OR ORC.* id>
- INPUT_LEVEL: <L0|L1|L2|L3|N/A>
- OUTPUT_LEVEL: <L0|L1|L2|L3|N/A>
- OUTPUT_ARTIFACT_TYPE: <...>
- OUTPUT_TARGET_RULE: <workshop path rule summary>
- REQUIRED_XREF: [<record types>]
- REQUIRED_REG_UPDATES: <YES|NO>
- GATE_POINT:
  - validators: [<VAL ids>]
  - qa_checks: [<QA ids>]
- CTL_ENFORCERS: [<CTL ids>]
- FAIL_POLICY: <STOP|ROLLBACK|SKIP_WITH_NOTE>

### 3.2 Recommended pipeline stages
- S01 DEFINE (foundation)
- S02 BUILD (draft)
- S03 CHECK (validators)
- S04 CANONIZE (L2)
- S05 PRODUCE OUTPUT (L3)

---

## 4) PROMOTION RULES (L0→L3) — MANDATORY

Promotion is a controlled operation.

### 4.1 Promotion conditions
To promote to next level:
- required validators PASS
- required QA checks PASS
- REG updated (if required)
- XREF updated (mandatory links exist)

### 4.2 Promotion record (mandatory xref)
Every promotion must create:
- `A -> B | TYPE:DERIVED_FROM` (draft/canon lineage)
- `L3_OUTPUT -> L2_CANON | TYPE:CANON_REF` (for outputs)

### 4.3 No orphan rule
- L2_CANON cannot exist without provenance xref
- L3_OUTPUT cannot exist without canon_ref xref

---

## 5) CHECKPOINTS (MANDATORY)

Checkpoints are non-negotiable.

### 5.1 Registry checkpoint
At least once per level transition:
- add/update registry entries for new artifacts/entities

### 5.2 XREF checkpoint
At least once per level transition:
- ensure all required xref record types exist

### 5.3 Dependency checkpoint
If any engine declares DEPENDS_ON:
- ensure matching XREF DEPENDS_ON records exist
- else fail pipeline (hidden dependency)

---

## 6) SYSTEM INTERFACE (MANDATORY)

## SYSTEM INTERFACE
- INPUTS:
  - artifacts: [pipeline inputs]
  - sources: [registries, xref indexes, engine mini-contracts]
- OUTPUTS:
  - artifacts: [pipeline outputs]
  - target_path: 05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/...
- REGISTRY_UPDATES:
  - required: YES
  - registries: [<REG ids/paths>]
  - entries_to_add: [<summary>]
- XREF_UPDATES:
  - required: YES
  - record_types: [DEPENDS_ON, DERIVED_FROM, PRODUCED_BY, CANON_REF, PRODUCTION_REF]
  - xref_targets: [<XREF ids/paths>]
- GATES:
  - validators: [<VAL ids>]
  - qa_checks: [<QA ids>]
- ORCHESTRATION:
  - orc_owner: []  # top-level orc
  - ctl_enforcers: [<CTL ids>]

---

## 7) EXECUTION NOTES (OPTIONAL)

- concurrency rules (if any)
- manual intervention points
- rollback strategy (if used)

---

## 8) RAW LINK (MANDATORY)

RAW: <raw github link to this orchestrator file>

---

## FINAL RULE (LOCK)

> Этот ORC определяет единственный допустимый порядок выполнения пайплайна.  
> Изменения пайплайна = изменение канона процесса и проходят governance.

OWNER: Universe Engine  
LOCK: OPEN
