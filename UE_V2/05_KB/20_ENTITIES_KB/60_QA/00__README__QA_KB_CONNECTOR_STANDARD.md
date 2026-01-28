# QA — KB CONNECTOR STANDARD (CANON)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/60_QA/00__README__QA_KB_CONNECTOR_STANDARD.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 60_QA
DOC_TYPE: KB_MODULE
KB_TYPE: STANDARD
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.QA.STD.CONNECTOR.001
OWNER: SYSTEM
ROLE: Canonical connector standard for Quality (QA) entities: deterministic KB loading, gate/rubric usage, exemplar calibration, regression guards, scoring consistency, and how QA produces auditable PASS/REWORK/FAIL outcomes.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created QA connector standard: gates + rubrics + exemplars + regression discipline + scoring consistency and trace."
- REASON: "QA must be stable and repeatable; without a connector standard, scoring drifts and releases become subjective."
- IMPACT: "More reliable QA, fewer regressions, and audit-compatible quality decisions."
- CHANGE_ID: UE.CHG.2026-01-14.KB.QA.STD.001

---

## 0) PURPOSE (KB)
QA exists to:
- decide PASS / REWORK / FAIL using explicit criteria
- maintain stable evaluation over time (prevent drift)
- maintain regression guards (prevent quality backslides)
- calibrate scoring using exemplars and protocols

QA is not “taste”. QA is a controlled evaluation system.

---

## 1) SCOPE (BOUNDARY)
COVERS:
- how QA uses KB deterministically
- how QA applies gates and rubrics
- exemplar calibration and scoring consistency
- regression guard design
- QA pack structure

EXCLUDES:
- authoring domain craft topics (belongs to `10_TOPICS`)
- governance law authoring (belongs to `00_KB_GOVERNANCE`)
- validation of rules compliance as “legal” (that is VAL domain); QA focuses on quality outcomes, but uses explicit criteria.

---

## 2) ABSOLUTE RULES (QA LAW)
R1 — Explicit criteria only
- QA decisions must be anchored to:
  - gate definitions (preferred), OR
  - checklists with pass/rework/fail, OR
  - rubric scoring with anchored examples
- No criteria → STOP or GAP.

R2 — UID-only authority
- All operational references are UID-only.
- Navigation via KB master index only.

R3 — Calibration required for key gates
- Any KEY gate used repeatedly or for certification must have:
  - exemplar set (GOOD/BAD/BORDERLINE)
  - consistency protocol where applicable

R4 — Regression guard for high impact
- Changes to gates/rubrics or core packs require regression checks.

R5 — Trace discipline
- QA outputs must include run trace and criteria list.

---

## 3) REQUIRED LOAD SET (MINIMAL)
QA runs must load (or have in memory):
- KB governance minimum set
- relevant gates/checklists/rubrics (criteria set)
- exemplar sets for key gates when evaluating borderline cases
- reference glossaries when term ambiguity exists

Do NOT load unrelated topic realms.

---

## 4) QA EXECUTION FLOW (DETERMINISTIC)
Step 1: Define target and context
- TARGET_OUTPUT (what is being evaluated)
- DOMAIN (visual/sound/narrative/etc.)
- CONTEXT (platform, format, constraints if relevant)

Step 2: Select criteria set (minimal)
- Gate UIDs (preferred)
- Checklist UIDs (support)
- Rubric UID (if scoring is needed)

Step 3: Evaluate
- Apply each gate/checklist deterministically
- If rubric used:
  - score axes + compute outcome rule

Step 4: Use exemplars when uncertain
- If borderline or disagreement:
  - compare to GOOD/BAD/BORDERLINE exemplars
  - if still inconsistent → run scoring consistency protocol

Step 5: Emit outcome
- PASS / REWORK / FAIL
- top fixes and recheck instructions

Step 6: Trace
- criteria UIDs used
- exemplar usage flag
- memory reuse flag
- status used (active_only/mixed)

