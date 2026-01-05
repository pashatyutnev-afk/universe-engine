# ENG ENGINE TEMPLATE — DOMAIN_CHARACTER_ENGINES (FAMILY OVERLAY v2)
FILE: 00__TEMPLATE__ENGINE__DOMAIN_CHARACTER_ENGINES.md

SCOPE: Universe Engine
LAYER: ENG
DOC_TYPE: TEMPLATE
ENTITY_GROUP: ENGINES (ENG)
TEMPLATE_KIND: ENGINE_FAMILY_OVERLAY
LEVEL: L2
STATUS: ACTIVE
VERSION: 2.0
ROLE: Character family overlay. Compatible with ENG ENGINE TEMPLATE (BASE v2). Adds character record schemas, relationship edges, and dialogue/speech constraints with required xref updates.

LOCK: FIXED
OWNER: Universe Engine

---

## 0) ENGINE IDENTITY (MANDATORY)

ENGINE_NAME: <UPPER_SNAKE_CASE>
ENGINE_ID: ENG.CHR.<NN>.<ENGINE_NAME>

FAMILY_CODE: CHR
ENGINE_NN_IN_FAMILY: <01..10>
ENGINE_CLASS: DOMAIN
ENGINE_LEVEL: L2

ROLE_IN_FAMILY: <FOUNDATION|BUILDER|VALIDATOR|OUTPUT>
PIPELINE_STAGE: <DEFINE|BUILD|CHECK|PRODUCE>

---

## 1) PURPOSE (WHAT THIS ENGINE DOES)

One paragraph:
- what part of character model it defines (core/motivation/value/psychology/behavior/relationships/dialogue/speech/growth/evolution)
- what artifacts it outputs (character sheet, constraints, graph edges)

---

## 2) OWNERSHIP BOUNDARIES (ANTI-DUPLICATION)

OWNS:
- internal character model + relationships + speech constraints

DOES NOT OWN (hard):
- story events and scene structure (NAR)
- world law facts (WLD)
- global tone/atmosphere (STY)
- montage timing (PRD)

Rule:
> Character outputs constraints. Narrative consumes constraints to build scenes.

---

## 3) TRIGGERS (WHEN TO RUN)

TRIGGERS:
- new character introduced
- contradictions found in behavior/motivation
- relationship changes
- dialogue feels “not them”
- trauma/growth needs coherence over time

---

## 4) MINI-CONTRACT (MANDATORY)

CONSUMES:
- CORE_IDENTITY + CORE_STATE (required)
- WORLD_CONTEXT (optional)
- NARRATIVE_CONTEXT (optional)
- STYLE_CONSTRAINTS_PACK (optional)
- existing character canon (if iterating)

PRODUCES:
- CHARACTER_PROFILE
- MOTIVATION_MAP
- VALUE_SYSTEM
- PSYCHO_MODEL
- BEHAVIOR_RULES
- RELATIONSHIP_EDGES
- DIALOGUE_CONSTRAINTS
- SPEECH_PROFILE
- TRAUMA_GROWTH_NOTES
- EVOLUTION_TRACK

DEPENDS_ON:
- [] (or engine IDs)

OUTPUT_TARGET (canonical defaults):
- character entity:
  `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/01_CHARACTERS/<ENTITY_ID>/<LEVEL_FOLDER>/`
- relationship entity (if separated):
  `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/08_RELATIONSHIPS/REL_<NAME>/<LEVEL_FOLDER>/`
- project bible pack:
  `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/05_PROJECT__L2/<LEVEL_FOLDER>/`

Rule:
> L2 canon requires REG + XREF updates.

---

## 5) CHARACTER SCHEMAS (MANDATORY)

### 5.1 CHARACTER_PROFILE (core)

ENTITY_ID: <CHR_<NAME>>
DISPLAY_NAME: <...>
ARCHETYPE: <optional>
ROLE_IN_STORY: <protagonist|antagonist|support|...>
CORE_WOUND: <optional>
CORE_NEED: <optional>
CORE_LIE: <optional>
CORE_TRUTH: <optional>
BOUNDARIES:
- will_never_do: [ ... ]
- will_always_do: [ ... ]
CANON_STATUS: <DRAFT|CANON>
CANON_REFS: [ ... ]

---

### 5.2 MOTIVATION_MAP

ENTITY_ID: <CHR_*>
DESIRES:
- short_term: [ ... ]
- long_term: [ ... ]
FEARS: [ ... ]
DRIVERS: [ ... ]
CONFLICTS_INTERNAL: [ ... ]
PRIORITIES: [ ... ]

---

### 5.3 VALUE_SYSTEM (moral/value)

