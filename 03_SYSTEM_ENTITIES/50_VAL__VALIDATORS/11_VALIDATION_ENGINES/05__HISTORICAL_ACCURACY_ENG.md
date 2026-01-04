# 🏺 HISTORICAL ACCURACY ENGINE
## Canonical Engine Specification  
**LEVEL: L4 · VALIDATION ENGINE · ERA + ANACHRONISM GATES · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 05__HISTORICAL_ACCURACY_ENG.md
- ENGINE_ID: L4-VAL-HISTORICAL-ACCURACY-ENGINE-005
- UID: UE.ENT.ENG.VAL.HISTORICAL_ACCURACY
- NAME: Historical Accuracy Engine
- CLASS: Validation Engine
- LEVEL: L4
- STATUS: FINAL
- FAILURE_MODE: fail-closed (era coherence)
- EDITABLE: true

### ABSOLUTE RULE
> If the era rules are broken without intent, the world collapses.

---

## 1. PURPOSE

Historical Accuracy Engine validates whether an artifact is consistent with:
- declared time period / era constraints
- declared geography constraints (if provided)
- known historical baseline (if artifact claims real history)
- canon history (if artifact is inside a fictional universe)

It detects:
- anachronisms (objects/terms/tech/social rules that do not fit the era)
- timeline inconsistencies
- calendar/date contradictions (if dates used)
- false precision (claims with dates/figures without evidence, if policy requires)

It produces:
- `VALIDATION_VERDICT` + repair plan + recheck gates.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Validate consistency with declared `time_period_ref`
- Detect anachronistic objects, language, customs, institutions
- Validate chronology inside artifact (event order, ages, durations)
- Validate compatibility with canon timeline (if fictional with canon locks)
- Enforce evidence requirements for real-history claims (if policy requires)

### OUT-OF-SCOPE (FORBIDDEN)
- Scientific plausibility (Scientific Plausibility Engine)
- Cultural sensitivity framing (Cultural Accuracy Engine)
- Governance decisions about canon changes
- Proving real-world history without provided sources (it flags, not proves)

---

## 3. INPUT / OUTPUT

### 3.1 INPUT — HISTORICAL_VALIDATION_REQUEST
Required fields:
- `hv_req_id`
- `timestamp`
- `artifact_ref`
- `artifact_type`
- `artifact_payload`
- `time_period_ref` (required)
- `geo_scope_ref` (optional)
- `canon_timeline_refs` (optional)
- `evidence_policy_ref` (optional)
- `trace_id` (optional)

Missing time_period_ref → INVALID (CRITICAL).

### 3.2 OUTPUT — VALIDATION_VERDICT
(uses realm README canonical schema)

---

## 4. TIME PERIOD PROFILE (REQUIRED)

### 4.1 TIME_PERIOD_PROFILE (required fields)
- `period_id`
- `label` (e.g., “Late Bronze Age”, “Europe 1914–1918”, “Fictional Era A”)
- `start_year` (optional)
- `end_year` (optional)
- `region_scope` (optional)
- `canon_lock` (bool; optional)
- `allowed_tech_level` (optional)
- `notes`

Hard rule:
- if period_id is missing or empty → INVALID (CRITICAL).

---

## 5. ANACHRONISM GATES (HARD)

### 5.1 ANACHRONISM TYPES
- **TECH anachronism:** tech exists before it should
- **LANGUAGE anachronism:** terms/slang that belong to other era
- **INSTITUTION anachronism:** organizations/laws not yet possible
- **MATERIAL CULTURE anachronism:** clothing, tools, architecture mismatch
- **SOCIAL RULE anachronism:** norms/roles out of era without explanation

### 5.2 INTENT OVERRIDE RULE
Anachronism can be allowed only if explicitly tagged as:
- `INTENTIONAL_ANACHRONISM: true`
and accompanied by:
- reason
- scope (which elements)
- containment (does not leak into baseline facts)

Without explicit tag → HIGH/CRITICAL.

---

## 6. CHRONOLOGY CONSISTENCY

### 6.1 INTERNAL TIMELINE CHECKS
- event order must respect causality
- durations must be possible (travel/time)
- character age and time jumps must reconcile
- dates must be consistent if explicit calendar used

Timeline contradiction:
- HIGH severity.
Multiple contradictions:
- CRITICAL if it affects core plot/canon.

---

