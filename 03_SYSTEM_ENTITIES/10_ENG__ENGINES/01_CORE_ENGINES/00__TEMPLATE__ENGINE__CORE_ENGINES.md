# ENG ENGINE TEMPLATE — CORE_ENGINES (FAMILY OVERLAY v2)
FILE: 00__TEMPLATE__ENGINE__CORE_ENGINES.md

SCOPE: Universe Engine
LAYER: ENG
DOC_TYPE: TEMPLATE
ENTITY_GROUP: ENGINES (ENG)
TEMPLATE_KIND: ENGINE_FAMILY_OVERLAY
LEVEL: L1
STATUS: ACTIVE
VERSION: 2.0
ROLE: Core family overlay. Compatible with ENG ENGINE TEMPLATE (BASE v2). Adds mandatory core identifiers, state gating, and lifecycle routing rules.

LOCK: FIXED
OWNER: Universe Engine

---

## 0) ENGINE IDENTITY (MANDATORY)

ENGINE_NAME: <UPPER_SNAKE_CASE>
ENGINE_ID: ENG.CORE.<NN>.<ENGINE_NAME>

FAMILY_CODE: CORE
ENGINE_NN_IN_FAMILY: <01..03>
ENGINE_CLASS: CORE
ENGINE_LEVEL: L1

ROLE_IN_FAMILY: <FOUNDATION|VALIDATOR|OUTPUT>
PIPELINE_STAGE: <DEFINE|CHECK|PRODUCE>

CANON_COMPAT:
- INDEX: 02__INDEX_ALL_ENGINES.md
- file name NN must match ENGINE_NN_IN_FAMILY

---

## 1) PURPOSE (WHAT THIS ENGINE DOES)

One paragraph:
- Identity: define minimal identity contract
- State: define and validate current status
- Lifecycle: define transitions and allowed moves between L0–L3 + archive

---

## 2) OWNERSHIP BOUNDARIES (ANTI-DUPLICATION)

### 2.1 OWNS
- core identity/state/lifecycle records and gates

### 2.2 DOES NOT OWN (hard)
- narrative/character/world/style/format/production/music content
- governance approvals
Rule:
> Core provides gates; it does not generate domain content.

---

## 3) TRIGGERS (WHEN TO RUN)

TRIGGERS:
- new entity created
- entity state changes (draft→canon, canon→archive)
- project starts a new output cycle
- before producing any L2/L3 artifact
- periodic integrity checks

---

## 4) MINI-CONTRACT (MANDATORY)

CONSUMES:
- ENTITY_REQUEST (create/update) OR PROJECT_CONTEXT
- EXISTING_CORE_RECORDS (if updating)
- GOVERNANCE_DECISION (if state change requires it) (optional)

PRODUCES:
- CORE_IDENTITY_RECORD
- CORE_STATE_RECORD
- LIFECYCLE_TRANSITION_RECORD

DEPENDS_ON:
- [] (or governance engines if enforced)

OUTPUT_TARGET:
- ENTITY scope:
  `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/<DOMAIN_FOLDER>/<ENTITY_ID>/<LEVEL_FOLDER>/`
- PROJECT scope:
  `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/03_PROJECT__L1/<LEVEL_FOLDER>/`
- SYSTEM scope (only for core laws/registries):
  `03_SYSTEM_ENTITIES/` (governance compatible)

---

## 5) PARAMETERS (MANDATORY)

PROJECT_ID: <PRJ_*>
OUTPUT_SCOPE: <ENTITY|PROJECT|SYSTEM>

DOMAIN_FOLDER:
- one of entity domains (characters/locations/objects/systems/etc) if ENTITY scope

ENTITY_ID:
- required if ENTITY scope

LEVEL_FOLDER:
- L0 `01_INTAKE_L0`
- L1 `02_DRAFT_L1`
- L2 `03_CANON_L2`
- L3 `04_OUTPUT_L3`

CORE_STATUS:
- <NEW|DRAFT|CANON|ACTIVE|ARCHIVED|DEPRECATED>

