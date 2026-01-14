# TEMPLATE — ENG PACK STRUCTURE (COPY) (CANON)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/20_ENG/01__TEMPLATE__ENG_PACK_STRUCTURE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 20_ENG
DOC_TYPE: KB_MODULE
KB_TYPE: TEMPLATE
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.ENG.TPL.PACK.002
OWNER: SYSTEM
ROLE: Copy-paste template for creating an Engine (ENG) competence pack: canonical folder/file layout + minimal required headers/fields for method, parameters, edge cases, examples, gates, regression guard, and UID-only bindings.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created ENG pack template: layout + minimal executable skeleton for deterministic engine behavior."
- REASON: "Engines must be reproducible and testable; template prevents missing IO, parameters, gates, and examples."
- IMPACT: "Faster engine pack creation and less behavior drift."
- CHANGE_ID: UE.CHG.2026-01-14.KB.ENG.TPL.002

---

## 0) HOW TO USE
- Copy this template when creating a new ENG pack folder.
- Keep file names exact.
- Replace placeholders.
- Bind to Topics via UID-only (do not duplicate domain topics inside pack).

---

## 1) PACK LAYOUT (CANON)
ENG_PACK_ROOT/
- 00__PACK_PASSPORT.md
- 01__ENGINE_SCOPE_AND_IO.md
- 02__METHOD_AND_PARAMETERS.md
- 03__EDGE_CASES_LIBRARY.md
- 04__OUTPUT_TEMPLATES.md
- 05__KB_GATES/
  - 00__README__GATES.md
  - 01__GATE__OUTPUT_QUALITY.md
  - 02__GATE__CONSISTENCY.md
- 06__EXAMPLES/
  - 00__README__EXAMPLES.md
  - 01__EXAMPLE__GOOD.md
  - 02__EXAMPLE__BAD.md
  - 03__EXAMPLE__BORDERLINE.md
- 07__REGRESSION_GUARD.md
- 08__KB_SOURCES.md
- 09__TOPIC_BINDINGS.md
- 10__XREF_BINDINGS.md

Notes:
- Expand examples and edge cases as needed.
- If some parts are not needed, keep the file but mark as EMPTY with reason.

---

## 2) FILE SKELETONS (COPY)

### 00__PACK_PASSPORT.md (COPY)
ENG_PACK_PASSPORT:
- PACK_UID:
- ENGINE_ENTITY_UID:
- ENGINE_NAME:
- DOMAIN:
- STATUS:
- LOCK:
- VERSION:
- PURPOSE:
- SCOPE:
  - COVERS:
  - EXCLUDES:
- PRIMARY_OUTPUTS:
- DEPENDENCIES (UID-ONLY):
  - <uid> | WHY
- CHANGE_NOTE:
  - DATE:
  - TYPE:
  - SUMMARY:
  - CHANGE_ID:

---

### 01__ENGINE_SCOPE_AND_IO.md (COPY)
ENGINE_SCOPE_AND_IO:
- PURPOSE:
- INPUTS:
  - REQUIRED:
  - OPTIONAL:
- OUTPUTS:
  - OUTPUT_SCHEMA:
- CONSTRAINTS:
- ASSUMPTIONS:
- HARD FAIL CONDITIONS:
- RELATED (UID-ONLY):
  - <uid> | WHY

---

### 02__METHOD_AND_PARAMETERS.md (COPY)
METHOD_AND_PARAMETERS:
- METHOD_STEPS (DETERMINISTIC):
  - 1)
  - 2)
  - 3)
- PARAMETERS (ENUM):
  - PARAM_NAME:
    - TYPE:
    - DEFAULT:
    - ALLOWED_RANGE:
    - EFFECT:
- COMMON FAILS + FIXES:
- SELF-CHECK (UID-ONLY):
  - <gate/checklist uid> | WHY

---

### 03__EDGE_CASES_LIBRARY.md (COPY)
EDGE_CASES_LIBRARY:
- EDGE_CASES:
  - EC-01:
    - CONDITION:
    - RISK:
    - HANDLING:
    - VALIDATION (UID-ONLY):
      - <uid> | WHY

---