## 7. GEO-SCOPE COHERENCE (OPTIONAL)

If geo_scope_ref is provided:
- validate that referenced places/institutions match region
- detect “region mashup” without explanation

Violation:
- MEDIUM/HIGH depending on prominence.

---

## 8. REAL HISTORY VS FICTION MODE

### 8.1 MODE DECLARATION
Artifact may declare:
- `HISTORY_MODE: REAL | FICTIONAL | ALT_HISTORY`

Default:
- FICTIONAL unless explicitly claiming real history.

### 8.2 RULES BY MODE
- REAL:
  - claims should align with baseline knowledge
  - strong claims should carry evidence if policy requires
- FICTIONAL:
  - must align with canon timeline locks
- ALT_HISTORY:
  - divergence point must be declared
  - post-divergence facts can differ but must be internally consistent

Missing divergence point in ALT_HISTORY:
- HIGH.

---

## 9. EVIDENCE GATES (OPTIONAL)

If evidence_policy_ref is present, enforce:
- dated claims require evidence refs
- numeric precision requires evidence refs
- “everyone knows” claims are forbidden in canonical docs

Missing evidence for required claims:
- HIGH/CRITICAL depending on artifact usage.

---

## 10. SEVERITY & VERDICT RULES

- Missing time_period_ref → INVALID (CRITICAL)
- Unintentional anachronism in core element → HIGH/CRITICAL
- Timeline contradiction on core events → HIGH/CRITICAL
- Minor anachronism (background) → MEDIUM
- Region mismatch without intent → MEDIUM/HIGH
- ALT_HISTORY without divergence point → HIGH

Verdict:
- any CRITICAL → INVALID
- multiple HIGH → INVALID/PARTIAL depending on fix locality
- only MEDIUM/LOW → PARTIAL/VALID

---

## 11. OUTPUT: ISSUES + REPAIR PLAN

### 11.1 ISSUE ITEM (historical)
- `issue_id`
- `type` = ANACHRONISM | TIMELINE_CONTRADICTION | DATE_CONFLICT | GEO_SCOPE_MISMATCH | MODE_MISSING | DIVERGENCE_MISSING | EVIDENCE_MISSING
- `location_ref`
- `description`
- `severity`
- `fix`

### 11.2 REPAIR ACTION TYPES
- `DECLARE_TIME_PERIOD_PROFILE`
- `TAG_INTENTIONAL_ANACHRONISM`
- `REPLACE_OBJECT_WITH_ERA_CORRECT`
- `REWRITE_SCENE_TO_MATCH_TECH_LEVEL`
- `FIX_EVENT_ORDER`
- `ADD_DIVERGENCE_POINT`
- `ADD_EVIDENCE_REFS`

Hard rule:
- repairs must specify exact replacement or exact tag + reason.

---

## 12. CORE OPERATIONS

- OP_01: INGEST_ARTIFACT_AND_TIME_PROFILE
- OP_02: DETECT_HISTORY_MODE (real/fiction/alt)
- OP_03: EXTRACT_ERA-SENSITIVE_MARKERS (tech/terms/institutions)
- OP_04: RUN_ANACHRONISM_CHECKS
- OP_05: RUN_INTERNAL_TIMELINE_CHECKS
- OP_06: RUN_GEO_SCOPE_CHECKS (if provided)
- OP_07: APPLY_CANON_TIMELINE_LOCKS (if provided)
- OP_08: APPLY_EVIDENCE_GATES (if policy provided)
- OP_09: BUILD_ISSUES_LIST
- OP_10: ASSIGN_SEVERITY_AND_VERDICT
- OP_11: BUILD_REPAIR_PLAN
- OP_12: EMIT_VALIDATION_VERDICT

---

## 13. FAILURE CONDITIONS (ENGINE)

CRITICAL:
- time_period_ref missing
- artifact too unstructured to extract markers
- mode is REAL but no baseline/evidence policy and artifact used for canonical truth claims

Reaction:
- verdict INVALID (CRITICAL)
- request time profile and/or evidence policy

---

## 14. NON-GOALS
- Does not replace research
- Does not claim certainty without sources
- Does not decide canon changes
- Does not validate scientific plausibility

---

## 15. FINAL STATEMENT

History is constraint.
Constraint is believability.
If you break it — declare it, contain it, and own the divergence.

---

**STATUS:** Historical Accuracy Engine v1.0  
**REALM:** ACTIVE
