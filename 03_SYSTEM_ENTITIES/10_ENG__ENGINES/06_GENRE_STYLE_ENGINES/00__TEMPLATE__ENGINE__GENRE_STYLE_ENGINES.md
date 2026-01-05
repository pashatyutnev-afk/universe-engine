# ENG ENGINE TEMPLATE — GENRE_STYLE_ENGINES (FAMILY OVERLAY v2)
FILE: 00__TEMPLATE__ENGINE__GENRE_STYLE_ENGINES.md

SCOPE: Universe Engine
LAYER: ENG
DOC_TYPE: TEMPLATE
ENTITY_GROUP: ENGINES (ENG)
TEMPLATE_KIND: ENGINE_FAMILY_OVERLAY
LEVEL: L3
STATUS: ACTIVE
VERSION: 2.0
ROLE: Style family overlay. Compatible with ENG ENGINE TEMPLATE (BASE v2). Adds Style Law Pack schema (tone/atmosphere/symbol/sensory), anti-style rules, and xref symbol maps.

LOCK: FIXED
OWNER: Universe Engine

---

## 0) ENGINE IDENTITY (MANDATORY)

ENGINE_NAME: <UPPER_SNAKE_CASE>
ENGINE_ID: ENG.STY.<NN>.<ENGINE_NAME>

FAMILY_CODE: STY
ENGINE_NN_IN_FAMILY: <01..06>
ENGINE_CLASS: STYLE
ENGINE_LEVEL: L3

ROLE_IN_FAMILY: <FOUNDATION|BUILDER|OUTPUT>
PIPELINE_STAGE: <DEFINE|BUILD|PRODUCE>

---

## 1) PURPOSE (WHAT THIS ENGINE DOES)

One paragraph:
- which style dimension it defines (tone/atmosphere/resonance/symbol/metaphor/sensory)
- what style constraints it produces for other engines

---

## 2) OWNERSHIP BOUNDARIES (ANTI-DUPLICATION)

OWNS:
- style intent and constraints packs

DOES NOT OWN (hard):
- character voice vocabulary rules (CHR owns; style may only set “degree of formality” globally)
- montage timing and technical grading specs (PRD owns; style provides intent targets)
Rule:
> If you define LUTs, exact shot timing, or edit rules — that belongs to Production.

---

## 3) TRIGGERS (WHEN TO RUN)

TRIGGERS:
- new project style is being established
- tone drift is detected
- symbols become inconsistent across scenes
- sensory description becomes generic or mismatched

---

## 4) MINI-CONTRACT (MANDATORY)

CONSUMES:
- CORE_STATE_VALIDATION (required)
- WORLD_CONTEXT (optional)
- NARRATIVE_CONTEXT (optional)
- existing style packs (if iterating)

PRODUCES:
- STYLE_LAW_PACK
- SYMBOL_MAP
- METAPHOR_RULES
- SENSORY_PALETTE
- ANTI_STYLE_RULES (what must not happen)

DEPENDS_ON:
- [] (or engine IDs)

OUTPUT_TARGET:
- default:
  `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/05_PROJECT__L2/<LEVEL_FOLDER>/STYLE_PACKS/`

Rule:
> Style outputs are project-scoped canon unless explicitly marked as overlay.

---

## 5) STYLE SCHEMAS (MANDATORY)

### 5.1 STYLE_LAW_PACK

PACK_ID: <STY_PACK_<NAME>>
PROJECT_ID: <PRJ_*>
CANON_STATUS: <DRAFT|CANON>
TONE_TARGETS:
- baseline: <...>
- under_threat: <...>
- under_wonder: <...>
- under_loss: <...>
ATMOSPHERE:
- textures: [ ... ]
- temperature: <cold|warm|neutral>
- density: <thin|thick|...>
EMOTIONAL_RESONANCE:
- primary: [ ... ]
- secondary: [ ... ]
SYMBOLS:
- required: [ ... ]
- forbidden: [ ... ]
SENSORY_PALETTE:
- sound: [ ... ]
- smell: [ ... ]
- tactile: [ ... ]
- light: [ ... ]
ANTI_STYLE_RULES:
- do_not: [ ... ]
CANON_REFS: [ ... ]

---

### 5.2 SYMBOL_MAP (xref-ready)

SYMBOL_ID: <SYM_<NAME>>
MEANING: <one line>
POLARITY: <positive|negative|ambiguous>
WHERE_USED: [<ARC_*|SCN_*|EVT_*>]
EVOLUTION: <optional>
CANON_REF: <refs>

Rule:
> Symbol meanings must be explicit, not “implied”.

---

### 5.3 METAPHOR_RULE

MET_ID: <MET_<NAME>>
TARGET_CONCEPT: <what concept>
SOURCE_DOMAIN: <what metaphor domain>
USAGE_RULES:
- allowed_forms: [ ... ]
- forbidden_forms: [ ... ]
NOTES: ...

---

### 5.4 SENSORY_ENTRY

SNS_ID: <SNS_<NAME>>
CHANNEL: <sound|smell|tactile|light|taste|temperature>
PALETTE: [ ... ]
AVOID: [ ... ]
SCENE_TAGS: [ ... ]

---

## 6) SYSTEM INTERFACE (MANDATORY) — ORC/CTL/VAL/QA/REG/XREF

ORCHESTRATED_BY (ORC): []
CONTROLLED_BY (CTL): []

VALIDATED_BY (VAL):
- <VAL.STY.01.COHERENCE> (placeholder) or []

QA_BY (QA):
- <QA.STY.01.CONSISTENCY> (placeholder) or []

REGISTRY_UPDATES:
- REQUIRED: YES for CANON packs
- TARGETS:
  - `00_REG__REGISTRIES/REG.PRJ.<PROJECT_ID>.CANON_L2.md`

XREF_UPDATES:
- REQUIRED: YES when symbols/metaphors are used
- TARGETS:
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__STYLE_RULES.md`
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__SYMBOL_MAP.md`
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__PROVENANCE.md`
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CANON_REFS.md`

Rule:
> If a symbol appears in canon scenes — update SYMBOL_MAP.

---

## 7) PROCESS (HOW TO EXECUTE)

1) Validate CORE state for project.
2) Define style law pack (tone+atmosphere+symbols+sensory).
3) Declare anti-style rules (hard “NO”).
4) Store pack into STYLE_PACKS routing.
5) Update registry + xref maps.
6) Validate coherence and run consistency QA.

---

## 8) QUALITY GATES (MANDATORY)

PASS if:
- style pack has explicit targets + anti-rules
- symbols have explicit meanings + usage references
- sensory palette is concrete
- no character-specific slang rules unless explicitly “global”

FAIL if:
- “vibes only” without constraints
- symbols without meanings
- technical production instructions inside style pack

---

## 9) RAW LINK (MANDATORY)

RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/06_GENRE_STYLE_ENGINES/00__TEMPLATE__ENGINE__GENRE_STYLE_ENGINES.md

---

## FINAL RULE (LOCK)

> Style defines intent and constraints. Production implements them.

LOCK: FIXED
