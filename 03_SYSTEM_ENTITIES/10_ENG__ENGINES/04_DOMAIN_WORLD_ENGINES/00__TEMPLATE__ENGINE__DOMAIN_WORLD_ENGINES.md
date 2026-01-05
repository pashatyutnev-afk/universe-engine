# ENG ENGINE TEMPLATE — DOMAIN_WORLD_ENGINES (FAMILY OVERLAY v2)
FILE: 00__TEMPLATE__ENGINE__DOMAIN_WORLD_ENGINES.md

SCOPE: Universe Engine
LAYER: ENG
DOC_TYPE: TEMPLATE
ENTITY_KIND: WORLD
PROJECT_SCOPE: GLOBAL
OUTPUT_LEVEL: N/A
ID: ENG.TPL.ENGINE.WORLD
STATUS: ACTIVE
VERSION: 2.0
ROLE: Family-specific overlay template for World engines. Compatible with ENG ENGINE TEMPLATE v2 and adds world defaults (world constraints, non-currency rule for great civilizations, REG/XREF requirements).

---

## 0) ENGINE IDENTITY (MANDATORY)

ENGINE_NAME: <UPPER_SNAKE_CASE>
ENGINE_ID: <ENG.WLD.<NN>.<ENGINE_NAME>>

FAMILY_CODE: WLD
ENGINE_NN_IN_FAMILY: <01..10>
ENGINE_CLASS: DOMAIN
ENGINE_LEVEL: L2

ROLE_IN_FAMILY: <FOUNDATION|BUILDER|VALIDATOR|BRIDGE|OUTPUT>
PIPELINE_STAGE: <DEFINE|BUILD|CHECK|PACKAGE|PRODUCE>

OWNER: Universe Engine
LOCK: OPEN

---

## 1) PURPOSE (WHAT THIS ENGINE DOES)

One paragraph: what world capability it defines.

### OWNERSHIP
- <world aspect this engine owns>

### DOES NOT OWN (hard)
- narrative scene ordering (NAR)
- character psychology/dialogue (CHR)
- style authoring (STYLE)
- production outputs (08)
- governance decisions (GOV)
- event atoms formalization (EXP)

---

## 2) TRIGGERS (WHEN TO RUN)

TRIGGERS:
- new project world seed
- new region/faction/system concept added
- timeline/epoch update
- tech/magic stack update
- economy/resource model requested
- contradiction detected (world conflict)
- narrative requests constraint clarification

---

## 3) MINI-CONTRACT (MANDATORY)

CONSUMES (examples):
- CORE_CARD (entity existence)
- NARRATIVE_REQUIREMENTS
- CHARACTER_REQUIREMENTS
- STYLE_CONSTRAINTS (presentation constraint)
- existing world canon/drafts

PRODUCES (examples):
- WORLD_BIBLE
- WORLD_LAWSET
- TIMELINE_PACK
- EPOCH_MAP
- CIVILIZATION_PROFILE_SET
- GEOPOLITICS_MAP
- ECON_RESOURCE_MODEL
- TECH_MAGIC_STACK
- MYTH_BELIEF_SYSTEM
- ECOLOGY_PROFILE
- WORLD_CONSTRAINTS_PACK

DEPENDS_ON:
- []  (if depends → mirror in XREF__DEPENDENCIES)

OUTPUT_ARTIFACT_TYPE:
- <WORLD_LAWSET|TIMELINE_PACK|ECON_RESOURCE_MODEL|WORLD_CONSTRAINTS_PACK|...>

---

## 4) SYSTEM INTERFACE (MANDATORY) — WORLD DEFAULTS

## SYSTEM INTERFACE
- INPUTS:
  - artifacts: [intake notes, drafts, canon constraints]
  - sources:
    - project registries
    - project xref indexes
    - family README boundary rules

