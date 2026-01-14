# KB — CONTRADICTION HANDLING PROTOCOL (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/65__KB_CONTRADICTION_HANDLING_PROTOCOL.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: PROTOCOL
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.PROC.CONTRADICTIONS.065
OWNER: SYSTEM
ROLE: Deterministic protocol for detecting, classifying, and resolving contradictions in KB modules and world knowledge sources, using authority tiers, provenance records, and hard gates that block ACTIVE promotion until resolved.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created contradiction handling protocol: detect→classify→resolve→record→gate."
- REASON: "Contradictions cause incorrect outputs and drift; they must be handled explicitly and auditable."
- IMPACT: "Safer KB evolution, clearer confidence labeling, and reliable ACTIVE promotions."
- CHANGE_ID: UE.CHG.2026-01-14.KB.PROC.065

---

## 0) PURPOSE (KB)
Handle contradictions deterministically:
- detect conflicts
- classify severity
- resolve using authority tiers
- record in provenance and audit trail
- block ACTIVE promotion when unresolved

---

## 1) DEFINITIONS
Contradiction:
- Two claims cannot both be true under the same scope.

Severity:
- CRITICAL: affects governance/law/validation or high-risk outputs
- MAJOR: affects core domain method outputs
- MINOR: affects edge cases or optional heuristics

Resolution types:
- TIER_OVERRIDE: higher-tier wins
- SCOPE_SPLIT: both true in different scopes/contexts
- TEMP_HYPOTHESIS: unresolved, labeled as hypothesis
- DEPRECATE_AND_REPLACE: replace faulty module with corrected one

---

## 2) INPUTS / OUTPUTS
INPUTS:
- Conflicting claims
- Source record UIDs (if external)
- Module UIDs involved

OUTPUTS:
- Contradiction record in provenance block
- Decision (resolution type)
- Update plan (module edit, deprecate, or split)
- Gate result (PASS/REWORK/FAIL for promotion)

---

## 3) DETECT (HOW TO FIND CONTRADICTIONS)
Triggers:
- two KB modules claim different rules for same procedure
- external source update conflicts with existing ACTIVE module
- QA regression indicates inconsistent outcomes
- user reports mismatch

Procedure:
- write both claims side-by-side
- confirm they overlap in scope
- identify which module(s) own the scope

---

## 4) CLASSIFY (SEVERITY)
Classify as CRITICAL if:
- affects governance baseline, indexing rules, deprecation rules, validation gates, or certification

Classify as MAJOR if:
- affects domain core methods (music hook rules, narrative structure rules, etc.)

Classify as MINOR if:
- affects optional heuristics or long-tail edge cases

---

## 5) RESOLVE (DETERMINISTIC)
### 5.1 Use authority tiers (default)
- Prefer higher AUTHORITY_TIER sources.
- Prefer ACTIVE modules over DRAFT.
- Prefer official standards/docs over community.

Decision:
- Choose winning claim OR convert to scope split.

### 5.2 Scope split (if both can be true)
If claims apply to different conditions:
- define explicit conditions
- split into:
  - separate modules OR
  - separate sections with strict condition gates

### 5.3 Unresolved (temporary hypothesis)
If not resolvable:
- label as HYPOTHESIS
- set confidence LOW/MED
- block promotion to ACTIVE for affected module if severity is CRITICAL/MAJOR

### 5.4 Replace
If an ACTIVE module is wrong:
- create corrected module
- deprecate old module (pointer-first)
- update bindings if packs are affected

---

## 6) RECORD (MANDATORY)
### 6.1 Provenance record
In the affected KB module:
- add a contradiction entry (PROVENANCE → Contradictions)
- include source record UIDs

### 6.2 Audit record
Create an audit record:
- EVENT_TYPE: INCIDENT or POLICY_CHANGED or MODULE_UPDATED
- include change id, validation, and remediation plan

### 6.3 Release notes (if wide impact)
If many entities are affected:
- add release notes entry (UID-only references)

---

## 7) GATES (PROMOTION BLOCKS)
ACTIVE promotion is BLOCKED if:
- contradiction severity is CRITICAL or MAJOR and unresolved
- source record provenance missing for the claims
- resolution is “temporary hypothesis” but module is marked ACTIVE

---

## 8) HARD FAIL CONDITIONS
FAIL IF:
- contradictions are ignored or hidden
- module promoted to ACTIVE while carrying unresolved CRITICAL/MAJOR contradictions
- claims are changed without audit trail
- resolution uses low-tier sources when higher-tier exist (without explicit reason)

---

## 9) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.POL.WORLD_SOURCES.030 | WHY: authority tiers for external sources
- XREF: UE.KB.STD.SOURCE_RECORDS.032 | WHY: provenance structure for sources
- XREF: UE.KB.TPL.PROVENANCE_BLOCK.033 | WHY: where contradiction records live
- XREF: UE.KB.POL.AUDIT_TRAIL.058 | WHY: contradictions require audit logging
- XREF: UE.KB.STD.RELEASE_NOTES.060 | WHY: wide-impact contradiction fixes require release notes

--- END.
