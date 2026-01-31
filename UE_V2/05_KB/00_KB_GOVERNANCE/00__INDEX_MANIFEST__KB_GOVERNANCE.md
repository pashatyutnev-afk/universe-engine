# KB — GLOBAL REGISTRY (TERMS & OBJECTS) (CANON)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/02__INDEX__KB_GLOBAL_REGISTRY.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 00_KB_GOVERNANCE
DOC_TYPE: INDEX
INDEX_TYPE: GLOBAL_REGISTRY
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.IDX.GLOBAL_REGISTRY.002
OWNER: SYSTEM
ROLE: Global registry of KB object definitions and shared enums used across the Knowledge Base (terms, object kinds, record kinds). Orientation/definitions only (NOT navigation authority).

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created KB global registry: canonical definitions for KB object kinds (modules, packs, records) and shared enums used across governance, topics, and workflows."
- REASON: "Entities need a shared vocabulary; without a registry, KB objects drift and templates become incompatible."
- IMPACT: "Consistent semantics for KB artifacts; easier validation and certification."
- CHANGE_ID: UE.CHG.2026-01-14.KB.GOV.IDX.002

---

## 0) PURPOSE (LAW)
This document defines the shared vocabulary of the Knowledge Base:
- what object kinds exist (conceptually)
- what records exist (audit/cert/score/example)
- shared enums used by governance workflows

This file is definitions-only.

---

## 1) WHAT THIS INDEX IS / IS NOT
### IS
- A registry of terms and object-kind definitions used across KB modules and workflows.

### IS NOT
- NOT a navigation authority (no RAW map, no existence registry).
- NOT a replacement for the KB master index.
- NOT a duplicate of entity-type index (that lives in KB_ENTITY_TYPES).

Rule:
- Navigation/existence authority remains ONLY the KB master index.

---

## 2) CORE KB OBJECT KINDS (CANON)
Below are the canonical object kinds used in KB content and governance.

### 2.1 KB_MODULE
Definition:
- A single atomic KB knowledge unit stored as a file.
- Examples: POLICY, STANDARD, RULE, MAP, CHECKLIST, TEMPLATE, PLAYBOOK, PROTOCOL, TOPIC, README.

Properties (minimum):
- has UID
- has DOC_TYPE + KB_TYPE (or equivalent typing)
- has scope boundary (what it covers / excludes)
- can be referenced by UID-only XREF

### 2.2 COMPETENCE_PACK
Definition:
- A KB module (or structured set) that teaches operational competence for a role/domain.
- Contains: capabilities, templates, gates, failure modes, (optional) drills.

Notes:
- Packs are bindable to entities (entity competence bindings).

### 2.3 GATE (QUALITY GATE)
Definition:
- A measurable pass/rework/fail check.
- Exists as:
  - a full gate definition module, OR
  - a compact gate card embedded in packs (derived from canon).

### 2.4 EXAMPLE (EXEMPLAR)
Definition:
- A labeled exemplar (GOOD/BAD/BORDERLINE) tied to gates/standards and skill tags.

### 2.5 SOURCE_RECORD (PROVENANCE)
Definition:
- A record describing an external information source used to build KB knowledge (authority tier, date accessed, scope, extraction notes).
- Used to prevent invented sources and enable refresh discipline.

### 2.6 SCORECARD (COVERAGE EVIDENCE)
Definition:
- A structured record showing skill-tag coverage (COVERED/MISSING + strength levels).
- Used to validate pack slots and entity readiness/certification.

### 2.7 CERT_RECORD (CERTIFICATION EVIDENCE)
Definition:
- A structured record of readiness/certification outcomes (PASS/REWORK/FAIL) with evidence references.

### 2.8 AUDIT_RECORD (CHANGE TRACE)
Definition:
- A structured record of changes and validation performed for high-impact updates.

### 2.9 POINTER / ALIAS (NON-AUTHORITY OBJECT)
Definition:
- A file that exists only to point to a canonical target (no new rules).
- Used to preserve old entrypoints or numbering convenience.

---

## 3) SHARED ENUMS (CANON)
These enums are shared across KB modules and governance procedures.

### 3.1 LIFECYCLE_STATUS (for KB modules)
- DRAFT
- ACTIVE
- DEPRECATED

Rules:
- ACTIVE is preferred authority.
- DEPRECATED is pointer-only authority (replacement is the canon).

### 3.2 LOCK_STATE
- FIXED (content meaning should not drift without change control)

### 3.3 RESULT_ENUM (gates/checklists/certification)
- PASS
- REWORK
- FAIL

### 3.4 LABEL_ENUM (examples)
- GOOD
- BAD
- BORDERLINE

### 3.5 PRIORITY_ENUM (gap/remediation)
- P1 (critical)
- P2 (important)
- P3 (nice-to-have)

### 3.6 STATUS_USED (run trace)
- ACTIVE_ONLY
- MIXED

### 3.7 MEMORY_REUSE_FLAG (run trace)
- YES
- NO

### 3.8 WEB_LOOKUP_FLAG (run trace)
- YES
- NO

---

## 4) GLOBAL “RECORD” SHAPES (ABSTRACT)
This section defines abstract shapes to keep records consistent.
Concrete templates live elsewhere.

### 4.1 RECORD_SHAPE.AUDIT
Minimum fields:
- RECORD_UID, DATE, EVENT_TYPE, TARGET_UID, VERSION_BEFORE/AFTER, CHANGE_ID, SUMMARY, VALIDATION, NEXT_ACTIONS

### 4.2 RECORD_SHAPE.CERT
Minimum fields:
- RECORD_UID, DATE, ENTITY_UID, CERT_TYPE, RESULT, SLOT_RESULTS, COVERAGE, PACKS_VALIDATED, SAMPLE_RUN_PROOF

### 4.3 RECORD_SHAPE.SCORECARD
Minimum fields:
- SCORECARD_UID, DOMAIN, TAGS, COVERED/MISSING, STRENGTH_LEVELS, COVERAGE_PERCENT

### 4.4 RECORD_SHAPE.SOURCE_RECORD
Minimum fields:
- SOURCE_UID, SOURCE_TYPE, AUTHORITY_TIER, DATE_ACCESSED, SCOPE, EXTRACTION_NOTES, REFRESH_INTERVAL

---

## 5) GLOBAL CONSTRAINTS (SUMMARY)
- No navigation authority outside KB master index.
- UID-only XREF for operational references.
- No invented facts/sources; provenance required when derived from external sources.
- Trace is mandatory for KB-driven runs.

---

## 6) HARD FAIL CONDITIONS
FAIL IF:
- this registry is used as a navigation map (adds RAW registry)
- duplicate object kinds are introduced with overlapping meaning
- enums are changed ad-hoc without governance change discipline
- registry contradicts governance RULES KB

---

## 7) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.RULES.GOV.001 | WHY: governance rules for KB usage
- XREF: UE.KB.IDX.MASTER.000 | WHY: master index is sole navigation/existence authority
- XREF: UE.KB.STD.SOURCE_RECORDS.032 | WHY: concrete provenance/source record standard
- XREF: UE.KB.STD.RUN_TRACE_MIN.067 | WHY: concrete run trace standard
- XREF: UE.KB.STD.GATE_DEF.088 | WHY: canonical gate definition standard
- XREF: UE.KB.POL.AUDIT_TRAIL.058 | WHY: audit requirements

--- END.
