# KB — EXAMPLE CARD TEMPLATE (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/82__KB_EXAMPLE_CARD_TEMPLATE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: TEMPLATE
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.TPL.EXAMPLE_CARD.082
OWNER: SYSTEM
ROLE: Copy-paste template for creating Example Cards (GOOD/BAD/BORDERLINE exemplars) with canonical skill tags, clear explanation, and UID-only links to relevant standards/gates/packs.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created example card template for KB example library."
- REASON: "Examples must be structured and traceable; template prevents random dumps."
- IMPACT: "Consistent exemplars that improve QA calibration and learning."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TPL.082

---

## 0) PURPOSE (KB)
Provide a standard card format for examples used in QA and training.

---

## 1) EXAMPLE CARD (COPY)
EXAMPLE_CARD:
- EXAMPLE_UID: EX-YYYYMMDD-001
- DOMAIN: <music/narrative/...>
- LABEL: GOOD | BAD | BORDERLINE
- SKILL_TAGS:
  - <skill tag>
- WHAT_IT_DEMONSTRATES:
  - <1 bullet>
  - <1 bullet>
- INPUT_CONTEXT:
  - <scenario/task>
- EXAMPLE_SNIPPET:
  - <short snippet>
- WHY_IT_PASSES_OR_FAILS:
  - <bullet tied to gates/standards>
- RELATED_UIDS (UID-ONLY):
  - <uid> | WHY: <gate/standard reference>
- NOTES:
  - <optional>
- PROVENANCE (optional):
  - SOURCE_RECORD_UID: <uid>
  - DATE_ACCESSED: YYYY-MM-DD

---

## 2) RULES (STRICT)
- Keep snippet short and focused.
- Use canonical skill tags only.
- Must reference at least one gate/standard/pack UID.
- Do not paste large external text; paraphrase or keep minimal quote.

---

## 3) HARD FAIL CONDITIONS
FAIL IF:
- label missing
- tags non-canonical
- no related UID references
- snippet is large dump
- example is treated as rule authority

---

## 4) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.POL.EXAMPLE_LIBRARY.081 | WHY: example library policy and curation rules
- XREF: UE.KB.DICT.SKILL_TAGS.040 | WHY: canonical tags used by example cards
- XREF: UE.KB.STD.SOURCE_RECORDS.032 | WHY: provenance for external-derived examples

--- END.
