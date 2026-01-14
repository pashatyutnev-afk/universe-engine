# TEMPLATE — ORC STEP CONTRACT (COPY) (CANON)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/30_ORC/02__TEMPLATE__STEP_CONTRACT.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 30_ORC
DOC_TYPE: KB_MODULE
KB_TYPE: TEMPLATE
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.ORC.TPL.STEP_CONTRACT.003
OWNER: SYSTEM
ROLE: Copy-paste template for defining a single ORC pipeline step contract: callee entities, IO, acceptance gates, rework/stop/failover rules, and trace requirements (UID-only). Compatible with pipeline contract template.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created ORC step contract template: explicit IO, acceptance criteria, rework/stop/failover, and trace discipline."
- REASON: "Pipelines fail when step outputs are unclear; template ensures each step is executable and auditable."
- IMPACT: "Cleaner handoffs, fewer missing requirements, and safer gate enforcement."
- CHANGE_ID: UE.CHG.2026-01-14.KB.ORC.TPL.003

---

## 0) HOW TO USE
- Copy this file per step and reference it from the pipeline contract.
- Keep references UID-only.
- Define acceptance criteria first (gates/checklists), then outputs.

---

## 1) STEP HEADER (COPY)
STEP_CONTRACT:
- STEP_UID:
- STEP_ID: S-XX
- STEP_NAME:
- PIPELINE_UID (UID-ONLY):
  - <pipeline uid>
- OWNER_ORC_UID:
- DOMAIN:
- PURPOSE (one sentence):
- CHANGE_NOTE:
  - DATE:
  - TYPE:
  - SUMMARY:
  - CHANGE_ID:

---

## 2) CALLED ENTITIES (UID-ONLY)
CALLED_ENTITIES:
- PRIMARY:
  - UID: <eng/spc uid>
  - ROLE: <what it produces>
- SUPPORT (optional):
  - UID: <spc/val/qa uid>
  - ROLE:
- CONTROLS (optional):
  - UID: <ctl policy uid>
  - ROLE:

---

## 3) INPUTS / OUTPUTS (EXPLICIT)
INPUTS_REQUIRED:
- <input>
INPUTS_OPTIONAL:
- <input>

OUTPUTS_PRODUCED:
- <output>

OUTPUT_SCHEMA / TEMPLATE (UID-ONLY):
- <template uid> | WHY

---

## 4) ACCEPTANCE CRITERIA (MUST BE EXPLICIT)
ACCEPTANCE_CRITERIA (UID-ONLY):
- GATES:
  - <gate uid> | WHY
- CHECKLISTS:
  - <chk uid> | WHY
- RUBRIC (optional):
  - <rubric uid> | WHY

PASS CONDITION:
- all required gates PASS
- required checklists PASS (or explicitly REWORK)
- rubric threshold met (if used)

---

## 5) REWORK / STOP / FAILOVER RULES
REWORK_CONDITIONS:
- RC-01:
  - TRIGGER (failed criterion uid):
  - ACTION: REWORK
  - FIX_GUIDE (short):
  - RECHECK (uid):
- RC-02:
  - TRIGGER:
  - ACTION:
  - RECHECK:

STOP_CONDITIONS:
- SC-01:
  - TRIGGER:
  - ACTION: STOP
  - WHY:
- SC-02:
  - TRIGGER:
  - ACTION:
  - WHY:

FAILOVER_CONDITIONS:
- FC-01:
  - TRIGGER:
  - ACTION: FAILOVER
  - FROM (uid):
  - TO OPTIONS (uid-only):
    - <uid> | WHY
  - RECHECK:

REWORK_LOOP_LIMIT:
- MAX_ATTEMPTS:
- ESCALATION_RULE (after limit):
  - FAILOVER / STOP / CALL_SUPPORT_SPC (uid)

---

## 6) TIMEBOX (OPTIONAL)
TIMEBOX:
- SOFT_LIMIT:
- HARD_LIMIT:
- WHAT TO DO IF TIMEBOX EXCEEDED:
  - degrade scope / stop / failover

---

## 7) TRACE REQUIREMENTS (MANDATORY)
TRACE_REQUIREMENTS:
- MUST_LIST_UIDS_USED: YES
- MUST_LIST_GATES_RUN: YES
- MUST_RECORD_MISSING_INPUTS: YES
- MUST_RECORD_EXCEPTION_USE: YES/NO
- MUST_RECORD_BYPASSES: YES/NO (default NO)
- MEMORY_REUSE_FLAG: REQUIRED
- WEB_LOOKUP_FLAG: REQUIRED

TRACE_OUTPUT_TEMPLATE (COPY):
STEP_RUN_TRACE:
- STEP_UID:
- KB_SOURCES_USED (UID-ONLY):
  - <uid>
- CRITERIA_RUN (UID-ONLY):
  - <uid>
- RESULT: PASS/REWORK/FAIL/STOP
- REWORK_COUNT:
- EXCEPTIONS_USED:
- BYPASSES_USED:
- MEMORY_REUSE: YES/NO
- WEB_LOOKUP_USED: YES/NO

---

## 8) COMMON FAIL MODES (SHORT)
COMMON_FAIL_MODES:
- missing acceptance criteria → step becomes non-executable
- outputs not templated → downstream handoff breaks
- rework loop has no limit → infinite loop risk

---

## 9) HARD FAIL CONDITIONS
HARD_FAIL_CONDITIONS:
- acceptance criteria missing
- outputs undefined
- UID-only discipline broken
- gates exist but are skipped silently

---

## 10) RELATED (UID-ONLY)
RELATED_UIDS:
- UE.KB.ORC.STD.CONNECTOR.001 | WHY: ORC connector rules
- UE.KB.ORC.TPL.PIPELINE_CONTRACT.002 | WHY: pipeline contract template compatibility
- UE.KB.STD.GATE_DEF.088 | WHY: gate definition standard used for acceptance criteria

--- END.
