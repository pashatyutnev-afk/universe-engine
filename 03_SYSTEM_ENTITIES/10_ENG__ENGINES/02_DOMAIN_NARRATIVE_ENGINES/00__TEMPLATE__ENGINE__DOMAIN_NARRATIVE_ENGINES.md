# ENG ENGINE TEMPLATE — DOMAIN_NARRATIVE_ENGINES (FAMILY OVERLAY v2)
FILE: 00__TEMPLATE__ENGINE__DOMAIN_NARRATIVE_ENGINES.md

SCOPE: Universe Engine
LAYER: ENG
DOC_TYPE: TEMPLATE
ENTITY_KIND: GENERIC
PROJECT_SCOPE: GLOBAL
OUTPUT_LEVEL: N/A
ID: ENG.TPL.ENGINE.NARRATIVE
STATUS: ACTIVE
VERSION: 2.0
ROLE: Family-specific overlay template for Narrative engines. Compatible with ENG ENGINE TEMPLATE v2 and adds narrative defaults (story-time outputs, boundary rules, REG/XREF requirements, format/style/world/character interfaces).

---

## 0) ENGINE IDENTITY (MANDATORY)

ENGINE_NAME: <UPPER_SNAKE_CASE>
ENGINE_ID: <ENG.NAR.<NN>.<ENGINE_NAME>>

FAMILY_CODE: NAR
ENGINE_NN_IN_FAMILY: <01..10>
ENGINE_CLASS: DOMAIN
ENGINE_LEVEL: L2

ROLE_IN_FAMILY: <FOUNDATION|BUILDER|VALIDATOR|BRIDGE|OUTPUT>
PIPELINE_STAGE: <DEFINE|BUILD|CHECK|PACKAGE|PRODUCE>

OWNER: Universe Engine
LOCK: OPEN

---

## 1) PURPOSE (WHAT THIS ENGINE DOES)

One paragraph: what narrative capability it provides.

### OWNERSHIP
- story logic/structure/arc/scene/continuity/theme aspects (depending on engine)

### DOES NOT OWN (hard)
- event atoms (EXPRESSION)
- editing rhythm (PRODUCTION/EDITING)
- deep character psychology/dialogue craft (CHARACTER)
- world law authoring (WORLD)
- genre style authoring (STYLE)

---

## 2) TRIGGERS (WHEN TO RUN)

TRIGGERS:
- new project narrative seed
- new arc/season/book outline requested
- format change (book → series/shorts/game)
- world/character constraints changed
- continuity conflict detected
- pacing/tension adjustments requested

---

## 3) MINI-CONTRACT (MANDATORY)

CONSUMES (examples):
- CORE_CARD (entities involved)
- WORLD_CONSTRAINTS
- CHARACTER_ARC / MOTIVATION
- FORMAT_CONSTRAINTS
- STYLE_CONSTRAINTS
- EXPRESSION_ATOMS (events/conflicts/resolutions as provided units)

PRODUCES (examples):
- STORY_BLUEPRINT
- BEAT_SHEET
- ARC_MAP
- SCENE_LIST
- CONTINUITY_MAP
- THEME_MAP
- FORMAT_ADAPTED_OUTLINE

DEPENDS_ON:
- []  (if depends → mirrored in XREF__DEPENDENCIES)

OUTPUT_ARTIFACT_TYPE:
- <STORY_BLUEPRINT|BEAT_SHEET|ARC_MAP|SCENE_LIST|CONTINUITY_MAP|THEME_MAP|FORMAT_ADAPTED_OUTLINE>

---

## 4) SYSTEM INTERFACE (MANDATORY) — NARRATIVE DEFAULTS

## SYSTEM INTERFACE
- INPUTS:
  - artifacts: [intake, drafts, canon constraints, expression atoms]
  - sources:
    - project registries
    - project xref indexes
    - family README boundary rules

- OUTPUTS:
  - artifacts: [narrative artifacts]
  - output_level: <L0_INTAKE|L1_DRAFT|L2_CANON|L3_OUTPUT>
  - entity_kind: <ARC|EVT|GENERIC>
  - target_path_rule:
    - base: `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/`
    - category:
      - ARC outputs: `09_ARCS/<ARC_NAME>/`
      - project-level packs: `05_PROJECT__L3/`
    - level_folder:
      - L0: `01_INTAKE_L0/`
      - L1: `02_DRAFT_L1/`
      - L2: `03_CANON_L2/`
      - L3: `04_OUTPUT_L3/`

    - file examples:
      - L0: `00__NARRATIVE_SEED.md`
      - L1: `00__OUTLINE_DRAFT.md`
      - L2: `00__OUTLINE_CANON.md` + `01__SCENE_LIST_CANON.md`
      - L3: `00__FORMAT_PACK_<BOOK|SERIES|SHORT|GAME>.md`

