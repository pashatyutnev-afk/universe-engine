# REGISTRY TEMPLATE — UNIVERSAL
FILE: 00__TEMPLATE__REGISTRY.md

SCOPE: Universe Engine Repository
LAYER: REG
DOC_TYPE: TEMPLATE
ENTITY_KIND: GENERIC
PROJECT_SCOPE: GLOBAL
OUTPUT_LEVEL: N/A
ID: REG.TEMPLATE.UNIVERSAL
STATUS: ACTIVE
VERSION: 2.0
ROLE: Universal template for any system registry (entities, artifacts, engines, pipelines, xref indexes). Defines existence rules and entry format.

---

## 0) PURPOSE (LAW)

Registry — это **слой существования**.
Он отвечает на вопросы:
- что существует в системе
- где это лежит (канонический путь)
- кто владелец
- какой статус / уровень (L0–L3)
- кто создал и чем (engine/orc)
- когда обновлялось

### EXISTENCE RULE
> Если объект/артефакт не внесён в Registry — он **не существует** для системы.

---

## 1) REGISTRY TYPE (MANDATORY)

REGISTRY_NAME: <human-readable name>
REGISTRY_ID: <REG.<DOMAIN>.<NAME>>
REGISTRY_SCOPE: <GLOBAL|PRJ:<PROJECT_ID>>
REGISTRY_TARGET:
- ENTITY_KIND: <CHR|LOC|OBJ|SYS|FAC|EVT|CPT|REL|ARC|STY|EXP|GENERIC>
- TRACKS: <ENTITIES|ARTIFACTS|ENGINES|ORCHESTRATORS|CONTROLLERS|VALIDATORS|QA_CHECKS|XREF_INDEXES|TEMPLATES>

---

## 2) CANON PATH RULE (MANDATORY)

CANON_PATH_RULE:
- Root must be one of:
  - 05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/...
  - 10_ENG__ENGINES/...
  - 20_ORC__ORCHESTRATORS/...
  - 40_CTL__CONTROLLERS/...
  - 50_VAL__VALIDATORS/...
  - 60_QA__QUALITY/...
  - 90_XREF__CROSSREF/...
  - 00_REG__REGISTRIES/...
  - 01_TPL__TEMPLATES/...

---

## 3) ENTRY FORMAT (MANDATORY)

Каждая запись — одна сущность/артефакт/документ.

### 3.1 Minimal Entry Fields (strict)
- ID: <canonical id>
- TYPE: <ENTITY|ARTIFACT|ENGINE|ORC|CTL|VAL|QA|XREF|REGISTRY|TEMPLATE|INDEX>
- ENTITY_KIND: <CHR|LOC|...|GENERIC>
- SCOPE: <GLOBAL|PRJ:<PROJECT_ID>>
- LEVEL: <L0_INTAKE|L1_DRAFT|L2_CANON|L3_OUTPUT|N/A>
- PATH: <canonical repo path>
- STATUS: <DRAFT|ACTIVE|DEPRECATED|ARCHIVED>
- OWNER: <team/person/system>
- LOCK: <OPEN|FIXED>
- CREATED_BY: <ENG.* or ORC.* or MANUAL>
- UPDATED_AT: <YYYY-MM-DD>
- NOTE: <1 line purpose>

### 3.2 Optional Fields (recommended)
- SOURCE_INPUTS: [<ids/paths>]
- PRODUCED_OUTPUTS: [<ids/paths>]
- XREF_INDEX: <path to xref index for this item>
- TAGS: [<...>]

---

## 4) REGISTRY OPERATIONS (STANDARD)

### 4.1 Add rule
When new item appears → add entry immediately.
- Entities: on creation of entity root folder (e.g., `CHR_<Name>/`)
- Artifacts: on creation of any L2_CANON or L3_OUTPUT file
- Engines/pipelines/validators/templates: on introduction into canon

### 4.2 Update rule
On changes to:
- PATH (moved/renamed)
- STATUS/LOCK
- LEVEL promotion (L0→L1→L2→L3)
- OWNER
Update `UPDATED_AT`.

### 4.3 Deprecation rule
When item is replaced:
- set STATUS: DEPRECATED
- add NOTE with “replaced by <ID>”
- ensure XREF record exists: `A -> B | TYPE:REPLACED_BY`

---

## 5) SYSTEM INTERFACE (MANDATORY FOR REGISTRIES)

## SYSTEM INTERFACE
- INPUTS:
  - artifacts: [new/changed items from any layer]
  - sources: [ENG outputs, ORC steps, manual edits]
- OUTPUTS:
  - artifacts: [registry entries]
  - target_path: 00_REG__REGISTRIES/<...>
- REGISTRY_UPDATES:
  - required: N/A (this is the registry)
  - registries: []
  - entries_to_add: [<entry lines>]
- XREF_UPDATES:
  - required: YES (when deprecating/replacing/moving)
  - record_types: [REPLACED_BY, MOVED_TO, RENAMED_TO]
  - xref_targets: [90_XREF__CROSSREF/<domain>/...]
- GATES:
  - validators: [VAL.REG.01.SCHEMA_CHECK]   # placeholder
  - qa_checks: [QA.REG.01.INTEGRITY_CHECK]  # placeholder
- ORCHESTRATION:
  - orc_owner: []
  - ctl_enforcers: [CTL.REG.01.ENTRY_ENFORCER] # placeholder

---

## 6) DEFAULT TABLE (COPY-PASTE)

Use this table style in concrete registries.

| ID | TYPE | ENTITY_KIND | SCOPE | LEVEL | PATH | STATUS | OWNER | LOCK | CREATED_BY | UPDATED_AT | NOTE |
|---|---|---|---|---|---|---|---|---|---|---|---|
| <...> | <...> | <...> | <...> | <...> | <...> | <...> | <...> | <...> | <...> | <...> | <...> |

---

## 7) EXAMPLE ENTRIES (REFERENCE)

| ID | TYPE | ENTITY_KIND | SCOPE | LEVEL | PATH | STATUS | OWNER | LOCK | CREATED_BY | UPDATED_AT | NOTE |
|---|---|---|---|---|---|---|---|---|---|---|---|
| ENG.NARR.02.STORY_STRUCTURE | ENGINE | GENERIC | GLOBAL | N/A | 10_ENG__ENGINES/02_DOMAIN_NARRATIVE_ENGINES/02__STORY_STRUCTURE_ENG.md | ACTIVE | Universe Engine | FIXED | MANUAL | 2026-01-05 | Narrative story structure engine |
| PRJ.ALPHA.CHR.AKIRA | ENTITY | CHR | PRJ:ALPHA | N/A | 05_PROJECTS/ALPHA/01_WORKSHOP/01_CHARACTERS/CHR_AKIRA/ | ACTIVE | Project ALPHA | OPEN | MANUAL | 2026-01-05 | Character root folder |
| PRJ.ALPHA.CHR.AKIRA.CANON | ARTIFACT | CHR | PRJ:ALPHA | L2_CANON | 05_PROJECTS/ALPHA/01_WORKSHOP/01_CHARACTERS/CHR_AKIRA/03_CANON_L2/00__CANON.md | ACTIVE | Project ALPHA | OPEN | ENG.CHAR.01.CHARACTER_CORE | 2026-01-05 | Approved character canon |

---

## FINAL RULE (LOCK)

> Этот шаблон используется для создания любых конкретных реестров системы.  
> Конкретные реестры обязаны ссылаться на этот стандарт.

OWNER: Universe Engine  
LOCK: FIXED
