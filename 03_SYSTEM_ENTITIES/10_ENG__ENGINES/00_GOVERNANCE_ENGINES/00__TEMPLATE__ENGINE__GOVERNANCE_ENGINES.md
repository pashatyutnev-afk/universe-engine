# ENG ENGINE TEMPLATE — GOVERNANCE_ENGINES (FAMILY OVERLAY v2)
FILE: 00__TEMPLATE__ENGINE__GOVERNANCE_ENGINES.md

SCOPE: Universe Engine
LAYER: ENG
DOC_TYPE: TEMPLATE
ENTITY_GROUP: ENGINES (ENG)
TEMPLATE_KIND: ENGINE_FAMILY_OVERLAY
LEVEL: L1
STATUS: ACTIVE
VERSION: 2.0
ROLE: Governance family overlay. Must be compatible with ENG ENGINE TEMPLATE (BASE v2). Adds governance record schemas, approvals, and allows SYSTEM scope outputs by design.

LOCK: FIXED
OWNER: Universe Engine

---

## 0) ENGINE IDENTITY (MANDATORY)

ENGINE_NAME: <UPPER_SNAKE_CASE>
ENGINE_ID: ENG.GOV.<NN>.<ENGINE_NAME>

FAMILY_CODE: GOV
ENGINE_NN_IN_FAMILY: <01..10>
ENGINE_CLASS: GOVERNANCE
ENGINE_LEVEL: L1

ROLE_IN_FAMILY: <FOUNDATION|BUILDER|VALIDATOR|OUTPUT>
PIPELINE_STAGE: <DEFINE|PACKAGE|CHECK|PRODUCE>

CANON_COMPAT:
- INDEX: 02__INDEX_ALL_ENGINES.md
- NAMING_RULE: file name NN must match ENGINE_NN_IN_FAMILY

---

## 1) PURPOSE (WHAT THIS ENGINE DOES)

One paragraph:
- what governance artifact it governs (audit/authority/rules/change/consistency/deps/decision/impact/risk/memory)
- what records it produces
- what systems consume it (ENG families + ORC/CTL/VAL/QA layers)

---

## 2) OWNERSHIP BOUNDARIES (ANTI-DUPLICATION)

### 2.1 OWNS
- governance records and policies of its domain

### 2.2 DOES NOT OWN (hard)
- domain canon content (world/character/narrative facts)
- production media assets
- deep music creation
Rule:
> Governance does not create content; it manages legality, consistency, and changes.

---

## 3) TRIGGERS (WHEN TO RUN)

TRIGGERS:
- new canon change proposed
- conflict detected by Consistency Engine
- new dependency introduced
- new engine/template introduced
- risk/scope review required
- version snapshot required

---

## 4) MINI-CONTRACT (MANDATORY)

CONSUMES: (1–5)
- CHANGE_PROPOSAL (CP) (if applicable)
- CANON_TARGETS (files/engines affected)
- DEPENDENCY_SNAPSHOT (if applicable)
- CONSISTENCY_REPORT (if applicable)
- PROJECT_OUTPUT_SIGNALS (optional)

PRODUCES: (1–5)
- AUDIT_ENTRY
- APPROVAL_DECISION
- POLICY_UPDATE
- DEPENDENCY_REGISTRY_UPDATE
- VERSION_SNAPSHOT

DEPENDS_ON:
- [] (or list engine IDs; always mirrored to XREF__DEPENDENCIES)

OUTPUT_TARGET:
- SYSTEM (allowed): `03_SYSTEM_ENTITIES/` and/or `00_REG__REGISTRIES/` and/or `90_XREF__CROSSREF/`
- PROJECT (optional): `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/99_META/<LEVEL_FOLDER>/`

Rule:
> Governance engines may use SYSTEM scope by design.

---

## 5) PARAMETERS (MANDATORY)

SCOPE_MODE: <SYSTEM|PROJECT>
PROJECT_ID: <optional if PROJECT mode>
OUTPUT_LEVEL (if PROJECT): <L0|L1|L2|L3>

GOV_RECORD_TYPE:
- <AUDIT|AUTHORITY|RULE_HIERARCHY|CHANGE_CONTROL|CONSISTENCY|DEPENDENCY_REGISTRY|DECISION|SCOPE_IMPACT|RISK_SAFETY|VERSIONING_MEMORY>

---

## 6) SYSTEM INTERFACE (MANDATORY) — ORC/CTL/VAL/QA/REG/XREF

### 6.1 ORCHESTRATION / CONTROL / VALIDATION

ORCHESTRATED_BY (ORC):
- [] (or explicit ORC IDs if you have them)

CONTROLLED_BY (CTL):
- [] (or explicit CTL IDs)

VALIDATED_BY (VAL):
- [] (or explicit VAL IDs)

QA_BY (QA):
- [] (or explicit QA IDs)

Rule:
> For governance outputs, validation may be internal to governance (Decision Approval + Consistency). If external validators exist — list them.

---

