# ENG ENGINE TEMPLATE — UNIVERSAL v2
FILE: 00__TEMPLATE__ENGINE__ENG.md

SCOPE: Universe Engine
LAYER: ENG
DOC_TYPE: TEMPLATE
ENTITY_KIND: GENERIC
PROJECT_SCOPE: GLOBAL
OUTPUT_LEVEL: N/A
ID: ENG.TEMPLATE.ENGINE
STATUS: ACTIVE
VERSION: 2.0
ROLE: Universal template for any ENG engine file. Defines engine identity, role in family, mini-contract, system interface (REG/XREF/WORKSHOP), process, quality gates, and failure handling.

---

## 0) ENGINE IDENTITY (MANDATORY)

ENGINE_NAME: <UPPER_SNAKE_CASE>
ENGINE_ID: <ENG.<FAMILYCODE>.<NN>.<ENGINE_NAME>>
FAMILY_CODE: <e.g., GOV|CORE|NARR|CHAR|WORLD|EXPR|STYLE|FORMAT|PROD|MUS|META>
ENGINE_NN_IN_FAMILY: <01..99>
ENGINE_CLASS: <GOVERNANCE|CORE|DOMAIN|EXPRESSION|STYLE|PRODUCTION|SOUND|META>
ENGINE_LEVEL: <L1|L2|L3|L4>

ROLE_IN_FAMILY: <FOUNDATION|BUILDER|VALIDATOR|BRIDGE|OUTPUT|REGISTRY|MODIFIER|ANALYTICS>
PIPELINE_STAGE: <DEFINE|BUILD|CHECK|PACKAGE|PRODUCE>

OWNER: Universe Engine
LOCK: OPEN

---

## 1) PURPOSE (WHAT THIS ENGINE DOES)

One paragraph:
- What decision/output this engine is responsible for
- What it explicitly does NOT do (boundary)

### OWNERSHIP (this engine owns)
- <1–5 bullets>

### DOES NOT OWN (belongs elsewhere)
- <1–5 bullets + pointers to other engines/families>

---

## 2) TRIGGERS (WHEN TO RUN)

TRIGGERS:
- <event 1: e.g., new entity intake created>
- <event 2: e.g., draft promoted to L1>
- <event 3: e.g., canon revision request>

OUTPUT_CONFIDENCE_TARGET: <LOW|MEDIUM|HIGH>

---

## 3) MINI-CONTRACT (MANDATORY)

CONSUMES:
- <1–5 input artifact types or ids>

PRODUCES:
- <1–5 output artifact types or ids>

DEPENDS_ON:
- [<ENG.* ids>] or []

OUTPUT_ARTIFACT_TYPE:
- <CANON_SPEC|CANON_MODEL|CANON_CARD|STYLE_BIBLE|FORMAT_SPEC|SHOTLIST|EDIT_PLAN|MUSIC_STEMS|...>

---

## 4) SYSTEM INTERFACE (MANDATORY) — REPO MACHINE CONTRACT

## SYSTEM INTERFACE
- INPUTS:
  - artifacts: [<ids/types>]
  - sources: [<paths/registries/xref indexes>]

- OUTPUTS:
  - artifacts: [<ids/types>]
  - output_level: <L0_INTAKE|L1_DRAFT|L2_CANON|L3_OUTPUT>
  - entity_kind: <CHR|LOC|OBJ|SYS|FAC|EVT|CPT|REL|ARC|STY|EXP|GENERIC>

  - target_path_rule:
    - base: `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/`
    - category: <01_CHARACTERS|02_LOCATIONS|03_OBJECTS|04_SYSTEMS|05_FACTIONS|06_EVENTS|07_CONCEPTS|08_RELATIONSHIPS|09_ARCS|10_STYLES|11_EXPERIMENTS|05_PROJECT__L3>
    - entity_folder: <e.g., CHR_<NAME> or EVT_<NAME> or STY_<NAME> or GENERIC_<NAME>>
    - level_folder:
      - L0: `01_INTAKE_L0/`
      - L1: `02_DRAFT_L1/`
      - L2: `03_CANON_L2/`
      - L3: `04_OUTPUT_L3/`
    - file: <e.g., 00__CANON.md / 00__STYLE_BIBLE.md / 00__SHOTLIST.md>

- REGISTRY_UPDATES:
  - required: <YES|NO>
  - registries: [<REG ids/paths>]
  - entries_to_add:
    - <ID, TYPE, LEVEL, PATH, STATUS, OWNER, CREATED_BY>

- XREF_UPDATES:
  - required: <YES|NO>
  - record_types:
    - [<DEPENDS_ON|DERIVED_FROM|PRODUCED_BY|CANON_REF|PRODUCTION_REF|ENTITY_LINK|REPLACED_BY|CONFLICTS_WITH|...>]
  - xref_targets: [<XREF index ids/paths>]
  - mandatory_links (fill when relevant):
    - <A_ID> -> <B_ID> | TYPE:<...> | SCOPE:<...> | WHY:<...> | BY:<...> | AT:<YYYY-MM-DD>

- GATES:
  - validators: [<VAL ids>]
  - qa_checks: [<QA ids>]

- ORCHESTRATION:
  - orc_owner: <ORC id or []>
  - ctl_enforcers: [<CTL ids>]

If SYSTEM INTERFACE is missing or incomplete → engine file is **invalid**.

---

## 5) PROCESS (HOW IT WORKS)

### 5.1 Steps (strict)
1) <step 1>
2) <step 2>
3) <step 3>

### 5.2 Input normalization
- what must be cleaned/standardized before processing

### 5.3 Output format rules
- exact headings / structure the output artifact must contain

---

## 6) QUALITY (MANDATORY)

### 6.1 Quality checklist
- Completeness: <what “complete” means>
- Consistency: <what must not contradict>
- Traceability: outputs must be linked in XREF and registered in REG (if required)
- Boundary compliance: no scope leaks

### 6.2 Validation gates
- Validators required: <list>
- QA checks required: <list>

### 6.3 Acceptance criteria (binary)
- PASS if:
  - <criteria>
- FAIL if:
  - <criteria>

---

## 7) FAILURE MODES (WHAT CAN GO WRONG)

- Missing inputs → action
- Conflicting canon → action (must create XREF CONFLICTS_WITH and/or route to governance)
- Hidden dependency found → action (must update XREF dependency)
- Output written to wrong level/path → action (CTL must reject)

---

## 8) RAW LINK (MANDATORY)

RAW: <raw github link to this engine file>

---

## 9) FINAL RULE (LOCK)

> Этот движок обязателен к соблюдению в рамках своего семейства и общего ENG index.  
> Любые изменения проходят governance pipeline.

OWNER: Universe Engine  
LOCK: OPEN