- OUTPUTS:
  - artifacts: [world artifacts]
  - output_level: <L0_INTAKE|L1_DRAFT|L2_CANON|L3_OUTPUT>
  - entity_kind: <SYS|LOC|FAC|CPT|WORLD|GENERIC>

  - target_path_rule:
    - base: `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/`
    - category:
      - world system: `04_SYSTEMS/WORLD_<NAME>/`
      - locations: `02_LOCATIONS/LOC_<NAME>/`
      - factions: `05_FACTIONS/FAC_<NAME>/`
      - concepts: `07_CONCEPTS/CPT_<NAME>/`
      - project-level pack: `05_PROJECT__L3/`
    - level_folder:
      - L0: `01_INTAKE_L0/`
      - L1: `02_DRAFT_L1/`
      - L2: `03_CANON_L2/`
      - L3: `04_OUTPUT_L3/`

    - file examples:
      - L0: `00__WORLD_NOTES.md`
      - L1: `00__WORLD_DRAFT.md`
      - L2: `00__WORLD_BIBLE_CANON.md` / `01__TIMELINE_CANON.md`
      - L3: `00__WORLD_CONSTRAINTS_PACK.md`

- REGISTRY_UPDATES:
  - required: YES (for L2/L3)
  - registries:
    - `REG.PRJ.<PROJECT_ID>.ENTITIES`
    - `REG.PRJ.<PROJECT_ID>.CANON_L2`
    - `REG.PRJ.<PROJECT_ID>.OUTPUT_L3`

- XREF_UPDATES:
  - required: YES
  - record_types:
    - [DEPENDS_ON, DERIVED_FROM, PRODUCED_BY, CANON_REF, ENTITY_LINK, CONFLICTS_WITH, REPLACED_BY]
  - xref_targets:
    - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__ENTITY_GRAPH.md`
    - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__DEPENDENCIES.md`
    - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__PROVENANCE.md`
    - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CANON_REFS.md`
    - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CONFLICTS.md`
    - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CHANGES.md` (replacements)
  - mandatory_links (examples):
    - `L2_WORLD_BIBLE -> L1_WORLD_DRAFT | TYPE:DERIVED_FROM | SCOPE:PRJ:<PROJECT_ID> | WHY:Canonized world bible | BY:ENG.WLD.<NN>.<ENGINE_NAME> | AT:<YYYY-MM-DD>`
    - `L3_CONSTRAINTS_PACK -> L2_WORLD_BIBLE | TYPE:CANON_REF | SCOPE:PRJ:<PROJECT_ID> | WHY:Pack derived from canon | BY:ENG.WLD.<NN>.<ENGINE_NAME> | AT:<YYYY-MM-DD>`

- GATES:
  - validators:
    - `VAL.WLD.01.COHERENCE_CHECK` (placeholder)
    - `VAL.WLD.02.NO_CURRENCY_GREAT_CIV` (placeholder; see family rule)
  - qa_checks:
    - `QA.WLD.01.USABILITY_FOR_OTHER_LAYERS` (placeholder)
    - `QA.XREF.01.LINK_INTEGRITY` (placeholder)

- ORCHESTRATION:
  - orc_owner: [<ORC.WLD.* if used>]
  - ctl_enforcers:
    - `CTL.WORKSHOP.PATH_ENFORCER` (placeholder)
    - `CTL.WORKSHOP.LEVEL_ENFORCER` (placeholder)
    - `CTL.XREF.NO_HIDDEN_LINKS` (placeholder)
    - `CTL.REG.ENTRY_ENFORCER` (placeholder)

---

## 5) PROCESS (HOW IT WORKS)

1) Consume requests + constraints from narrative/character
2) Build world component (law/timeline/civ/econ/tech/ecology)
3) Validate coherence (tech↔econ↔ecology↔timeline)
4) Enforce no-currency rule for great civilizations
5) Canonize + register + provenance + dependency links
6) Produce constraints pack for other families

---

## 6) QUALITY (MANDATORY)

PASS if:
- constraints pack is explicit and linkable
- no-currency rule respected or exception logged
- dependencies are explicit in XREF
- L3 outputs reference L2 canon via CANON_REF

FAIL if:
- hidden dependencies
- contradictions not logged
- great civilization uses currency without exception record

---

## 7) FAILURE MODES

- World contradiction detected → XREF CONFLICTS_WITH + route to governance decision
- Economy model accidentally includes currency in great civ → block until rewritten or exception approved
- Timeline breaks causality → require epoch correction and provenance update

---

## 8) RAW LINK (MANDATORY)

RAW: <raw github link to this template file>

---

## FINAL RULE (LOCK)

> World engines define reality constraints. Everything else must reference them explicitly. Great civilizations do not use currency.

OWNER: Universe Engine  
LOCK: OPEN
