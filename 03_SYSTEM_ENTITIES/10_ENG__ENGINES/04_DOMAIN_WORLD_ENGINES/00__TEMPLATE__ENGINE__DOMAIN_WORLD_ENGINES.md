# ENG ENGINE TEMPLATE — DOMAIN_WORLD_ENGINES (FAMILY OVERLAY v2)
FILE: 00__TEMPLATE__ENGINE__DOMAIN_WORLD_ENGINES.md

SCOPE: Universe Engine
LAYER: ENG
DOC_TYPE: TEMPLATE
ENTITY_GROUP: ENGINES (ENG)
TEMPLATE_KIND: ENGINE_FAMILY_OVERLAY
LEVEL: L2
STATUS: ACTIVE
VERSION: 2.0
ROLE: World family overlay. Compatible with ENG ENGINE TEMPLATE (BASE v2). Adds world-law schemas (laws/epochs/civs/resources/tech/ecology) and mandatory world graphs (law/epoch/resource/power).

LOCK: FIXED
OWNER: Universe Engine

---

## 0) ENGINE IDENTITY (MANDATORY)

ENGINE_NAME: <UPPER_SNAKE_CASE>
ENGINE_ID: ENG.WLD.<NN>.<ENGINE_NAME>

FAMILY_CODE: WLD
ENGINE_NN_IN_FAMILY: <01..10>
ENGINE_CLASS: DOMAIN
ENGINE_LEVEL: L2

ROLE_IN_FAMILY: <FOUNDATION|BUILDER|VALIDATOR|OUTPUT>
PIPELINE_STAGE: <DEFINE|BUILD|CHECK|PRODUCE>

---

## 1) PURPOSE (WHAT THIS ENGINE DOES)

One paragraph:
- what world aspect it defines (law/epochs/civs/economy/tech/ecology/etc)
- what structured artifacts it outputs

---

## 2) OWNERSHIP BOUNDARIES (ANTI-DUPLICATION)

OWNS:
- world facts/laws/constraints as canonical system data

DOES NOT OWN (hard):
- narrative events/scenes (NAR)
- character psyche (CHR)
- global artistic tone (STY)
- production timing (PRD)
- music works (MUS)

---

## 3) TRIGGERS (WHEN TO RUN)

TRIGGERS:
- new location/system/civilization introduced
- contradiction in laws or timeline
- economy/resource model required
- tech/magic capability needed
- ecology sustainability check needed

---

## 4) MINI-CONTRACT (MANDATORY)

CONSUMES:
- CORE_STATE_VALIDATION (required)
- existing world canon (if iterating)
- narrative requirements (optional)
- style constraints (optional, only if they affect cultural facts)

PRODUCES:
- WORLD_STRUCTURE_SPEC
- WORLD_LAW_SPEC
- EPOCH_SPEC
- CIV_SPEC
- POWER_MODEL
- GEO_MODEL
- ECON_RESOURCE_MODEL
- TECH_MAGIC_MODEL
- MYTH_BELIEF_MODEL
- ECOLOGY_MODEL

DEPENDS_ON:
- [] (or engine IDs)

OUTPUT_TARGET (canonical defaults):
- world systems:
  `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/04_SYSTEMS/SYS_<NAME>/<LEVEL_FOLDER>/`
- locations:
  `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/02_LOCATIONS/LOC_<NAME>/<LEVEL_FOLDER>/`
- civilizations/factions:
  `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/05_FACTIONS/FAC_<NAME>/<LEVEL_FOLDER>/`
- world bible bundle:
  `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/05_PROJECT__L2/<LEVEL_FOLDER>/`

Rule:
> L2 canon requires REG + XREF world graphs updates.

---

## 5) WORLD SCHEMAS (MANDATORY)

### 5.1 WORLD_LAW_SPEC

LAW_ID: <LAW_<NAME>>
TYPE: <PHYSICAL|META|MAGIC|SOCIAL|TECH|ECOLOGY|ECONOMY>
STATEMENT: <one clear law>
SCOPE: <GLOBAL|REGION|CIV|LOCAL>
CONSTRAINTS: [ ... ]
ALLOWANCES: [ ... ]
VIOLATIONS:
- detection_signals: [ ... ]
- resolution_policy: <fix canon|justify as exception|reject>
CANON_STATUS: <DRAFT|CANON>
CANON_REFS: [ ... ]

