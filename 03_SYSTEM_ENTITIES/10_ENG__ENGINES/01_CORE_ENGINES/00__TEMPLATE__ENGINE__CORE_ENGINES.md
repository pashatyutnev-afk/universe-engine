# ENG ENGINE TEMPLATE — CORE_ENGINES (FAMILY OVERLAY v2)
FILE: 00__TEMPLATE__ENGINE__CORE_ENGINES.md

SCOPE: Universe Engine
LAYER: ENG
DOC_TYPE: TEMPLATE
ENTITY_KIND: GENERIC
PROJECT_SCOPE: GLOBAL
OUTPUT_LEVEL: N/A
ID: ENG.TPL.ENGINE.CORE
STATUS: ACTIVE
VERSION: 2.0
ROLE: Family-specific overlay template for CORE engines. Compatible with ENG ENGINE TEMPLATE v2 and adds CORE defaults (entity routing, core artifact types, required REG/XREF).

---

## 0) ENGINE IDENTITY (MANDATORY)

ENGINE_NAME: <UPPER_SNAKE_CASE>
ENGINE_ID: <ENG.CORE.<NN>.<ENGINE_NAME>>

FAMILY_CODE: CORE
ENGINE_NN_IN_FAMILY: <01..03>
ENGINE_CLASS: CORE
ENGINE_LEVEL: L1

ROLE_IN_FAMILY: <FOUNDATION|BUILDER|VALIDATOR|BRIDGE|OUTPUT>
PIPELINE_STAGE: <DEFINE|BUILD|CHECK|PACKAGE|PRODUCE>

OWNER: Universe Engine
LOCK: OPEN

---

## 1) PURPOSE (WHAT THIS ENGINE DOES)

CORE engine defines minimal existence data.

### OWNERSHIP
- identity fields OR state snapshot OR lifecycle rules (depending on engine)

### DOES NOT OWN
- lore/meaning/story/psychology/world rules
- production assets and outputs

---

## 2) TRIGGERS (WHEN TO RUN)

TRIGGERS:
- new entity created (folder initialized)
- entity promoted to L1 draft
- attempt to canonize L2
- state change event (active/archived/deprecated)
- merge/split entity request

OUTPUT_CONFIDENCE_TARGET: HIGH for L2 core canon.

---

## 3) MINI-CONTRACT (MANDATORY)

CONSUMES (examples):
- ENTITY_INTAKE
- ENTITY_METADATA
- PROJECT_CONTEXT
- EXISTING_ENTITY_REG_ENTRY (optional)

PRODUCES (examples):
- CORE_CARD
- STATE_SNAPSHOT
- LIFECYCLE_RULESET
- CORE_MANIFEST (optional)

DEPENDS_ON:
- []  (if depends → must be mirrored in XREF DEPENDS_ON)

OUTPUT_ARTIFACT_TYPE:
- <CORE_CARD|STATE_SNAPSHOT|LIFECYCLE_RULESET|CORE_MANIFEST>

---

## 4) SYSTEM INTERFACE (MANDATORY) — CORE DEFAULTS

## SYSTEM INTERFACE
- INPUTS:
  - artifacts: [entity intake, drafts, existing canon]
  - sources:
    - project entities registry
    - project xref indexes
    - family README (core boundaries)

- OUTPUTS:
  - artifacts: [core artifacts]
  - output_level: <L0_INTAKE|L1_DRAFT|L2_CANON|L3_OUTPUT>
  - entity_kind: <CHR|LOC|OBJ|SYS|FAC|EVT|CPT|REL|ARC|STY|EXP|GENERIC>

  - target_path_rule:
    - base: `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/`
    - category: <by entity_kind>
    - entity_folder: `<KIND>_<ENTITY_NAME>`
    - level_folder:
      - L0: `01_INTAKE_L0/`
      - L1: `02_DRAFT_L1/`
      - L2: `03_CANON_L2/`
      - L3: `04_OUTPUT_L3/`

    - file examples:
      - L0: `00__CORE_INTAKE.md`
      - L1: `00__CORE_DRAFT.md`
      - L2: `00__CORE_CANON.md` (или секция inside `00__CANON.md`)
      - L3: `00__CORE_MANIFEST.md` (если нужно)

