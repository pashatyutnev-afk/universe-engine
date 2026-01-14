# KB — COMPETENCE PACK DRILLS TEMPLATE (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/48__KB_COMPETENCE_PACK_DRILLS_TEMPLATE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: TEMPLATE
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.TPL.COMP_PACK_DRILLS.048
OWNER: SYSTEM
ROLE: Template to add practice drills to competence packs: micro-tasks, difficulty levels, evaluation rubric, and progression criteria. Enables L3 mastery and measurable improvement.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created drills template for competence packs (practice tasks + rubric + progression)."
- REASON: "Expert-level competence requires drills and evaluation; otherwise packs cannot reach L3 reliably."
- IMPACT: "Entities can iterate skill improvement with deterministic practice and scoring."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TPL.048

---

## 0) PURPOSE (KB)
Provide a standard drills section:
- exercises to practice capabilities
- difficulty levels
- scoring rubric
- progression criteria (when L2 → L3)

---

## 1) DRILLS SECTION (COPY)
## DRILLS (PRACTICE & EVALUATION)
DRILL_SET:
- TARGET_CAPABILITY: C01 <name>
- SKILL_TAGS:
  - <skill tag>
- LEVELS:
  - L1: baseline
  - L2: strong
  - L3: expert

DRILLS:
- DRILL: D-01
  - GOAL:
  - INPUTS:
  - TASK:
  - CONSTRAINTS:
  - TIMEBOX: <minutes>
  - OUTPUT:
  - EVALUATION (RUBRIC):
    - PASS criteria:
    - REWORK criteria:
    - FAIL criteria:
  - SCORING (0..10):
    - clarity:
    - correctness:
    - efficiency:
    - style/fit (if applicable):
  - COMMON_FAILURES:
    - FM refs or notes
  - NEXT:
    - if score < 7 → repeat with constraint changes
    - if score ≥ 7 → next drill level

PROGRESSION RULES:
- Promote capability to L2 if:
  - 3 drills scored ≥ 7 with different inputs
- Promote capability to L3 if:
  - 5 drills scored ≥ 8 including at least 2 edge-case drills
  - plus regression guard checklist exists (if domain requires)

---

## 2) RULES (STRICT)
- Each drill must have measurable evaluation criteria.
- Drills must map to a specific capability and tags.
- Timebox required to prevent infinite tweaking.
- Progression must include repeated success with varied inputs.

---

## 3) PASS/FAIL
PASS IF:
- at least 1 drill exists for a critical capability
- each drill has rubric and scoring
- progression rules present

FAIL IF:
- drills are vague (no rubric)
- no progression criteria
- drills not tied to capability/tags

---

## 4) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.STD.COMP_PACK.036 | WHY: competence pack structure (drills are optional but recommended)
- XREF: UE.KB.STD.COMP_PACK_QA.045 | WHY: L3 requires drills + edge cases
- XREF: UE.KB.DICT.SKILL_TAGS.040 | WHY: drills must use canonical skill tags

--- END.
