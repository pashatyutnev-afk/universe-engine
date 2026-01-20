# XREF INDEX — TEMPLATE (CANON)

FILE: 03_SYSTEM_ENTITIES/90_XREF__CROSSREF/00__TEMPLATE__XREF_INDEX.md
SCOPE: Universe Engine (Games volume) / System Entities / Crossref (XREF)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: TEMPLATE
TEMPLATE_TYPE: XREF_INDEX
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.TPL.XREF.INDEX.001
OWNER: SYSTEM
ROLE: Canonical template for any XREF index file (SoT list of maps/records with RAW-only links).

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: MINOR
- SUMMARY: "Normalized XREF index template: SoT rules, required fields, RAW-only interfaces, and registration checklist."
- REASON: "Prevent broken navigation and non-registered mapping files."
- IMPACT: "Any XREF index becomes stable and auditable."
- CHANGE_ID: UE.CHG.2026-01-20.TPL.XREF.INDEX.001

---

## 0) PURPOSE
XREF index file is a SoT list of:
- maps (layer-to-layer)
- matrices (validation placement)
- pipeline maps
- records (optional: exceptions, deprecations, replacements)

---

## 1) REQUIRED STRUCTURE (ORDER LOCK)
1) PURPOSE (SoT)
2) EXISTENCE RULE
3) INDEX CONTENT (lists)
4) CHANGE NOTE
5) INTERFACES (RAW ONLY)

---

## 2) INDEX CONTENT FORMAT (MANDATORY)
MAPS:
- MAP_01:
  - NAME:
  - UID:
  - STATUS:
  - SCOPE:
  - RAW:
- MAP_02:
  - ...

MATRICES:
- MATRIX_01:
  - NAME:
  - UID:
  - RAW:

PIPELINES:
- PIPELINE_MAP_01:
  - NAME:
  - UID:
  - RAW:

RECORDS (optional):
- REC_01:
  - NAME:
  - UID:
  - RAW:

---

## 3) EXISTENCE CHECKLIST (MANDATORY)
- Each listed item must exist by RAW link
- Each listed item must have UID and DOC CONTROL header
- If item is deprecated: must point to replacement (RAW) in record

---

## 4) KNOWLEDGE BASE (KB) SCOPE
KB INPUTS:
- patterns for maps/matrices

KB OUTPUTS:
- none

BOUNDARIES:
- template does not define pipeline logic; only mapping documentation.

---

## 5) INTERFACES (RAW ONLY)
- XREF REALM README:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/00__README__CROSSREF.md
- XREF STANDARD:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/04__REL_POLICY_XREF_STANDARD.md
- DOC CONTROL STANDARD:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md

--- END.
