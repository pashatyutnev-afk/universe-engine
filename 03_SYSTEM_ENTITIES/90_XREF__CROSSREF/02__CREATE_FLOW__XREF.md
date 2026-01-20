# XREF CREATE FLOW — CANON

FILE: 03_SYSTEM_ENTITIES/90_XREF__CROSSREF/02__CREATE_FLOW__XREF.md
SCOPE: Universe Engine (Games volume) / System Entities / Crossref (XREF)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: WORKFLOW
ENTITY_GROUP: CROSSREF (XREF)
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.XREF.CREATE_FLOW.001
OWNER: SYSTEM
ROLE: Canonical creation workflow for XREF maps/records: template → UID → file → SoT registration → gate checks.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: MINOR
- SUMMARY: "Created XREF create flow to enforce registry-first mapping discipline."
- REASON: "Avoid non-registered maps and implicit routing."
- IMPACT: "New maps become deterministic and auditable."
- CHANGE_ID: UE.CHG.2026-01-20.XREF.CREATEFLOW.001

---

## 0) CORE LAW
XREF map/record exists in canon only if registered in XREF INDEX (SoT).

---

## 1) STEPS (CANON ORDER)
1) Select artifact type:
- MAP / MATRIX / PIPELINE_MAP / RECORD

2) Assign UID:
- use UID rules

3) Create file from template:
- MAP/INDEX: use `00__TEMPLATE__XREF_INDEX.md` when creating an index
- RECORD: use `00__TEMPLATE__XREF_RECORD.md`

4) Fill mandatory sections:
- scope, applies_when, mapping, validation

5) Register in XREF INDEX (SoT):
- add RAW link entry
- ensure minimal map set coverage stays complete

6) Gate check:
- RAW-only links
- role boundaries respected
- resolvable mapping

---

## 2) STOP CONDITIONS (ONLY THESE)
- RAW missing (no template/index link)
- marker not confirmed (gate fail)
- input absent (no mapping target)

---

## 3) INTERFACES (RAW ONLY)
- XREF INDEX (SoT):
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/00__INDEX__CROSSREF.md
- XREF TEMPLATE (INDEX):
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/00__TEMPLATE__XREF_INDEX.md
- XREF TEMPLATE (RECORD):
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/00__TEMPLATE__XREF_RECORD.md

--- END.