### 04__OUTPUT_TEMPLATES.md (COPY)
OUTPUT_TEMPLATES:
- TEMPLATE LIST:
  - OUTPUT_TYPE:
    - TEMPLATE:
      - <fields>
    - REQUIRED_FIELDS:
    - OPTIONAL_FIELDS:
    - EXAMPLE LINK (UID-ONLY):
      - <uid> | WHY

---

## 05__KB_GATES/00__README__GATES.md (COPY)
GATES_README:
- PURPOSE:
- GATE LIST:
  - 01__GATE__OUTPUT_QUALITY.md
  - 02__GATE__CONSISTENCY.md

---

## 05__KB_GATES/01__GATE__OUTPUT_QUALITY.md (COPY)
GATE_OUTPUT_QUALITY:
- TARGET_OUTPUT:
- TEST_METHOD:
- PASS_CRITERIA:
- REWORK_CRITERIA:
- FAIL_CRITERIA:
- EXAMPLES:
  - PASS:
  - FAIL:
- RELATED_UIDS (UID-ONLY):
  - <uid> | WHY

---

## 05__KB_GATES/02__GATE__CONSISTENCY.md (COPY)
GATE_CONSISTENCY:
- TARGET:
- CHECKS:
- PASS/REWORK/FAIL:

---

## 06__EXAMPLES/00__README__EXAMPLES.md (COPY)
EXAMPLES_README:
- PURPOSE:
- EXAMPLE LIST:
- CALIBRATION LINKS (UID-ONLY):
  - <gate uid> | WHY

---

## 06__EXAMPLES/01__EXAMPLE__GOOD.md (COPY)
EXAMPLE_GOOD:
- EXAMPLE_ID:
- INPUT:
- OUTPUT (SUMMARY):
- WHY GOOD:
- PASSES (UID-ONLY):
  - <uid> | WHY

---

## 06__EXAMPLES/02__EXAMPLE__BAD.md (COPY)
EXAMPLE_BAD:
- EXAMPLE_ID:
- INPUT:
- OUTPUT (SUMMARY):
- WHY BAD:
- FAILS (UID-ONLY):
  - <uid> | WHY

---

## 06__EXAMPLES/03__EXAMPLE__BORDERLINE.md (COPY)
EXAMPLE_BORDERLINE:
- EXAMPLE_ID:
- INPUT:
- OUTPUT (SUMMARY):
- WHY BORDERLINE:
- DECISION:
- VALIDATED_BY (UID-ONLY):
  - <uid> | WHY

---

### 07__REGRESSION_GUARD.md (COPY)
REGRESSION_GUARD:
- WHAT MUST NOT REGRESS:
- FIXED TEST SET:
  - RG-01:
    - INPUT:
    - EXPECTED:
    - VALIDATED_BY (UID-ONLY):
      - <uid> | WHY
- UPDATE DISCIPLINE:
  - version bump rule
  - re-run gates

---

### 08__KB_SOURCES.md (COPY)
KB_SOURCES:
- SOURCE_RECORDS:
  - SOURCE_UID:
    - SOURCE_TYPE:
    - AUTHORITY_TIER:
    - DATE_ACCESSED:
    - SCOPE:
    - EXTRACTION_NOTES:
    - REFRESH_INTERVAL:
- NOTES:
  - Do not paste large text.
  - Extract operational principles only.

---

### 09__TOPIC_BINDINGS.md (COPY)
TOPIC_BINDINGS:
- REQUIRED TOPICS (UID-ONLY):
  - <uid> | WHY | WHEN TO LOAD
- OPTIONAL TOPICS (UID-ONLY):
  - <uid> | WHY | WHEN TO LOAD
- REFERENCE GLOSSARIES (UID-ONLY):
  - <uid> | WHY

---

### 10__XREF_BINDINGS.md (COPY)
XREF_BINDINGS:
- CALLED_BY_ORC (UID-ONLY):
  - <orc uid> | WHY
- SUPPORT_SPC (UID-ONLY):
  - <spc uid> | WHY
- VALIDATED_BY (UID-ONLY):
  - <val/qa uid> | WHY
- PIPELINE_MAPS (UID-ONLY):
  - <xref map uid> | WHY

---

## 3) STRICT RULES (REMINDER)
- Method + IO + parameters must be explicit.
- Every engine must have at least one gate + examples.
- UID-only linking discipline is mandatory.
- If missing knowledge or criteria → STOP/GAP (no fantasy execution).

--- END.