ENTITY_ID: <CHR_*>
VALUES: [ ... ]
TABOOS: [ ... ]
JUSTIFICATIONS: [ ... ]
RED_LINES: [ ... ]

---

### 5.4 PSYCHO_MODEL (psychology)

ENTITY_ID: <CHR_*>
TEMPERAMENT: <...>
COPING_STRATEGIES: [ ... ]
ATTACHMENT_STYLE: <optional>
TRIGGERS: [ ... ]
SOOTHERS: [ ... ]

---

### 5.5 BEHAVIOR_RULES

ENTITY_ID: <CHR_*>
DEFAULT_BEHAVIOR: [ ... ]
UNDER_STRESS: [ ... ]
UNDER_POWER: [ ... ]
UNDER_LOSS: [ ... ]
HABITS: [ ... ]

---

### 5.6 RELATIONSHIP_EDGE (graph entry)

EDGE_ID: <unique>
FROM: <CHR_*>
TO: <CHR_*|FAC_*|SYS_*|OBJ_*>
REL_TYPE: <ALLY|ENEMY|LOVE|RIVAL|MENTOR|FAMILY|DEBT|FEAR|CONTROL|DEPENDENCY|...>
INTENSITY: <LOW|MED|HIGH>
TRUST: <0..1>
POWER_BALANCE: <TO->FROM|FROM->TO|BALANCED>
HISTORY_NOTE: <short>
CANON_REF: <refs>

Rule:
> Relationships are edges. No prose-only relationships in canon.

---

### 5.7 DIALOGUE_CONSTRAINTS

ENTITY_ID: <CHR_*>
SPEECH_TONE: <dry|warm|cold|sarcastic|formal|...>
VOCABULARY:
- likes: [ ... ]
- avoids: [ ... ]
SENTENCE_STYLE:
- short_vs_long: <...>
- questions_rate: <...>
- swear_level: <...>
TOPICS:
- loves: [ ... ]
- avoids: [ ... ]
DEFAULT_INTENTIONS:
- persuade|deflect|attack|bond|test|hide|...

---

### 5.8 SPEECH_PROFILE (naturalization)

ENTITY_ID: <CHR_*>
DIALECT: <optional>
FILLERS: [ ... ]
RHYTHM: <fast|measured|...>
SIGNATURE_PHRASES: [ ... ]
NONVERBAL: [ ... ]

---

### 5.9 EVOLUTION_TRACK

ENTITY_ID: <CHR_*>
ARC_LINKS: [<ARC_*...>]
STATE_OVER_TIME:
- <epoch/act/season>: <core changes>
TRAUMA_EVENTS: [<EVT_*...>]
GROWTH_MARKERS: [ ... ]

---

## 6) SYSTEM INTERFACE (MANDATORY) — ORC/CTL/VAL/QA/REG/XREF

ORCHESTRATED_BY (ORC):
- [] (or ORC IDs)

CONTROLLED_BY (CTL):
- [] (or CTL IDs)

VALIDATED_BY (VAL):
- <VAL.CHR.01.COHERENCE> (placeholder) or []

QA_BY (QA):
- <QA.CHR.01.VOICE_CONSISTENCY> (placeholder) or []

REGISTRY_UPDATES:
- REQUIRED: YES (for L2)
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
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__RELATIONSHIP_GRAPH.md`
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__DIALOGUE_CONSTRAINTS.md`
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__ENTITY_GRAPH.md`
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__PROVENANCE.md`
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__DEPENDENCIES.md`
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CANON_REFS.md`

Rule:
> Relationship edges MUST be recorded in XREF__RELATIONSHIP_GRAPH.

---

## 7) PROCESS (HOW TO EXECUTE)

1) Validate CORE identity/state of character (exists + allowed).
2) Read narrative/world/style constraints as needed.
3) Produce structured character artifacts (no pure prose).
4) Write outputs to character entity folder (routing).
5) Update REG + XREF.
6) Run coherence validator + voice QA.
7) If modifying locked canon — route through governance.

---

## 8) QUALITY GATES (MANDATORY)

PASS if:
- core + motivation + behavior + relationships exist
- dialogue constraints consistent with profile
- relationship edges graph-like and typed
- REG + XREF updated

FAIL if:
- only prose, no structured artifacts
- relationships described without edges
- dialogue rules contradict core values
- hidden dependencies

---

## 9) RAW LINK (MANDATORY)

RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/03_DOMAIN_CHARACTER_ENGINES/00__TEMPLATE__ENGINE__DOMAIN_CHARACTER_ENGINES.md

---

## FINAL RULE (LOCK)

> Character outputs constraints and models. Narrative consumes them to build story events.

LOCK: FIXED
