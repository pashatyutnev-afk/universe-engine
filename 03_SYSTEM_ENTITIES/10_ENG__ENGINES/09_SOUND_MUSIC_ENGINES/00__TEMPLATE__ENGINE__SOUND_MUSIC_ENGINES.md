# ENG ENGINE TEMPLATE — SOUND_MUSIC_ENGINES (FAMILY OVERLAY v2)
FILE: 00__TEMPLATE__ENGINE__SOUND_MUSIC_ENGINES.md

SCOPE: Universe Engine
LAYER: ENG
DOC_TYPE: TEMPLATE
ENTITY_KIND: MUS
PROJECT_SCOPE: GLOBAL
OUTPUT_LEVEL: N/A
ID: ENG.TPL.ENGINE.MUSIC
STATUS: ACTIVE
VERSION: 2.0
ROLE: Family-specific overlay template for Music engines. Compatible with ENG ENGINE TEMPLATE v2 and adds music pack schema + strict boundary with 08 production sound.

---

## 0) ENGINE IDENTITY (MANDATORY)

ENGINE_NAME: <UPPER_SNAKE_CASE>
ENGINE_ID: <ENG.MUS.<NN>.<ENGINE_NAME>>

FAMILY_CODE: MUS
ENGINE_NN_IN_FAMILY: <01..13>
ENGINE_CLASS: SOUND
ENGINE_LEVEL: L3

ROLE_IN_FAMILY: <FOUNDATION|BUILDER|VALIDATOR|BRIDGE|OUTPUT>
PIPELINE_STAGE: <DEFINE|BUILD|CHECK|PACKAGE|PRODUCE>

OWNER: Universe Engine
LOCK: OPEN

---

## 1) PURPOSE (WHAT THIS ENGINE DOES)

One paragraph: which music capability it creates (composition/harmony/etc.) and what artifacts it outputs.

### DOES NOT OWN (hard)
- placement/sync/clarity in final video (08 sound production)
- video montage timing (08 editing)

---

## 2) TRIGGERS (WHEN TO RUN)

TRIGGERS:
- need theme/motif
- need scoring for a scene
- need consistent music style across episodes
- need final masters/stems
- style constraints updated
- scene emotional targets updated

---

## 3) MINI-CONTRACT (MANDATORY)

CONSUMES (examples):
- STYLE_CONSTRAINTS_PACK
- SCENE_CONTEXT / ARC_CONTEXT (if scoring)
- WORLD_CULTURE_CONTEXT (optional)
- existing motifs/tracks (if iterating)

PRODUCES (examples):
- TRACK_SPEC
- THEME_MOTIF_SET
- MASTER_TRACK
- STEMS_SET
- ALT_VERSIONS
- MUSIC_PACK

DEPENDS_ON:
- []  (if depends → mirror in XREF__DEPENDENCIES)

OUTPUT_ARTIFACT_TYPE:
- <TRACK_SPEC|MASTER_TRACK|STEMS_SET|MUSIC_PACK|MUSIC_BIBLE|...>

---

## 4) MUSIC PACK SCHEMA (MANDATORY)

MUSIC_PACK_ID: <unique>

INPUT_CONSTRAINTS:
  DEPENDS_ON_STYLE_PACK: <ref>
  CANON_REF_SCENE: <ref or NONE>
  DEPENDS_ON_WORLD_CONTEXT: <ref or NONE>

TRACK_SPEC:
  EMOTIONAL_TARGETS: [ ... ]
  TEMPO_RANGE: <optional>
  INSTRUMENT_PALETTE: [ ... ]
  MOTIFS: [ ... ]
  DURATION_HINT: <range, optional>

DELIVERABLES:
  MASTER: <path>
  STEMS: <optional paths>
  ALT_VERSIONS:
    - <loop>
    - <sting>
    - <no-drums> (optional)

NOTES:
  MIX_NOTES: ...
  MASTER_NOTES: ...
  USAGE_NOTES: <for 08 placement>

XREF_POINTERS:
  - <xref links>

Rule:
> Must include DEPENDS_ON_STYLE_PACK and deliverable master reference.

---

## 5) SYSTEM INTERFACE (MANDATORY) — MUSIC DEFAULTS

## SYSTEM INTERFACE
- OUTPUTS:
  - output_level: <L1_DRAFT|L2_CANON|L3_OUTPUT>
  - target_path_rule:
    - base: `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/`
    - category: `13_MUSIC/`
    - subfolders:
      - ideas: `01_IDEAS/`
      - specs: `02_SPECS/`
      - stems: `03_STEMS/`
      - masters: `04_MASTERS/`
    - level_folder:
      - L1: `02_DRAFT_L1/`
      - L2: `03_CANON_L2/`
      - L3: `04_OUTPUT_L3/`

- REGISTRY_UPDATES:
  - required: YES
  - registries:
    - `REG.PRJ.<PROJECT_ID>.OUTPUT_L3`
    - `REG.PRJ.<PROJECT_ID>.ASSETS`
    - `REG.PRJ.<PROJECT_ID>.CANON_L2` (music bible/style consistency)

- XREF_UPDATES:
  - required: YES
  - record_types:
    - [DEPENDS_ON, CANON_REF, DERIVED_FROM, PRODUCED_BY, ASSET_LINK]
  - xref_targets:
    - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CANON_REFS.md`
    - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__DEPENDENCIES.md`
    - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__PROVENANCE.md`
    - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__ASSET_GRAPH.md`

- GATES:
  - validators:
    - `VAL.MUS.01.STYLE_DEPENDENCY_PRESENT` (placeholder)
    - `VAL.MUS.02.DELIVERABLE_MASTER_PRESENT` (placeholder)
  - qa_checks:
    - `QA.MUS.01.CONSISTENCY_WITH_STYLE` (placeholder)
    - `QA.MUS.02.USABLE_FOR_08_PLACEMENT` (placeholder)

---

## 6) QUALITY (MANDATORY)

PASS if:
- track has style dependency and (if scoring) scene canon reference
- deliverables exist (master, optional stems)
- no instructions about video montage timing included

FAIL if:
- tries to do placement/sync as final mix for video (route to 08)
- missing style dependency
- outputs not registered/linked

---

## FINAL RULE (LOCK)

> Music engines create tracks and music systems. Placement is 08. Music must reference style and (when scoring) narrative scene context.

OWNER: Universe Engine  
LOCK: OPEN
