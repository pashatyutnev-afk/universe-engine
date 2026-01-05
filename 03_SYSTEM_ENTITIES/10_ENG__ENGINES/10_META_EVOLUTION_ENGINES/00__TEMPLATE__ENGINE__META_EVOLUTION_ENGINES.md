# ENG ENGINE TEMPLATE — META_EVOLUTION_ENGINES (FAMILY OVERLAY v2)
FILE: 00__TEMPLATE__ENGINE__META_EVOLUTION_ENGINES.md

SCOPE: Universe Engine
LAYER: ENG
DOC_TYPE: TEMPLATE
ENTITY_GROUP: ENGINES (ENG)
TEMPLATE_KIND: ENGINE_FAMILY_OVERLAY
LEVEL: L4
STATUS: ACTIVE
VERSION: 2.0
ROLE: Meta family overlay. Compatible with ENG ENGINE TEMPLATE (BASE v2). Adds proposal schema, pattern library schema, optimization/roadmap schemas, and governance-first enforcement.

LOCK: FIXED
OWNER: Universe Engine

---

## 0) ENGINE IDENTITY (MANDATORY)

ENGINE_NAME: <UPPER_SNAKE_CASE>
ENGINE_ID: ENG.META.<NN>.<ENGINE_NAME>

FAMILY_CODE: META
ENGINE_NN_IN_FAMILY: <01..05>
ENGINE_CLASS: META
ENGINE_LEVEL: L4

ROLE_IN_FAMILY: <FOUNDATION|BUILDER|OUTPUT>
PIPELINE_STAGE: <DEFINE|BUILD|PRODUCE>

---

## 1) PURPOSE (WHAT THIS ENGINE DOES)

One paragraph:
- what meta improvement it provides (learning/pattern/optimization/mutation/projection)
- what it outputs (proposals/patterns/roadmaps)
- what it MUST NOT do (silent canon edits)

---

## 2) META SAFETY LAW (MANDATORY)

DEFAULT_OUTPUT_MODE: PROPOSAL

Rule:
> Any output that changes canon must be wrapped as CHANGE_PROPOSAL and routed to governance.

NO_SILENT_CANON:
- If LOCK: FIXED is touched → always governance pipeline.

---

## 3) TRIGGERS (WHEN TO RUN)

TRIGGERS:
- repeated inconsistencies or duplications detected
- pipelines get too slow/complex
- new engines/entities make old patterns outdated
- need future roadmap for building next layers

---

## 4) MINI-CONTRACT (MANDATORY)

CONSUMES:
- system registries (REG)
- dependency graph (XREF__DEPENDENCIES)
- audit log entries (optional)
- engine docs across families (optional)

PRODUCES:
- CHANGE_PROPOSALS
- PATTERN_LIBRARY_ENTRIES
- OPTIMIZATION_PLANS
- MUTATION_VARIANTS
- ROADMAPS
- PROVENANCE_RECORDS

DEPENDS_ON:
- `ENG.GOV.06.DEPENDENCY_REGISTRY` (recommended)
- `ENG.GOV.04.CHANGE_CONTROL` (recommended)

OUTPUT_TARGET:
- proposals:
  `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/99_META/PROPOSALS/`
- patterns:
  `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/99_META/PATTERNS/`
- optimizations:
  `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/99_META/OPTIMIZATIONS/`
- roadmaps:
  `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/99_META/ROADMAPS/`

---

## 5) META SCHEMAS (MANDATORY)

### 5.1 CHANGE_PROPOSAL

PROPOSAL_ID: <CHG_<YYYYMMDD>_<NN>>
TITLE: <...>
SCOPE: <ENGINE|FAMILY|INDEX|PROJECT|SYSTEM>
TARGETS:
- files: [ ...paths... ]
- engines: [ ...engine IDs... ]
RATIONALE: <why change?>
IMPACT:
- breaking_changes: [ ... ]
- dependencies_affected: [ ... ]
RISK: <LOW|MED|HIGH>
ROLLBACK: <how to revert?>
APPROVAL_REQUIRED: <true>
GOVERNANCE_PATH:
- change_control: `00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md`
- audit_log: `00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG.md`
STATUS: <DRAFT|SUBMITTED|APPROVED|REJECTED>
CANON_REFS: [ ... ]
PROVENANCE: <...>