---

### 5.2 EPOCH_SPEC

EPOCH_ID: <EPOCH_<NAME>>
TIME_RANGE: <...>
WORLD_STATE: <summary>
TECH_TIER: <...>
POWER_DISTRIBUTION: <summary>
KEY_CIVS: [FAC_*]
KEY_LAWS: [LAW_*]
NOTES: ...

---

### 5.3 CIV_SPEC (civilization/faction)

FAC_ID: <FAC_<NAME>>
TYPE: <CIV|FACTION|EMPIRE|ORDER|NETWORK|...>
PRINCIPLES: [ ... ]
GOVERNANCE_MODEL: <...>
RESOURCE_MODEL: <see ECON_RESOURCE_MODEL refs>
CURRENCY_USED: <NO|YES|LOCAL_SURROGATE>
CURRENCY_JUSTIFICATION: <required if not NO>
TECH_MAGIC_ACCESS: <...>
ECOLOGY_FOOTPRINT: <...>

Rule:
> Great civilizations must set CURRENCY_USED=NO unless explicitly justified as “not great / transitional / local”.

---

### 5.4 ECON_RESOURCE_MODEL

MODEL_ID: <ECON_<NAME>>
CURRENCY: <NONE|LOCAL|YES>
MECHANISM:
- distribution: <allocation|access|reputation|quota|gift|contract_access|...>
RESOURCE_FLOWS:
- producers: [ ... ]
- transformers: [ ... ]
- consumers: [ ... ]
SCARCITY: <...>
FAILURE_MODES: [ ... ]
CANON_REFS: [ ... ]

---

### 5.5 TECH_MAGIC_MODEL

MODEL_ID: <TECH_<NAME>>
DOMAINS: [tech|magic|hybrid]
CAPABILITIES: [ ... ]
LIMITATIONS: [ ... ]
COSTS: [energy|risk|time|social|...]
ACCESS_CONTROL: <...>
CANON_REFS: [ ... ]

---

### 5.6 ECOLOGY_MODEL

ECO_ID: <ECO_<NAME>>
SYSTEMS: [ ... ]
CYCLES: [ ... ]
STABILITY: <stable|fragile|collapsing>
HUMAN_OR_CIV_IMPACT: <...>
CANON_REFS: [ ... ]

---

## 6) SYSTEM INTERFACE (MANDATORY) — ORC/CTL/VAL/QA/REG/XREF

ORCHESTRATED_BY (ORC):
- []

CONTROLLED_BY (CTL):
- []

VALIDATED_BY (VAL):
- <VAL.WLD.01.COHERENCE> (placeholder) or []

QA_BY (QA):
- <QA.WLD.01.CANON_INTEGRITY> (placeholder) or []

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
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__WORLD_LAW_GRAPH.md`
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__EPOCH_GRAPH.md`
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__RESOURCE_FLOW_GRAPH.md`
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__POWER_GRAPH.md`
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__ENTITY_GRAPH.md`
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__PROVENANCE.md`
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__DEPENDENCIES.md`
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CANON_REFS.md`

Rule:
> Any world law or economy model update must update WORLD_LAW_GRAPH and (if resources) RESOURCE_FLOW_GRAPH.

---

## 7) PROCESS (HOW TO EXECUTE)

1) Validate CORE state of target entities.
2) Define/update structured world specs (laws/epochs/civs/resources/tech/ecology).
3) Check currency constraint explicitly (CURRENCY_USED + justification).
4) Store outputs in routing paths.
5) Update REG + XREF graphs.
6) Run coherence validation + canon integrity QA.
7) If changing locked laws — governance pipeline.

---

## 8) QUALITY GATES (MANDATORY)

PASS if:
- laws are explicit and testable
- epochs link to laws + civs
- economy model states currency=NONE for great civs (or justified)
- REG + XREF updated

FAIL if:
- implicit laws (prose only)
- economy uses currency without justification
- hidden dependencies
- writes outside routing law

---

## 9) RAW LINK (MANDATORY)

RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/04_DOMAIN_WORLD_ENGINES/00__TEMPLATE__ENGINE__DOMAIN_WORLD_ENGINES.md

---

## FINAL RULE (LOCK)

> World canon is constraint data. Other layers consume it; they do not override it.

LOCK: FIXED
