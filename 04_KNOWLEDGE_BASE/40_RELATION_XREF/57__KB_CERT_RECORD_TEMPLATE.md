# KB — ENTITY CERTIFICATION RECORD (TEMPLATE) (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/57__KB_CERT_RECORD_TEMPLATE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: TEMPLATE
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.TPL.ENTITY_CERT_RECORD.057
OWNER: SYSTEM
ROLE: Standard template for recording entity readiness/certification outcomes (PASS/REWORK/FAIL) with evidence references: slots, scorecards, pack QA, and sample run trace.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created universal entity certification record template."
- REASON: "Certification must be auditable and comparable across entities; a shared record format enables tracking."
- IMPACT: "Entities can be certified consistently; blockers and next steps become standardized."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TPL.057

---

## 0) PURPOSE (KB)
Provide a copy-paste record format for:
- readiness gate results
- active certification
- recertification
- remediation plans

---

## 1) CERTIFICATION RECORD (COPY)
ENTITY_CERT_RECORD:
- RECORD_UID: <unique id for this record>
- DATE: YYYY-MM-DD
- ENTITY_UID: <entity uid>
- ENTITY_CLASS: SPC | ENG | ORC | CTL | VAL | QA | XREF
- PRIMARY_DOMAIN: <domain>
- CERT_TYPE: READINESS_MIN | ACTIVE_CERT | RECERT
- RESULT: PASS | REWORK | FAIL

EVIDENCE:
- READINESS_GATE_UID: UE.KB.GATE.ENTITY_READY_MIN.055
- READINESS_GATE_RESULT_REF: <ref or note>

- REQUIRED_SLOTS:
  - <slot>: PASS/REWORK/FAIL | EVIDENCE_REF: <ref>
  - <slot>: PASS/REWORK/FAIL | EVIDENCE_REF: <ref>

- COVERAGE_SCORECARD_REF: <uid/ref>
- COVERAGE_SCORE_PERCENT: <0..100>
- CRITICAL_MISSING_TAGS:
  - <tag>

- REQUIRED_PACK_UIDS_VALIDATED:
  - <pack uid>: PASS/REWORK/FAIL | QA_EVIDENCE_REF: <ref>
  - <pack uid>: PASS/REWORK/FAIL | QA_EVIDENCE_REF: <ref>

SAMPLE_RUNS (TRACE PROOF):
- RUN_REF: <ref>
  - KB_SOURCES_PRESENT: YES/NO
  - MEMORY_REUSE_DECLARED: YES/NO
  - STATUS_USED_DECLARED: YES/NO
  - WEB_LOOKUP_DISCLOSED: YES/NO
- RUN_REF: <ref>
  - ...

BLOCKERS (IF NOT PASS):
- B1: <blocker>
- B2: <blocker>

REMEDIATION PLAN:
- ACTION: CREATE/EXTEND/DEPRECATE
  - TARGET: <pack uid or planned name>
  - PRIORITY: P1/P2/P3
  - WHY:
  - DONE: YES/NO

NOTES:
- <optional>

NEXT_REVIEW_DATE: YYYY-MM-DD (optional)

---

## 2) RULES (STRICT)
- RESULT must be evidence-backed (no “just trust me”).
- If RESULT = FAIL, blockers and remediation plan are mandatory.
- Tags must be canonical.
- Packs must be referenced by UID.
- This record stores outcomes, not rules.

---

## 3) PASS/FAIL
PASS IF:
- all evidence fields are filled appropriately
- slots and coverage are supported by references
- remediation plan exists when needed

FAIL IF:
- result declared without evidence
- non-canonical tags used
- deprecated packs listed as authority without replacement

---

## 4) HARD FAIL CONDITIONS
FAIL IF:
- RESULT is PASS but any required slot is REWORK/FAIL
- coverage percent missing
- required packs missing from validation list (for ACTIVE cert)

---

## 5) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.STD.ENTITY_CERT_ACTIVE.056 | WHY: defines active certification requirements
- XREF: UE.KB.GATE.ENTITY_READY_MIN.055 | WHY: readiness minimum gate
- XREF: UE.KB.TPL.SKILL_TAG_SCORECARD.041 | WHY: coverage evidence
- XREF: UE.KB.CHK.SLOT_SATISFY.054 | WHY: slot satisfaction evidence
- XREF: UE.KB.STD.COMP_PACK_QA.045 | WHY: pack QA validation standard

--- END.