- REGISTRY_UPDATES:
  - required: YES (Entities registry всегда; L2 отдельный файл — в canon registry)
  - registries:
    - `REG.PRJ.<PROJECT_ID>.ENTITIES`
    - `REG.PRJ.<PROJECT_ID>.CANON_L2` (optional)
  - entries_to_add:
    - <ENTITY_ID + path + status + owner + lock>

- XREF_UPDATES:
  - required: YES (для lineage/canon refs при нужных переходах)
  - record_types:
    - [ENTITY_LINK, DERIVED_FROM, PRODUCED_BY, CANON_REF, REPLACED_BY, SPLIT_INTO, MERGED_INTO]
  - xref_targets:
    - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__ENTITY_GRAPH.md`
    - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__PROVENANCE.md`
    - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CANON_REFS.md`
    - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CHANGES.md` (for merge/split/replaced)
  - mandatory_links (examples):
    - `L2_CORE_CANON -> L1_CORE_DRAFT | TYPE:DERIVED_FROM | SCOPE:PRJ:<PROJECT_ID> | WHY:Core canonized | BY:ENG.CORE.<NN>.<ENGINE_NAME> | AT:<YYYY-MM-DD>`
    - `L3_MANIFEST -> L2_CORE_CANON | TYPE:CANON_REF | SCOPE:PRJ:<PROJECT_ID> | WHY:Manifest uses core canon | BY:ENG.CORE.<NN>.<ENGINE_NAME> | AT:<YYYY-MM-DD>`

- GATES:
  - validators:
    - `VAL.ENG.01.SCHEMA_HEADER_CHECK` (placeholder)
    - `VAL.REG.01.ENTITY_REG_INTEGRITY` (placeholder)
  - qa_checks:
    - `QA.ENG.01.READABILITY_COMPLETENESS` (placeholder)
    - `QA.XREF.01.LINK_INTEGRITY` (placeholder)

- ORCHESTRATION:
  - orc_owner:
    - [<ORC.CORE.* if used>]
  - ctl_enforcers:
    - `CTL.WORKSHOP.PATH_ENFORCER` (placeholder)
    - `CTL.WORKSHOP.LEVEL_ENFORCER` (placeholder)
    - `CTL.REG.ENTRY_ENFORCER` (placeholder)
    - `CTL.XREF.NO_ORPHANS` (placeholder)

---

## 5) PROCESS (HOW IT WORKS)

1) Normalize intake → create minimal identity fields
2) Create/update state snapshot
3) Validate lifecycle transitions (if applicable)
4) Write draft or canon depending on requested level
5) Update Entities Registry
6) Write provenance/canon_ref links when level >= L2 or outputs created

---

## 6) QUALITY (MANDATORY)

PASS if:
- entity has stable ID/kind/name/owner/status/lock/version
- registry entry exists and path is correct
- no duplicate entity root exists
- if L2: provenance exists and gates PASS

FAIL if:
- missing required identity fields
- wrong path/level
- L2 exists without DERIVED_FROM lineage
- merge/split done without XREF records

---

## 7) FAILURE MODES

- Duplicate entity folders → require MERGED_INTO or rename + changes xref
- State transition invalid → block promotion and route to lifecycle rules
- Registry mismatch (id/path) → block until synced

---

## 8) RAW LINK (MANDATORY)

RAW: <raw github link to this template file>

---

## FINAL RULE (LOCK)

> CORE engines define minimal existence of entities. Without CORE compliance, no canon promotion is allowed.

OWNER: Universe Engine  
LOCK: OPEN
