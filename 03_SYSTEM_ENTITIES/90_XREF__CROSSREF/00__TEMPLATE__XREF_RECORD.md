# XREF RECORD TEMPLATE — UNIVERSAL LINK UNIT
FILE: 00__TEMPLATE__XREF_RECORD.md

SCOPE: Universe Engine Repository
LAYER: XREF
DOC_TYPE: TEMPLATE
ENTITY_KIND: GENERIC
PROJECT_SCOPE: GLOBAL
OUTPUT_LEVEL: N/A
ID: XREF.TEMPLATE.RECORD
STATUS: ACTIVE
VERSION: 2.0
ROLE: Universal template for a single cross-reference record that expresses a relationship between two IDs (entities, artifacts, engines, registries, outputs). Enforces no hidden dependencies.

---

## 0) PURPOSE (LAW)

XREF Record — это атом связи.
Он фиксирует:
- кто с кем связан (A → B)
- какой тип связи
- почему (WHY)
- в каком контексте (SCOPE)
- кто создал/поддерживает (BY)
- где лежит связь (TARGET INDEX)

### NO HIDDEN LINKS RULE
> Любая зависимость/производность/ссылка, не отражённая XREF record — считается **hidden / invalid**.

---

## 1) XREF RECORD HEADER (MANDATORY)

XREF_ID: <XREF.<DOMAIN>.<NAME> or generated id>
SCOPE: <GLOBAL|PRJ:<PROJECT_ID>>
LINK_TYPE: <see section 2>
A_ID: <canonical id>
B_ID: <canonical id>
A_PATH: <optional canonical path>
B_PATH: <optional canonical path>
BY: <ENG.* | ORC.* | CTL.* | MANUAL>
CREATED_AT: <YYYY-MM-DD>
UPDATED_AT: <YYYY-MM-DD>
STATUS: <ACTIVE|DEPRECATED>
NOTE: <1 line>

---

## 2) LINK TYPE CATALOG (STANDARD)

Choose exactly one primary LINK_TYPE.
Optional: add SUBTYPE.

### 2.1 Dependency / build graph
- DEPENDS_ON
- REQUIRED_FOR
- BLOCKS
- UNBLOCKS

### 2.2 Provenance / derivation
- DERIVED_FROM
- PRODUCED_BY
- INPUT_FOR

### 2.3 Canon / reference
- CANON_REF          (output or draft references canon)
- CANON_SOURCE_OF    (canon is source of something)

### 2.4 Production links
- PRODUCTION_REF     (output references production inputs)
- OUTPUT_OF          (this artifact is output of engine/pipeline)

### 2.5 Entity graph
- ENTITY_LINK        (relationship between entities)
- MEMBER_OF          (entity belongs to faction/system)
- LOCATED_IN         (entity location link)
- OWNS / OWNED_BY

### 2.6 Change / replacement / movement
- REPLACED_BY
- MOVED_TO
- RENAMED_TO
- SPLIT_INTO
- MERGED_INTO

### 2.7 Conflict / exclusion
- CONFLICTS_WITH
- DUPLICATES
- MUTUALLY_EXCLUSIVE

---

## 3) REQUIRED WHY + EVIDENCE (MANDATORY)

WHY: <short justification in one sentence>

EVIDENCE:
- SOURCE: <path/url/id>
- EXTRACT: <short quote or summary>
- CONFIDENCE: <LOW|MEDIUM|HIGH>

If WHY is missing → record invalid.

---

## 4) REGISTRY INTEGRATION (MANDATORY)

Every XREF record MUST be compatible with registries.

REG_LINKS:
- A_REGISTRY: <REG id/path or []>
- B_REGISTRY: <REG id/path or []>

If A or B does not exist in registry:
- record is allowed only if STATUS:DRAFT and NOTE explains why.

---

## 5) SYSTEM INTERFACE (MANDATORY)

## SYSTEM INTERFACE
- INPUTS:
  - artifacts: [A_ID, B_ID, supporting artifacts]
  - sources: [engine outputs, orchestrator steps, manual decisions]
- OUTPUTS:
  - artifacts: [xref record entry]
  - target_path: 90_XREF__CROSSREF/<domain>/<xref_index>.md
- REGISTRY_UPDATES:
  - required: YES
  - registries: [REG.XREF.INDEXES]   # placeholder id
  - entries_to_add: [this xref record registered]
- XREF_UPDATES:
  - required: N/A (this is xref record)
  - record_types: []
  - xref_targets: []
- GATES:
  - validators: [VAL.XREF.01.SCHEMA_CHECK]   # placeholder
  - qa_checks: [QA.XREF.01.INTEGRITY_CHECK]  # placeholder
- ORCHESTRATION:
  - orc_owner: []
  - ctl_enforcers: [CTL.XREF.01.NO_HIDDEN_LINKS] # placeholder

---

## 6) CANONICAL ONE-LINE FORMAT (FOR INDEX TABLES)

Use this normalized line inside XREF indexes:

`<A_ID> -> <B_ID> | TYPE:<LINK_TYPE> | SCOPE:<...> | WHY:<...> | BY:<...> | AT:<YYYY-MM-DD>`

---

## 7) EXAMPLES (REFERENCE)

### Example: Dependency
`ENG.NARR.04.SCENE_CONSTRUCTION -> ENG.NARR.02.STORY_STRUCTURE | TYPE:DEPENDS_ON | SCOPE:GLOBAL | WHY:Scene construction requires story structure constraints | BY:MANUAL | AT:2026-01-05`

### Example: Output derived from canon
`PRJ.ALPHA.FILM.EP01.SHOTLIST -> PRJ.ALPHA.NARR.CANON | TYPE:CANON_REF | SCOPE:PRJ:ALPHA | WHY:Shotlist must reference approved canon | BY:ORC.PROD.01.SHOT_PIPELINE | AT:2026-01-05`

### Example: Entity relationship
`PRJ.ALPHA.CHR.AKIRA -> PRJ.ALPHA.FAC.ARK | TYPE:MEMBER_OF | SCOPE:PRJ:ALPHA | WHY:Akira is member of Ark faction | BY:ENG.CHAR.06.RELATIONSHIP | AT:2026-01-05`

---

## FINAL RULE (LOCK)

> Этот шаблон определяет единицу связи XREF.  
> Все XREF index файлы обязаны хранить записи в нормализованном one-line формате.

OWNER: Universe Engine  
LOCK: FIXED
