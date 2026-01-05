# ENG ENGINE TEMPLATE — KNOWLEDGE_PRODUCTION_ENGINES (FAMILY OVERLAY v2)
FILE: 00__TEMPLATE__ENGINE__KNOWLEDGE_PRODUCTION_ENGINES.md

SCOPE: Universe Engine
LAYER: ENG
DOC_TYPE: TEMPLATE
ENTITY_KIND: PRD
PROJECT_SCOPE: GLOBAL
OUTPUT_LEVEL: N/A
ID: ENG.TPL.ENGINE.PRODUCTION
STATUS: ACTIVE
VERSION: 2.0
ROLE: Family-specific overlay template for Production engines. Compatible with ENG ENGINE TEMPLATE v2 and adds production pack schema + asset/edit xref requirements.

---

## 0) ENGINE IDENTITY (MANDATORY)

ENGINE_NAME: <UPPER_SNAKE_CASE>
ENGINE_ID: <ENG.PRD.<NN>.<ENGINE_NAME>>

FAMILY_CODE: PRD
ENGINE_NN_IN_FAMILY: <01..08>
ENGINE_CLASS: PRODUCTION
ENGINE_LEVEL: L3

ROLE_IN_FAMILY: <FOUNDATION|BUILDER|VALIDATOR|BRIDGE|OUTPUT>
PIPELINE_STAGE: <DEFINE|BUILD|CHECK|PACKAGE|PRODUCE>

OWNER: Universe Engine
LOCK: OPEN

---

## 1) PURPOSE (WHAT THIS ENGINE DOES)

One paragraph: what production capability it defines (composition/style/camera/light/gen/edit/sound) and which artifacts it produces.

### DOES NOT OWN (hard)
- deep music composition (09)
- story-time rhythm (NAR pacing)
- canon story/world/character decisions

---

## 2) TRIGGERS (WHEN TO RUN)

TRIGGERS:
- need to produce assets for an episode/short/chapter adaptation
- style/format constraints updated
- narrative pack updated
- montage pass required
- sound pass required

---

## 3) MINI-CONTRACT (MANDATORY)

CONSUMES (examples):
- NARRATIVE_OUTLINE / NARRATIVE_OUTPUT_PACK
- STYLE_CONSTRAINTS_PACK
- FORMAT_CONSTRAINTS_PACK + DELIVERY_SPEC
- WORLD_CONSTRAINTS_PACK
- CHARACTER_CANON (if needed)

PRODUCES (examples):
- SHOTLIST
- ASSET_SET
- EDIT_PLAN
- SOUND_PLAN
- EXPORT_SPEC
- FINAL_EXPORTS
- PRODUCTION_PACK

DEPENDS_ON:
- []  (if depends → mirror in XREF__DEPENDENCIES)

OUTPUT_ARTIFACT_TYPE:
- <SHOTLIST|ASSET_SET|EDIT_PLAN|SOUND_PLAN|FINAL_EXPORTS|PRODUCTION_PACK>

---

## 4) PRODUCTION PACK SCHEMA (MANDATORY)

PROD_PACK_ID: <unique>
INPUT_CANON_REFS:
  - <CANON_REF to narrative L2/L3>
  - <DEPENDS_ON to format delivery spec>
  - <DEPENDS_ON to style pack>
  - <DEPENDS_ON to world constraints>
ASSET_LIST:
  IMAGES: [ ... ]
  VIDEO: [ ... ]
  AUDIO: [ ... ]
SHOTLIST:
  - SHOT_ID: ...
    SOURCE: <scene/beat reference>
    NOTES: <non-canon production notes>
EDIT_PLAN:
  RHYTHM: <screen-time rhythm notes>
  CUT_RULES: [ ... ]
SOUND_PLAN:
  SYNC_NOTES: ...
  CLARITY_NOTES: ...
  MUSIC_PLACEMENT_NOTES: <placement only, not composition>
EXPORT_SPEC:
  DELIVERABLES: [ ... ]
PROVENANCE:
  DERIVED_FROM: [ ... ]
XREF_POINTERS:
  - <xref links>

Rule:
> PROD_PACK must include INPUT_CANON_REFS and EXPORT_SPEC.

---

## 5) SYSTEM INTERFACE (MANDATORY) — PRODUCTION DEFAULTS

## SYSTEM INTERFACE
- OUTPUTS:
  - output_level: <L1_DRAFT|L2_CANON|L3_OUTPUT>
  - target_path_rule:
    - base: `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/`
    - category: `12_PRODUCTION/`
    - subfolders:
      - plans: `01_PLANS/`
      - assets: `02_ASSETS/`
      - edits: `03_EDITS/`
      - exports: `04_EXPORTS/`
    - level_folder:
      - L1: `02_DRAFT_L1/`
      - L2: `03_CANON_L2/`
      - L3: `04_OUTPUT_L3/`

- REGISTRY_UPDATES:
  - required: YES
  - registries:
    - `REG.PRJ.<PROJECT_ID>.OUTPUT_L3`
    - `REG.PRJ.<PROJECT_ID>.ASSETS` (if used)
    - `REG.PRJ.<PROJECT_ID>.CANON_L2` (if plan canonized)

- XREF_UPDATES:
  - required: YES
  - record_types:
    - [DEPENDS_ON, CANON_REF, DERIVED_FROM, PRODUCED_BY, ASSET_LINK, EDIT_DECISION]
  - xref_targets:
    - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CANON_REFS.md`
    - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__DEPENDENCIES.md`
    - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__PROVENANCE.md`
    - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__ASSET_GRAPH.md`
    - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__EDIT_DECISIONS.md`

- GATES:
  - validators:
    - `VAL.PRD.01.CANON_LINKS_PRESENT` (placeholder)
    - `VAL.PRD.02.EXPORT_SPEC_PRESENT` (placeholder)
  - qa_checks:
    - `QA.PRD.01.DELIVERABLES_MATCH_FORMAT` (placeholder)
    - `QA.PRD.02.MONTAGE_COHERENCE` (placeholder)

---

## 6) QUALITY (MANDATORY)

PASS if:
- has CANON_REF/DEPENDS_ON to narrative/style/format/world
- export spec matches delivery spec
- edit plan is explicit (screen-time)
- sound plan is placement/clarity (no deep composition)

FAIL if:
- production pack “changes canon”
- missing xref links
- includes deep music composition tasks (route to 09)

---

## FINAL RULE (LOCK)

> Production engines produce media artifacts and screen-time rhythm. They must remain linked to canon constraints and not rewrite canon.

OWNER: Universe Engine  
LOCK: OPEN
