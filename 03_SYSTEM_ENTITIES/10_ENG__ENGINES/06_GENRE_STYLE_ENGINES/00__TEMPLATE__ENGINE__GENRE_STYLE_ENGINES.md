# ENG ENGINE TEMPLATE — GENRE_STYLE_ENGINES (FAMILY OVERLAY v2)
FILE: 00__TEMPLATE__ENGINE__GENRE_STYLE_ENGINES.md

SCOPE: Universe Engine
LAYER: ENG
DOC_TYPE: TEMPLATE
ENTITY_KIND: STY
PROJECT_SCOPE: GLOBAL
OUTPUT_LEVEL: N/A
ID: ENG.TPL.ENGINE.STYLE
STATUS: ACTIVE
VERSION: 2.0
ROLE: Family-specific overlay template for Style engines. Compatible with ENG ENGINE TEMPLATE v2 and adds style constraints schema + dependency requirements.

---

## 0) ENGINE IDENTITY (MANDATORY)

ENGINE_NAME: <UPPER_SNAKE_CASE>
ENGINE_ID: <ENG.STY.<NN>.<ENGINE_NAME>>

FAMILY_CODE: STY
ENGINE_NN_IN_FAMILY: <01..06>
ENGINE_CLASS: STYLE
ENGINE_LEVEL: L3

ROLE_IN_FAMILY: <FOUNDATION|BUILDER|VALIDATOR|BRIDGE|OUTPUT>
PIPELINE_STAGE: <DEFINE|BUILD|CHECK|PACKAGE|PRODUCE>

OWNER: Universe Engine
LOCK: OPEN

---

## 1) PURPOSE (WHAT THIS ENGINE DOES)

One paragraph: which style axis it defines (tone/atmosphere/etc.) and how it becomes a constraint for other families.

### OWNERSHIP
- <style axis>

### DOES NOT OWN (hard)
- story structure (NAR)
- event atoms (EXP)
- character psychology/dialogue content (CHR)
- world laws (WLD)
- production technical params and montage timing (08)
- deep music composition (09)

---

## 2) TRIGGERS (WHEN TO RUN)

TRIGGERS:
- project style needs definition or refinement
- narrative asks for emotional path targets
- character needs voice register constraints
- production needs style constraints pack
- style drift detected between outputs

---

## 3) MINI-CONTRACT (MANDATORY)

CONSUMES (examples):
- WORLD_CONTEXT
- NARRATIVE_REQUIREMENTS
- CHARACTER_VOICE_REQUIREMENTS
- existing style drafts/canon

PRODUCES (examples):
- TONE_RANGE
- ATMOSPHERE_PROFILE
- EMOTIONAL_PATH
- SYMBOL_SET
- METAPHOR_SET
- SENSORY_PALETTES
- STYLE_CONSTRAINTS_PACK
- STYLE_BIBLE

DEPENDS_ON:
- []  (if depends → mirror in XREF__DEPENDENCIES)

OUTPUT_ARTIFACT_TYPE:
- <TONE_RANGE|ATMOSPHERE_PROFILE|STYLE_CONSTRAINTS_PACK|STYLE_BIBLE|...>

---

## 4) STYLE SCHEMA (MANDATORY)

STYLE_ID: <unique>
TONE_RANGE:
  ALLOWED: [ ... ]
  FORBIDDEN: [ ... ]
ATMOSPHERE_NOTES: ...
EMOTIONAL_TARGETS: [ ... ]
SYMBOL_SET:
  - SYMBOL: ...
    MEANING: ...
METAPHOR_SET:
  - METAPHOR: ...
    PURPOSE: ...
SENSORY_PALETTES:
  TOUCH: [ ... ]
  SMELL: [ ... ]
  TEMP: [ ... ]
  SOUND_AS_FEEL: [ ... ]
  LIGHT_AS_FEEL: [ ... ]
VOICE_GUIDE:
  REGISTER: <formal|neutral|street|ritual|...>
  RHYTHM_NOTES: <text only, no seconds>
PRODUCTION_HINTS:
  - <high-level, no numbers>

Rule:
> Must include ALLOWED/FORBIDDEN, иначе это не constraint.

---

## 5) SYSTEM INTERFACE (MANDATORY) — STYLE DEFAULTS

## SYSTEM INTERFACE
- OUTPUTS:
  - output_level: <L0_INTAKE|L1_DRAFT|L2_CANON|L3_OUTPUT>
  - target_path_rule:
    - base: `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/`
    - category: `10_STYLE/`
    - level_folder:
      - L0: `01_INTAKE_L0/`
      - L1: `02_DRAFT_L1/`
      - L2: `03_CANON_L2/`
      - L3: `04_OUTPUT_L3/`

    - file examples:
      - L2: `00__STYLE_BIBLE_CANON.md`
      - L3: `00__STYLE_CONSTRAINTS_PACK.md`

- REGISTRY_UPDATES:
  - required: YES (L2/L3)
  - registries:
    - `REG.PRJ.<PROJECT_ID>.CANON_L2`
    - `REG.PRJ.<PROJECT_ID>.OUTPUT_L3`

- XREF_UPDATES:
  - required: YES
  - record_types:
    - [DERIVED_FROM, PRODUCED_BY, CANON_REF, DEPENDS_ON]
  - xref_targets:
    - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__PROVENANCE.md`
    - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CANON_REFS.md`
    - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__DEPENDENCIES.md`
  - mandatory_links (examples):
    - `L3_STYLE_PACK -> L2_STYLE_BIBLE | TYPE:CANON_REF | SCOPE:PRJ:<PROJECT_ID> | WHY:Consumers rely on canon style | BY:ENG.STY.<NN>.<ENGINE_NAME> | AT:<YYYY-MM-DD>`

---

## 6) QUALITY (MANDATORY)

PASS if:
- style outputs are actionable constraints (allowed/forbidden + palettes)
- packs are referenced by dependents (DEPENDS_ON exists)
- no technical production numbers included
- drift is detectable (clear constraints)

FAIL if:
- purely poetic text without constraint structure
- hidden dependencies
- montage timing/technical params included

---

## 7) FAILURE MODES

- style drift across outputs → require validator pass + pack refresh
- tone contradictions → log conflict + revise tone range

---

## 8) RAW LINK (MANDATORY)

RAW: <raw github link to this template file>

---

## FINAL RULE (LOCK)

> Style must be consumable as constraints by other families. No technical production numbers, no montage timing.

OWNER: Universe Engine  
LOCK: OPEN
