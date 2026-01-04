# 🧯 ERROR DETECTION ENGINE
## Canonical Engine Specification  
**LEVEL: L4 · VALIDATION ENGINE · FORMAL ERRORS · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 01__ERROR_DETECTION_ENG.md
- ENGINE_ID: L4-VAL-ERROR-DETECTION-ENGINE-001
- UID: UE.ENT.ENG.VAL.ERROR_DETECTION
- NAME: Error Detection Engine
- CLASS: Validation Engine
- LEVEL: L4
- STATUS: FINAL
- FAILURE_MODE: fail-closed
- EDITABLE: true

### ABSOLUTE RULE
> If required structure is broken — downstream truth is impossible.

---

## 1. PURPOSE

Error Detection Engine validates **formal correctness** of artifacts:
- missing required fields
- invalid naming / numbering
- broken references
- invalid formats (IDs, timestamps, enums)
- structural contradictions (e.g., “READ_ONLY: true” + “EDITABLE: true”)
- template compliance (does it match canonical engine/spec format)

It produces:
- `VALIDATION_VERDICT` with repair plan
- standardized error map for other validators

This engine is the first gate: **structure before meaning**.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Validate required sections exist
- Validate required fields exist
- Validate field types and enums
- Validate ID patterns and UID patterns
- Validate file naming conventions and numbering
- Validate references (links, file refs, spec refs) are present and well-formed
- Detect internal formal contradictions
- Emit repair instructions (exact)

### OUT-OF-SCOPE (FORBIDDEN)
- Judging facts (Fact Consistency Engine does)
- Language quality beyond structural rules (Language Engine does)
- Cultural/historical/scientific plausibility (other engines)
- Creating new content beyond repair instructions

---

## 3. INPUT / OUTPUT

### 3.1 INPUT — ARTIFACT_TO_VALIDATE
Required fields:
- `artifact_ref` (file path or object id)
- `artifact_type` (ENGINE_SPEC / INDEX / TEMPLATE / MODEL / OUTPUT / OTHER)
- `artifact_payload` (the content or structured fields)
- `constraints_refs` (optional)
- `trace_id` (optional)

Missing required fields → INVALID (CRITICAL).

### 3.2 OUTPUT — VALIDATION_VERDICT
(uses realm README canonical schema)

---

## 4. REQUIRED CHECK SET (DEFAULT)

Error Detection Engine runs these checks unless overridden:

### 4.1 FILE + NAME CHECKS
- file name follows realm naming rule
- numbering matches index position (if index ref provided)
- README uses 00 prefix
- engine files use NN__ pattern

### 4.2 HEADER CHECKS (ENGINE SPEC)
Required:
- `ENGINE_FILE`
- `ENGINE_ID`
- `UID`
- `NAME`
- `CLASS`
- `LEVEL`
- `STATUS`
- `FAILURE_MODE`
- `EDITABLE`

### 4.3 SECTION CHECKS
Required sections (by type):
- ENGINE_SPEC: 0..Final Statement + required blocks declared by template
- INDEX: status, purpose, map, final rule
- TEMPLATE: required fields + usage notes

### 4.4 FIELD TYPE CHECKS
- boolean fields are boolean-like (true/false)
- enums are within allowed sets
- lists are lists (not ambiguous prose)
- IDs follow pattern rules

### 4.5 INTERNAL CONTRADICTION CHECKS
Examples:
- `READ_ONLY: true` and `EDITABLE: true`
- `STATUS: FINAL` and “planned” markers
- `FAILURE_MODE: fail-closed` but “continue anyway” rule exists

### 4.6 REFERENCE WELL-FORMEDNESS CHECKS
- URLs are syntactically valid
- raw github links follow correct raw pattern (if used)
- file refs follow registry path conventions (if used)
- spec refs not empty placeholders

---

## 5. PATTERN RULES (CANONICAL)

### 5.1 ENGINE_ID (recommended format)
`L<level>-<class>-<engine_name>-<nnn>`
Example:
- `L4-VAL-ERROR-DETECTION-ENGINE-001`

### 5.2 UID (recommended format)
`UE.ENT.ENG.<LAYER>.<NAME>`
Example:
- `UE.ENT.ENG.VAL.ERROR_DETECTION`

### 5.3 VERDICT ENUM
VALID | PARTIAL | INVALID

### 5.4 SEVERITY ENUM
LOW | MEDIUM | HIGH | CRITICAL

Hard rule:
- missing required field → CRITICAL.

---

## 6. CHECKLISTS BY ARTIFACT TYPE

### 6.1 ENGINE_SPEC CHECKLIST
- file name OK
- engine id exists + pattern OK
- UID exists + non-empty
- level/class consistent
- failure mode present
- absolute rule exists
- required sections exist
- required artifact schemas exist
- operations list exists
- failure conditions exist
- final statement exists
- status marker exists

### 6.2 INDEX CHECKLIST
- index id/version/state exist
- purpose exists
- numbering rules exist (if applicable)
- map exists
- links exist or file refs exist
- final rule exists
- status line exists

### 6.3 TEMPLATE CHECKLIST
- required fields listed
- fail rules defined
- usage notes present
- minimal example present (optional but recommended)

---

## 7. OUTPUT: ERROR MAP FORMAT

### 7.1 ERROR_MAP (optional but recommended)
- `missing_fields` (list)
- `invalid_enums` (list)
- `format_errors` (list)
- `broken_refs` (list)
- `contradictions` (list)
- `naming_numbering_errors` (list)

Each entry:
- `location_ref`
- `description`
- `fix`

---

## 8. SEVERITY RULES (FORMAL)

- Missing required field → CRITICAL
- Invalid enum / invalid ID format → HIGH
- Broken reference (required) → HIGH/CRITICAL depending on type
- Numbering mismatch → HIGH
- Minor formatting issue (spacing) → LOW

Hard rule:
> If CRITICAL exists → verdict cannot be VALID.

---

## 9. REPAIR PLAN RULES

Repair plan must be:
- explicit: “Add field X to section Y”
- local: avoid broad rewrites unless necessary
- ordered: list fixes in dependency order
- re-check gates: specify which checks must rerun

No repair plan → INVALID (CRITICAL).

---

## 10. CORE OPERATIONS

- OP_01: INGEST_ARTIFACT
- OP_02: DETECT_ARTIFACT_TYPE
- OP_03: RUN_FILE_NAMING_CHECKS
- OP_04: RUN_REQUIRED_SECTION_CHECKS
- OP_05: RUN_REQUIRED_FIELD_CHECKS
- OP_06: RUN_FIELD_TYPE_ENUM_CHECKS
- OP_07: RUN_INTERNAL_CONTRADICTION_CHECKS
- OP_08: RUN_REFERENCE_WELLFORMED_CHECKS
- OP_09: BUILD_ERROR_MAP
- OP_10: ASSIGN_SEVERITY_AND_VERDICT
- OP_11: BUILD_REPAIR_PLAN
- OP_12: EMIT_VALIDATION_VERDICT

---

## 11. FAILURE CONDITIONS (ENGINE)

CRITICAL:
- engine cannot parse artifact
- artifact type undefined and cannot be inferred
- validation verdict cannot be produced

Reaction:
- verdict INVALID (CRITICAL)
- request structured payload or specify artifact type

---

## 12. NON-GOALS
- Does not judge truth of statements
- Does not improve prose style
- Does not rewrite content fully
- Does not resolve governance conflicts (it only flags)

---

## 13. FINAL STATEMENT

Structure is the gateway to truth.
If structure fails — nothing downstream can be trusted.

---

**STATUS:** Error Detection Engine v1.0  
**REALM:** ACTIVE