- REGISTRY_UPDATES:
  - required: YES (for L2/L3)
  - registries:
    - `REG.PRJ.<PROJECT_ID>.CANON_L2`
    - `REG.PRJ.<PROJECT_ID>.OUTPUT_L3`
  - entries_to_add:
    - <artifact id/path + level + status + produced_by>

- XREF_UPDATES:
  - required: YES
  - record_types:
    - [DEPENDS_ON, DERIVED_FROM, PRODUCED_BY, CANON_REF, ENTITY_LINK, CONFLICTS_WITH]
  - xref_targets:
    - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__DEPENDENCIES.md`
    - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__PROVENANCE.md`
    - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CANON_REFS.md`
    - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__ENTITY_GRAPH.md`
    - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CONFLICTS.md`
  - mandatory_links (examples):
    - `L2_OUTLINE -> L1_OUTLINE_DRAFT | TYPE:DERIVED_FROM | SCOPE:PRJ:<PROJECT_ID> | WHY:Outline canonized | BY:ENG.NAR.<NN>.<ENGINE_NAME> | AT:<YYYY-MM-DD>`
    - `L3_FORMAT_PACK -> L2_OUTLINE | TYPE:CANON_REF | SCOPE:PRJ:<PROJECT_ID> | WHY:Output derived from canon outline | BY:ENG.NAR.<NN>.<ENGINE_NAME> | AT:<YYYY-MM-DD>`
    - `L2_OUTLINE -> WORLD_CANON | TYPE:DEPENDS_ON | SCOPE:PRJ:<PROJECT_ID> | WHY:World constraints | BY:ENG.NAR.<NN>.<ENGINE_NAME> | AT:<YYYY-MM-DD>`
    - `L2_OUTLINE -> FORMAT_RULES | TYPE:DEPENDS_ON | SCOPE:PRJ:<PROJECT_ID> | WHY:Format constraints | BY:ENG.NAR.<NN>.<ENGINE_NAME> | AT:<YYYY-MM-DD>`

- GATES:
  - validators:
    - `VAL.NAR.01.CONTINUITY_CHECK` (placeholder)
    - `VAL.REG.02.CANON_ENTRY_CHECK` (placeholder)
  - qa_checks:
    - `QA.NAR.01.OUTLINE_USABILITY` (placeholder)
    - `QA.XREF.01.LINK_INTEGRITY` (placeholder)

- ORCHESTRATION:
  - orc_owner: [<ORC.NAR.* if used>]
  - ctl_enforcers:
    - `CTL.WORKSHOP.PATH_ENFORCER` (placeholder)
    - `CTL.WORKSHOP.LEVEL_ENFORCER` (placeholder)
    - `CTL.XREF.NO_ORPHANS` (placeholder)
    - `CTL.XREF.NO_HIDDEN_LINKS` (placeholder)

---

## 5) PROCESS (HOW IT WORKS)

1) Consume constraints (world/character/style/format) + expression atoms
2) Build story blueprint (outline)
3) Build arc map + scene list
4) Validate continuity / pacing / stakes
5) Canonize (L2) + register + provenance
6) Produce format pack (L3) if needed (still story-time, no editing)

---

## 6) QUALITY (MANDATORY)

PASS if:
- outline/scene list is complete and navigable
- continuity conflicts resolved or logged
- dependencies are explicit in XREF DEPENDS_ON
- L3 outputs reference L2 canon via CANON_REF
- boundaries respected (no event-atom authoring inside narrative file; reference EXPRESSION outputs)

FAIL if:
- hidden dependencies
- L2 without provenance
- L3 without canon ref
- mixing story-time rhythm with editing rhythm instructions

---

## 7) FAILURE MODES

- Continuity break detected → create XREF CONFLICTS_WITH + require fix
- Format constraints change → require new L3 pack referencing same L2 outline or re-canonize outline if structural changes
- Story-time vs screen-time confusion → route editing notes to 08 editing engine

---

## 8) RAW LINK (MANDATORY)

RAW: <raw github link to this template file>

---

## FINAL RULE (LOCK)

> Narrative engines produce story-time structures. They must remain traceable and boundary-safe (EXPRESSION atoms, EDITING rhythm separated).

OWNER: Universe Engine  
LOCK: OPEN
