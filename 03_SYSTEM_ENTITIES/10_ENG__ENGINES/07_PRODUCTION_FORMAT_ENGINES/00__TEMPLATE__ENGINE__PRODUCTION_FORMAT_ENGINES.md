# ENG ENGINE TEMPLATE — PRODUCTION_FORMAT_ENGINES (FAMILY OVERLAY v2)
FILE: 00__TEMPLATE__ENGINE__PRODUCTION_FORMAT_ENGINES.md

SCOPE: Universe Engine
LAYER: ENG
DOC_TYPE: TEMPLATE
ENTITY_GROUP: ENGINES (ENG)
TEMPLATE_KIND: ENGINE_FAMILY_OVERLAY
LEVEL: L3
STATUS: ACTIVE
VERSION: 2.0
ROLE: Format family overlay. Compatible with ENG ENGINE TEMPLATE (BASE v2). Adds format spec schemas and deliverable mapping to Production pipelines and L3 outputs.

LOCK: FIXED
OWNER: Universe Engine

---

## 0) ENGINE IDENTITY (MANDATORY)

ENGINE_NAME: <UPPER_SNAKE_CASE>
ENGINE_ID: ENG.FMT.<NN>.<ENGINE_NAME>

FAMILY_CODE: FMT
ENGINE_NN_IN_FAMILY: <01..08>
ENGINE_CLASS: PRODUCTION
ENGINE_LEVEL: L3

ROLE_IN_FAMILY: <FOUNDATION|OUTPUT>
PIPELINE_STAGE: <DEFINE|PRODUCE>

---

## 1) PURPOSE (WHAT THIS ENGINE DOES)

One paragraph:
- which format it defines
- what deliverables it requires
- how Production must implement it

---

## 2) OWNERSHIP BOUNDARIES (ANTI-DUPLICATION)

OWNS:
- format requirements and deliverable specs

DOES NOT OWN:
- story creation (NAR/EXP)
- style laws (STY)
- technical production execution (PRD)

---

## 3) TRIGGERS (WHEN TO RUN)

TRIGGERS:
- project start (choose format)
- before production pipeline design
- when a deliverable pack definition is missing
- when format change is requested

---

## 4) MINI-CONTRACT (MANDATORY)

CONSUMES:
- CORE_STATE_VALIDATION (required)
- NARRATIVE_PACK refs (optional)
- STYLE_PACK refs (optional)
- production capabilities constraints (optional)

PRODUCES:
- FORMAT_SPEC (canonical)
- DELIVERABLE_MAP
- RELEASE_RULES
- EPISODE_RULES (if episodic)
- LENGTH_RULES

DEPENDS_ON:
- [] (or engine IDs)

OUTPUT_TARGET:
- format specs:
  `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/05_PROJECT__L2/<LEVEL_FOLDER>/FORMAT_SPECS/`
- deliverables:
  `05_PROJECTS/<PROJECT_ID>/02_OUTPUT/<FORMAT>/...`
  (or in workshop output folder if you keep everything inside)

Rule:
> Canon format spec must be registered in REG.PRJ.<PROJECT_ID>.CANON_L2.md.

---

## 5) FORMAT SPEC SCHEMAS (MANDATORY)

### 5.1 FORMAT_SPEC (base)

FMT_ID: <FMT_<NAME>>
PRIMARY_FORMAT: <BOOK|SERIES|SHORTS|YOUTUBE_LONG|GAME>
SECONDARY_FORMATS: [ ... ] (optional)
AUDIENCE_TARGET: <optional>
RUNTIME_RULES:
- unit: <minutes|pages|chapters|levels>
- typical: <...>
- min: <...>
- max: <...>

STRUCTURE_RULES:
- parts: <...>
- episodes: <...>
- chapters: <...>

