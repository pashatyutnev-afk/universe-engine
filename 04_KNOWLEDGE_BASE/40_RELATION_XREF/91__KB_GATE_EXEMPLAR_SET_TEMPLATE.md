# KB — GATE EXEMPLAR SET TEMPLATE (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/91__KB_GATE_EXEMPLAR_SET_TEMPLATE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: TEMPLATE
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.TPL.GATE_EXEMPLAR_SET.091
OWNER: SYSTEM
ROLE: Copy-paste template for defining a GATE exemplar set (GOOD/BAD/BORDERLINE) linked by UID-only references. Used to calibrate QA application of a specific gate.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created gate exemplar set template for consistent QA calibration records."
- REASON: "Gates need calibrated exemplar sets; a template prevents inconsistent formats and missing fields."
- IMPACT: "Faster gate calibration and more consistent QA judgments."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TPL.091

---

## 0) PURPOSE (KB)
Provide a standard format to bind examples to a specific gate.

---

## 1) EXEMPLAR SET (COPY)
GATE_EXEMPLAR_SET:
- SET_UID: GX-YYYYMMDD-001
- DATE: YYYY-MM-DD
- GATE_UID: <uid>
- DOMAIN: <domain>
- SKILL_TAGS:
  - <tag>

EXEMPLARS:
- GOOD:
  - <example uid>
  - <example uid>
- BAD:
  - <example uid>
  - <example uid>
- BORDERLINE:
  - <example uid>

CALIBRATION_STATUS:
- STATUS: DRAFT | ACTIVE_READY
- LAST_CALIBRATION_RESULT: PASS/REWORK/FAIL
- NOTES:

VALIDATION:
- CURATION_CHECK: UE.KB.CHK.EXAMPLE_CURATE.083 | RESULT: PASS/REWORK/FAIL
- GATE_LINK_RULE: UE.KB.RULE.EXAMPLE_GATE_LINK.084 | RESULT: PASS/REWORK/FAIL

RELATED_UIDS (UID-ONLY):
- <uid> | WHY: <policy/standard reference>

---

## 2) RULES (STRICT)
- Each example listed must link back to the gate UID in its own RELATED_UIDS.
- Use canonical tags.
- Keep at least 2 GOOD and 2 BAD for key gates (policy-defined).
- Update status after calibration protocol run.

---

## 3) HARD FAIL CONDITIONS
FAIL IF:
- gate UID missing
- exemplar list contains examples without gate linkage
- uses URL/PATH instead of UID-only references
- status marked ACTIVE_READY while validation fails

---

## 4) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.RULE.GATE_EXAMPLE_BIND.090 | WHY: binding rule defines minimum exemplar set requirements
- XREF: UE.KB.PROC.DOMAIN_QA_CALIB.087 | WHY: calibration protocol validates exemplar labels vs gate criteria
- XREF: UE.KB.POL.EXAMPLE_LIBRARY.081 | WHY: example library policy baseline

--- END.
