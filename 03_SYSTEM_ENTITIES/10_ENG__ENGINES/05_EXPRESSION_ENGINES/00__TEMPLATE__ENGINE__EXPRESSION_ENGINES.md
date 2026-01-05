# ENG ENGINE TEMPLATE — EXPRESSION_ENGINES (FAMILY OVERLAY v2)
FILE: 00__TEMPLATE__ENGINE__EXPRESSION_ENGINES.md

SCOPE: Universe Engine
LAYER: ENG
DOC_TYPE: TEMPLATE
ENTITY_KIND: EXP
PROJECT_SCOPE: GLOBAL
OUTPUT_LEVEL: N/A
ID: ENG.TPL.ENGINE.EXPRESSION
STATUS: ACTIVE
VERSION: 2.0
ROLE: Family-specific overlay template for Expression engines. Compatible with ENG ENGINE TEMPLATE v2 and adds atom standard + cause-effect graph enforcement + boundary rules (no montage timing).

---

## 0) ENGINE IDENTITY (MANDATORY)

ENGINE_NAME: <UPPER_SNAKE_CASE>
ENGINE_ID: <ENG.EXP.<NN>.<ENGINE_NAME>>

FAMILY_CODE: EXP
ENGINE_NN_IN_FAMILY: <01..09>
ENGINE_CLASS: EXPRESSION
ENGINE_LEVEL: L3

ROLE_IN_FAMILY: <FOUNDATION|BUILDER|VALIDATOR|BRIDGE|OUTPUT>
PIPELINE_STAGE: <DEFINE|BUILD|CHECK|PACKAGE|PRODUCE>

OWNER: Universe Engine
LOCK: OPEN

---

## 1) PURPOSE (WHAT THIS ENGINE DOES)

One paragraph: which atom type(s) it defines/validates and how.

### OWNERSHIP
- define/validate atom schemas and outputs

### DOES NOT OWN (hard)
- narrative arc/scene ordering (NAR)
- editing timing/seconds/montage (08 editing)
- character psychology/dialogue (CHR)
- world law authoring (WLD)
- style authoring (STYLE)

---

## 2) TRIGGERS (WHEN TO RUN)

TRIGGERS:
- new arc/scene needs atoms
- causality unclear
- conflict needed for stakes
- turning point/climax/resolution not explicit
- scheduling needed (story logic)
- randomness needed as controlled factor

---

## 3) MINI-CONTRACT (MANDATORY)

CONSUMES (examples):
- NARRATIVE_REQUIREMENTS
- WORLD_CONSTRAINTS
- CHARACTER_CONSTRAINTS
- existing atom drafts/canon
- style constraints (optional)

PRODUCES (examples):
- EVENT_ATOM / CONFLICT_ATOM / ...
- CAUSE_EFFECT_LINK_SET
- EVENT_SCHEDULE
- ATOM_PACK

DEPENDS_ON:
- []  (if depends → mirror in XREF__DEPENDENCIES)

OUTPUT_ARTIFACT_TYPE:
- <EVENT_ATOM|CAUSE_EFFECT_LINK_SET|CONFLICT_ATOM|TURNING_POINT_ATOM|CLIMAX_ATOM|RESOLUTION_ATOM|SYSTEM_SHOCK_ATOM|EVENT_SCHEDULE|ATOM_PACK>

---

## 4) ATOM SCHEMA (MANDATORY)

Each atom must include:

ATOM_ID: <unique>
ATOM_TYPE: <EVENT|CAUSE_EFFECT|CONFLICT|TURNING_POINT|CLIMAX|RESOLUTION|SYSTEM_SHOCK|SCHEDULE|RANDOMNESS>
SUBJECTS: [<entity refs>]
CONTEXT:
  WHERE: <loc/system>
  WHEN: <epoch/story time>
TRIGGER: <what starts it>
PRESSURE: <what increases>
CHANGE: <what changes after>
CONSEQUENCES:
  - <cause-effect links>
DEPENDS_ON:
  - <world/character/narrative constraints>
CANON_LEVEL: <L1_DRAFT|L2_CANON>
XREF_POINTERS:
  - <links to XREF indexes>

Rule:
> Atom without CHANGE + CONSEQUENCES is invalid.

---

## 5) SYSTEM INTERFACE (MANDATORY) — EXPRESSION DEFAULTS

## SYSTEM INTERFACE
- OUTPUTS:
  - output_level: <L0_INTAKE|L1_DRAFT|L2_CANON|L3_OUTPUT>
  - entity_kind:
    - if atoms stored under arc: ARC
    - if stored as event entity: EVT/EXP
  - target_path_rule:
    - base: `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/`
    - category:
      - arc-local packs: `09_ARCS/ARC_<NAME>/`
      - event entities: `06_EVENTS/EVT_<NAME>/`
      - project packs: `05_PROJECT__L3/`
    - level_folder:
      - L0: `01_INTAKE_L0/`
      - L1: `02_DRAFT_L1/`
      - L2: `03_CANON_L2/`
      - L3: `04_OUTPUT_L3/`

- REGISTRY_UPDATES:
  - required: YES (for L2/L3)
  - registries:
    - `REG.PRJ.<PROJECT_ID>.CANON_L2`
    - `REG.PRJ.<PROJECT_ID>.OUTPUT_L3`
    - `REG.PRJ.<PROJECT_ID>.ENTITIES` (if events are entities)

- XREF_UPDATES:
  - required: YES
  - record_types:
    - [CAUSES, LEADS_TO, DEPENDS_ON, DERIVED_FROM, PRODUCED_BY, CANON_REF, CONFLICTS_WITH]
  - xref_targets:
    - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CAUSE_EFFECT_GRAPH.md`
    - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__DEPENDENCIES.md`
    - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__PROVENANCE.md`
    - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CANON_REFS.md`
    - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CONFLICTS.md`

- GATES:
  - validators:
    - `VAL.EXP.01.ATOM_SCHEMA_CHECK` (placeholder)
    - `VAL.EXP.02.CAUSE_EFFECT_GRAPH_REQUIRED` (placeholder)
  - qa_checks:
    - `QA.EXP.01.ATOM_USABILITY_FOR_NARRATIVE` (placeholder)

---

## 6) QUALITY (MANDATORY)

PASS if:
- atoms include CHANGE + CONSEQUENCES
- cause-effect edges are in XREF graph
- dependencies explicit (DEPENDS_ON)
- no montage timing included

FAIL if:
- atoms are only “описание” without change
- cause-effect exists only in prose
- hidden constraints

---

## 7) FAILURE MODES

- causality loop unclear → log conflict + require clarification
- scheduling tries to use seconds/timing → route to 08 editing
- atom contradicts world law → XREF CONFLICTS_WITH + route to world/governance

---

## 8) RAW LINK (MANDATORY)

RAW: <raw github link to this template file>

---

## FINAL RULE (LOCK)

> Expression outputs must be formal atoms with explicit change and explicit cause-effect graph.

OWNER: Universe Engine  
LOCK: OPEN
