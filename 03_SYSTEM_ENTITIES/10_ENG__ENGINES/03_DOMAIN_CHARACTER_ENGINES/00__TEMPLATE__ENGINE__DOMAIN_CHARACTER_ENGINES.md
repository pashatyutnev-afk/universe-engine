# ENG ENGINE TEMPLATE — DOMAIN_CHARACTER_ENGINES (FAMILY OVERLAY v2)
FILE: 00__TEMPLATE__ENGINE__DOMAIN_CHARACTER_ENGINES.md

SCOPE: Universe Engine
LAYER: ENG
DOC_TYPE: TEMPLATE
ENTITY_KIND: CHR
PROJECT_SCOPE: GLOBAL
OUTPUT_LEVEL: N/A
ID: ENG.TPL.ENGINE.CHARACTER
STATUS: ACTIVE
VERSION: 2.0
ROLE: Family-specific overlay template for Character engines. Compatible with ENG ENGINE TEMPLATE v2 and adds character defaults (CHR routing, output artifacts, boundary rules, REG/XREF requirements).

---

## 0) ENGINE IDENTITY (MANDATORY)

ENGINE_NAME: <UPPER_SNAKE_CASE>
ENGINE_ID: <ENG.CHR.<NN>.<ENGINE_NAME>>

FAMILY_CODE: CHR
ENGINE_NN_IN_FAMILY: <01..10>
ENGINE_CLASS: DOMAIN
ENGINE_LEVEL: L2

ROLE_IN_FAMILY: <FOUNDATION|BUILDER|VALIDATOR|BRIDGE|OUTPUT>
PIPELINE_STAGE: <DEFINE|BUILD|CHECK|PACKAGE|PRODUCE>

OWNER: Universe Engine
LOCK: OPEN

---

## 1) PURPOSE (WHAT THIS ENGINE DOES)

One paragraph: what character capability it produces.

### OWNERSHIP
- <specific character aspect>

### DOES NOT OWN (hard)
- story structure / scene ordering (NAR)
- event atoms formalization (EXP)
- world law authoring (WORLD)
- genre/style authoring (STYLE)
- timing/editing/seconds (08 editing)
- production sound placement (08 sound production)
- deep music (09)

---

## 2) TRIGGERS (WHEN TO RUN)

TRIGGERS:
- new character entity created
- update to world constraints (culture/tech)
- update to narrative constraints (role in arc)
- dialogue/voice style needed
- relationship network change
- character growth pivot requested

---

## 3) MINI-CONTRACT (MANDATORY)

CONSUMES (examples):
- CORE_CARD (entity existence)
- WORLD_CONSTRAINTS
- NARRATIVE_CONSTRAINTS
- STYLE_CONSTRAINTS
- RELATION_CONTEXT (xref links)
- previous drafts/canon (if any)

PRODUCES (examples):
- CHARACTER_BIBLE
- MOTIVATION_MAP
- VALUE_COMPASS
- PSYCH_PROFILE
- BEHAVIOR_RULES
- RELATIONSHIP_MAP
- DIALOGUE_PACK
- SPEECH_PROFILE
- GROWTH_TRAUMA_MAP
- EVOLUTION_ARC

DEPENDS_ON:
- []  (if depends → mirror in XREF__DEPENDENCIES)

OUTPUT_ARTIFACT_TYPE:
- <CHARACTER_BIBLE|DIALOGUE_PACK|RELATIONSHIP_MAP|SPEECH_PROFILE|EVOLUTION_ARC|...>

---

## 4) SYSTEM INTERFACE (MANDATORY) — CHARACTER DEFAULTS

## SYSTEM INTERFACE
- INPUTS:
  - artifacts: [intake notes, drafts, canon constraints]
  - sources:
    - project entities registry
    - project xref indexes
    - family README boundary rules

- OUTPUTS:
  - artifacts: [character artifacts]
  - output_level: <L0_INTAKE|L1_DRAFT|L2_CANON|L3_OUTPUT>
  - entity_kind: CHR

  - target_path_rule:
    - base: `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/`
    - category: `01_CHARACTERS`
    - entity_folder: `CHR_<CHARACTER_NAME>`
    - level_folder:
      - L0: `01_INTAKE_L0/`
      - L1: `02_DRAFT_L1/`
      - L2: `03_CANON_L2/`
      - L3: `04_OUTPUT_L3/`

    - file examples:
      - L0: `00__VOICE_NOTES.md`
      - L1: `00__CHARACTER_BIBLE_DRAFT.md`
      - L2: `00__CANON.md` (preferred single canon card)
      - L3: `00__DIALOGUE_PACK.md` / `01__RELATIONSHIP_SNAPSHOT.md`

