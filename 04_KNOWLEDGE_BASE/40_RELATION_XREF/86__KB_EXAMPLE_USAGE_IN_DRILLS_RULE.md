# KB — EXAMPLE USAGE IN DRILLS RULE (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/86__KB_EXAMPLE_USAGE_IN_DRILLS_RULE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: RULE
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.RULE.EXAMPLE_IN_DRILLS.086
OWNER: SYSTEM
ROLE: Defines deterministic use of example cards in drills: calibration (GOOD/BAD), task execution, comparison, and evaluation using linked gates. Integrates example library into skill training.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created rule for integrating example library into drills via calibration and gate-based evaluation."
- REASON: "Drills improve competence faster when anchored by exemplars; examples must be used systematically, not randomly."
- IMPACT: "More consistent training and stronger L2/L3 progression."
- CHANGE_ID: UE.CHG.2026-01-14.KB.RULE.086

---

## 0) PURPOSE (KB)
Use examples to train skills deterministically:
- calibrate what PASS/FAIL looks like
- run drill tasks
- compare outputs to exemplars
- score using gate criteria

---

## 1) ABSOLUTE RULES
R1 — Examples must be linked to gates
- Use only examples that have gate linkage (required by example policy).

R2 — Calibration before production
- Training starts with GOOD/BAD recognition to align judgement.

R3 — Gate-based scoring
- Evaluation must use the linked gate/standard criteria, not taste.

---

## 2) DRILL FLOW WITH EXAMPLES (DETERMINISTIC)
Step 1: Calibration
- Review 1 GOOD and 1 BAD example for the target skill tag cluster.
- Identify which gate criteria are met/violated.

Step 2: Task execution
- Perform the drill task (as defined in drills template).

Step 3: Comparison
- Compare output against:
  - GOOD example: what you matched
  - BAD example: what you avoided

Step 4: Evaluation
- Score using gate rubric:
  - PASS/REWORK/FAIL
  - numeric scoring if used

Step 5: Iteration
- If FAIL:
  - apply failure-mode recovery
  - repeat drill with modified constraints

---

## 3) MINIMUM REQUIREMENTS FOR “EXAMPLE-BASED DRILL”
- At least 2 examples used (GOOD + BAD)
- Each example linked to at least one gate UID
- Output evaluated against gate criteria
- Result recorded with score and notes

---

## 4) HARD FAIL CONDITIONS
FAIL IF:
- examples used without gate linkage
- evaluation is subjective without gate criteria
- only GOOD examples used (no BAD calibration)
- drill has no recorded evaluation outcome

---

## 5) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.POL.EXAMPLE_LIBRARY.081 | WHY: example library policy
- XREF: UE.KB.RULE.EXAMPLE_GATE_LINK.084 | WHY: gate linkage requirement for examples
- XREF: UE.KB.TPL.COMP_PACK_DRILLS.048 | WHY: drills template can include examples
- XREF: UE.KB.TPL.EXAMPLE_CARD.082 | WHY: example card structure

--- END.
