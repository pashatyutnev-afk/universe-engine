# ORC — KB CONNECTOR STANDARD (CANON)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/30_ORC/00__README__ORC_KB_CONNECTOR_STANDARD.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 30_ORC
DOC_TYPE: KB_MODULE
KB_TYPE: STANDARD
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.ORC.STD.CONNECTOR.001
OWNER: SYSTEM
ROLE: Canonical connector standard for Orchestrator entities: how to design and run pipelines deterministically, define step contracts (inputs/outputs), place gates, manage failover/rework loops, and load KB minimally (UID-only, no-fantasy).

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created ORC connector standard: pipeline contract discipline, step IO, gate placement, failover, and minimal KB load rules."
- REASON: "Without orchestration standards, workflows drift, handoffs are unclear, and quality gates are skipped."
- IMPACT: "More executable pipelines, fewer missing assets, and consistent gate enforcement."
- CHANGE_ID: UE.CHG.2026-01-14.KB.ORC.STD.001

---

## 0) PURPOSE (KB)
An Orchestrator (ORC) exists to:
- sequence work into pipeline steps
- define handoff contracts (IO) between steps
- place gates/checkpoints
- handle rework and failover deterministically

ORC is the “workflow controller”, not the content creator.

---

## 1) SCOPE (BOUNDARY)
COVERS:
- pipeline design and execution rules
- step contracts and handoffs
- gate placement strategy
- rework/failover loops
- minimal KB load discipline for pipelines

EXCLUDES:
- domain craft knowledge (topics realm)
- governance law authoring
- “engine methods” (ENG owns methods; ORC sequences them)

---

## 2) ABSOLUTE RULES (ORC LAW)
R1 — Pipeline must be explicit
- A pipeline must define:
  - steps in order
  - IO per step
  - gates per step
  - rework conditions and loops

R2 — No silent skipping of gates
- If a gate exists, it must be executed or explicitly bypassed with a recorded reason.

R3 — UID-only authority
- Operational references are UID-only.
- Navigation via KB master index only.

R4 — Minimal loading
- Load only what the pipeline needs for the current step:
  - step’s caller modules + criteria + required topics
- Avoid loading entire realms.

R5 — No-fantasy pipeline execution
- If a step requires knowledge or templates not available → STOP or GAP.

---

## 3) REQUIRED LOAD SET (MINIMAL)
ORC run requires:
- governance minimum set
- pipeline definition module (this pipeline’s UID)
- step contracts
- gates/checklists/rubrics referenced by the pipeline
- domain topics required by the current step only
- (optional) reference glossaries when terminology ambiguity exists

---

## 4) PIPELINE CONTRACT (CANON)
A pipeline must include the following:

PIPELINE_CONTRACT:
- PIPELINE_UID:
- PURPOSE:
- INPUTS:
- OUTPUTS:
- STEPS (ordered):
  - STEP_ID
  - STEP_PURPOSE
  - CALLED_ENTITIES (UID-only): SPC/ENG/VAL/QA
  - INPUTS_REQUIRED
  - OUTPUTS_PRODUCED
  - GATES (UID-only):
  - FAILOVER / REWORK RULES
- GLOBAL GATES (UID-only) (optional)
- HARD FAIL CONDITIONS
- TRACE REQUIREMENTS

---

## 5) STEP CONTRACT (CANON)
Each step must define:

STEP_CONTRACT:
- STEP_ID:
- OWNER_ENTITY_CLASS: ORC
- CALLEE (UID-only): ENG/SPC/…
- INPUTS:
- OUTPUTS:
- ACCEPTANCE CRITERIA (UID-only): gates/checklists
- REWORK CONDITIONS:
- TIMEBOX (optional)
- NOTES (constraints only)

---

## 6) GATE PLACEMENT STRATEGY (RULES)
Place gates:
- after any transformation that can drift quality
- before handoff to downstream steps that assume correctness
- at final readiness stage

Types:
- EARLY sanity gates (cheap)
- MID quality gates (domain)
- FINAL release gates (packaging/compliance)

Rule:
- early gates must be fast; deep gates reserved for later.

---

## 7) FAILOVER / REWORK LOOPS (DETERMINISTIC)
When a gate fails:
- decide: REWORK vs STOP using explicit rules

REWORK_RULE:
- if failure is localized and fixable → REWORK current step
- if failure indicates missing inputs/knowledge → STOP or GAP
- if repeated failure occurs → escalate to different specialist or adjust parameters

Failover options:
- call alternative ENG method (UID-only)
- call a different SPC specialist (UID-only)
- downgrade scope (if allowed by policy)

All failovers must be recorded in trace.

---

## 8) COMMON FAIL MODES (ORC) (AND FIXES)
F1 — Vague step outputs
- Fix: define output schema/templates

F2 — Gate skipping
- Fix: hard rule: gate must run or be recorded bypass (rare)

F3 — Overloading knowledge
- Fix: step-local loading only

F4 — No rework plan
- Fix: define rework conditions and loop limits

---

## 9) HARD FAIL CONDITIONS
FAIL IF:
- pipeline has no explicit IO contracts
- gates exist but are skipped silently
- URL/PATH used as authority inside pipeline contracts
- pipeline calls entities without specifying expected outputs
- repeated rework loops without escalation rule

---

## 10) RELATED (UID-ONLY)
XREF:
- UE.KB.RULES.GOV.001 | WHY: global KB governance rules
- UE.KB.ENG.STD.CONNECTOR.001 | WHY: engines are called by ORC with explicit IO
- UE.KB.SPC.STD.PRO_PACK.001 | WHY: specialists provide competence packs ORC can call
- UE.KB.VAL.STD.CONNECTOR.001 | WHY: validators report violations for rework loops
- UE.KB.QA.STD.CONNECTOR.001 | WHY: QA gates define readiness and final decisions
- UE.KB.XREF.STD.CONNECTOR.001 | WHY: mapping artifacts for pipelines and entity selection
- UE.KB.STD.GATE_DEF.088 | WHY: gate definitions used as acceptance criteria

--- END.
