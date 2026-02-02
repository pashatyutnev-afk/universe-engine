# ENTITY WORKSHOP TEMPLATE — UNIVERSAL (CHR/LOC/OBJ/...)
FILE: 00__TEMPLATE__ENTITY_WORKSHOP.md

SCOPE: Projects Workshop
LAYER: PRJ
DOC_TYPE: TEMPLATE
ENTITY_KIND: GENERIC
PROJECT_SCOPE: PROJECT_ONLY
OUTPUT_LEVEL: N/A
ID: PRJ.WORKSHOP.TEMPLATE.ENTITY
STATUS: ACTIVE
VERSION: 2.0
ROLE: Universal project workshop template for an entity workspace folder. Provides L0/L1/L2/L3 structure, registry/xref integration, and engine/orchestrator routing.

---

## 0) PURPOSE (WORKSHOP LAW)

Entity Workshop Folder — единая “точка жизни” сущности в проекте.
Внутри:
- L0_INTAKE: сырьё и заметки
- L1_DRAFT: структурные черновики
- L2_CANON: утверждённый канон
- L3_OUTPUT: производные выходы (для книги/видео/игры/музыки/арта)

### SINGLE SOURCE RULE (ENTITY)
> Для одной сущности существует один root-folder в WORKSHOP.  
> Дубли = запрещены (только через MERGED_INTO/SPLIT_INTO в XREF).

---

## 1) ENTITY IDENTITY (MANDATORY)

PROJECT_ID: <PROJECT_ID>
ENTITY_KIND: <CHR|LOC|OBJ|SYS|FAC|EVT|CPT|REL|ARC|STY|EXP>
ENTITY_NAME: <UPPER_SNAKE_CASE or readable>
ENTITY_ID: <PRJ.<PROJECT_ID>.<ENTITY_KIND>.<ENTITY_NAME>>

WORKSHOP_ROOT:
`05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/<CATEGORY>/<ENTITY_FOLDER>/`

CATEGORY (by kind):
- CHR -> 01_CHARACTERS
- LOC -> 02_LOCATIONS
- OBJ -> 03_OBJECTS
- SYS -> 04_SYSTEMS
- FAC -> 05_FACTIONS
- EVT -> 06_EVENTS
- CPT -> 07_CONCEPTS
- REL -> 08_RELATIONSHIPS
- ARC -> 09_ARCS
- STY -> 10_STYLES
- EXP -> 11_EXPERIMENTS

ENTITY_FOLDER_NAME (standard):
- `<KIND>_<ENTITY_NAME>` e.g., `CHR_AKIRA`, `LOC_ALMATY`, `OBJ_RELIC_01`

OWNER: <project owner>
LOCK: OPEN

---

## 2) FOLDER STRUCTURE (MANDATORY)

Inside entity folder create:

- `00__ENTITY_OVERVIEW.md`            (this file; navigation hub)
- `01_INTAKE_L0/`                     (raw intake)
- `02_DRAFT_L1/`                      (structured drafts)
- `03_CANON_L2/`                      (approved canon)
- `04_OUTPUT_L3/`                     (production outputs)

Optional:
- `05_ASSETS/`                        (images/audio refs for this entity)
- `90_NOTES/`                         (free notes that are not artifacts)

---

## 3) NAVIGATION HUB FILE (MANDATORY)

Create `00__ENTITY_OVERVIEW.md` using this structure:

### 3.1 Universal header (required)
FILE: 00__ENTITY_OVERVIEW.md
SCOPE: Project:<PROJECT_ID>
LAYER: PRJ
DOC_TYPE: ENTITY
ENTITY_KIND: <...>
PROJECT_SCOPE: PROJECT_ONLY
OUTPUT_LEVEL: N/A
ID: <ENTITY_ID>
STATUS: ACTIVE
VERSION: 1.0
ROLE: Entity workspace navigation hub + lifecycle control

### 3.2 Quick links
- L0 intake: `01_INTAKE_L0/`
- L1 drafts: `02_DRAFT_L1/`
- L2 canon: `03_CANON_L2/`
- L3 outputs: `04_OUTPUT_L3/`

