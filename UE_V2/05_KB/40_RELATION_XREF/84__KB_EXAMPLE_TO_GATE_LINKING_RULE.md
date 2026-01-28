# KB — EXAMPLE ↔ GATE LINKING RULE (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/84__KB_EXAMPLE_TO_GATE_LINKING_RULE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: RULE
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.RULE.EXAMPLE_GATE_LINK.084
OWNER: SYSTEM
ROLE: Enforces that every example in the KB example library is explicitly linked to at least one canon gate/standard/pack UID and explains how it passes/fails that gate. Prevents abstract examples that cannot calibrate QA.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created rule requiring every example to link to gates/standards and explain pass/fail reasons."
- REASON: "Examples must calibrate QA; without gate linkage they are subjective and non-actionable."
- IMPACT: "Higher-signal example library and stronger QA training."
- CHANGE_ID: UE.CHG.2026-01-14.KB.RULE.084

---

## 0) PURPOSE (KB)
Make examples operational:
- each example must map to a specific gate or standard
- explanation must reference the gate criteria
- examples can be used directly in QA calibration and drills

---

## 1) ABSOLUTE RULES
R1 — Mandatory gate linkage
- Every example card must include at least one RELATED_UID that is a canon gate/standard/pack.

R2 — Explicit pass/fail explanation
- WHY_IT_PASSES_OR_FAILS must cite the reason in terms of gate criteria, not personal taste.

R3 — UID-only referencing
- Gate/standard references are UID-only (no URL/PATH).

R4 — No orphan examples
- Any example without gate linkage is invalid and must be edited or removed.

---

## 2) LINKING PATTERN (COPY)
RELATED_UIDS (UID-ONLY):
- <gate/standard/pack uid> | WHY: <which rule/check it illustrates>

WHY_IT_PASSES_OR_FAILS:
- <bullet mapped to gate criterion>
- <bullet mapped to gate criterion>

---

## 3) MULTI-GATE EXAMPLES (ALLOWED)
An example may link to multiple gates if:
- each linkage is explicit
- the example remains focused (one main point)

If the example covers multiple unrelated points:
- split into multiple examples.

---

## 4) VALIDATION
PASS IF:
- at least one gate/standard UID exists
- explanation references gate criteria
- tags are canonical and match the gate’s domain

FAIL IF:
- example has no related UID
- explanation is “because it feels good/bad”
- example contradicts the linked gate or is mislabeled

---

## 5) HARD FAIL CONDITIONS
FAIL IF:
- examples accumulate without linkage to gates/standards
- gate linkage uses URL/PATH
- examples are used as authority instead of gates/standards

---

## 6) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.POL.EXAMPLE_LIBRARY.081 | WHY: example library policy
- XREF: UE.KB.TPL.EXAMPLE_CARD.082 | WHY: example card includes RELATED_UIDS field
- XREF: UE.KB.CHK.EXAMPLE_CURATE.083 | WHY: curation checklist validates linkage compliance

--- END.
