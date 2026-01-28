# KB — RELEASE NOTES STANDARD (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/60__KB_RELEASE_NOTES_STANDARD.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: STANDARD
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.STD.RELEASE_NOTES.060
OWNER: SYSTEM
ROLE: Defines how to write KB Release Notes for significant KB updates: what changed, why, impact on entities, migration guidance, and validation summary. Enables communication and auditability of KB evolution.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created KB release notes standard for major KB updates."
- REASON: "As KB grows, changes must be communicated; release notes prevent silent behavior changes across entities."
- IMPACT: "Clear change communication, safer upgrades, and easier debugging."
- CHANGE_ID: UE.CHG.2026-01-14.KB.STD.060

---

## 0) PURPOSE (KB)
KB Release Notes document significant changes:
- new modules/packs
- promotions to ACTIVE
- deprecations and replacements
- taxonomy/map/policy changes
- expected impact on entity outputs

Release Notes do not replace per-file CHANGE_NOTE or audit records.

---

## 1) WHEN RELEASE NOTES ARE REQUIRED
Required when:
- multiple modules changed in a batch
- governance baseline changes
- taxonomy changes (skill tags, relation types)
- master index structure changes
- major competence pack releases
- changes likely affect many entity outputs

Optional when:
- small patch changes only

---

## 2) RELEASE NOTES CONTENT (MUST)
A Release Notes entry must include:
- release identifier (date + version)
- summary (what/why)
- change inventory (added/changed/deprecated)
- impact assessment (who affected)
- migration guidance (what to update)
- validation summary (what checks were run)
- known issues (if any)

---

## 3) TEMPLATE (CANON)
RELEASE_NOTES:
- RELEASE_ID: KB-YYYY-MM-DD-vX.Y.Z
- DATE: YYYY-MM-DD
- SCOPE: <domains impacted>
- SUMMARY:
  - <short>
- ADDED:
  - UID: <uid> | WHAT: <short>
- CHANGED:
  - UID: <uid> | FROM: <v> | TO: <v> | WHAT: <short>
- DEPRECATED:
  - UID: <old uid> | REPLACED_BY: <new uid>
- IMPACT:
  - AFFECTED_ENTITY_CLASSES:
    - SPC / ENG / ORC / CTL / VAL / QA
  - AFFECTED_DOMAINS:
    - <domain list>
  - EXPECTED_BEHAVIOR_CHANGES:
    - <bullet>
- MIGRATION:
  - UPDATE_BINDINGS:
    - <entity uid> replace <old pack uid> -> <new pack uid>
  - UPDATE_SCORECARDS:
    - <what to re-run>
- VALIDATION:
  - CHECKS_RUN:
    - <uid> | RESULT: PASS/REWORK/FAIL
  - OVERALL_RESULT: PASS/REWORK/FAIL
- KNOWN_ISSUES:
  - <bullet>
- NEXT_ACTIONS:
  - <gap fill or recertification actions>

---

## 4) UID-ONLY RULES
- Use UID-only references for modules/packs/entities.
- No RAW links or PATHs in the release notes body.
- Navigation remains in the master index.

---

## 5) HARD FAIL CONDITIONS
FAIL IF:
- release notes omit DEPRECATED replacements
- impact section missing for governance/taxonomy changes
- validation summary missing for major changes
- uses URL/PATH instead of UID-only references

---

## 6) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.POL.AUDIT_TRAIL.058 | WHY: release notes complement audit records
- XREF: UE.KB.TPL.AUDIT_RECORD.059 | WHY: audit record format for individual events
- XREF: UE.KB.POL.STATUS_LOCK.029 | WHY: promotions/depcrecations rely on lifecycle discipline
- XREF: UE.KB.STD.DEPRECATION_POINTER.007 | WHY: deprecation replacements must be tracked

--- END.
