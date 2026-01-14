# KB — QA RUBRIC STANDARD (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/96__KB_QA_RUBRIC_STANDARD.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: STANDARD
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.STD.QA_RUBRIC.096
OWNER: SYSTEM
ROLE: Defines a canonical scoring rubric standard for QA: axes, 0–10 scoring guidelines, mapping to PASS/REWORK/FAIL, and linkage to gates and skill tags. Enables consistent quantitative evaluation across domains.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created QA rubric standard: scoring axes, 0–10 guidance, and mapping to pass/rework/fail with gate linkage."
- REASON: "QA needs consistent measurable scoring; otherwise evaluation becomes subjective and unstable across entities."
- IMPACT: "Comparable QA scores, clearer improvements, and better certification signals."
- CHANGE_ID: UE.CHG.2026-01-14.KB.STD.096

---

## 0) PURPOSE (KB)
Provide a standard rubric model:
- choose axes (what dimensions matter)
- score each axis 0..10
- aggregate into PASS/REWORK/FAIL
- link rubric to gates and skill tags

---

## 1) RUBRIC DESIGN PRINCIPLES
- Axes must be measurable (avoid taste-only).
- Keep 3–6 axes (too many becomes noise).
- Use clear thresholds for PASS/REWORK/FAIL.
- Tie axes to gates and skill tags for traceability.

---

## 2) CANON AXES (DEFAULT SET)
Use these default axes unless domain requires others:
A1 Clarity (0..10)
- how clear and unambiguous the output is

A2 Correctness (0..10)
- adherence to constraints, rules, and required structure

A3 Completeness (0..10)
- required parts present; no missing sections

A4 Fit (0..10)
- matches domain/style/intent constraints (measurable via gate checks)

A5 Efficiency (0..10)
- minimal overload, avoids unnecessary content, follows minimal set rules

Optional domain axes:
- Music: Hook strength, mix translation, uniqueness
- Narrative: Stakes/tension, continuity
- Visual: readability/contrast, composition hierarchy
- Marketing: clarity of positioning, channel fit

---

## 3) SCORING GUIDELINES (0..10)
- 0–3: FAIL zone (major violations)
- 4–6: REWORK zone (usable but clearly needs fixes)
- 7–8: PASS zone (meets requirements well)
- 9–10: EXCELLENT (top-tier; few/no issues)

Rule:
- If any key gate FAILs, overall result cannot be PASS even if average score is high.

---

## 4) AGGREGATION & RESULT MAPPING
Compute:
- Average score across axes (AVG)

Mapping:
- PASS if:
  - AVG ≥ 7
  - and no key gate FAIL
- REWORK if:
  - AVG 4..6 OR any non-key gate FAIL
- FAIL if:
  - AVG < 4 OR any key gate FAIL OR structural non-compliance

Key gate override:
- Any KEY gate FAIL forces overall FAIL.

---

## 5) RUBRIC CARD TEMPLATE (COPY)
QA_RUBRIC:
- DOMAIN:
- SKILL_TAGS:
  - <tag>
- GATES_USED (UID-ONLY):
  - <uid>
- AXES:
  - A1 Clarity: <0..10>
  - A2 Correctness: <0..10>
  - A3 Completeness: <0..10>
  - A4 Fit: <0..10>
  - A5 Efficiency: <0..10>
- AVG_SCORE:
- KEY_GATE_FAIL: YES/NO
- RESULT: PASS/REWORK/FAIL
- NOTES:
  - <top issues>
  - <top improvements>

---

## 6) HARD FAIL CONDITIONS
FAIL IF:
- rubric uses subjective axes only without gate linkage
- no thresholds defined for PASS/REWORK/FAIL
- score claims PASS while key gate fails
- tags are non-canonical or missing

---

## 7) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.STD.GATE_DEF.088 | WHY: rubrics should be anchored to measurable gates
- XREF: UE.KB.POL.GATE_LIBRARY.092 | WHY: key gate discipline affects scoring overrides
- XREF: UE.KB.DICT.SKILL_TAGS.040 | WHY: rubrics must use canonical tags
- XREF: UE.KB.STD.COMP_PACK_QA.045 | WHY: pack QA often uses rubrics for scoring

--- END.
