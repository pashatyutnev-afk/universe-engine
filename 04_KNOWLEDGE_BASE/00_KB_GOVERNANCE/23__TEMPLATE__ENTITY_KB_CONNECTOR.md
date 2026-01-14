# TEMPLATE — ENTITY KB CONNECTOR (UNIVERSAL)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/23__TEMPLATE__ENTITY_KB_CONNECTOR.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TEMPLATE
INDEX_TYPE: ENTITY_KB_CONNECTOR_TEMPLATE
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.TPL.ENTITY.CONNECTOR.001
OWNER: SYSTEM
ROLE: Copy template for how any entity (SPC/ENG/ORC/CTL/VAL/QA/XREF) connects to KB; defines mandatory KB_SOURCES, KB_GATES, OUTPUT CONTRACT, STOP conditions, and evidence blocks for usage gate

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created universal entity KB connector template: mandatory sources/gates/output contract + compliance evidence blocks."
- REASON: "Entities must use KB deterministically; results must be auditable and fantasy-proof."
- IMPACT: "Every entity becomes KB-driven and can be validated via KB usage gate."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TPL.ENTITY.001

---

## 0) HEADER FIELDS (FILL THESE)
ENTITY_CLASS: <SPC | ENG | ORC | CTL | VAL | QA | XREF>
ENTITY_NAME: <exact entity name or pattern>
CONNECTOR_TYPE: <standard | instance>
STATE: <UNREAD | READ_ONCE | VERIFIED | DEPRECATED>
TAGS:
- domain_governance
- type_entity_connector
- <optional: gate_usage_required; maturity_*>

---

## 1) PURPOSE
(1–3 строки: что делает сущность и зачем ей KB.)

---

## 2) SCOPE / BOUNDARIES (MANDATORY)
### In scope
- ...

### Out of scope
- ...

---

## 3) INPUT CONTRACT (MANDATORY)
Inputs (minimum):
- ...

Assumptions (if any):
- ...

Stop triggers (input missing):
- ...

---

## 4) OUTPUT CONTRACT (MANDATORY)
Output type:
- ...

Required format/template:
- PATH: 04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/30_TEMPLATES/TPL__<NAME>.md
(or N/A if not applicable)

Evidence block required:
- YES (mandatory)

---

## 5) KB_SOURCES (MANDATORY / PATH ONLY)
KB_SOURCES:
- REQUIRED:
  - PATH: ...
  - PATH: ...
- OPTIONAL:
  - PATH: ...

Rules:
- REQUIRED источники обязаны покрывать core decisions/procedures этой сущности.
- Запрещено ссылаться на файлы вне master-index (оперативно их нет).
- Если REQUIRED источник не открыт и Memory-OK нельзя → STOP.

---

## 6) KB_GATES (MANDATORY / PATH ONLY)
KB_GATES:
- Gate:
  - NAME: ...
  - PATH: ...
  - PURPOSE: ...
  - APPLIES_TO: <output|decision|artifact>
  - RESULT: PASS|FAIL|REWORK

Rules:
- Если gate обозначен как REQUIRED в task→scope или entity→scope, он обязан присутствовать здесь.
- FAIL по REQUIRED gate = STOP (или REWORK, если это разрешено контрактом).

---

## 7) SOURCE-LOCK / MEMORY POLICY (MANDATORY)
SOURCE_LOCK:
- REQUIRED (no invention)

MEMORY_MODE:
- Allowed only for VERIFIED modules (Memory-OK)
- Otherwise: re-open source or STOP

If conflict:
- prefer source-locked doc
- require re-open
- no output until resolved

---

## 8) STOP CONDITIONS (MANDATORY)
STOP if any of:
- REQUIRED KB source missing/unavailable
- required module not opened and not Memory-OK
- conflict between required rules without policy resolution
- evidence block cannot be produced
- output contract cannot be satisfied

---

## 9) RELATED (PATH ONLY) (RECOMMENDED)
REL:
- REL: depends_on -> PATH: ...
- REL: gated_by -> PATH: ...
- REL: validated_by -> PATH: ...

XREF:
- XREF: entity_to_scope -> PATH: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/02__ENTITY_TO_KB_SCOPE_MAP.md
- XREF: task_to_scope -> PATH: 04_KNOWLEDGE_BASE/40_RELATION_XREF/01__TASK_TO_KB_SCOPE_MAP.md

---

## 10) COMPLIANCE EVIDENCE BLOCK (MANDATORY OUTPUT FORMAT)
When producing any result, include:

KB_SOURCES_USED:
- PATH: ...
- PATH: ...

KB_GATES_APPLIED:
- NAME: ...
  PATH: ...
  RESULT: PASS|FAIL|REWORK

OUTPUT_CONTRACT_USED:
- PATH: ...

COMPLIANCE:
- SOURCE_LOCK: ON|OFF
- MEMORY_MODE: ON (VERIFIED only) | OFF

---

## 11) ACCEPTANCE (PASS/FAIL)
PASS if:
- KB_SOURCES includes required scope
- KB_GATES are defined and applied
- output contract is clear and used
- source-lock is enforced (no invention)
- stop conditions are explicit

FAIL if:
- any required source/gate missing
- evidence block missing
- invention detected
- output contract absent when required

--- END.