### 6.2 REGISTRY UPDATES (MANDATORY)

REGISTRY_UPDATES:
- REQUIRED: YES
- TARGETS (system):
  - `00_REG__REGISTRIES/REG.SYS.AUDIT_LOG.md` (for AUDIT_ENTRY)
  - `00_REG__REGISTRIES/REG.SYS.DECISIONS.md` (for APPROVAL_DECISION)
  - `00_REG__REGISTRIES/REG.SYS.DEPENDENCIES.md` (for dependency registry)
  - `00_REG__REGISTRIES/REG.SYS.VERSIONING_MEMORY.md` (for snapshots)
  - `00_REG__REGISTRIES/REG.SYS.CHANGE_CONTROL.md` (for CP lifecycle)

---

### 6.3 XREF UPDATES (MANDATORY)

XREF_UPDATES:
- REQUIRED: YES
- RECORD_TYPES:
  - CANON_REF
  - DEPENDS_ON
  - DERIVED_FROM
  - PRODUCED_BY
  - REPLACES
  - BREAKS
  - CONFLICTS_WITH
- TARGETS (system):
  - `90_XREF__CROSSREF/XREF__CHANGES.md`
  - `90_XREF__CROSSREF/XREF__DEPENDENCIES.md`
  - `90_XREF__CROSSREF/XREF__PROVENANCE.md`
  - `90_XREF__CROSSREF/XREF__CANON_REFS.md` (if used)

Rule:
> Any governance decision impacting canon must be recorded in XREF__CHANGES + Audit Log.

---

## 7) GOVERNANCE RECORD SCHEMAS (MANDATORY)

### 7.1 CHANGE PROPOSAL (CP) — if applicable

CP_ID: <unique>
TARGET_SCOPE: <ENG_TEMPLATES|ENG_FAMILY_RULES|REGISTRY|XREF|PROJECT_PIPELINE|SYSTEM_POLICY>
PROBLEM: ...
EVIDENCE: [ ... ]
PROPOSED_CHANGE: ...
IMPACT:
  AFFECTED_FILES: [ ... ]
  BREAKING: true|false
MIGRATION_PLAN:
  STEPS: [ ... ]
  ROLLBACK: [ ... ]
RISK: [ ... ]
REQUIRED_APPROVALS:
  - ENG.GOV.04.CHANGE_CONTROL
  - ENG.GOV.02.CANON_AUTHORITY
STATUS: <DRAFT|PROPOSED|APPROVED|REJECTED>

---

### 7.2 AUDIT ENTRY (always when canon/system changes)

AUDIT_ID: <unique>
TIMESTAMP: <ISO>
ACTOR: <user/system>
ACTION: <created|modified|approved|rejected|migrated>
TARGETS: [<file refs>]
SUMMARY: <short>
LINKS:
  - CP_ID: <optional>
  - DECISION_ID: <optional>

---

### 7.3 DECISION / APPROVAL RECORD

DECISION_ID: <unique>
SCOPE: <SYSTEM|PROJECT>
DECISION_TYPE: <APPROVE|REJECT|DEFER>
RATIONALE: ...
CONDITIONS: [ ... ]  # required changes before approval
AFFECTED_TARGETS: [ ... ]
SIGNED_BY: <authority>
TIMESTAMP: <ISO>

---

### 7.4 DEPENDENCY REGISTRY ENTRY

DEP_ID: <unique>
SUBJECT: <engine/file>
DEPENDS_ON: [ ... ]
REASON: ...
CYCLE: <true|false>
NOTES: ...

---

### 7.5 VERSIONING / MEMORY SNAPSHOT

SNAPSHOT_ID: <unique>
SCOPE: <SYSTEM|PROJECT>
INCLUDES: [ ... ]  # files/registries/xref
CHANGESET: [ ... ] # references to CP/decisions
TIMESTAMP: <ISO>
NOTES: ...

Rule:
> Governance records must be structured (not essays) and must reference affected targets.

---

## 8) PROCESS (HOW TO EXECUTE)

STEPS:
1) Receive CP or trigger signal.
2) Validate completeness (impact + migration + approvals list).
3) Run consistency/risk/scope checks as needed.
4) Produce decision record (approve/reject/defer).
5) Write audit entry.
6) Update registries + xref.
7) If approved, route implementation to correct layer (ENG family / ORC/CTL/VAL/QA).

---

## 9) QUALITY GATES (MANDATORY)

PASS if:
- CP complete (impact + migration + approvals)
- decision recorded + audit logged
- registries updated
- xref updated (changes/deps/provenance)
- no hidden dependencies

FAIL if:
- canon changed without governance decision
- missing audit entry
- missing xref/registry updates

---

## 10) RAW LINK (MANDATORY)

RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/00__TEMPLATE__ENGINE__GOVERNANCE_ENGINES.md

---

## FINAL RULE (LOCK)

> Governance engines are allowed to write SYSTEM-level artifacts. They must log every canon/system-impacting change.

LOCK: FIXED