---

### 5.2 PATTERN_LIBRARY_ENTRY

PATTERN_ID: <PAT_<NAME>>
CATEGORY: <NAMING|ROUTING|XREF|REGISTRY|STRUCTURE|QA|...>
DESCRIPTION: <one paragraph>
WHEN_TO_USE: [ ... ]
WHEN_NOT_TO_USE: [ ... ]
EXAMPLES:
- good: [ ... ]
- bad: [ ... ]
DEPENDENCIES: [ ... ]
NOTES: ...

---

### 5.3 OPTIMIZATION_PLAN

OPT_ID: <OPT_<NAME>>
TARGET: <process|docs|routing|duplication|...>
METRIC: <speed|clarity|consistency|...>
ACTIONS: [ ... ]
EXPECTED_GAIN: <...>
RISKS: [ ... ]
STATUS: <DRAFT|RUNNING|DONE>

---

### 5.4 MUTATION_VARIANT

MUT_ID: <MUT_<NAME>>
WHAT_MUTATES: <template|engine|rule|structure>
VARIANTS:
- v1: ...
- v2: ...
SELECTION_RULE: <how to pick?>
SAFETY: <bounds so it won't break canon>

---

### 5.5 ROADMAP

ROADMAP_ID: <RMP_<YYYYQ#>>
HORIZON: <weeks|months|quarters>
GOALS: [ ... ]
MILESTONES: [ ... ]
DEPENDENCY_NOTES: [ ... ]
RISKS: [ ... ]
NEXT_ACTIONS: [ ... ]

---

## 6) SYSTEM INTERFACE (MANDATORY) — ORC/CTL/VAL/QA/REG/XREF

ORCHESTRATED_BY (ORC): []
CONTROLLED_BY (CTL): []

VALIDATED_BY (VAL):
- <VAL.META.01.SAFETY> (placeholder) or []
- <VAL.META.02.DEPENDENCY_IMPACT> (placeholder) or []

QA_BY (QA):
- <QA.META.01.CANON_GUARD> (placeholder) or []

REGISTRY_UPDATES:
- REQUIRED: YES (for proposals/roadmaps if you track them)
- TARGETS:
  - `00_REG__REGISTRIES/REG.PRJ.<PROJECT_ID>.META_PROPOSALS.md` (recommended)
  - `00_REG__REGISTRIES/REG.PRJ.<PROJECT_ID>.RUNS.md` (recommended)

XREF_UPDATES:
- REQUIRED: YES
- TARGETS:
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CHANGE_PROPOSALS.md`
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__PATTERN_LIBRARY.md`
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__PROVENANCE.md`
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__DEPENDENCIES.md`

---

## 7) PROCESS (HOW TO EXECUTE)

1) Scan system artifacts (indexes, registries, xrefs).
2) Detect patterns/duplication/inconsistencies.
3) Produce proposals (not edits) with impact + rollback.
4) Update proposal registries/xrefs.
5) Submit through governance pipeline.
6) After approval — execute changes, log in audit.

---

## 8) QUALITY GATES (MANDATORY)

PASS if:
- outputs are labeled PROPOSAL by default
- each proposal has impact + rollback + governance path
- dependencies are explicit
- no silent edits to locked canon

FAIL if:
- direct canon rewrite without proposal
- missing rollback
- hidden dependency changes

---

## 9) RAW LINK (MANDATORY)

RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/10_META_EVOLUTION_ENGINES/00__TEMPLATE__ENGINE__META_EVOLUTION_ENGINES.md

---

## FINAL RULE (LOCK)

> META improves the system via proposals and governance, never via silent canon edits.

LOCK: FIXED
