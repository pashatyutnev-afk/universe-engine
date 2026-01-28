# KB — QA RUBRIC CARD TEMPLATE (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/97__KB_QA_RUBRIC_CARD_TEMPLATE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: TEMPLATE
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.TPL.QA_RUBRIC_CARD.097
OWNER: SYSTEM
ROLE: Compact copy-paste QA rubric card template (0–10 axis scoring + PASS/REWORK/FAIL mapping) for use in packs, drills, audits, and certifications. Anchored to gate UIDs and skill tags.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created compact QA rubric card template for practical repeated use."
- REASON: "Rubrics must be easy to apply; a compact card increases adoption and consistency."
- IMPACT: "Faster evaluations and comparable QA scores."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TPL.097

---

## 0) PURPOSE (KB)
Provide a minimal operational rubric card to score outputs consistently.

---

## 1) QA RUBRIC CARD (COPY)
QA_RUBRIC_CARD:
- DATE: YYYY-MM-DD
- DOMAIN:
- TARGET_OUTPUT:
- SKILL_TAGS:
  - <tag>
- GATES_USED (UID-ONLY):
  - <uid>

SCORES (0..10):
- Clarity:
- Correctness:
- Completeness:
- Fit:
- Efficiency:

AGGREGATE:
- AVG_SCORE:
- KEY_GATE_FAIL: YES/NO
- RESULT: PASS/REWORK/FAIL

TOP ISSUES:
- <bullet>
- <bullet>

TOP FIXES:
- <bullet>
- <bullet>

---

## 2) RULES (STRICT)
- If KEY_GATE_FAIL = YES → RESULT must be FAIL.
- Use canonical tags only.
- Gates are UID-only.
- Keep issues/fixes short (top 2–3).

---

## 3) HARD FAIL CONDITIONS
FAIL IF:
- gate references use URL/PATH
- RESULT marked PASS while KEY_GATE_FAIL = YES
- missing domain or target output

---

## 4) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.STD.QA_RUBRIC.096 | WHY: defines rubric axes and mapping rules
- XREF: UE.KB.POL.GATE_LIBRARY.092 | WHY: key gate discipline affects scoring overrides
- XREF: UE.KB.DICT.SKILL_TAGS.040 | WHY: canonical tags

--- END.
