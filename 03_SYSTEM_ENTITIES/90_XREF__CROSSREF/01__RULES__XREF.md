# CROSSREF (XREF) — RULESET (LAW) (CANON)

FILE: 03_SYSTEM_ENTITIES/90_XREF__CROSSREF/01__RULES__XREF.md
SCOPE: Universe Engine (Games volume) / System Entities / Crossref (XREF)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: RULESET
ENTITY_GROUP: CROSSREF (XREF)
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.XREF.RULES.001
OWNER: SYSTEM
ROLE: Hard rules for XREF: existence registry, minimal map set, RAW-only navigation, and anti-contamination.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: MINOR
- SUMMARY: "Created XREF ruleset to enforce registry-first mapping and prevent implicit routing."
- REASON: "XREF maps existed but lacked a single enforceable ruleset."
- IMPACT: "Routing becomes auditable and deterministic."
- CHANGE_ID: UE.CHG.2026-01-20.XREF.RULES.001

---

## R1 — SoT existence (ABSOLUTE)
Any XREF map/record is canon only if registered in:
- `00__INDEX__CROSSREF.md`

## R2 — RAW-only navigation (ABSOLUTE)
All links in XREF maps/index/records must be RAW-only.

## R3 — Minimal map set (ABSOLUTE)
Canon must include:
- ENG→ORC map
- ORC→SPC map
- Validation matrix
- Pipeline map

Missing any item = routing incomplete (S0 for routing tasks).

## R4 — No hidden routing
If a pipeline uses an engine/specialist/validator chain, it must be discoverable in XREF maps/matrix.

## R5 — Role boundaries (S0)
XREF must not:
- decide pipeline order (ORC)
- implement methods (ENG)
- set policies/limits (CTL)
- validate canon (VAL)
- score quality (QA)
- package deliverables (SPC)

## R6 — Deprecation requires replacement
If a map is deprecated, it must point to a replacement by RAW link.

---

## INTERFACES (RAW ONLY)
- XREF INDEX (SoT):
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/00__INDEX__CROSSREF.md
- XREF REALM README:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/00__README__CROSSREF.md

--- END.
