# TEMPLATE — QA EXEMPLAR SET (COPY) (CANON)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/60_QA/01__TEMPLATE__EXEMPLAR_SET.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 60_QA
DOC_TYPE: KB_MODULE
KB_TYPE: TEMPLATE
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.QA.TPL.EXEMPLARS.001
OWNER: SYSTEM
ROLE: Copy-paste template for building QA exemplar sets: labeled positive/negative/borderline examples, grading rubric, failure taxonomy, evaluation procedure, and trace discipline (UID-only).

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created QA exemplar set template for deterministic quality evaluation and training-by-example."
- REASON: "QA requires calibration and repeatability; exemplars convert taste into enforceable checks."
- IMPACT: "Faster regression detection, consistent scoring, and stable quality gates."
- CHANGE_ID: UE.CHG.2026-01-14.KB.QA.TPL.001

---

## 0) HOW TO USE
- Copy this template to create a new exemplar set for a specific QA goal.
- Keep examples minimal but sharp: 3–7 per class is enough to calibrate.
- Store evidence as text only (no external assumptions).
- Use UID-only references for related modules/gates/policies.

---

## 1) EXEMPLAR SET HEADER (COPY)
EXEMPLAR_SET:
- SET_UID:
- SET_NAME:
- OWNER_QA_UID:
- STATUS:
- LOCK:
- VERSION:
- PURPOSE (what quality property we calibrate):
- SCOPE:
  - OUTPUT_TYPES:
  - LANGUAGES:
  - GENRES / DOMAINS:
  - EXCLUDES:
- EVALUATION_CONTEXT:
  - MODEL / TOOL:
  - USER CONSTRAINTS (if any):
  - HARD RULES (UID-only refs):
- CHANGE_NOTE:
  - DATE:
  - TYPE:
  - SUMMARY:
  - CHANGE_ID:

---

## 2) SCORING RUBRIC (MUST BE EXPLICIT)
RUBRIC:
- SCALE: 0..3 | 0..5 | PASS/FAIL (choose one)
- DIMENSIONS:
  - D-01:
    - NAME:
    - WHAT GOOD LOOKS LIKE:
    - WHAT BAD LOOKS LIKE:
    - WEIGHT (optional):
    - PASS THRESHOLD:
  - D-02:
    - NAME:
    - GOOD:
    - BAD:
    - WEIGHT:
    - PASS:

SCORING_RULES:
- How to combine dimensions:
- Tie-break rule:
- What triggers instant FAIL (hard fails):

---

## 3) LABEL TAXONOMY (ERROR / ISSUE TYPES)
ISSUE_TYPES:
- I-01:
  - NAME:
  - DESCRIPTION:
  - DETECTION SIGNALS:
  - SEVERITY: S0 | S1 | S2 | S3
  - DEFAULT RESPONSE: REWORK | FAIL | WARN
- I-02:
  - NAME:
  - DESCRIPTION:
  - SIGNALS:
  - SEVERITY:
  - RESPONSE:

Notes:
- Keep taxonomy small. If too many, QA becomes non-operational.

---

## 4) EXEMPLARS (THE CORE)
### 4.1 POSITIVE EXEMPLARS (GOOD)
GOOD_EXAMPLES:
- G-01:
  - CONTEXT / PROMPT:
  - OUTPUT (excerpt):
  - WHY GOOD (map to rubric dimensions):
  - SCORE:
  - TAGS: [style, domain, risk, etc]
  - TRACE:
    - issue_types_triggered: none
- G-02:
  - CONTEXT / PROMPT:
  - OUTPUT:
  - WHY GOOD:
  - SCORE:
  - TAGS:
  - TRACE:

### 4.2 NEGATIVE EXEMPLARS (BAD)
BAD_EXAMPLES:
- B-01:
  - CONTEXT / PROMPT:
  - OUTPUT (excerpt):
  - WHAT FAILS (issue types + rubric mapping):
  - SCORE:
  - CORRECTION NOTE (what would fix it, short):
  - TAGS:
  - TRACE:
    - issue_types_triggered: [I-.., I-..]
- B-02:
  - CONTEXT / PROMPT:
  - OUTPUT:
  - FAILS:
  - SCORE:
  - FIX NOTE:
  - TAGS:
  - TRACE:

### 4.3 BORDERLINE EXEMPLARS (CALIBRATION)
BORDERLINE_EXAMPLES:
- BL-01:
  - CONTEXT / PROMPT:
  - OUTPUT (excerpt):
  - WHY BORDERLINE:
  - DECISION: PASS | REWORK | FAIL
  - SCORE:
  - WHAT WOULD PUSH IT TO PASS:
  - TAGS:

---

## 5) EVALUATION PROCEDURE (TESTABILITY)
EVAL_PROCEDURE:
- INPUTS:
  - output text
  - original prompt/context
  - constraints (if any)
- STEPS:
  1) run hard-fail checks
  2) score rubric dimensions
  3) assign issue types (if any)
  4) make decision (PASS/REWORK/FAIL)
  5) record trace
- OUTPUT:
  - decision
  - score
  - issues
  - short fix direction (if REWORK)

WHAT TO RECORD (TRACE):
- exemplar_set_uid
- version
- decision + score
- issues (UIDs)
- evidence snippet(s)

---

## 6) REGRESSION / DRIFT GUARD
REGRESSION_GUARD:
- What changed when quality drifted:
- Which exemplar(s) catch it:
- Minimal detection set (IDs):
  - [G-.., B-.., BL-..]
- Update rule:
  - Do not rewrite old exemplars; add new ones and bump version.

---

## 7) COMMON FAILURE PATTERNS (SHORT LIBRARY)
FAILURE_PATTERNS:
- P-01:
  - PATTERN:
  - SYMPTOMS:
  - LIKELY CAUSE:
  - FIX STRATEGY:
- P-02:
  - PATTERN:
  - SYMPTOMS:
  - CAUSE:
  - FIX:

---

## 8) HARD FAIL CONDITIONS (COPY)
HARD_FAIL_CONDITIONS:
- rubric missing or ambiguous
- exemplars exist but no evaluation procedure exists
- issue taxonomy missing
- UID-only discipline broken
- exemplar set used without version recorded

---

## 9) RELATED (UID-ONLY)
RELATED_UIDS:
- <uid> | WHY

--- END.
