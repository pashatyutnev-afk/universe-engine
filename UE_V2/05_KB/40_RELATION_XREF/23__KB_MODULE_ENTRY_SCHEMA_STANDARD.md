# KB — KB MODULE ENTRY SCHEMA STANDARD (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/23__KB_MODULE_ENTRY_SCHEMA_STANDARD.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: STANDARD
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.STD.MODULE_SCHEMA.023
OWNER: SYSTEM
ROLE: Defines the canonical schema for any KB module document (non-index): header fields, required sections, compliance blocks, and hard-fail conditions. Ensures all KB modules are machine-readable, auditable, and compatible with entity usage.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Defined canonical schema for KB module entries (non-index)."
- REASON: "Without a strict schema, KB becomes inconsistent and entities cannot reliably apply knowledge."
- IMPACT: "All KB modules become interoperable; traceability improves; drift reduces."
- CHANGE_ID: UE.CHG.2026-01-14.KB.STD.023

---

## 0) PURPOSE (KB)
This standard defines how any KB module must be written so that:
- entities can load it deterministically
- scope & intent are explicit
- rules are enforceable via fail conditions
- relations are UID-only

This standard does NOT define the master index format (separate).

---

## 1) CANONICAL HEADER (REQUIRED)
Every KB module MUST start with a full header block.

### 1.1 Mandatory header keys
- TITLE line: `# KB — <TITLE> (CANON)`
- FILE: <path>
- SCOPE: Universe Engine
- LAYER: 04_KNOWLEDGE_BASE
- DOC_TYPE: KB_MODULE
- KB_TYPE: one of: STANDARD | PROTOCOL | MAP | DICT | PLAYBOOK | CHECKLIST | EXAMPLE | TEMPLATE
- LEVEL: L2 (default) or explicit if different
- STATUS: DRAFT | ACTIVE | DEPRECATED
- LOCK: FIXED | OPEN
- VERSION: x.y.z
- UID: <system uid>
- OWNER: SYSTEM
- ROLE: 1–2 lines describing why it exists

### 1.2 Change note (mandatory)
CHANGE_NOTE must include:
- DATE
- TYPE (MAJOR/MINOR/PATCH)
- SUMMARY
- REASON
- IMPACT
- CHANGE_ID

---

## 2) REQUIRED SECTIONS (MINIMUM SET)
A KB module MUST include (as applicable):

### 2.1 PURPOSE
- `## 0) PURPOSE (KB)` — single paragraph: what problem it solves.

### 2.2 DEFINITIONS (if any terms are used)
- `## 1) DEFINITIONS` — strict terms.

### 2.3 RULES / PROCEDURE / CONTENT BODY
Choose one primary body form:
A) STANDARD: rules + boundaries  
B) PROTOCOL: step-by-step procedure + checks  
C) MAP: table/matrix + selection logic + fail conditions  
D) DICT: enumerations + meaning + usage notes  
E) PLAYBOOK: decision flow + fallback branches (no “fantasy”)
F) CHECKLIST: check items + pass/fail criteria
G) EXAMPLE: good/bad exemplars + why
H) TEMPLATE: fillable spec with required fields

### 2.4 HARD FAIL CONDITIONS (mandatory)
- `## X) HARD FAIL CONDITIONS`
Must list explicit FAIL triggers that stop a run or invalidate usage.

### 2.5 RELATED (UID-ONLY) (mandatory)
- `## Y) RELATED (UID-ONLY)`
Format:
`XREF: <UID> | WHY: <reason>`
Rule:
- NEVER put PATH or RAW URLs here (UID-only references).

---

## 3) CONTENT RULES (MANDATORY)
### 3.1 No fantasy / no invention
A KB module must not instruct “assume”, “invent”, “roleplay”.
If uncertainty exists:
- mandate opening sources (RAW) or declare gap and stop.

### 3.2 Determinism
Rules must be written so that two runs produce the same decision:
- prefer enumerated steps
- prefer explicit thresholds/criteria
- avoid “do it nicely” without measurable checks

### 3.3 Scope purity
Module must stay within its KB_SCOPE boundary.
If it crosses domains:
- move content to correct scope, and keep only a pointer rule (UID-only) here.

### 3.4 Compatibility
Use consistent headings:
- numbered section headers `## 0)`, `## 1)` etc.
- tables are allowed but must include definitions for columns

---

## 4) UID-ONLY RELATION POLICY (MANDATORY)
Within KB modules:
- reference other KB modules by UID only (XREF section)
- do not embed RAW links except in master index documents
- do not use PATH as a navigation mechanism

---

## 5) MINIMUM QUALITY GATE (KB)
A module is READY only if:
- all mandatory header keys exist
- it contains HARD FAIL CONDITIONS
- it contains RELATED (UID-ONLY)
- it does not break scope boundaries
- it contains no RAW links (unless it is the master index)

---

## 6) HARD FAIL CONDITIONS
FAIL IF:
- any mandatory header key is missing
- CHANGE_NOTE is missing required fields
- HARD FAIL CONDITIONS section is missing
- RELATED (UID-ONLY) section is missing
- module contains RAW links (unless explicitly a master index)
- module instructs invention/roleplay or lacks determinism

---

## 7) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.STD.MASTER_INDEX_REG.008 | WHY: index is the only place where RAW links may appear
- XREF: UE.KB.DICT.XREF_RULES.005 | WHY: uid-only crossref rules for KB
- XREF: UE.KB.STD.SCOPE_BOUNDARY_TABLE.022 | WHY: scope boundary quick check for correct placement
- XREF: UE.KB.STD.SCOPE.GOVERNANCE.021 | WHY: governance scope constraints for determinism
- XREF: UE.KB.TOPIC.META.USAGE.001 | WHY: no-fantasy + traceability usage protocol

--- END.
