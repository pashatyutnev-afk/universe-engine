# CONTROLLER TEMPLATE — UNIVERSAL ENFORCEMENT RULESET
FILE: 00__TEMPLATE__CONTROLLER.md

SCOPE: Universe Engine
LAYER: CTL
DOC_TYPE: TEMPLATE
ENTITY_KIND: GENERIC
PROJECT_SCOPE: GLOBAL
OUTPUT_LEVEL: N/A
ID: CTL.TEMPLATE.UNIVERSAL
STATUS: ACTIVE
VERSION: 2.0
ROLE: Universal template for CTL controllers. Defines enforcement rules for structure, levels (L0→L3), registry/xref requirements, and prevention of hidden dependencies.

---

## 0) PURPOSE (LAW)

Controller — это механизм enforcement.
Он:
- проверяет, что артефакт создан в правильном месте (path)
- проверяет, что уровень (L0/L1/L2/L3) корректен
- проверяет, что обязательные REG/XREF обновления выполнены
- запрещает hidden dependencies
- может отклонять (REJECT) артефакты/шаги пайплайна

### ENFORCEMENT RULE
> Если CTL правило нарушено — результат считается invalid и не может быть promoted.

---

## 1) CONTROLLER IDENTITY (MANDATORY)

CTL_NAME: <UPPER_SNAKE_CASE>
CTL_ID: <CTL.<DOMAIN>.<NN>.<CTL_NAME>>

DOMAIN: <REG|XREF|ENG|PRJ|WORKSHOP|CANON|OUTPUT|GENERIC>
APPLIES_TO:
- SCOPE: <GLOBAL|PRJ:<PROJECT_ID>>
- ENTITY_KIND: <CHR|LOC|OBJ|SYS|FAC|EVT|CPT|REL|ARC|STY|EXP|GENERIC>
- LEVELS: [L0_INTAKE, L1_DRAFT, L2_CANON, L3_OUTPUT]

OWNER: Universe Engine
LOCK: OPEN

---

## 2) POLICY (WHAT THIS CONTROLLER ENFORCES)

POLICY_TYPE: <PATH_ENFORCEMENT|LEVEL_ENFORCEMENT|REGISTRY_ENFORCEMENT|XREF_ENFORCEMENT|DEPENDENCY_ENFORCEMENT|PROMOTION_ENFORCEMENT>

SEVERITY:
- VIOLATION_LEVEL: <WARN|ERROR|FATAL>
- DEFAULT_ACTION: <ALLOW_WITH_NOTE|BLOCK|REJECT>

---

## 3) RULE SET (MANDATORY)

Each rule must be explicit and testable.

### 3.1 Rule format
RULE:
- RULE_ID: <CTL...R01 / R02...>
- NAME: <short>
- CONDITION: <human readable>
- CHECK:
  - inputs: [<paths/ids/metadata>]
  - logic: <what must be true>
- PASS_ACTION: <ALLOW|ALLOW_WITH_NOTE>
- FAIL_ACTION: <BLOCK|REJECT>
- FAIL_MESSAGE: <exact message>
- FIX_GUIDE: <how to fix in 1–3 bullets>

---

## 4) CANONICAL CONTROLLER PACK (RECOMMENDED BASE RULES)

### 4.1 Path enforcement (WORKSHOP)
R01 — Output must be under workshop root:
- Must match: `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/<CATEGORY>/<ENTITY>/<LEVEL_FOLDER>/...`

R02 — Category must match ENTITY_KIND:
- CHR -> 01_CHARACTERS
- LOC -> 02_LOCATIONS
- OBJ -> 03_OBJECTS
- SYS -> 04_SYSTEMS
- FAC -> 05_FACTIONS
- EVT -> 06_EVENTS
- CPT -> 07_CONCEPTS
- REL -> 08_RELATIONSHIPS
- ARC -> 09_ARCS
- STY -> 10_STYLES
- EXP -> 11_EXPERIMENTS
- Outputs -> 05_PROJECT__L3

### 4.2 Level enforcement
R03 — No skip promotion:
- L2_CANON cannot be created if there is no L1_DRAFT lineage (unless exception is logged)
R04 — L3_OUTPUT must reference L2_CANON (XREF CANON_REF required)

### 4.3 Registry enforcement
R05 — L2_CANON must be registered:
- If OUTPUT_LEVEL == L2_CANON → REG entry required
R06 — L3_OUTPUT must be registered:
- If OUTPUT_LEVEL == L3_OUTPUT → REG entry required

### 4.4 XREF enforcement
R07 — No orphan outputs:
- If L3_OUTPUT exists → must have CANON_REF to L2_CANON in XREF index
R08 — Dependencies must be mirrored:
- If engine declares DEPENDS_ON → XREF DEPENDS_ON record must exist

### 4.5 Hidden dependency enforcement
R09 — If an artifact uses/mentions another artifact/entity as prerequisite:
- must create XREF DEPENDS_ON or CANON_REF (depending on type)

---

## 5) EXCEPTIONS (CONTROLLED)

EXCEPTIONS are allowed only if:
- logged in governance (Audit Log)
- have WHY and APPROVER

EXCEPTION_RECORD_FORMAT:
- ITEM: <id/path>
- RULE_ID: <...>
- WHY: <...>
- APPROVED_BY: <ENG.GOV.07.DECISION_APPROVAL or MANUAL>
- AT: <YYYY-MM-DD>

---

## 6) SYSTEM INTERFACE (MANDATORY)

## SYSTEM INTERFACE
- INPUTS:
  - artifacts: [candidate outputs, pipeline steps]
  - sources: [REG entries, XREF indexes, engine headers, workshop paths]
- OUTPUTS:
  - artifacts: [PASS/FAIL decisions, enforcement notes]
  - target_path: <may write to audit log / ctl reports>
- REGISTRY_UPDATES:
  - required: NO (CTL itself usually does not register outputs)
  - registries: []
  - entries_to_add: []
- XREF_UPDATES:
  - required: NO (CTL requires others to update XREF; it can demand it)
  - record_types: []
  - xref_targets: []
- GATES:
  - validators: [] 
  - qa_checks: [] 
- ORCHESTRATION:
  - orc_owner: [<ORC ids that call this CTL>]
  - ctl_enforcers: []  # self

---

## 7) RAW LINK (MANDATORY)

RAW: <raw github link to this controller file>

---

## FINAL RULE (LOCK)

> CTL rules are enforcement law. Violations block promotion and canonization unless exception is approved.

OWNER: Universe Engine  
LOCK: OPEN
