# XREF RECORD — TEMPLATE (CANON)

FILE: 03_SYSTEM_ENTITIES/90_XREF__CROSSREF/00__TEMPLATE__XREF_RECORD.md
SCOPE: Universe Engine (Games volume) / System Entities / Crossref (XREF)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: TEMPLATE
TEMPLATE_TYPE: XREF_RECORD
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.TPL.XREF.RECORD.001
OWNER: SYSTEM
ROLE: Canonical template for any XREF mapping record (single mapping / replacement / deprecation / exception).

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: MINOR
- SUMMARY: "Normalized XREF record template: mapping schema, deprecation/replacement fields, RAW-only interfaces."
- REASON: "Prevent implicit links and untracked routing changes."
- IMPACT: "Mappings become explicit and reviewable."
- CHANGE_ID: UE.CHG.2026-01-20.TPL.XREF.RECORD.001

---

## 0) RECORD HEADER (REQUIRED)
RECORD_NAME:
RECORD_UID:
STATUS: ACTIVE | DEPRECATED
LOCK: FIXED
VERSION:
OWNER:
SCOPE:

---

## 1) PURPOSE
- why this mapping exists
- what routing problem it solves

---

## 2) MAPPING (MANDATORY)
FROM:
- ENTITY_TYPE: <ENG|ORC|SPC|CTL|VAL|QA|XREF>
- UID_OR_PATH:
- RAW: <optional>

TO:
- ENTITY_TYPE:
- UID_OR_PATH:
- RAW: <optional>

APPLIES_WHEN:
- <conditions or task types>

OUTPUT_EFFECT:
- <what this enables/changes>

---

## 3) DEPRECATION (OPTIONAL, STRICT)
If STATUS = DEPRECATED:
REPLACED_BY:
- UID:
- RAW:

REASON:
- <why deprecated>

EFFECTIVE_DATE:
- <YYYY-MM-DD>

---

## 4) VALIDATION (MANDATORY)
- mapping must be resolvable with RAW-only links
- if mapping changes canon routing → must be mirrored in maps/matrix (or explicitly scoped)

---

## 5) KNOWLEDGE BASE (KB) SCOPE
KB INPUTS:
- examples of mapping patterns

KB OUTPUTS:
- none

BOUNDARIES:
- record does not implement logic; it documents routing links only.

---

## 6) INTERFACES (RAW ONLY)
- XREF INDEX (SoT):
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/00__INDEX__CROSSREF.md
- XREF REALM README:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/00__README__CROSSREF.md
- XREF STANDARD:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/04__REL_POLICY_XREF_STANDARD.md

--- END.
