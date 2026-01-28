# KB — COMPETENCE PACK TEMPLATE INDEX STANDARD (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/49__KB_COMPETENCE_PACK_TEMPLATES_INDEX_STANDARD.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: STANDARD
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.STD.COMP_PACK_TPL_INDEX.049
OWNER: SYSTEM
ROLE: Standard for organizing and referencing templates inside competence packs: required template types, naming pattern, and UID-only referencing rules—ensuring packs remain operational and reusable.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created standard for competence pack template indexing and required template set."
- REASON: "Packs need copyable artifacts (cards/forms); without a template index, packs become narrative and non-executable."
- IMPACT: "Template reuse increases; packs become faster to apply and easier to QA."
- CHANGE_ID: UE.CHG.2026-01-14.KB.STD.049

---

## 0) PURPOSE (KB)
Define how competence packs must manage templates:
- required template categories
- consistent naming for templates/cards
- UID-only references
- minimal internal index section inside the pack

This does not replace the KB master index.

---

## 1) REQUIRED TEMPLATE CATEGORIES (MUST)
A competence pack should include templates for:
- CAPABILITY CARD (inputs/outputs + steps + gate)
- CHECKLIST (pre/execution/post)
- QA GATE CARD (pass/rework/fail)
- FAILURE MODE CARD (symptom→fix→re-test)
Recommended (for L3):
- PLAYBOOK (decision tree)
- DRILLS (practice + rubric)
- SCORECARD (domain-specific scoring)

---

## 2) TEMPLATE NAMING PATTERN (IN-PACK)
Inside a pack, templates should be labeled consistently:

TPL:
- TPL-01: <template name>
- TPL-02: <template name>

Rules:
- short, descriptive template names
- templates are copy blocks, not essays

---

## 3) UID-ONLY REFERENCING RULE
If a template is a standalone KB module:
- refer to it by UID in XREF blocks only.

If a template is embedded inside the pack:
- label it as TPL-XX and reference by label internally.

Forbidden:
- using URLs/PATH as references to templates
- duplicating external templates without noting the canon UID (if one exists)

---

## 4) INTERNAL TEMPLATE INDEX SECTION (COPY)
## TEMPLATES (INDEX)
TPL:
- TPL-01: Capability Card
- TPL-02: QA Gate Card
- TPL-03: Checklist (Pre/Exec/Post)
- TPL-04: Failure Mode Card
- TPL-05: Playbook (optional)
- TPL-06: Drills (optional)

Rule:
- If a template category is not present, explain why briefly.

---

## 5) QA RULES (PACK TEMPLATE COMPLETENESS)
PASS IF:
- required categories exist (Section 1)
- templates are copyable and minimal
- templates align with skill tags and gates

REWORK IF:
- templates exist but are inconsistent or too verbose

FAIL IF:
- pack has procedures but no templates/cards
- templates are not actionable (no fields)
- pack relies on external navigation links

---

## 6) HARD FAIL CONDITIONS
FAIL IF:
- no internal template index section exists in a competence pack
- required template categories missing without justification
- any template reference uses URL/PATH

---

## 7) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.STD.COMP_PACK.036 | WHY: packs require templates to be operational
- XREF: UE.KB.STD.COMP_PACK_QA.045 | WHY: QA gates check template completeness
- XREF: UE.KB.TPL.COMP_PACK_PLAYBOOK.046 | WHY: playbook template category
- XREF: UE.KB.TPL.COMP_PACK_FAILUREMODE.047 | WHY: failure mode template category
- XREF: UE.KB.TPL.COMP_PACK_DRILLS.048 | WHY: drills template category

--- END.
