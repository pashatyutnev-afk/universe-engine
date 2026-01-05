# ENG ENGINE TEMPLATE — DOMAIN_NARRATIVE_ENGINES (FAMILY OVERLAY v2)
FILE: 00__TEMPLATE__ENGINE__DOMAIN_NARRATIVE_ENGINES.md

SCOPE: Universe Engine
LAYER: ENG
DOC_TYPE: TEMPLATE
ENTITY_GROUP: ENGINES (ENG)
TEMPLATE_KIND: ENGINE_FAMILY_OVERLAY
LEVEL: L2
STATUS: ACTIVE
VERSION: 2.0
ROLE: Narrative family overlay. Compatible with ENG ENGINE TEMPLATE (BASE v2). Adds narrative unit schemas (scene/beat/arc), story-time pacing boundary, and mandatory cause-effect xref.

LOCK: FIXED
OWNER: Universe Engine

---

## 0) ENGINE IDENTITY (MANDATORY)

ENGINE_NAME: <UPPER_SNAKE_CASE>
ENGINE_ID: ENG.NAR.<NN>.<ENGINE_NAME>

FAMILY_CODE: NAR
ENGINE_NN_IN_FAMILY: <01..10>
ENGINE_CLASS: DOMAIN
ENGINE_LEVEL: L2

ROLE_IN_FAMILY: <FOUNDATION|BUILDER|VALIDATOR|OUTPUT>
PIPELINE_STAGE: <DEFINE|BUILD|CHECK|PRODUCE>

---

## 1) PURPOSE (WHAT THIS ENGINE DOES)

One paragraph:
- which narrative unit it shapes (logic/structure/arc/scene/etc)
- which artifacts it outputs (scene spec, arc spec, continuity notes, theme map)

---

## 2) OWNERSHIP BOUNDARIES (ANTI-DUPLICATION)

### 2.1 OWNS
- story-time narrative design

### 2.2 DOES NOT OWN (hard)
- screen-time timing in seconds (belongs to 08)
- visual style law (belongs to 06)
- world law facts (belongs to 04; narrative may reference)
Rule:
> If you need seconds or shots — route to 08 Editing/Montage.

---

## 3) TRIGGERS (WHEN TO RUN)

TRIGGERS:
- new arc planned
- scene needs construction
- continuity conflicts detected
- pacing issues reported (story-time)
- theme drift reported

---

## 4) MINI-CONTRACT (MANDATORY)

CONSUMES:
- CORE_STATE_VALIDATION (entity exists, active)
- WORLD_CONTEXT (optional)
- CHARACTER_CONSTRAINTS (optional)
- STYLE_CONSTRAINTS_PACK (optional)
- existing arcs/scenes/events (if iterating)

PRODUCES:
- ARC_SPEC
- SCENE_SPEC
- BEAT_LIST
- CONTINUITY_NOTES
- THEME_MAP

DEPENDS_ON:
- [] (or engine IDs)

OUTPUT_TARGET (canonical defaults):
- entity-scoped:
  - arcs: `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/09_ARCS/ARC_<NAME>/<LEVEL_FOLDER>/`
  - events/beats: `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/06_EVENTS/EVT_<NAME>/<LEVEL_FOLDER>/`
  - scenes: `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/06_EVENTS/SCN_<NAME>/<LEVEL_FOLDER>/` (if you store scenes as events)
- project-scoped:
  - story bible: `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/05_PROJECT__L2/<LEVEL_FOLDER>/`

Rule:
> L2 canon outputs must be registered and xref-linked.

---

## 5) NARRATIVE UNIT SCHEMAS (MANDATORY)

### 5.1 ARC_SPEC

ARC_ID: <ARC_<NAME>>
PROJECT_ID: <PRJ_*>
STATUS: <DRAFT|CANON>
THEME_TAGS: [ ... ]
LOG_LINE: ...
START_STATE: ...
END_STATE: ...
KEY_TURNS: [ ... ]
DEPENDENCIES:
- WORLD_CANON_REFS: [ ... ]
- CHARACTER_CANON_REFS: [ ... ]
SCENES: [<SCN_ID>...]

---

### 5.2 SCENE_SPEC

SCN_ID: <SCN_<NAME>>
ARC_ID: <optional>
SETTING: <where/when>
POV: <who experiences>
GOAL: ...
CONFLICT: ...
STAKE: ...
TURN: <what changes>
OUTCOME: ...
FORESHADOW: <optional>
REVEAL: <optional>
NOTES:
- pacing_story_time: <fast|medium|slow + reason>
- continuity_risks: [ ... ]

---

### 5.3 CAUSE_EFFECT_ENTRY (for XREF graph)

CE_ID: <unique>
CAUSE: <event/decision>
EFFECT: <consequence>
SCOPE: <SCENE|ARC|WORLD>
STRENGTH: <LOW|MED|HIGH>
CANON_REF: <refs>

Rule:
> For any arc with >1 scene, cause-effect entries are required.

---

## 6) SYSTEM INTERFACE (MANDATORY) — ORC/CTL/VAL/QA/REG/XREF

ORCHESTRATED_BY (ORC):
- [] (or ORC IDs if used)

CONTROLLED_BY (CTL):
- [] (or CTL IDs)

VALIDATED_BY (VAL):
- <VAL.NAR.01.CONTINUITY> (placeholder) or []

QA_BY (QA):
- <QA.NAR.01.NARRATIVE_COHERENCE> (placeholder) or []

REGISTRY_UPDATES:
- REQUIRED: YES (for L2 canon)
- TARGETS:
  - `00_REG__REGISTRIES/REG.PRJ.<PROJECT_ID>.ENTITIES.md`
  - `00_REG__REGISTRIES/REG.PRJ.<PROJECT_ID>.CANON_L2.md`

XREF_UPDATES:
- REQUIRED: YES
- RECORD_TYPES:
  - CANON_REF
  - DEPENDS_ON
  - DERIVED_FROM
  - PRODUCED_BY
  - CONFLICTS_WITH
- TARGETS:
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CANON_REFS.md`
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__DEPENDENCIES.md`
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__PROVENANCE.md`
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CAUSE_EFFECT_GRAPH.md`
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__ENTITY_GRAPH.md`

Rule:
> If arc/scene impacts multiple entities — update ENTITY_GRAPH + CAUSE_EFFECT_GRAPH.

---

## 7) PROCESS (HOW TO EXECUTE)

1) Validate CORE state of target entities (exists + allowed).
2) Read world/character/style constraints (if listed).
3) Produce ARC_SPEC / SCENE_SPEC / continuity notes.
4) Write to OUTPUT_TARGET (routing law).
5) Update REG + XREF (mandatory for L2).
6) Run continuity validation + coherence QA.
7) If changes affect locked canon — route through governance.

---

## 8) QUALITY GATES (MANDATORY)

PASS if:
- scene/arc specs are structurally complete
- cause-effect entries exist for multi-scene arcs
- continuity notes included
- REG + XREF updated
- no screen-time seconds included

FAIL if:
- mixes montage timing / shot lists / second-by-second edit instructions
- creates canon without xref/registry
- hides dependencies

---

## 9) RAW LINK (MANDATORY)

RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/02_DOMAIN_NARRATIVE_ENGINES/00__TEMPLATE__ENGINE__DOMAIN_NARRATIVE_ENGINES.md

---

## FINAL RULE (LOCK)

> Narrative engines output story-time structures and canon refs. Screen-time and montage belong to Production.

LOCK: FIXED