---

## 4) L0 — INTAKE (RAW INPUTS)

Folder: `01_INTAKE_L0/`

Allowed content:
- raw notes, references, loose ideas, screenshots, links
- fragments without structure

Rules:
- No canon claims
- No production outputs

Recommended files:
- `00__INTAKE_NOTES.md`
- `01__REFERENCES.md`

---

## 5) L1 — DRAFT (STRUCTURED WORK)

Folder: `02_DRAFT_L1/`

Purpose:
- create structured drafts for later canonization

Recommended files (examples):
- `00__DRAFT_MAIN.md`
- `01__DRAFT_VARIANTS.md`
- `02__DRAFT_CONFLICTS.md`

Rule:
> Any draft that aims for canon must declare intended output (what slot it fills).

---

## 6) L2 — CANON (APPROVED)

Folder: `03_CANON_L2/`

Canonical file standard:
- `00__CANON.md`  (single source canon card)
Optional:
- `01__CANON_APPENDIX.md`

Hard rules:
- Only one primary canon file: `00__CANON.md`
- L2 requires:
  - validator PASS
  - QA PASS
  - registry entry
  - provenance xref (DERIVED_FROM / PRODUCED_BY)

---

## 7) L3 — OUTPUT (PRODUCTION DERIVED)

Folder: `04_OUTPUT_L3/`

Output rules:
- Every L3 output must reference L2 canon via XREF: CANON_REF
- Outputs can be multiple (shots, art notes, voice lines, music cues, etc.)

Recommended files:
- `00__OUTPUT_INDEX.md` (list of outputs)
- `01__SCRIPT_LINES.md`
- `02__VISUAL_PROMPTS.md`
- `03__SHOTLIST.md`
- `04__AUDIO_NOTES.md`

---

## 8) REGISTRY + XREF INTEGRATION (MANDATORY)

### 8.1 Registry entry
This entity root folder must be registered:
- ID: <ENTITY_ID>
- TYPE: ENTITY
- PATH: `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/.../<ENTITY_FOLDER>/`
- STATUS/OWNER/LOCK

### 8.2 Required XREF indexes (recommended)
- entity graph: `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__ENTITY_GRAPH.md`
- canon refs: `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CANON_REFS.md`
- provenance: `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__PROVENANCE.md`
- changes: `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CHANGES.md`

---

## 9) ENGINE / ORC ROUTING (MANDATORY)

Declare which engines typically act on this entity kind:

ENGINES_RECOMMENDED:
- <ENG.* ids> (foundation/build/check/output)

ORCHESTRATORS_RECOMMENDED:
- <ORC.* ids> (pipelines)

Controllers / gates:
- CTL: [<CTL ids>]
- VAL: [<VAL ids>]
- QA: [<QA ids>]

---

## 10) SYSTEM INTERFACE (MANDATORY)

## SYSTEM INTERFACE
- INPUTS:
  - artifacts: [L0 intake items, external refs]
  - sources: [project goals, registries, xref indexes]
- OUTPUTS:
  - artifacts: [L1 drafts, L2 canon, L3 outputs]
  - target_path: `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/<CATEGORY>/<ENTITY_FOLDER>/...`
- REGISTRY_UPDATES:
  - required: YES
  - registries: [<project entity registry id/path>]
  - entries_to_add: [<ENTITY_ID registered>]
- XREF_UPDATES:
  - required: YES
  - record_types: [ENTITY_LINK, DERIVED_FROM, PRODUCED_BY, CANON_REF, REPLACED_BY]
  - xref_targets: [<project xref indexes>]
- GATES:
  - validators: [<VAL ids>]
  - qa_checks: [<QA ids>]
- ORCHESTRATION:
  - orc_owner: [<ORC ids>]
  - ctl_enforcers: [<CTL ids>]

---

## FINAL RULE (LOCK)

> Этот шаблон задаёт единую жизнь сущности в проекте.  
> Любой артефакт сущности должен жить внутри этой папки и быть связан через REG/XREF.

OWNER: Projects Workshop  
LOCK: FIXED
