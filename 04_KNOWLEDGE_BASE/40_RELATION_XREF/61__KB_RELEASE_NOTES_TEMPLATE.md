# KB — RELEASE NOTES TEMPLATE (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/61__KB_RELEASE_NOTES_TEMPLATE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: TEMPLATE
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.TPL.RELEASE_NOTES.061
OWNER: SYSTEM
ROLE: Copy-paste template for writing KB Release Notes entries in a consistent, UID-only, auditable format.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created KB release notes template (copy-paste)."
- REASON: "Release notes must be consistent and comparable; template prevents omissions."
- IMPACT: "Faster release communication and safer migrations."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TPL.061

---

## 0) PURPOSE (KB)
Provide a ready-to-use release notes entry template.

---

## 1) RELEASE NOTES (COPY)
RELEASE_NOTES:
- RELEASE_ID: KB-YYYY-MM-DD-vX.Y.Z
- DATE: YYYY-MM-DD
- SCOPE:
  - DOMAINS:
    - <music/narrative/...>
  - ENTITY_CLASSES:
    - SPC / ENG / ORC / CTL / VAL / QA / XREF

SUMMARY:
- WHAT:
  - <short>
- WHY:
  - <short>

INVENTORY:
- ADDED:
  - UID: <uid> | WHAT: <short>
- CHANGED:
  - UID: <uid> | FROM: <v> | TO: <v> | WHAT: <short>
- DEPRECATED:
  - UID: <old uid> | REPLACED_BY: <new uid>

IMPACT:
- EXPECTED_BEHAVIOR_CHANGES:
  - <bullet>
- RISKS:
  - <bullet>
- AFFECTED_BINDINGS:
  - <entity uid> uses <pack uid> (if any)

MIGRATION:
- UPDATE_BINDINGS:
  - <entity uid>: <old uid> -> <new uid>
- RE-RUN_CHECKS:
  - <scorecard uid/ref>
  - <readiness/cert uid/ref>

VALIDATION:
- CHECKS_RUN:
  - <uid> | RESULT: PASS/REWORK/FAIL
- OVERALL_RESULT: PASS/REWORK/FAIL

KNOWN_ISSUES:
- <bullet>

NEXT_ACTIONS:
- ACTION: CREATE/EXTEND/DEPRECATE/RECERTIFY
  - TARGET: <uid or planned>
  - PRIORITY: P1/P2/P3
  - WHY:
  - DONE: YES/NO

---

## 2) RULES (STRICT)
- UID-only references; no URL/PATH.
- If deprecations exist, replacements must be listed.
- Validation must be present for major/gov/taxonomy changes.

---

## 3) HARD FAIL CONDITIONS
FAIL IF:
- release notes omit migration info while deprecations exist
- OVERALL_RESULT missing
- uses URL/PATH instead of UID-only references

---

## 4) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.STD.RELEASE_NOTES.060 | WHY: defines what release notes must contain
- XREF: UE.KB.POL.AUDIT_TRAIL.058 | WHY: release notes complement audit trail
- XREF: UE.KB.TPL.AUDIT_RECORD.059 | WHY: audit record template for individual events

--- END.
