# VAL — KB CONNECTOR STANDARD (CANON)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/50_VAL/00__README__VAL_KB_CONNECTOR_STANDARD.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 50_VAL
DOC_TYPE: KB_MODULE
KB_TYPE: STANDARD
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.VAL.STD.CONNECTOR.001
OWNER: SYSTEM
ROLE: Canonical connector standard for Validator entities: what validators must do, how they load and apply KB deterministically, how they produce violations, and how validation packs are structured (UID-only, no-fantasy, evidence-based).

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created VAL connector standard: deterministic KB loading, validation workflow, violation record schema, and pack structure."
- REASON: "Validators must be consistent and evidence-driven; a connector standard prevents subjective or invented validation."
- IMPACT: "More reliable PASS/REWORK/FAIL decisions and consistent violation reporting."
- CHANGE_ID: UE.CHG.2026-01-14.KB.VAL.STD.001

---

## 0) PURPOSE (KB)
A Validator (VAL) exists to:
- check compliance against explicit standards/gates/rules
- detect violations deterministically
- output actionable violation records (what failed + why + how to fix)
- prevent “opinion-only” validation

VAL does not invent criteria. It applies registered criteria.

---

## 1) SCOPE (BOUNDARY)
COVERS:
- KB usage rules for validators
- minimal load set for validation
- violation reporting schema
- validation pack layout

EXCLUDES:
- authoring domain craft topics (belongs to `10_TOPICS`)
- governance law authoring (belongs to `00_KB_GOVERNANCE`)
- “creative taste” judging without measurable criteria

---

## 2) ABSOLUTE RULES (VAL LAW)
R1 — Criteria must be explicit
- A validator may only validate against:
  - RULE / POLICY / STANDARD modules, OR
  - defined GATE criteria, OR
  - CHECKLIST criteria producing PASS/REWORK/FAIL
- If criteria are missing → STOP or GAP, not guessing.

R2 — UID-only authority
- All operational references are UID-only (XREF).
- Navigation via KB master index only.

R3 — Evidence-first
- Every violation must cite:
  - which criterion failed (UID)
  - what evidence in the output triggered failure (short)
  - fix guidance (actionable)

R4 — No-fantasy validation
- Never claim a rule exists unless opened/known from KB.
- If uncertain: mark “UNKNOWN” and request ingestion.

---

## 3) REQUIRED LOAD SET (MINIMAL)
VAL runs must load (or have in memory):
- KB governance minimum set
- relevant gate/standard/checklist modules being validated against
- relevant reference glossaries when terminology ambiguity exists

Do NOT load:
- unrelated domain topics
- “everything just in case”

---

## 4) VAL EXECUTION FLOW (DETERMINISTIC)
Step 1: Define target
- TARGET_OUTPUT: what is being validated (shotlist, scene, lyrics, etc.)
- TARGET_DOMAIN: narrative/visual/sound/…

Step 2: Select criteria set
- Pick the minimal set of criteria UIDs (gates/standards/checklists).
- If none exist → STOP or GAP.

Step 3: Run checks
- Apply each criterion deterministically.
- Record PASS/REWORK/FAIL per criterion.

Step 4: Emit violations (if any)
- Create violation records for FAIL and optionally REWORK.

Step 5: Provide remediation plan
- Top 1–3 fixes that would most likely make criteria pass.

Step 6: Trace
- Provide run trace:
  - KB_SOURCES (UIDs used)
  - MEMORY_REUSE flag
  - STATUS_USED (ACTIVE_ONLY/MIXED)

---

## 5) VIOLATION RECORD STANDARD (COPY)
VAL_VIOLATION:
- VIOLATION_UID: VAL-YYYYMMDD-001
- DATE: YYYY-MM-DD
- TARGET_OUTPUT_ID:
- DOMAIN:
- SEVERITY: MINOR | MAJOR | CRITICAL
- CRITERION_UID (FAILED):
  - <uid>
- WHAT FAILED (symptom):
- EVIDENCE (short, observable):
- WHY IT MATTERS:
- FIX (actionable):
- RECHECK:
  - how to verify the fix passes
- RELATED_UIDS (UID-ONLY):
  - <uid> | WHY

Severity guidance:
- CRITICAL: fails a core gate; output is unusable without fix
- MAJOR: strongly degrades quality/clarity/compliance
- MINOR: polish-level issues

---

## 6) VALIDATOR PACK STRUCTURE (CANON)
A VAL pack is a folder with at least:

VAL_PACK_ROOT:
- 00__PACK_PASSPORT.md
- 01__VALIDATION_SCOPE.md
- 02__CRITERIA_LIBRARY.md
- 03__VIOLATION_TEMPLATES.md
- 04__CHECK_PROCEDURES.md
- 05__EXAMPLE_VIOLATIONS/
  - 01__EXAMPLE__GOOD.md
  - 02__EXAMPLE__BAD.md
  - 03__EXAMPLE__BORDERLINE.md
- 06__REGRESSION_GUARD.md
- 07__TOPIC_BINDINGS.md (UID-only; reference glossaries mostly)

Notes:
- VAL pack primarily binds to:
  - standards, gates, checklists
  - reference glossaries for terminology

---

## 7) COMMON FAIL MODES (VAL) (AND FIXES)
F1 — Opinion-only validation
- Fix: require criterion UID; no UID → no claim

F2 — Over-validation (too many criteria)
- Fix: minimal criteria set; validate only what matters for the task

F3 — Vague violations (“bad quality”)
- Fix: include observable evidence + actionable fix + recheck method

F4 — Terminology confusion
- Fix: load reference glossary; define term usage

---

## 8) HARD FAIL CONDITIONS
FAIL IF:
- validator invents criteria
- violations omit criterion UID or evidence
- URL/PATH used as authority in operational references
- validator validates against “taste” without measurable criteria
- missing criteria but validator proceeds anyway

---

## 9) RELATED (UID-ONLY)
XREF:
- UE.KB.RULES.GOV.001 | WHY: KB governance rules (no-fantasy, trace, nav)
- UE.KB.RULE.ENTITIES.001 | WHY: entity pack boundaries and minimums
- UE.KB.MAP.ENTITY_TO_SCOPE.002 | WHY: minimal loading map
- UE.KB.STD.GATE_DEF.088 | WHY: gate definition pattern used as criteria
- UE.KB.TPL.QA_RUBRIC_CARD.097 | WHY: compact scoring format (optional in VAL)
- UE.KB.TPL.QA_SCORE_REPORT.099 | WHY: consistency reporting format (optional)

--- END.
