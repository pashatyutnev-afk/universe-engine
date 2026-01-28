# KB — ACTIVE ENTITY CERTIFICATION STANDARD (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/56__KB_ACTIVE_ENTITY_CERTIFICATION_STANDARD.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: STANDARD
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.STD.ENTITY_CERT_ACTIVE.056
OWNER: SYSTEM
ROLE: Defines deterministic certification requirements for marking an entity as ACTIVE-ready: minimum readiness passes, required slots satisfied at strength, coverage thresholds met, competence packs quality validated, and certification record produced.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created ACTIVE certification standard for entities (evidence-based readiness and competence validation)."
- REASON: "ACTIVE entities must be trustworthy; certification prevents promoting weak/unprepared entities to production usage."
- IMPACT: "Entities become auditable; ACTIVE status reflects real competence and coverage."
- CHANGE_ID: UE.CHG.2026-01-14.KB.STD.056

---

## 0) PURPOSE (KB)
Define how an entity can be certified as ACTIVE-ready:
- evidence-based readiness
- slot satisfaction with strength requirements
- competence pack QA validated
- stable trace discipline
- certification record produced and stored

---

## 1) CERTIFICATION PREREQUISITES
Required:
- Entity readiness minimum gate result exists and is PASS (not REWORK).
- Governance baseline modules are ACTIVE.
- Entity bindings reference ACTIVE packs where possible.

---

## 2) CERTIFICATION REQUIREMENTS (PASS/FAIL)
C1 — Readiness gate PASS
- Must pass UE.KB.GATE.ENTITY_READY_MIN.055

C2 — Required slots satisfied with strength
For each required slot:
- Must be PASS via slot satisfaction checklist.
Strength requirements:
- Governance/QA/Validation slots:
  - at least half required tags at L2+
- Domain core slot:
  - at least half required tags at L2+
  - at least one tag at L3 (recommended; required for top-tier specialists)

C3 — Coverage threshold
- Coverage percent must be ≥ 80% for the domain’s required tag clusters.
- Critical missing tags must be empty.

C4 — Competence packs quality
For each REQUIRED_PACK_UID:
- Must pass competence pack QA gates:
  - no “water” (vague content)
  - capabilities and gates present
  - templates present
Recommended:
- majority capabilities ≥ L2

C5 — No deprecated authority
- No deprecated pack is used as authority.

C6 — Trace discipline proven
- At least 3 sample runs demonstrate:
  - KB_SOURCES present
  - MEMORY_REUSE declared
  - STATUS_USED declared
  - WEB_LOOKUP_USED disclosed if applicable

---

## 3) CERTIFICATION OUTPUT (RECORD TEMPLATE)
Create a certification record (format example):

ENTITY_CERT_RECORD:
- ENTITY_UID:
- ENTITY_CLASS:
- DOMAIN:
- DATE:
- CERT_RESULT: PASS/FAIL
- READINESS_GATE_REF:
- SLOT_RESULTS:
  - <slot>: PASS
- COVERAGE:
  - SCORE:
  - SCORECARD_REF:
- PACKS_VALIDATED:
  - <pack uid> : PASS
- SAMPLE_RUN_REFS:
  - <ref>
- NOTES:
- NEXT_REVIEW_DATE: (optional)

Rule:
- If FAIL, include blockers and gap-fill plan.

---

## 4) RECERTIFICATION RULES
Recertify when:
- major pack replacements occur (supersedes)
- governance policy changes
- entity domain scope changes

Recertification may be lighter if only patch updates occurred.

---

## 5) HARD FAIL CONDITIONS
FAIL IF:
- readiness gate not PASS
- any required slot not PASS
- coverage below threshold
- any required pack fails pack QA gates
- deprecated authority present
- trace discipline not demonstrated

---

## 6) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.GATE.ENTITY_READY_MIN.055 | WHY: minimum readiness gate prerequisite
- XREF: UE.KB.CHK.SLOT_SATISFY.054 | WHY: slot satisfaction evidence
- XREF: UE.KB.TPL.SKILL_TAG_SCORECARD.041 | WHY: coverage evidence
- XREF: UE.KB.STD.COMP_PACK_QA.045 | WHY: validates competence packs quality
- XREF: UE.KB.POL.STATUS_LOCK.029 | WHY: ACTIVE status discipline

--- END.