---

## 5) QA OUTPUT RECORD (COPY)
QA_RESULT_RECORD:
- QA_UID: QA-YYYYMMDD-001
- DATE: YYYY-MM-DD
- TARGET_OUTPUT_ID:
- DOMAIN:
- CRITERIA_SET (UID-ONLY):
  - GATES:
    - <uid>
  - CHECKLISTS:
    - <uid>
  - RUBRIC:
    - <uid>
- EXEMPLARS_USED: YES/NO
- SCORES (if rubric):
  - AXIS: <score>
- RESULT: PASS/REWORK/FAIL
- TOP_ISSUES:
  - <issue>
- TOP_FIXES:
  - <fix>
- RECHECK_METHOD:
  - which gates/checklists to re-run
- RUN_TRACE:
  - KB_SOURCES (UID-ONLY):
    - <uid>
  - MEMORY_REUSE: YES/NO
  - STATUS_USED: ACTIVE_ONLY/MIXED
  - WEB_LOOKUP_USED: YES/NO

---

## 6) SCORING CONSISTENCY (ANTI-DRIFT)
When multiple evaluators/entities score the same output:
- run the scoring consistency protocol
- record mismatch rate and remediation

Rule:
- if key gate disagreement exists → FAIL (process failure) until calibrated.

---

## 7) REGRESSION GUARD DISCIPLINE
Regression guard must exist for:
- key gate updates
- rubric updates
- core pack updates affecting output quality

Minimum regression guard:
- a small fixed test set (5–10 cases)
- expected outcomes
- periodic re-run after changes

---

## 8) QA PACK STRUCTURE (CANON)
A QA pack is a folder with at least:

QA_PACK_ROOT:
- 00__PACK_PASSPORT.md
- 01__QA_SCOPE.md
- 02__GATE_LIBRARY.md (criteria UIDs + why)
- 03__RUBRIC_LIBRARY.md
- 04__EXEMPLAR_SETS/
  - 01__EXEMPLARS__GOOD.md
  - 02__EXEMPLARS__BAD.md
  - 03__EXEMPLARS__BORDERLINE.md
- 05__REGRESSION_GUARD.md
- 06__SCORING_CONSISTENCY.md
- 07__REPORT_TEMPLATES.md
- 08__TOPIC_BINDINGS.md (UID-only)

Notes:
- QA pack binds primarily to gates/checklists/rubrics and exemplar sets.
- Domain topics are referenced only when needed to interpret quality dimensions.

---

## 9) COMMON FAIL MODES (QA) (AND FIXES)
F1 — Subjective “vibes” scoring
- Fix: require explicit gate/rubric anchors; use exemplars

F2 — Drift over time
- Fix: periodic scoring consistency checks; refresh exemplars

F3 — No regression guard
- Fix: create fixed test set and expected outcomes

F4 — Overloading criteria
- Fix: minimal criteria set; focus on key gates

---

## 10) HARD FAIL CONDITIONS
FAIL IF:
- QA outcome is produced without explicit criteria UIDs
- key gate used without exemplars (when key)
- scoring consistency disagreement ignored
- regression guard missing after high impact changes
- URL/PATH used as authority inside operational records

---

## 11) RELATED (UID-ONLY)
XREF:
- UE.KB.RULES.GOV.001 | WHY: KB governance rules
- UE.KB.STD.GATE_DEF.088 | WHY: gate definition standard
- UE.KB.STD.QA_RUBRIC.096 | WHY: rubric standard
- UE.KB.TPL.QA_RUBRIC_CARD.097 | WHY: rubric card template
- UE.KB.PROC.QA_SCORE_CONSIST.098 | WHY: scoring consistency protocol
- UE.KB.TPL.QA_SCORE_REPORT.099 | WHY: score report template
- UE.KB.POL.GATE_LIBRARY.092 | WHY: key gate discipline

--- END.
