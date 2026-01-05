# ENG ENGINE TEMPLATE — GOVERNANCE_ENGINES (FAMILY OVERLAY v2)
FILE: 00__TEMPLATE__ENGINE__GOVERNANCE_ENGINES.md

SCOPE: Universe Engine
LAYER: ENG
DOC_TYPE: TEMPLATE
ENTITY_KIND: GENERIC
PROJECT_SCOPE: GLOBAL
OUTPUT_LEVEL: N/A
ID: ENG.TPL.ENGINE.GOVERNANCE
STATUS: ACTIVE
VERSION: 2.0
ROLE: Family-specific overlay template for GOV engines. Compatible with ENG ENGINE TEMPLATE v2 and adds governance defaults (roles, REG/XREF checkpoints, workshop routing).

---

## 0) ENGINE IDENTITY (MANDATORY)

ENGINE_NAME: <UPPER_SNAKE_CASE>
ENGINE_ID: <ENG.GOV.<NN>.<ENGINE_NAME>>

FAMILY_CODE: GOV
ENGINE_NN_IN_FAMILY: <01..10>
ENGINE_CLASS: GOVERNANCE
ENGINE_LEVEL: L1

ROLE_IN_FAMILY: <FOUNDATION|BUILDER|VALIDATOR|BRIDGE|OUTPUT>
PIPELINE_STAGE: <DEFINE|BUILD|CHECK|PACKAGE|PRODUCE>

OWNER: Universe Engine
LOCK: OPEN

---

## 1) PURPOSE (WHAT THIS ENGINE DOES)

One paragraph:
- что именно этот engine фиксирует/проверяет/разрешает
- какие решения он “владеет”
- что он не делает (boundary)

### OWNERSHIP
- <1–5 bullets>

### DOES NOT OWN
- <1–5 bullets + pointers>

---

## 2) TRIGGERS (WHEN TO RUN)

TRIGGERS:
- new change request (L0)
- governance decision needed (L1)
- canon/templating update requested
- conflict or duplication detected
- dependency change proposed
- version bump required

OUTPUT_CONFIDENCE_TARGET: HIGH (для L2 решений) / MEDIUM (для черновиков)

---

## 3) MINI-CONTRACT (MANDATORY)

CONSUMES:
- CHANGE_REQUEST
- DECISION_PROPOSAL
- DEPENDENCY_DECLARATION
- CONFLICT_REPORT
- VERSION_NOTE

PRODUCES:
- APPROVED_DECISION
- AUDIT_LOG_ENTRY
- DEPENDENCY_REGISTRY_UPDATE
- VERSION_RECORD
- RELEASE_NOTES / CANON_CHANGELOG (если OUTPUT)

DEPENDS_ON:
- []  (если есть зависимости — обязаны быть отражены в XREF DEPENDS_ON)

OUTPUT_ARTIFACT_TYPE:
- <APPROVED_DECISION|AUDIT_LOG_ENTRY|DEPENDENCY_REGISTRY_UPDATE|VERSION_RECORD|RELEASE_NOTES>

---

## 4) SYSTEM INTERFACE (MANDATORY) — GOVERNANCE DEFAULTS

## SYSTEM INTERFACE
- INPUTS:
  - artifacts: [change requests, draft decisions, dependency proposals, conflict reports]
  - sources:
    - ENG INDEX + family README
    - relevant REG registries
    - project XREF indexes

- OUTPUTS:
  - artifacts: [governance artifacts]
  - output_level: <L0_INTAKE|L1_DRAFT|L2_CANON|L3_OUTPUT>
  - entity_kind: GENERIC

  - target_path_rule (project-scoped governance workspace):
    - base: `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/`
    - category: `11_EXPERIMENTS`
    - entity_folder: `GENERIC_GOVERNANCE`
    - level_folder:
      - L0: `01_INTAKE_L0/`
      - L1: `02_DRAFT_L1/`
      - L2: `03_CANON_L2/`
      - L3: `04_OUTPUT_L3/`
    - file examples:
      - `00__CHANGE_REQUEST.md` (L0)
      - `00__DECISION_DRAFT.md` (L1)
      - `00__APPROVED_DECISION.md` (L2)
      - `00__RELEASE_NOTES.md` (L3)

