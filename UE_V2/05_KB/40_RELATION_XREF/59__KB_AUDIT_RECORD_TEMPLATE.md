# KB — AUDIT RECORD TEMPLATE (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/59__KB_AUDIT_RECORD_TEMPLATE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: TEMPLATE
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.TPL.AUDIT_RECORD.059
OWNER: SYSTEM
ROLE: Copy-paste template for KB audit trail records: standardized fields, UID-only related references, validation result, and next actions. Used whenever audit trail policy requires an audit record.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created audit record template for KB audit trail."
- REASON: "A consistent audit format makes KB changes traceable and comparable across time."
- IMPACT: "Faster debugging and safer promotions/depcrecations."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TPL.059

---

## 0) PURPOSE (KB)
Provide a canonical audit record format:
- for module changes
- for index/taxonomy updates
- for promotions/deprecations
- for incident regressions

---

## 1) AUDIT RECORD (COPY)
AUDIT_RECORD:
- RECORD_UID: <unique id>
- DATE: YYYY-MM-DD
- EVENT_TYPE: MODULE_CREATED | MODULE_UPDATED | MODULE_PROMOTED | MODULE_DEPRECATED | MODULE_REPLACED | INDEX_UPDATED | TAXONOMY_UPDATED | POLICY_CHANGED | CERTIFICATION_ISSUED | INCIDENT
- TARGET_UID: <uid>
- TARGET_FILE: <path label>
- VERSION_BEFORE: <x.y.z or NONE>
- VERSION_AFTER: <x.y.z>
- CHANGE_ID: <from CHANGE_NOTE>

SUMMARY:
- <1–2 lines>

REASON:
- <why change was needed>

IMPACT:
- <what changes operationally>

RELATED_UIDS (UID-ONLY):
- <uid> | WHY: <short>
- <uid> | WHY: <short>

VALIDATION:
- CHECKS_RUN:
  - <checklist/gate uid> | RESULT: PASS/REWORK/FAIL
- OVERALL_RESULT: PASS/REWORK/FAIL
- NOTES:

BLOCKERS (IF NOT PASS):
- B1:
- B2:

NEXT_ACTIONS:
- ACTION: CREATE/EXTEND/DEPRECATE/REGISTER/RECERTIFY
  - TARGET: <uid or planned name>
  - PRIORITY: P1/P2/P3
  - WHY:
  - DONE: YES/NO

---

## 2) RULES (STRICT)
- Use UID-only in RELATED_UIDS (no URL/PATH).
- VALIDATION must be explicit; “looks ok” is not valid.
- If event is PROMOTED/DEPRECATED/INDEX_UPDATED/TAXONOMY_UPDATED:
  - VALIDATION is mandatory (at least one gate/checklist).

---

## 3) HARD FAIL CONDITIONS
FAIL IF:
- record missing CHANGE_ID for events that involve module edits
- related references include URL/PATH
- OVERALL_RESULT missing
- promotion/deprecation recorded without validation

---

## 4) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.POL.AUDIT_TRAIL.058 | WHY: audit trail policy requires audit records
- XREF: UE.KB.POL.GAP_PRIORITY.042 | WHY: next actions should be prioritized consistently

--- END.