DELIVERABLES_REQUIRED:
- [SCRIPT|STORY_BIBLE|SHOT_LIST|ANIMATIC|FINAL_VIDEO|AUDIO_STEMS|SUBTITLES|THUMBNAILS|METADATA|BUILD|...]
QUALITY_BAR:
- must_have: [ ... ]
- nice_to_have: [ ... ]

CANON_STATUS: <DRAFT|CANON>
CANON_REFS: [ ... ]

---

### 5.2 DELIVERABLE_MAP

MAP_ID: <DELIV_MAP_<NAME>>
FOR_FORMAT: <FMT_ID>
PIPELINE_TARGETS:
- narrative_inputs: [ ... ]
- production_engines: [ ... ] (refs to 08_KNOWLEDGE_PRODUCTION_ENGINES)
- qa_targets: [ ... ] (refs to QA family if used)
OUTPUT_PATHS:
- final: `05_PROJECTS/<PROJECT_ID>/02_OUTPUT/<FORMAT>/...`
- intermediates: `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/05_PROJECT__L3/04_OUTPUT_L3/<FORMAT>/...`

---

### 5.3 EPISODE_RULES (if SERIES/SHORTS/YOUTUBE)

EP_RULES_ID: <EP_RULES_<NAME>>
EPISODE_COUNT: <...>
EPISODE_ARC_POLICY: <one arc per ep|multi-arc|season arc|...>
CLIFFHANGER_POLICY: <none|soft|hard>
RECAP_POLICY: <none|light|standard>
SERIES_BIBLE_REQUIRED: <true|false>

---

### 5.4 RELEASE_RULES

REL_ID: <REL_<NAME>>
CADENCE: <weekly|daily|batch|...>
VERSIONING: <semantic|date|...>
METADATA_REQUIRED:
- title
- description
- tags
- thumbnails
- credits
PLATFORM_CONSTRAINTS:
- aspect_ratio
- loudness targets (intent only; implementation in Production)
- subtitle format

Rule:
> Technical loudness/bitrate settings belong to Production; format only states intent and targets.

---

## 6) SYSTEM INTERFACE (MANDATORY) — ORC/CTL/VAL/QA/REG/XREF

ORCHESTRATED_BY (ORC): []
CONTROLLED_BY (CTL): []

VALIDATED_BY (VAL):
- <VAL.FMT.01.CONSISTENCY> (placeholder) or []

QA_BY (QA):
- <QA.FMT.01.DELIVERABLE_COMPLETENESS> (placeholder) or []

REGISTRY_UPDATES:
- REQUIRED: YES (for CANON)
- TARGETS:
  - `00_REG__REGISTRIES/REG.PRJ.<PROJECT_ID>.CANON_L2.md`
  - `00_REG__REGISTRIES/REG.PRJ.<PROJECT_ID>.OUTPUT_L3.md` (deliverables)

XREF_UPDATES:
- REQUIRED: YES
- TARGETS:
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__DELIVERABLE_MAP.md`
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__DEPENDENCIES.md`
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__PROVENANCE.md`
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CANON_REFS.md`

---

## 7) PROCESS (HOW TO EXECUTE)

1) Validate CORE project state.
2) Select primary format and runtime boundaries.
3) Define deliverables and mapping to production engines.
4) Store format spec in routing path.
5) Update REG + XREF.
6) If production already started and format changes — governance.

---

## 8) QUALITY GATES (MANDATORY)

PASS if:
- format spec includes runtime + structure + deliverables
- deliverable map routes to output paths
- no technical implementation settings inside spec
- registry and xref updated

FAIL if:
- format is implied but not explicit
- deliverables missing
- contains montage instructions or exact codec settings

---

## 9) RAW LINK (MANDATORY)

RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/07_PRODUCTION_FORMAT_ENGINES/00__TEMPLATE__ENGINE__PRODUCTION_FORMAT_ENGINES.md

---

## FINAL RULE (LOCK)

> Format defines deliverables and constraints; Production executes; Governance controls changes.

LOCK: FIXED