- REGISTRY_UPDATES:
  - required: YES (for L2/L3; optional for L0/L1)
  - registries:
    - `REG.PRJ.<PROJECT_ID>.GOV.CHANGES`
    - `REG.PRJ.<PROJECT_ID>.GOV.DECISIONS`
    - `REG.PRJ.<PROJECT_ID>.GOV.VERSIONS`
  - entries_to_add:
    - <artifact id/path + level + status + created_by>

- XREF_UPDATES:
  - required: YES
  - record_types:
    - [DEPENDS_ON, DERIVED_FROM, PRODUCED_BY, REPLACED_BY, MOVED_TO, RENAMED_TO, CONFLICTS_WITH, DUPLICATES, CANON_REF]
  - xref_targets:
    - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__DEPENDENCIES.md`
    - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CHANGES.md`
    - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CONFLICTS.md`
    - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CANON_REFS.md`
  - mandatory_links (examples; adapt per engine):
    - `L2_DECISION_ID -> L1_DRAFT_ID | TYPE:DERIVED_FROM | SCOPE:PRJ:<PROJECT_ID> | WHY:Decision approved from draft | BY:ENG.GOV.<NN>.<ENGINE_NAME> | AT:<YYYY-MM-DD>`
    - `NEW_CANON_ID -> OLD_CANON_ID | TYPE:REPLACED_BY | SCOPE:GLOBAL | WHY:Canon updated by governance decision | BY:ENG.GOV.<NN>.<ENGINE_NAME> | AT:<YYYY-MM-DD>`

- GATES:
  - validators:
    - `VAL.XREF.02.INDEX_CONSISTENCY` (placeholder)
    - `VAL.REG.01.SCHEMA_CHECK` (placeholder)
  - qa_checks:
    - `QA.ENG.01.READABILITY_COMPLETENESS` (placeholder)
    - `QA.XREF.01.LINK_INTEGRITY` (placeholder)

- ORCHESTRATION:
  - orc_owner: [<ORC.GOV.* if used>]
  - ctl_enforcers:
    - `CTL.XREF.NO_HIDDEN_LINKS` (placeholder)
    - `CTL.REG.ENTRY_ENFORCER` (placeholder)
    - `CTL.WORKSHOP.LEVEL_ENFORCER` (placeholder)

If SYSTEM INTERFACE is missing → engine invalid.

---

## 5) PROCESS (HOW IT WORKS)

1) Intake: принять request/проблему/конфликт (L0)
2) Draft: сформировать вариант решения + последствия (L1)
3) Check: проверить scope impact + consistency + risks (VAL/QA) (L1)
4) Canonize: утвердить решение (L2) и зарегистрировать его (REG)
5) Link: записать XREF (dependencies/changes/conflicts/canon refs)
6) Output: при необходимости собрать release notes / changelog (L3)

---

## 6) QUALITY (MANDATORY)

### Checklist
- WHY exists for each decision
- No scope leaks (governance не пишет domain-canon напрямую)
- No hidden dependencies (DEPENDS_ON mirrored in XREF)
- Traceability: L2 decision has provenance; replacements logged

### Acceptance
PASS if:
- REG updated correctly for L2/L3
- XREF updated for dependencies/changes/conflicts
- CTL checks do not reject paths/levels

FAIL if:
- any L2/L3 without REG entry
- any dependency without XREF
- any replacement without REPLACED_BY/MOVED_TO/RENAMED_TO

---

## 7) FAILURE MODES

- Hidden dependency discovered → FAIL + require XREF DEPENDS_ON
- Conflicting canon claims → create XREF CONFLICTS_WITH + route to decision approval
- Wrong path/level → CTL rejects; move artifact to correct folder
- No WHY / no approver → cannot be L2

---

## 8) RAW LINK (MANDATORY)

RAW: <raw github link to this template file>

---

## FINAL RULE (LOCK)

> Governance engines enforce system law. Any canon-impacting action must be traceable via REG + XREF + Audit/Decision.

OWNER: Universe Engine  
LOCK: OPEN
