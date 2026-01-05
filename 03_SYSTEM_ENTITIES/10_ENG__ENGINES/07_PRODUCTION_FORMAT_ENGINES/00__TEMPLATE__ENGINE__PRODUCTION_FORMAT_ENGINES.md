# ENG ENGINE TEMPLATE — PRODUCTION_FORMAT_ENGINES (FAMILY OVERLAY v2)
FILE: 00__TEMPLATE__ENGINE__PRODUCTION_FORMAT_ENGINES.md

SCOPE: Universe Engine
LAYER: ENG
DOC_TYPE: TEMPLATE
ENTITY_KIND: FMT
PROJECT_SCOPE: GLOBAL
OUTPUT_LEVEL: N/A
ID: ENG.TPL.ENGINE.FORMAT
STATUS: ACTIVE
VERSION: 2.0
ROLE: Family-specific overlay template for Format engines. Compatible with ENG ENGINE TEMPLATE v2 and adds format constraints schema + handoff rules.

---

## 0) ENGINE IDENTITY (MANDATORY)

ENGINE_NAME: <UPPER_SNAKE_CASE>
ENGINE_ID: <ENG.FMT.<NN>.<ENGINE_NAME>>

FAMILY_CODE: FMT
ENGINE_NN_IN_FAMILY: <01..08>
ENGINE_CLASS: PRODUCTION
ENGINE_LEVEL: L3

ROLE_IN_FAMILY: <FOUNDATION|BUILDER|VALIDATOR|BRIDGE|OUTPUT>
PIPELINE_STAGE: <DEFINE|BUILD|CHECK|PACKAGE|PRODUCE>

OWNER: Universe Engine
LOCK: OPEN

---

## 1) PURPOSE (WHAT THIS ENGINE DOES)

One paragraph: what format rule-set it outputs and who consumes it.

### OWNERSHIP
- format constraints and delivery specification

### DOES NOT OWN (hard)
- story arc/scene ordering (NAR)
- event atoms (EXP)
- style authoring (STY)
- editing timing/seconds (08)
- world law authoring (WLD)
- character psychology/dialogue (CHR)

---

## 2) TRIGGERS (WHEN TO RUN)

TRIGGERS:
- project selects or changes format
- need delivery spec for production
- narrative outline must be adapted to format units
- platform constraints change

---

## 3) MINI-CONTRACT (MANDATORY)

CONSUMES (examples):
- NARRATIVE_CANON_OUTLINE (L2)
- STYLE_CONSTRAINTS_PACK
- WORLD_CONSTRAINTS_PACK
- constraints from production capacity (optional)

PRODUCES (examples):
- FORMAT_CONSTRAINTS_PACK
- DELIVERY_SPEC
- UNIT_TEMPLATE
- ADAPTATION_MAP

DEPENDS_ON:
- []  (if depends → mirror in XREF__DEPENDENCIES)

OUTPUT_ARTIFACT_TYPE:
- <FORMAT_CONSTRAINTS_PACK|DELIVERY_SPEC|UNIT_TEMPLATE|ADAPTATION_MAP>

---

## 4) FORMAT SCHEMA (MANDATORY)

FORMAT_ID: <unique>
FORMAT_TYPE: <BOOK|SERIES|SHORT|YTLONG|GAME>

UNIT_DEFINITION:
  UNIT_NAME: <chapter|episode|short|quest>
  REQUIRED_FIELDS: [title, hook, turn, payoff, ...]  # pattern fields
  OPTIONAL_FIELDS: [...]

DELIVERABLES:
  - <deliverable name + expected file kind>

STRUCTURE_RULES:
  - <pattern rules, no plot content, no seconds>

LENGTH_RANGE:
  - <min..max>  # units: pages/minutes/words (choose), no montage timing

CADENCE:
  OPTIONAL: true|false
  RULES: <release cadence rules if used>

HANDOFF_TO_NARRATIVE:
  REQUIRED_FROM_OUTLINE:
    - <what narrative must provide>

HANDOFF_TO_PRODUCTION:
  REQUIRED_ARTIFACTS:
    - <what production must produce>

Rule:
> format schema must be explicit, иначе его нельзя использовать как constraints.

---

## 5) SYSTEM INTERFACE (MANDATORY) — FORMAT DEFAULTS

## SYSTEM INTERFACE
- OUTPUTS:
  - output_level: <L1_DRAFT|L2_CANON|L3_OUTPUT>
  - target_path_rule:
    - base: `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/`
    - category: `11_FORMAT/`
    - level_folder:
      - L1: `02_DRAFT_L1/`
      - L2: `03_CANON_L2/`
      - L3: `04_OUTPUT_L3/`

- REGISTRY_UPDATES:
  - required: YES
  - registries:
    - `REG.PRJ.<PROJECT_ID>.CANON_L2`
    - `REG.PRJ.<PROJECT_ID>.OUTPUT_L3`

- XREF_UPDATES:
  - required: YES
  - record_types:
    - [DEPENDS_ON, DERIVED_FROM, CANON_REF, PRODUCED_BY]
  - xref_targets:
    - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__DEPENDENCIES.md`
    - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__PROVENANCE.md`
    - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CANON_REFS.md`
  - mandatory_links (examples):
    - `L2_FORMAT_CANON -> STYLE_PACK | TYPE:DEPENDS_ON | ...`
    - `L3_DELIVERY_SPEC -> L2_FORMAT_CANON | TYPE:CANON_REF | ...`

- GATES:
  - validators:
    - `VAL.FMT.01.DELIVERABLES_PRESENT` (placeholder)
    - `VAL.FMT.02.UNIT_TEMPLATE_VALID` (placeholder)

---

## 6) QUALITY (MANDATORY)

PASS if:
- deliverables clear
- unit template explicit
- length range defined (no montage seconds)
- handoffs to narrative/production explicit
- dependencies explicit

FAIL if:
- format doc becomes story outline
- missing deliverables or unit schema
- timing/montage instructions included

---

## FINAL RULE (LOCK)

> Format engines define packaging constraints and deliverables, not plot.

OWNER: Universe Engine  
LOCK: OPEN
