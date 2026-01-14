# ENTITIES KB — SPC PROFICIENCY MATRIX (CANON)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/04__COVERAGE__SPC_PROFICIENCY_MATRIX.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB
DOC_TYPE: KB_MODULE
KB_TYPE: MAP
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.COV.SPC_PROFICIENCY.004
OWNER: SYSTEM
ROLE: Defines proficiency levels for SPC competence packs (L0..L4) and the minimum coverage requirements per level: skill depth, playbooks, cases, gates, rubric, sources, and regression guard expectations.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created SPC proficiency matrix: levels, required artifacts, and pass criteria to qualify SPC packs as 'pro-level'."
- REASON: "SPC packs must be deep and testable; a proficiency matrix prevents shallow packs being treated as authoritative."
- IMPACT: "Clear bar for SPC competence and safer certification readiness."
- CHANGE_ID: UE.CHG.2026-01-14.KB.COV.004

---

## 0) PURPOSE (KB)
Define what “SPC proficiency” means operationally:
- levels (L0..L4)
- required pack components per level
- pass criteria for “pro-ready” SPC packs

This is a coverage matrix, not navigation.

---

## 1) LEVEL DEFINITIONS (L0..L4)
L0 — EMPTY / NON-OPERATIONAL
- skeleton only; no reliable competence

L1 — BASIC OPERATIONAL
- can execute simple tasks with guidance
- has minimal structure and a couple of checklists

L2 — PRACTITIONER
- consistent execution in normal cases
- has playbooks and common failure handling

L3 — PRO
- deep craft coverage + edge cases
- has measurable gates, strong case library, rubric anchors
- can teach/guide other entities reliably

L4 — MASTER
- strategic + diagnostic competence
- handles novel cases, creates new gates/patterns safely
- maintains regression guards and calibration exemplars

---

## 2) REQUIRED ARTIFACTS (BY LEVEL)
Coverage dimensions:
- D1 Skill Tree Depth
- D2 Golden Principles
- D3 Playbooks / Methods
- D4 Checklists
- D5 Gates (measurable)
- D6 Case Library (good/bad/borderline)
- D7 Evaluation Rubric (with anchors)
- D8 Sources / Provenance (when applicable)
- D9 Regression Guard / Calibration (for key competencies)

### L1 — BASIC OPERATIONAL (minimum)
- D1 Skill Tree: exists (high-level branches only)
- D2 Principles: 5–10 core principles/constraints
- D3 Playbooks: 1–2 core playbooks
- D4 Checklists: ≥ 2 checklists (pass/rework/fail)
- D5 Gates: ≥ 1 simple gate OR checklist-as-gate
- D6 Cases: ≥ 3 cases (at least 1 good, 1 bad)
- D7 Rubric: basic rubric card exists
- D8 Sources: optional unless external claims are used
- D9 Regression: not required

### L2 — PRACTITIONER
- D1 Skill Tree: medium depth (skills decomposed to actionable leaf skills)
- D2 Principles: includes anti-patterns (what NOT to do)
- D3 Playbooks: ≥ 3 (core task + failure recovery + quality polish)
- D4 Checklists: ≥ 4 (incl. readiness + quality)
- D5 Gates: ≥ 2 measurable gates (or one key gate + one support gate)
- D6 Cases: ≥ 10 (incl. borderline)
- D7 Rubric: rubric with 3–5 axes and pass thresholds
- D8 Sources: required if knowledge derived from external material
- D9 Regression: ≥ 1 regression check scenario

### L3 — PRO (target for “super pro”)
- D1 Skill Tree: deep (leaf skills with observable outcomes)
- D2 Principles: strong constraints + anti-pattern library
- D3 Playbooks: ≥ 6 (incl. diagnosis, rework strategy, escalation handling)
- D4 Checklists: ≥ 6 (incl. compliance, quality, and drift prevention)
- D5 Gates: ≥ 3 measurable gates (at least 1 KEY gate candidate)
- D6 Cases: ≥ 25 (good/bad/borderline balanced)
- D7 Rubric: anchored rubric (examples for scores 3/6/8/10)
- D8 Sources: mandatory provenance discipline where claims exist
- D9 Regression/Calibration:
  - exemplar set for key gate(s)
  - scoring consistency check recommended

### L4 — MASTER
- D1 Skill Tree: deep + strategy layer (when to choose which method)
- D2 Principles: includes system-level constraints and safety boundaries
- D3 Playbooks: ≥ 10 (incl. novel-case handling and creation flow)
- D4 Checklists: ≥ 8 (incl. audit and certification readiness)
- D5 Gates: ≥ 5 (with calibration; key gate replacement/versioning discipline)
- D6 Cases: ≥ 50 (incl. rare/edge cases)
- D7 Rubric: fully calibrated rubric across multiple evaluators
- D8 Sources: maintained and refreshed (refresh discipline)
- D9 Regression/Calibration:
  - formal regression suite
  - periodic recalibration protocol

---

## 3) PASS CRITERIA (PER LEVEL)
PASS L1:
- all L1 minimums satisfied

PASS L2:
- all L2 minimums satisfied
- at least one gate has examples

PASS L3:
- all L3 minimums satisfied
- at least one key-gate candidate has exemplar set (good/bad/borderline)
- rubric has anchored examples

PASS L4:
- all L4 minimums satisfied
- regression + calibration protocols exist and are used

If a pack is used for certification:
- it must be at least L3.

---

## 4) QUICK ASSESSMENT TEMPLATE (COPY)
SPC_PROFICIENCY_ASSESSMENT:
- DATE: YYYY-MM-DD
- SPC_PACK_UID:
- TARGET_LEVEL: L1/L2/L3/L4
- D1 Skill Tree: PASS/REWORK/FAIL
- D2 Principles: PASS/REWORK/FAIL
- D3 Playbooks: PASS/REWORK/FAIL
- D4 Checklists: PASS/REWORK/FAIL
- D5 Gates: PASS/REWORK/FAIL
- D6 Cases: PASS/REWORK/FAIL
- D7 Rubric: PASS/REWORK/FAIL
- D8 Sources: PASS/REWORK/FAIL (if required)
- D9 Regression/Calibration: PASS/REWORK/FAIL (as required)
- RESULT: PASS/REWORK/FAIL
- NEXT_ACTIONS:
  - <action>

---

## 5) HARD FAIL CONDITIONS
FAIL IF:
- SPC pack claims “pro” without gates + case library + rubric anchors
- key gate used without exemplar calibration
- external knowledge claims are present with no provenance discipline
- levels are marked PASS without evidence artifacts existing

---

## 6) RELATED (UID-ONLY)
XREF:
- UE.KB.RULE.ENTITIES.001 | WHY: entity pack minimum requirements
- UE.KB.STD.QA_RUBRIC.096 | WHY: rubric standard used for scoring
- UE.KB.PROC.QA_SCORE_CONSIST.098 | WHY: scoring consistency for L4 calibration
- UE.KB.POL.GATE_LIBRARY.092 | WHY: key gate discipline
- UE.KB.RULE.GATE_EXAMPLE_BIND.090 | WHY: exemplar sets for key gates

--- END.