---

## 6) SYSTEM INTERFACE (MANDATORY) — ORC/CTL/VAL/QA/REG/XREF

### 6.1 ORC/CTL/VAL/QA

ORCHESTRATED_BY (ORC):
- [] (or ORC IDs if used)

CONTROLLED_BY (CTL):
- [] (or CTL IDs)

VALIDATED_BY (VAL):
- <VAL.CORE.01.STATE_VALIDATION> (placeholder) or []

QA_BY (QA):
- <QA.CORE.01.CORE_INTEGRITY> (placeholder) or []

Rule:
> If the engine writes L2/L3 state changes — validation is required.

---

### 6.2 REGISTRY UPDATES (MANDATORY)

REGISTRY_UPDATES:
- REQUIRED: YES
- TARGETS:
  - `00_REG__REGISTRIES/REG.PRJ.<PROJECT_ID>.ENTITIES.md`
  - `00_REG__REGISTRIES/REG.PRJ.<PROJECT_ID>.CANON_L2.md` (if canonized)
  - `00_REG__REGISTRIES/REG.SYS.ENTITIES.md` (optional system mirror)

---

### 6.3 XREF UPDATES (MANDATORY)

XREF_UPDATES:
- REQUIRED: YES
- RECORD_TYPES:
  - CANON_REF
  - DERIVED_FROM
  - REPLACES
  - BREAKS
  - PRODUCED_BY
- TARGETS:
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__ENTITY_GRAPH.md`
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__PROVENANCE.md`
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CHANGES.md` (if lifecycle change is major)

---

## 7) CORE RECORD SCHEMAS (MANDATORY)

### 7.1 CORE IDENTITY RECORD

ENTITY_ID: <CHR_*|LOC_*|OBJ_*|EVT_*|ARC_*|...>
ENTITY_TYPE: <CHARACTER|LOCATION|OBJECT|SYSTEM|FACTION|EVENT|CONCEPT|RELATIONSHIP|ARC|STYLE|...>
DISPLAY_NAME: <human name>
PROJECT_ID: <PRJ_*>
CREATED_AT: <ISO>
STATUS: <CORE_STATUS>
NOTES: <optional>
CANON_REF: <if canon exists>

---

### 7.2 CORE STATE RECORD

ENTITY_ID: <...>
STATE: <NEW|DRAFT|CANON|ACTIVE|ARCHIVED|DEPRECATED>
LAST_UPDATED: <ISO>
ALLOWED_ACTIONS:
- <edit|canonize|output|archive|revive>
REQUIRES_GOVERNANCE:
- <true|false>
GOV_DECISION_REF: <optional>

---

### 7.3 LIFECYCLE TRANSITION RECORD

TRANSITION_ID: <unique>
ENTITY_ID: <...>
FROM: <state>
TO: <state>
REASON: ...
TIMESTAMP: <ISO>
AFFECTED_ARTIFACTS: [ ... ]
MIGRATION_NOTES: <optional>
GOV_DECISION_REF: <optional>

Rule:
> Any transition to CANON or ARCHIVED must be explicitly recorded.

---

## 8) PROCESS (HOW TO EXECUTE)

1) Ensure ENTITY_ID exists (or create it).
2) Validate state and allowed actions.
3) If action requires governance — attach decision reference.
4) Write identity/state/transition records to correct routing.
5) Update registries.
6) Update xref (entity graph + provenance).
7) If canonized — lock relevant outputs.

---

## 9) QUALITY GATES (MANDATORY)

PASS if:
- entity has stable ID + type
- state record is consistent with lifecycle transition
- registries updated
- xref updated
- governance reference included when required

FAIL if:
- entity produced outputs without identity/state
- state jumps without transition record
- canon changes without governance link

---

## 10) RAW LINK (MANDATORY)

RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/01_CORE_ENGINES/00__TEMPLATE__ENGINE__CORE_ENGINES.md

---

## FINAL RULE (LOCK)

> CORE gates identity and state. No L2/L3 production without CORE validity.

LOCK: FIXED
