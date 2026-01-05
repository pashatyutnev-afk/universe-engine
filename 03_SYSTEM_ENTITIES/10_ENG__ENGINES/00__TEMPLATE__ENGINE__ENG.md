# ENG ENGINE TEMPLATE (BASE v2)
FILE: 00__TEMPLATE__ENGINE__ENG.md

SCOPE: Universe Engine
LAYER: ENG
DOC_TYPE: TEMPLATE
ENTITY_GROUP: ENGINES (ENG)
TEMPLATE_KIND: ENGINE_BASE
LEVEL: L1
STATUS: ACTIVE
VERSION: 2.0
ROLE: Canonical base template for any ENG engine file. Defines mandatory interface, project output routing (L0–L3), and integration with ORC/CTL/VAL/QA/REG/XREF.

LOCK: FIXED
OWNER: Universe Engine

---

## 0) ENGINE IDENTITY (MANDATORY)

ENGINE_NAME: <UPPER_SNAKE_CASE>
ENGINE_ID: ENG.<FAMILY_CODE>.<NN>.<ENGINE_NAME>

FAMILY_CODE: <GOV|CORE|NAR|CHR|WLD|EXP|STY|FMT|PRD|MUS|MET>
ENGINE_NN_IN_FAMILY: <01..99>
ENGINE_CLASS: <GOVERNANCE|CORE|DOMAIN|EXPRESSION|STYLE|PRODUCTION|SOUND|META>
ENGINE_LEVEL: <L1|L2|L3|L4>

ROLE_IN_FAMILY: <FOUNDATION|BUILDER|VALIDATOR|BRIDGE|OUTPUT>
PIPELINE_STAGE: <DEFINE|BUILD|CHECK|PACKAGE|PRODUCE>

CANON_COMPAT:
- INDEX: 02__INDEX_ALL_ENGINES.md
- NAMING_RULE: NN in file name MUST match ENGINE_NN_IN_FAMILY

---

## 1) PURPOSE (WHAT THIS ENGINE DOES)

One paragraph (3–6 lines):
- What problem it solves
- What it produces (artifact types)
- Who consumes it (other engines / layers)

---

## 2) OWNERSHIP BOUNDARIES (ANTI-DUPLICATION)

### 2.1 OWNS (this engine is responsible for)
- <bullet list of what it owns>

### 2.2 DOES NOT OWN (hard boundaries)
- <bullet list of what is explicitly NOT owned>
Rule:
> If it is in DOES NOT OWN — this engine must not generate or modify it.

---

## 3) TRIGGERS (WHEN TO RUN)

TRIGGERS:
- <trigger 1>
- <trigger 2>
- <trigger 3>

---

## 4) MINI-CONTRACT (MANDATORY)

CONSUMES: (1–5)
- <INPUT_ARTIFACT_TYPE_1>
- <INPUT_ARTIFACT_TYPE_2>

PRODUCES: (1–5)
- <OUTPUT_ARTIFACT_TYPE_1>
- <OUTPUT_ARTIFACT_TYPE_2>

DEPENDS_ON:
- []  (or list of engine IDs; must also be recorded in XREF__DEPENDENCIES)

OUTPUT_TARGET:
- DEFAULT: `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/<ROUTING>/`
- See section 6 (System Interface) for exact routing law.

Rule:
> If MINI-CONTRACT is missing — engine is incomplete.

---

## 5) PARAMETERS (MANDATORY)

PROJECT_ID: <PRJ_<NAME> or your project key>
OUTPUT_SCOPE: <ENTITY|PROJECT|SYSTEM>

DOMAIN_FOLDER (WORKSHOP):
- <01_CHARACTERS|02_LOCATIONS|03_OBJECTS|04_SYSTEMS|05_FACTIONS|06_EVENTS|07_CONCEPTS|08_RELATIONSHIPS|09_ARCS|10_STYLES|11_EXPERIMENTS|12_PRODUCTION|13_MUSIC|99_META|...>

ENTITY_ID (if OUTPUT_SCOPE=ENTITY):
- <CHR_<NAME> | LOC_<NAME> | OBJ_<NAME> | EVT_<NAME> | ARC_<NAME> | ...>

LEVEL_FOLDER:
- L0: `01_INTAKE_L0`
- L1: `02_DRAFT_L1`
- L2: `03_CANON_L2`
- L3: `04_OUTPUT_L3`

FORMAT_NOTE:
- Format constraints (FMT) are dependencies, not storage rules.
- Storage rules are defined here, by OUTPUT_SCOPE + DOMAIN_FOLDER + LEVEL_FOLDER.

---

## 6) SYSTEM INTERFACE (MANDATORY) — ORC/CTL/VAL/QA/REG/XREF INTEGRATION

### 6.1 ROUTING LAW (OUTPUT PATHS)

Base root (always):
`05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/`

#### A) ENTITY scope (canonical)
`05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/<DOMAIN_FOLDER>/<ENTITY_ID>/<LEVEL_FOLDER>/`