- REGISTRY_UPDATES:
  - required: YES (entity exists; L2/L3 artifacts registered when separate)
  - registries:
    - `REG.PRJ.<PROJECT_ID>.ENTITIES`
    - `REG.PRJ.<PROJECT_ID>.CANON_L2` (if separate artifacts)
    - `REG.PRJ.<PROJECT_ID>.OUTPUT_L3` (if outputs registered)
  - entries_to_add:
    - <ENTITY_ID + path + status + lock>

- XREF_UPDATES:
  - required: YES
  - record_types:
    - [ENTITY_LINK, RELATES_TO, DERIVED_FROM, PRODUCED_BY, CANON_REF, DEPENDS_ON, REPLACED_BY, MERGED_INTO, SPLIT_INTO]
  - xref_targets:
    - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__ENTITY_GRAPH.md`
    - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__PROVENANCE.md`
    - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CANON_REFS.md`
    - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__DEPENDENCIES.md`
    - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CHANGES.md`
    - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__RELATIONSHIPS.md` (optional)
  - mandatory_links (examples):
    - `L2_CANON -> L1_DRAFT | TYPE:DERIVED_FROM | SCOPE:PRJ:<PROJECT_ID> | WHY:Canonized character | BY:ENG.CHR.<NN>.<ENGINE_NAME> | AT:<YYYY-MM-DD>`
    - `L3_DIALOGUE_PACK -> L2_CANON | TYPE:CANON_REF | SCOPE:PRJ:<PROJECT_ID> | WHY:Dialogue pack derived from canon | BY:ENG.CHR.<NN>.<ENGINE_NAME> | AT:<YYYY-MM-DD>`
    - `CHR_A -> CHR_B | TYPE:RELATES_TO | SCOPE:PRJ:<PROJECT_ID> | WHY:Relationship link | BY:ENG.CHR.06.RELATIONSHIP_ENG | AT:<YYYY-MM-DD>`

- GATES:
  - validators:
    - `VAL.CHR.01.MOTIVATION_COHERENCE` (placeholder)
    - `VAL.XREF.02.RELATIONSHIP_LINKS` (placeholder)
  - qa_checks:
    - `QA.CHR.01.DIALOGUE_USABILITY` (placeholder)
    - `QA.XREF.01.LINK_INTEGRITY` (placeholder)

- ORCHESTRATION:
  - orc_owner: [<ORC.CHR.* if used>]
  - ctl_enforcers:
    - `CTL.WORKSHOP.PATH_ENFORCER` (placeholder)
    - `CTL.WORKSHOP.LEVEL_ENFORCER` (placeholder)
    - `CTL.XREF.NO_ORPHANS` (placeholder)
    - `CTL.XREF.NO_HIDDEN_LINKS` (placeholder)

---

## 5) PROCESS (HOW IT WORKS)

1) Consume core + constraints (world/narrative/style)
2) Build character bible draft (identity, values, motives)
3) Build behavior rules + relationship map
4) Produce dialogue packs and speech profile (no timing)
5) Validate coherence + naturalness
6) Canonize and register + provenance + links

---

## 6) QUALITY (MANDATORY)

PASS if:
- motives match values and behavior (no contradictions)
- speech profile consistent with background and style constraints
- relationships are explicit in XREF (not only in prose)
- L3 packs reference L2 canon (CANON_REF)
- boundaries respected (no editing timing, no event atom authoring)

FAIL if:
- hidden dependencies
- missing relationship links
- L2 without lineage
- mixing montage/timing into dialogue packs

---

## 7) FAILURE MODES

- Character contradiction → log conflict + revise motivation/value/behavior triangle
- Relationship drift without XREF update → block promotion
- Voice feels “generic” → run speech naturalization and tie to background constraints

---

## 8) RAW LINK (MANDATORY)

RAW: <raw github link to this template file>

---

## FINAL RULE (LOCK)

> Character engines build internal truth of персонажа. Outputs must be usable, traceable, and boundary-safe.

OWNER: Universe Engine  
LOCK: OPEN
