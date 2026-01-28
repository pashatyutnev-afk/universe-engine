# TEMPLATE — PIPELINE CONTRACT (ORC) (COPY) (CANON)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/30_ORC/01__TEMPLATE__PIPELINE_CONTRACT.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 30_ORC
DOC_TYPE: KB_MODULE
KB_TYPE: TEMPLATE
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.ORC.TPL.PIPELINE_CONTRACT.002
OWNER: SYSTEM
ROLE: Copy-paste template for defining an Orchestrator pipeline contract: steps with IO, acceptance gates, handoffs, rework loops, failover, and trace requirements. Produces an executable pipeline spec (UID-only).

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created ORC pipeline contract template: step contracts, gate placement, rework/failover rules, and trace record format."
- REASON: "Pipelines drift without explicit contracts; template ensures deterministic execution and audit readiness."
- IMPACT: "More reliable orchestration and fewer skipped gates."
- CHANGE_ID: UE.CHG.2026-01-14.KB.ORC.TPL.002

---

## 0) HOW TO USE
- Copy this file to create a new pipeline spec.
- Replace placeholders.
- Keep all operational references UID-only.
- Do not embed RAW link registries here.

---

## 1) PIPELINE CONTRACT (COPY)
PIPELINE_CONTRACT:
- PIPELINE_UID:
- PIPELINE_NAME:
- OWNER_ORC_UID:
- DOMAIN:
- PURPOSE:
- SCOPE:
  - COVERS:
  - EXCLUDES:
- INPUTS (REQUIRED):
  - <input>
- INPUTS (OPTIONAL):
  - <input>
- OUTPUTS (REQUIRED):
  - <output>
- OUTPUT_SCHEMA / ARTIFACTS:
  - <artifact>
- GLOBAL CONSTRAINTS (UID-ONLY):
  - <ctl/policy uid> | WHY
- GLOBAL GATES (UID-ONLY) (optional):
  - <qa/val gate uid> | WHY
- PIPELINE STEPS (ORDERED):
  - STEP_ID: S-01
    STEP_REF: <uid or local step contract block>
  - STEP_ID: S-02
    STEP_REF:
- REWORK POLICY:
  - MAX_REWORK_LOOPS_PER_STEP:
  - ESCALATION_RULE:
- FAILOVER POLICY:
  - WHEN_TO_FAILOVER:
  - FAILOVER_OPTIONS (UID-ONLY):
    - <eng uid> | WHY
    - <spc uid> | WHY
- HARD FAIL CONDITIONS:
  - <condition>
- RUN_TRACE REQUIREMENTS:
  - MUST_LIST_UIDS_USED: YES
  - MUST_LIST_GATES_RUN: YES
  - MUST_RECORD_BYPASSES: YES/NO (default NO)
  - MEMORY_REUSE_FLAG: REQUIRED
  - WEB_LOOKUP_FLAG: REQUIRED
- CHANGE_NOTE:
  - DATE:
  - TYPE:
  - SUMMARY:
  - CHANGE_ID:

---

## 2) STEP CONTRACT (COPY)
Repeat this block per step (or store each step as its own file if preferred).

STEP_CONTRACT:
- STEP_ID:
- STEP_NAME:
- PURPOSE:
- CALLED_ENTITIES (UID-ONLY):
  - PRIMARY: <eng/spc uid>
  - SUPPORT (optional):
    - <spc uid>
    - <val uid>
    - <qa uid>
- INPUTS REQUIRED:
  - <input>
- INPUTS OPTIONAL:
  - <input>
- OUTPUTS PRODUCED:
  - <output>
- OUTPUT_SCHEMA / TEMPLATE (UID-ONLY):
  - <template uid> | WHY
- ACCEPTANCE CRITERIA (UID-ONLY):
  - GATES:
    - <gate uid> | WHY
  - CHECKLISTS:
    - <chk uid> | WHY
  - RUBRIC (optional):
    - <rubric uid> | WHY
- REWORK CONDITIONS:
  - <condition> -> ACTION: REWORK
- STOP CONDITIONS:
  - <condition> -> ACTION: STOP
- FAILOVER CONDITIONS:
  - <condition> -> ACTION: FAILOVER
- REWORK LOOP LIMIT:
  - MAX_ATTEMPTS:
- NOTES (constraints only):
- TRACE REQUIREMENTS:
  - LIST_UIDS_USED: YES
  - LIST_GATES_RUN: YES
  - RECORD_INPUTS_MISSING: YES
  - RECORD_EXCEPTION_USE: YES/NO

---

## 3) GATE PLACEMENT NOTE (COPY)
GATE_PLACEMENT_NOTE:
- GATE_UID:
- WHY HERE:
- COST (cheap/medium/expensive):
- FAIL ACTION:
  - REWORK / STOP / FAILOVER
- RECHECK METHOD:

---

## 4) REWORK RECORD (COPY)
REWORK_RECORD:
- RW_UID: RW-YYYYMMDD-001
- STEP_ID:
- TRIGGER (failed gate/checklist UID):
- ISSUE SUMMARY:
- FIX APPLIED:
- RECHECK RESULT: PASS/REWORK/FAIL
- LOOP_COUNT:
- NEXT ACTION:
  - CONTINUE / REWORK / FAILOVER / STOP
- TRACE:

---

## 5) FAILOVER RECORD (COPY)
FAILOVER_RECORD:
- FO_UID: FO-YYYYMMDD-001
- STEP_ID:
- TRIGGER:
- FROM (UID-ONLY):
  - <eng/spc uid>
- TO (UID-ONLY):
  - <eng/spc uid>
- WHY:
- RESULT:
- TRACE:

---

## 6) BYPASS RECORD (RARE) (COPY)
BYPASS_RECORD:
- BP_UID: BP-YYYYMMDD-001
- GATE_UID:
- STEP_ID:
- JUSTIFICATION:
- RISK:
- MITIGATION:
- APPROVAL (if required):
- TRACE:

Rule:
- Gate bypasses should be extremely rare.
- If bypass happens, it must be in RUN_TRACE and include mitigation.

---

## 7) HARD FAIL CONDITIONS (REMINDER)
FAIL IF:
- steps have no explicit IO
- acceptance criteria not specified (UID-only)
- gates exist but are skipped silently
- rework loops have no limits/escalation
- this file becomes a RAW registry / second index

--- END.