Example:
`05_PROJECTS/PRJ_ALPHA/01_WORKSHOP/01_CHARACTERS/CHR_Ilya/02_DRAFT_L1/`

#### B) PROJECT scope (canonical)
`05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/<PROJECT_AREA>/<LEVEL_FOLDER>/`

PROJECT_AREA examples:
- `02_INTAKE_L0/` (global intake index)
- `03_PROJECT__L1/`
- `04_PROJECT__L2/`
- `05_PROJECT__L3/`

Example:
`05_PROJECTS/PRJ_ALPHA/01_WORKSHOP/05_PROJECT__L3/04_OUTPUT_L3/`

#### C) SYSTEM scope (only if explicitly allowed by governance)
`03_SYSTEM_ENTITIES/<...>/` (must go through Governance change control)

Rule:
> Default is ENTITY or PROJECT scope. SYSTEM scope requires Governance approval.

---

### 6.2 ORCHESTRATION / CONTROL / VALIDATION (MANDATORY)

ORCHESTRATED_BY (ORC):
- <ORC.<GROUP>.<NN>.<NAME>> or []

CONTROLLED_BY (CTL):
- <CTL.<GROUP>.<NN>.<NAME>> or []

VALIDATED_BY (VAL):
- <VAL.<GROUP>.<NN>.<NAME>> or []

QA_BY (QA):
- <QA.<GROUP>.<NN>.<NAME>> or []

Rule:
> If the engine outputs L2 or L3 — VALIDATED_BY and QA_BY cannot be empty.

---

### 6.3 REGISTRY UPDATES (MANDATORY)

REGISTRY_UPDATES:
- REQUIRED: <YES|NO>
- TARGETS (choose):
  - `00_REG__REGISTRIES/REG.PRJ.<PROJECT_ID>.ENTITIES.md`
  - `00_REG__REGISTRIES/REG.PRJ.<PROJECT_ID>.CANON_L2.md`
  - `00_REG__REGISTRIES/REG.PRJ.<PROJECT_ID>.OUTPUT_L3.md`
  - `00_REG__REGISTRIES/REG.PRJ.<PROJECT_ID>.ASSETS.md`
  - `00_REG__REGISTRIES/REG.SYS.<NAME>.md` (system-level; governance required)

Rule:
> If output_level is L2 or L3 — registry update is REQUIRED.

---

### 6.4 XREF Updates (MANDATORY)

XREF_UPDATES:
- REQUIRED: <YES|NO>
- RECORD_TYPES (pick):
  - CANON_REF
  - DEPENDS_ON
  - DERIVED_FROM
  - PRODUCED_BY
  - CONFLICTS_WITH
  - REPLACES
  - BREAKS
  - ASSET_LINK
  - EDIT_DECISION
- TARGETS (choose):
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CANON_REFS.md`
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__DEPENDENCIES.md`
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__PROVENANCE.md`
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__ENTITY_GRAPH.md`
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CAUSE_EFFECT_GRAPH.md` (if applicable)
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__ASSET_GRAPH.md` (if applicable)
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__EDIT_DECISIONS.md` (if applicable)
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CHANGES.md` (meta/governance)

Rule:
> If DEPENDS_ON in MINI-CONTRACT is not empty — XREF__DEPENDENCIES is REQUIRED.

---

### 6.5 DEPENDENCY LAW (MANDATORY)

- DEPENDS_ON must list engines as engine IDs (ENG.<FAMILY_CODE>.<NN>.<NAME>)
- Any dependency must be duplicated into:
  - XREF__DEPENDENCIES
  - (if system-level) Governance dependency registry

Rule:
> No hidden dependencies.

---

## 7) PROCESS (HOW TO EXECUTE)

STEPS:
1) Read required constraints (Style/Format/World/Canon as listed in CONSUMES + DEPENDS_ON).
2) Produce outputs strictly in PRODUCES types.
3) Write outputs to OUTPUT_TARGET (routing law).
4) Update registries (if REQUIRED).
5) Update xref indexes (if REQUIRED).
6) Run validators + QA (if required by output level).
7) If output is L2 CANON — route through Governance pipeline before locking.

---

## 8) QUALITY GATES (MANDATORY)

PASS if:
- MINI-CONTRACT complete (consumes/produces/depends/output_target)
- Output stored in correct routing path
- REG + XREF updated (when required)
- Validators + QA listed (when L2/L3)
- No violation of DOES NOT OWN boundaries

FAIL if:
- Output written outside routing law
- Hidden dependencies
- Missing REG/XREF for L2/L3
- Engine attempts to modify canon without Governance

---

## 9) FAILURE MODES

- Dependency missing → stop, register dependency and xref it
- Output location ambiguous → apply routing law; never invent new folder without governance
- Conflict detected (contradictions) → record CONFLICTS_WITH in XREF + escalate to governance

---

## 10) RAW LINK (MANDATORY)

RAW: <raw github link to this file>

---

## FINAL RULE (LOCK)

> This base template is the contract of ENG engines with the whole system (ORC/CTL/VAL/QA/REG/XREF + routing).  
> All family engine templates MUST be compatible with it.

LOCK: FIXED
