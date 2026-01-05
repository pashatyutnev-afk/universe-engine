# ENG ENGINE TEMPLATE — KNOWLEDGE_PRODUCTION_ENGINES (FAMILY OVERLAY v2)
FILE: 00__TEMPLATE__ENGINE__KNOWLEDGE_PRODUCTION_ENGINES.md

SCOPE: Universe Engine
LAYER: ENG
DOC_TYPE: TEMPLATE
ENTITY_GROUP: ENGINES (ENG)
TEMPLATE_KIND: ENGINE_FAMILY_OVERLAY
LEVEL: L3
STATUS: ACTIVE
VERSION: 2.0
ROLE: Production family overlay. Compatible with ENG ENGINE TEMPLATE (BASE v2). Adds production run schema, asset provenance contract, and strict boundary rules vs Narrative and Music.

LOCK: FIXED
OWNER: Universe Engine

---

## 0) ENGINE IDENTITY (MANDATORY)

ENGINE_NAME: <UPPER_SNAKE_CASE>
ENGINE_ID: ENG.PRD.<NN>.<ENGINE_NAME>

FAMILY_CODE: PRD
ENGINE_NN_IN_FAMILY: <01..08>
ENGINE_CLASS: PRODUCTION
ENGINE_LEVEL: L3

ROLE_IN_FAMILY: <FOUNDATION|BUILDER|OUTPUT>
PIPELINE_STAGE: <DEFINE|BUILD|PRODUCE>

---

## 1) PURPOSE (WHAT THIS ENGINE DOES)

One paragraph:
- what production capability this engine provides
- what artifact types it outputs
- which upstream packs it obeys (Format/Style/Narrative/World/Character)

---

## 2) OWNERSHIP BOUNDARIES (ANTI-DUPLICATION)

OWNS:
- implementation of style intent into assets
- screen-time montage rules (ONLY inside Editing engine)
- production sound (sync/clarity/placement)

DOES NOT OWN:
- story-time pacing (NAR)
- deep music composition (MUS)
- world facts, character psyche, narrative canon

Rule:
> If output changes canon meaning, it must be declared as retcon and go governance.

---

## 3) TRIGGERS (WHEN TO RUN)

TRIGGERS:
- deliverable required by format spec
- new scene/sequence needs assets
- quality/consistency failure in previous output
- re-render / re-edit / re-mix requested

---

## 4) MINI-CONTRACT (MANDATORY)

CONSUMES:
- FORMAT_SPEC (required)
- STYLE_LAW_PACK (required)
- NARRATIVE_PACK / SCENE_SPECS (optional but typical)
- WORLD_CANON_REFS (optional)
- CHARACTER_CONSTRAINTS (optional)
- existing assets (if iterating)

PRODUCES:
- ASSET_PACK (images/video/audio/subtitles/metadata)
- EDIT_SEQUENCE (if editing)
- AUDIO_STEMS (if sound)
- DELIVERY_BUNDLE (final deliverables)
- PROVENANCE_RECORDS

DEPENDS_ON:
- [] (or engine IDs)

OUTPUT_TARGET:
- runs:
  `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/05_PROJECT__L3/PRODUCTION_RUNS/RUN_<ID>/`
- intermediate outputs:
  `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/05_PROJECT__L3/04_OUTPUT_L3/PRODUCTION/`
- final outputs:
  `05_PROJECTS/<PROJECT_ID>/02_OUTPUT/<FORMAT>/`

Rule:
> Every output must have provenance and mapping to inputs.

---

## 5) PRODUCTION RUN SCHEMAS (MANDATORY)

### 5.1 RUN_RECORD

RUN_ID: <RUN_<YYYYMMDD>_<NN>>
ENGINE_ID: <ENG.PRD.*>
FORMAT_REF: <FMT_*>
STYLE_PACK_REF: <STY_PACK_*>
INPUT_REFS:
- scene_or_arc_refs: [ ... ]
- canon_refs: [ ... ]
PARAMS:
- version: <...>
- notes: <...>
OUTPUTS:
- assets: [ ... ] (file ids/paths)
- deliverables: [ ... ]
QA_RESULTS:
- passed: <true|false>
- issues: [ ... ]
PROVENANCE_REF: <XREF__PROVENANCE entry id>

---

### 5.2 ASSET_RECORD

ASSET_ID: <AST_<NAME>>
TYPE: <IMG|VID|AUD|SUB|META|PROJECT_FILE>
SOURCE:
- generated_by: <engine/tool>
- derived_from: [ ... ]
CANON_SCOPE: <L0|L1|L2|L3>
PATH: <repo path>
LICENSE: <optional>
NOTES: ...

Rule:
> No asset without PATH + derived_from.

---

## 6) SYSTEM INTERFACE (MANDATORY) — ORC/CTL/VAL/QA/REG/XREF

ORCHESTRATED_BY (ORC):
- [] (or ORC IDs)

CONTROLLED_BY (CTL):
- [] (or CTL IDs)

VALIDATED_BY (VAL):
- <VAL.PRD.01.PROVENANCE> (placeholder) or []
- <VAL.PRD.02.FORMAT_COMPLIANCE> (placeholder) or []

QA_BY (QA):
- <QA.PRD.01.VISUAL_QUALITY> (placeholder) or []
- <QA.PRD.02.AUDIO_QUALITY> (placeholder) or []
- <QA.PRD.03.CONSISTENCY> (placeholder) or []

REGISTRY_UPDATES:
- REQUIRED: YES (deliverables)
- TARGETS:
  - `00_REG__REGISTRIES/REG.PRJ.<PROJECT_ID>.OUTPUT_L3.md`
  - `00_REG__REGISTRIES/REG.PRJ.<PROJECT_ID>.RUNS.md` (recommended)

XREF_UPDATES:
- REQUIRED: YES
- TARGETS:
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__PROVENANCE.md`
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__ASSET_GRAPH.md`
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__DELIVERABLE_MAP.md`
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__DEPENDENCIES.md`
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CANON_REFS.md`

Rule:
> Provenance is mandatory for every production output.

---

## 7) PROCESS (HOW TO EXECUTE)

1) Read FORMAT_SPEC + STYLE_LAW_PACK.
2) Pull scene/arc specs (if any).
3) Produce assets or edits under engine specialization.
4) Store outputs in RUN folder + intermediate/final paths.
5) Update registry (deliverables/runs).
6) Update provenance + asset graph.
7) Run validators + QA gates.
8) If output changes canon meaning (retcon) → governance.

---

## 8) QUALITY GATES (MANDATORY)

PASS if:
- deliverable matches format spec
- style intent is respected
- provenance exists and complete
- no narrative canon edits inside production docs

FAIL if:
- missing provenance
- contains story-time pacing decisions (belongs to NAR)
- tries to “compose music” (belongs to MUS)

---

## 9) RAW LINK (MANDATORY)

RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/08_KNOWLEDGE_PRODUCTION_ENGINES/00__TEMPLATE__ENGINE__KNOWLEDGE_PRODUCTION_ENGINES.md

---

## FINAL RULE (LOCK)

> Production outputs must be traceable and format-compliant. Canon stays upstream.

LOCK: FIXED
