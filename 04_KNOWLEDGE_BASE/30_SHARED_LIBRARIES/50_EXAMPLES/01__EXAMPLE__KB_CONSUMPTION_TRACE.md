# EXAMPLE — KB CONSUMPTION TRACE (CANON)

FILE: 04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/50_EXAMPLES/01__EXAMPLE__KB_CONSUMPTION_TRACE.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 04_KNOWLEDGE_BASE
REALM: 30_SHARED_LIBRARIES/50_EXAMPLES
DOC_TYPE: EXAMPLE (KB)
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.EXAMPLE.CONSUMPTION_TRACE.001
OWNER: SYSTEM
ROLE: Canon example of how a runtime output must record KB usage (KB_SOURCES_USED + KB_GATES_APPLIED + provenance), so future KB creation and pipeline runs remain auditable and repeatable.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: CREATE
- SUMMARY: "Created exemplar trace format for KB-consuming outputs."
- REASON: "Without an exemplar, different outputs record KB usage inconsistently."
- IMPACT: "Trace becomes consistent; audits and regressions become possible."
- CHANGE_ID: UE.CHG.2026-01-20.KB.EXAMPLE.TRACE.001

---

## 0) WHAT THIS EXAMPLE SHOWS
This example shows the minimum evidence blocks required when:
- A pipeline is KB-consuming (TRUE/CONDITIONAL)
- A gate depends on KB scopes/modules
- Output includes any non-user content (provenance required)

---

## 1) EXAMPLE CONTEXT (SIMULATED)
PIPELINE_ID: UE.PIPE.MUSIC.POET_PACK.105  
KB_CONSUMPTION: TRUE  
INPUTS:
- KB_SCOPE_RAW: (one or more RAW links to corpus source scope)
- TASK: build poet pack for a track

---

## 2) REQUIRED EVIDENCE BLOCKS (COPY THIS PATTERN)

### KB_SCOPE_USED
- KB_SCOPE_RAW:
  - <RAW_LINK_1>
  - <RAW_LINK_2>

### KB_SOURCES_USED
- KB_SOURCE_RAW:
  - <RAW_LINK_TO_SOURCE_RECORD_OR_LIBRARY_ITEM>
- SOURCE_STATUS: PD_CONFIRMED | LICENSE_CONFIRMED
- SOURCE_NOTE: <short note>
- FULL_TEXT_ALLOWED: YES|NO

### KB_MODULES_LOADED
- <RAW_LINK_TO_MODULE_A> (state: VERIFIED)
- <RAW_LINK_TO_MODULE_B> (state: VERIFIED)

### KB_GATES_APPLIED
- Gate: <RAW_LINK_TO_GATE>
  - Result: PASS|FAIL
  - Notes: <short>
- Gate: <RAW_LINK_TO_GATE>
  - Result: PASS|FAIL
  - Notes: <short>

### OUTPUT_PROVENANCE (ONLY IF EXTERNAL CONTENT USED)
- Provenance required: YES
- Included markers:
  - KB_SOURCE_RAW
  - SOURCE_STATUS
  - SOURCE_NOTE
  - FULL_TEXT_ALLOWED

### TRACE_SUMMARY
- What was decided:
- What was blocked:
- What must be fixed next:

---

## 3) FAILURE EXAMPLE (STOP CONDITIONS)
If KB_SCOPE_RAW is missing when required:
- STOP: input absent

If provenance markers cannot be confirmed:
- STOP: marker not confirmed

If a needed RAW link is missing:
- STOP: RAW missing

---

END.
