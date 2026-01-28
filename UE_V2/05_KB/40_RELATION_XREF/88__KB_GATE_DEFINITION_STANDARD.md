# KB — GATE DEFINITION STANDARD (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/88__KB_GATE_DEFINITION_STANDARD.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: STANDARD
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.STD.GATE_DEF.088
OWNER: SYSTEM
ROLE: Defines the canonical structure for KB quality gates: what is checked, how to test, pass/rework/fail criteria, thresholds, examples, and linkage to skill tags. Ensures gates are measurable and usable across entities.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created gate definition standard for measurable QA gates with examples and tag linkage."
- REASON: "Gates are only useful if measurable; vague gates create inconsistent QA and subjective drift."
- IMPACT: "Clear, repeatable QA across packs, examples, and certifications."
- CHANGE_ID: UE.CHG.2026-01-14.KB.STD.088

---

## 0) PURPOSE (KB)
Define a canonical structure for any gate/check:
- measurable criteria
- deterministic test method
- clear PASS/REWORK/FAIL outcomes
- linkage to skill tags and exemplars

---

## 1) REQUIRED FIELDS (MUST)
A gate definition must include:

GATE_IDENTITY:
- GATE_NAME
- DOMAIN
- TARGET_OUTPUT (what it evaluates)
- SKILL_TAGS (canonical)

TEST_METHOD:
- WHAT_TO_CHECK (short)
- HOW_TO_CHECK (procedure)
- REQUIRED_INPUTS (what is needed)
- TIMEBOX (optional)

CRITERIA:
- PASS (measurable)
- REWORK (measurable)
- FAIL (measurable)
- THRESHOLDS (if applicable)

EXAMPLES:
- PASS_EXAMPLE (short)
- FAIL_EXAMPLE (short)

NOTES:
- common pitfalls
- edge cases (optional)

TRACE_LINKS (UID-ONLY):
- standards/policies/packs that define constraints
- example cards that calibrate this gate (optional)

---

## 2) TEMPLATE (COPY)
GATE_DEFINITION:
- GATE_UID: <uid>
- DOMAIN: <domain>
- SKILL_TAGS:
  - <tag>

TEST_METHOD:
- WHAT_TO_CHECK:
- HOW_TO_CHECK:
  1) ...
  2) ...
- REQUIRED_INPUTS:
  - ...
- TIMEBOX:

CRITERIA:
- PASS:
- REWORK:
- FAIL:
- THRESHOLDS:
  - <metric>: <value>

EXAMPLES:
- PASS_EXAMPLE:
- FAIL_EXAMPLE:

RELATED_UIDS (UID-ONLY):
- <uid> | WHY: <constraint or calibration link>

---

## 3) ANTI-VAGUENESS RULES
Forbidden gate language:
- “good quality”
- “sounds nice”
- “make it better”
Unless paired with measurable criteria.

All criteria must be testable.

---

## 4) PASS/FAIL FOR GATE QUALITY
PASS IF:
- test method is step-by-step
- pass/rework/fail criteria are measurable
- tags are canonical
- at least one pass and fail example exist

FAIL IF:
- criteria are vague
- no test method
- no examples
- non-canonical tags

---

## 5) HARD FAIL CONDITIONS
FAIL IF:
- gate can’t be tested deterministically
- gate claims absolute truth without scope/inputs
- gate conflicts with higher authority policy without resolution

---

## 6) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.DICT.SKILL_TAGS.040 | WHY: gates must link to canonical skill tags
- XREF: UE.KB.POL.EXAMPLE_LIBRARY.081 | WHY: examples calibrate gates
- XREF: UE.KB.RULE.EXAMPLE_GATE_LINK.084 | WHY: examples must link to gates
- XREF: UE.KB.STD.COMP_PACK_QA.045 | WHY: pack QA uses gate structures

--- END.
