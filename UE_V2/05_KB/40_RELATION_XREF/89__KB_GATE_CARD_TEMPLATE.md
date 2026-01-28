# KB — GATE CARD TEMPLATE (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/89__KB_GATE_CARD_TEMPLATE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: TEMPLATE
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.TPL.GATE_CARD.089
OWNER: SYSTEM
ROLE: Copy-paste “gate card” template for quick QA checks inside competence packs, drills, and example explanations. Encodes test method + pass/rework/fail criteria in a compact operational card with canonical tag linkage.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created gate card template for compact repeatable QA checks."
- REASON: "Gates must be operational and reusable; a compact card makes them easy to apply across packs."
- IMPACT: "More consistent QA and faster training/certification."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TPL.089

---

## 0) PURPOSE (KB)
Provide a minimal operational gate format that is easy to apply:
- what to check
- how to check
- pass/rework/fail

---

## 1) GATE CARD (COPY)
GATE_CARD:
- GATE_NAME:
- DOMAIN:
- SKILL_TAGS:
  - <tag>

WHAT_TO_CHECK:
- <1 line>

HOW_TO_CHECK:
1) ...
2) ...

PASS:
- <measurable>

REWORK:
- <measurable>

FAIL:
- <measurable>

NOTES (optional):
- pitfalls:
- edge cases:

RELATED_UIDS (UID-ONLY):
- <gate/std/policy uid> | WHY: <authority or calibration>

---

## 2) RULES (STRICT)
- Criteria must be measurable.
- Tags must be canonical.
- Must link to at least one authority UID if this card derives from a standard/policy.
- Keep it compact; if complex, use full gate definition module.

---

## 3) HARD FAIL CONDITIONS
FAIL IF:
- gate card is vague (“sounds good”)
- tags are non-canonical
- no pass/rework/fail separation
- uses URL/PATH in related references

---

## 4) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.STD.GATE_DEF.088 | WHY: full gate definition standard
- XREF: UE.KB.DICT.SKILL_TAGS.040 | WHY: canonical skill tag taxonomy

--- END.
