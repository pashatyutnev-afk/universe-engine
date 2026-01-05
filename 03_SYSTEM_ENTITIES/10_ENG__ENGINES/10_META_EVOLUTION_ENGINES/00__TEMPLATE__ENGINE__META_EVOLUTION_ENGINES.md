# ENG ENGINE TEMPLATE — META_EVOLUTION_ENGINES (FAMILY OVERLAY v2)
FILE: 00__TEMPLATE__ENGINE__META_EVOLUTION_ENGINES.md

SCOPE: Universe Engine
LAYER: ENG
DOC_TYPE: TEMPLATE
ENTITY_KIND: META
PROJECT_SCOPE: GLOBAL
OUTPUT_LEVEL: N/A
ID: ENG.TPL.ENGINE.META
STATUS: ACTIVE
VERSION: 2.0
ROLE: Family-specific overlay template for Meta engines. Compatible with ENG ENGINE TEMPLATE v2 and enforces Change Proposal outputs + governance approval path.

---

## 0) ENGINE IDENTITY (MANDATORY)

ENGINE_NAME: <UPPER_SNAKE_CASE>
ENGINE_ID: <ENG.MET.<NN>.<ENGINE_NAME>>

FAMILY_CODE: MET
ENGINE_NN_IN_FAMILY: <01..05>
ENGINE_CLASS: META
ENGINE_LEVEL: L4

ROLE_IN_FAMILY: <FOUNDATION|BUILDER|VALIDATOR|OUTPUT>
PIPELINE_STAGE: <DEFINE|BUILD|CHECK|PRODUCE>

OWNER: Universe Engine
LOCK: OPEN

---

## 1) PURPOSE (WHAT THIS ENGINE DOES)

One paragraph: which meta capability it performs and what proposals or reports it outputs.

### DOES NOT OWN (hard)
- direct canon edits
- approvals
- unregistered changes

---

## 2) TRIGGERS (WHEN TO RUN)

TRIGGERS:
- audit log shows recurring issues
- consistency engine flags conflicts
- dependency graph grows chaotic
- templates drift across families
- quality drops or production friction rises
- roadmap planning needed

---

## 3) MINI-CONTRACT (MANDATORY)

CONSUMES (examples):
- AUDIT_LOG
- CONSISTENCY_REPORTS
- DEPENDENCY_REGISTRY_SNAPSHOT
- QA outputs
- project outcome metrics/feedback

PRODUCES (examples):
- SIGNAL_REPORT
- PATTERN_REPORT
- CHANGE_PROPOSAL (CP)
- MIGRATION_PACK
- EVOLUTION_ROADMAP

DEPENDS_ON:
- []  (if depends → mirror in XREF__DEPENDENCIES)

OUTPUT_ARTIFACT_TYPE:
- <SIGNAL_REPORT|PATTERN_REPORT|CHANGE_PROPOSAL|MIGRATION_PACK|EVOLUTION_ROADMAP>

---

## 4) CHANGE PROPOSAL SCHEMA (MANDATORY WHEN OUTPUT=CP)

CP_ID: <unique>
TARGET_SCOPE: <ENG_TEMPLATES|FAMILY_RULES|REGISTRIES|XREF|GOVERNANCE|PROJECT_PIPELINE>
PROBLEM: ...
EVIDENCE:
  - <refs>
PROPOSED_CHANGE: ...
IMPACT:
  AFFECTED_FILES: [ ... ]
  AFFECTED_FAMILIES: [ ... ]
  BREAKING: true|false
MIGRATION_PLAN:
  STEPS:
    - ...
  ROLLBACK:
    - ...
RISK:
  - ...
REQUIRED_APPROVALS:
  - `00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md`
  - `00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG.md`
STATUS: <DRAFT|PROPOSED|APPROVED|REJECTED>

Rule:
> CP must include IMPACT + MIGRATION_PLAN + REQUIRED_APPROVALS.

---

## 5) SYSTEM INTERFACE (MANDATORY) — META DEFAULTS

## SYSTEM INTERFACE
- OUTPUTS:
  - output_level: <L0_INTAKE|L1_DRAFT|L2_CANON|L3_OUTPUT>
  - target_path_rule:
    - base: `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/`
    - category: `99_META/`
    - subfolders:
      - signals: `01_SIGNALS/`
      - proposals: `02_PROPOSALS/`
      - migrations: `03_MIGRATIONS/`
      - roadmap: `04_ROADMAP/`
    - level_folder:
      - L0: `01_INTAKE_L0/`
      - L1: `02_DRAFT_L1/`
      - L2: `03_CANON_L2/`
      - L3: `04_OUTPUT_L3/`

- REGISTRY_UPDATES:
  - required: YES (for CP and roadmap)
  - registries:
    - `REG.PRJ.<PROJECT_ID>.META_PROPOSALS`
    - `REG.SYS.META_PROPOSALS` (if system-wide)

- XREF_UPDATES:
  - required: YES
  - record_types:
    - [CANON_REF, DEPENDS_ON, DERIVED_FROM, PRODUCED_BY, REPLACES, BREAKS]
  - xref_targets:
    - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CHANGES.md`
    - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__PROVENANCE.md`
    - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__DEPENDENCIES.md`

- GATES:
  - validators:
    - `VAL.MET.01.CP_SCHEMA_VALID` (placeholder)
    - `VAL.MET.02.GOV_APPROVALS_LISTED` (placeholder)

---

## 6) QUALITY (MANDATORY)

PASS if:
- CP includes impact + migration + approvals
- references to affected files are explicit
- does not attempt to apply changes directly

FAIL if:
- “рекомендации” без плана миграции
- попытка поменять канон без governance

---

## FINAL RULE (LOCK)

> Meta engines propose. Governance approves. Layers implement.

OWNER: Universe Engine  
LOCK: OPEN
