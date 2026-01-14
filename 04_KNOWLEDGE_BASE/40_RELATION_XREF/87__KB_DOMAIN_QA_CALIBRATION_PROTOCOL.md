# KB — DOMAIN QA CALIBRATION PROTOCOL (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/87__KB_DOMAIN_QA_CALIBRATION_PROTOCOL.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: PROTOCOL
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.PROC.DOMAIN_QA_CALIB.087
OWNER: SYSTEM
ROLE: Deterministic protocol for calibrating QA judgment per domain using canonical gates and exemplar sets (GOOD/BAD/BORDERLINE). Ensures consistent evaluation across entities and reduces subjective drift.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created domain QA calibration protocol using gate-linked exemplars and consistency checks."
- REASON: "Quality gates must be applied consistently; calibration prevents different entities from judging outputs differently."
- IMPACT: "More reliable QA outcomes, smoother certification, and better training."
- CHANGE_ID: UE.CHG.2026-01-14.KB.PROC.087

---

## 0) PURPOSE (KB)
Calibrate QA evaluation so that:
- PASS/REWORK/FAIL is consistent across entities
- examples align with current gates
- borderline cases are recognized and handled consistently

---

## 1) INPUTS / OUTPUTS
INPUTS:
- Domain (music/narrative/...)
- Canon gates/standards for that domain
- Exemplar set (GOOD/BAD/BORDERLINE) linked to those gates

OUTPUTS:
- Calibration result (PASS/REWORK/FAIL)
- List of mismatches (example↔gate disagreement)
- Updated exemplar set (curated)
- Optional: audit record if changes affect many evaluations

---

## 2) CALIBRATION SET REQUIREMENTS
Minimum calibration set per domain:
- 3 GOOD examples
- 3 BAD examples
- 2 BORDERLINE examples
All must:
- use canonical skill tags
- link to at least one domain gate/standard UID
- include pass/fail explanations mapped to gate criteria

---

## 3) CALIBRATION FLOW (DETERMINISTIC)
Step 1: Select gates
- Choose the domain’s key gates (2–5) that define PASS quality.

Step 2: Select exemplar set
- Pull examples that link to these gates and cover key tag clusters.

Step 3: Independent scoring (repeatable)
For each example:
- apply the gate criteria
- produce expected label:
  - should be GOOD / BAD / BORDERLINE

Step 4: Consistency check
- Compare expected label with example’s stored label.
- Record mismatches.

Step 5: Fix mismatches
If mismatch occurs:
- either:
  - relabel the example
  - fix the explanation (map correctly to criteria)
  - deprecate/remove the example if outdated
  - update gates if the gate definition changed (rare; governance controlled)

Step 6: Calibration PASS criteria
Calibration is PASS when:
- ≥ 80% examples match expected labels
- all critical gates have at least one GOOD and one BAD example

---

## 4) RESULT RULES
PASS IF:
- mismatch rate ≤ 20%
- exemplar set is balanced across key tag clusters
- explanations correctly reference gate criteria

REWORK IF:
- mismatch rate 20–40%
- examples missing for some gates/tag clusters
- borderline set too weak

FAIL IF:
- mismatch rate > 40%
- examples contradict current canon gates
- gate linkage missing or incorrect

---

## 5) HARD FAIL CONDITIONS
FAIL IF:
- examples used without gate linkage
- calibration performed with outdated examples (contradict canon)
- calibration results are ignored and exemplars remain inconsistent

---

## 6) OUTPUT TEMPLATE (COPY)
DOMAIN_QA_CALIBRATION_RESULT:
- DATE: YYYY-MM-DD
- DOMAIN:
- GATES_USED:
  - <uid>
- EXEMPLAR_SET:
  - GOOD: <count>
  - BAD: <count>
  - BORDERLINE: <count>
- MISMATCH_RATE: <percent>
- RESULT: PASS/REWORK/FAIL
- MISMATCHES:
  - EXAMPLE_UID: <id> | EXPECTED: <label> | FOUND: <label> | FIX: <action>
- ACTIONS:
  - CURATE_EXAMPLES: YES/NO
  - UPDATE_GATES: YES/NO (rare; governance controlled)

---

## 7) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.POL.EXAMPLE_LIBRARY.081 | WHY: example library policy
- XREF: UE.KB.CHK.EXAMPLE_CURATE.083 | WHY: example curation checklist
- XREF: UE.KB.RULE.EXAMPLE_GATE_LINK.084 | WHY: every example must link to gates
- XREF: UE.KB.RULE.EXAMPLE_IN_DRILLS.086 | WHY: examples integrated into drills/training

--- END.
