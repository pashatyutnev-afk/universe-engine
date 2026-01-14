# KB — COMPETENCE PACK FAILURE MODE TEMPLATE (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/47__KB_COMPETENCE_PACK_FAILURE_MODE_TEMPLATE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: TEMPLATE
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.TPL.COMP_PACK_FAILUREMODE.047
OWNER: SYSTEM
ROLE: Template to document failure modes inside competence packs: symptom → detection → likely causes → fix → prevention → re-test → escalation. Makes troubleshooting deterministic.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created failure mode template for competence packs with deterministic troubleshooting flow."
- REASON: "Professional competence requires diagnosing and fixing failures; without a template packs become idealized and unusable."
- IMPACT: "Entities can recover from common defects consistently; QA becomes repeatable."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TPL.047

---

## 0) PURPOSE (KB)
Provide a standard structure for failure modes so that:
- defects are detectable
- causes are analyzable
- fixes are repeatable
- prevention exists
- re-test is mandatory

---

## 1) FAILURE MODE CARD (COPY)
FAILURE_MODE:
- ID: FM-01
- NAME: <short>
- SYMPTOM:
  - <what is observed>
- DETECTION (HOW TO SPOT):
  - test/check:
  - threshold (if any):
- LIKELY_CAUSES:
  - C1:
  - C2:
- FIX (STEP-BY-STEP):
  1) ...
  2) ...
- PREVENTION (GUARDRAILS):
  - rule:
  - checklist item:
- RE-TEST (MANDATORY):
  - run the same detection test again
  - expected PASS condition
- ESCALATE IF:
  - <conditions>
- NOTES:
  - <optional>

---

## 2) RULES (STRICT)
- Each failure mode must have a detection method.
- Each fix must be step-by-step.
- Prevention must map to a checklist item.
- Re-test must be explicit (same test as detection).
- Escalation must specify next action (load more modules / consult validator / stop).

---

## 3) PASS/FAIL
PASS IF:
- at least 3 failure modes exist per competence pack (recommended)
- each has detection + fix + prevention + re-test

FAIL IF:
- failure modes are vague (“bad quality”) without detection
- no re-test
- prevention absent

---

## 4) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.STD.COMP_PACK.036 | WHY: competence pack standard requires failure modes
- XREF: UE.KB.STD.COMP_PACK_QA.045 | WHY: QA gates validate failure mode completeness
- XREF: UE.KB.TPL.COMP_PACK_PLAYBOOK.046 | WHY: playbook uses recovery paths built from failure modes

--- END.
