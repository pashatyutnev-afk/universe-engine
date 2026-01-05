# VALIDATOR TEMPLATE — UNIVERSAL FORMAL CHECK
FILE: 00__TEMPLATE__VALIDATOR.md

SCOPE: Universe Engine
LAYER: VAL
DOC_TYPE: TEMPLATE
ENTITY_KIND: GENERIC
PROJECT_SCOPE: GLOBAL
OUTPUT_LEVEL: N/A
ID: VAL.TEMPLATE.UNIVERSAL
STATUS: ACTIVE
VERSION: 2.0
ROLE: Universal template for validators. Defines formal validation rules, issue schema, severity levels, pass/fail logic, and integration with REG/XREF/CTL/ORC.

---

## 0) PURPOSE (LAW)

Validator — формальная проверка артефактов/сущностей/пайплайнов.
Он отвечает на вопросы:
- корректна ли структура документа (schema)
- соблюдены ли обязательные поля (header / system interface / mini-contract)
- нет ли конфликтов с каноном
- есть ли все обязательные ссылки (REG/XREF)
- выполнены ли границы “OWN / DOES NOT OWN”
- корректен ли уровень (L0–L3) относительно входов/выходов

### VALIDATION LAW
> Без PASS валидатора артефакт не может быть повышен (promoted) на следующий уровень.

---

## 1) VALIDATOR IDENTITY (MANDATORY)

VAL_NAME: <UPPER_SNAKE_CASE>
VAL_ID: <VAL.<DOMAIN>.<NN>.<VAL_NAME>>

DOMAIN: <REG|XREF|ENG|ORC|CTL|PRJ|CANON|OUTPUT|GENERIC>
APPLIES_TO:
- SCOPE: <GLOBAL|PRJ:<PROJECT_ID>>
- ENTITY_KIND: <CHR|LOC|OBJ|SYS|FAC|EVT|CPT|REL|ARC|STY|EXP|GENERIC>
- LEVELS: [L0_INTAKE, L1_DRAFT, L2_CANON, L3_OUTPUT, N/A]
- DOC_TYPES: [ENGINE, README, REGISTRY, XREF_INDEX, ORCHESTRATOR, CONTROLLER, ENTITY, INDEX, ...]

OWNER: Universe Engine
LOCK: OPEN

---

## 2) INPUT / OUTPUT (MANDATORY)

### 2.1 Inputs
INPUTS:
- artifacts: [<paths/ids>]
- registries: [<REG ids/paths>]
- xref_indexes: [<XREF ids/paths>]
- policies: [<CTL ids>]   # controllers that define enforcement laws

### 2.2 Outputs
OUTPUTS:
- result: <PASS|FAIL|PASS_WITH_WARNINGS>
- issues: [<issue records>]
- reports:
  - target_path_rule: `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/<...>/` (if project scoped) OR `50_VAL__VALIDATORS/<...>/reports/`

---

## 3) ISSUE SCHEMA (MANDATORY)

Every issue must follow a strict record.

ISSUE:
- ISSUE_ID: <VAL...I001>
- SEVERITY: <INFO|WARN|ERROR|FATAL>
- CATEGORY: <SCHEMA|MISSING_FIELD|PATH|LEVEL|REGISTRY|XREF|CONFLICT|DUPLICATION|BOUNDARY|QUALITY>
- TARGET: <id/path>
- MESSAGE: <short>
- EVIDENCE: <what triggered it>
- REQUIRED_ACTION: <what must be done>
- AUTO_FIX: <YES|NO>
- FIX_GUIDE: <1–3 bullets>

Severity meaning:
- INFO: does not affect promotion
- WARN: promotion allowed but should be fixed soon
- ERROR: blocks promotion to next level
- FATAL: invalid artifact; must be rejected

---

## 4) VALIDATION RULES (MANDATORY)

Define explicit testable rules. Recommended base pack:

### 4.1 Schema rules
R01 — Universal header present and complete (all required fields)
R02 — LOCK exists exactly once (policy from standard)
R03 — Mini-contract present for engines
R04 — SYSTEM INTERFACE present for engines/entities/outputs

### 4.2 Path + level rules
R05 — Output path matches workshop path rules for ENTITY_KIND/category
R06 — OUTPUT_LEVEL is consistent with folder (L0/L1/L2/L3)
R07 — No orphan L3 outputs (must have CANON_REF in XREF)
R08 — L2 canon must have provenance (DERIVED_FROM / PRODUCED_BY)

### 4.3 Registry rules
R09 — If artifact is L2_CANON or L3_OUTPUT, registry entry must exist (unless explicitly exempted)
R10 — Registry entry path must match actual file path

### 4.4 XREF rules
R11 — DEPENDS_ON in engines must exist in XREF dependency index
R12 — Replacement/move must have REPLACED_BY/MOVED_TO record

### 4.5 Conflict + duplication rules
R13 — Detect duplicate canon artifacts for same entity/slot
R14 — Detect conflicting canon claims (requires defined conflict heuristics)

### 4.6 Boundary rules
R15 — DOES NOT OWN violations: content belongs to other family/layer (must reference correct engine)

---

## 5) PASS/FAIL LOGIC (MANDATORY)

PASS criteria:
- no FATAL issues
- no ERROR issues (for promotion to higher level)
- WARN allowed (configurable)

FAIL criteria:
- any FATAL
- any ERROR when promotion is requested

PROMOTION_COMPATIBILITY:
- L0 → L1: allow WARN, block ERROR/FATAL
- L1 → L2: allow WARN (rare), block ERROR/FATAL
- L2 → L3: allow WARN (rare), block ERROR/FATAL
- Direct L0 → L2: always FAIL unless exception approved

---

## 6) AUTO-FIX POLICY (OPTIONAL)

AUTO_FIX_ALLOWED: <YES|NO>

If YES, list fixes:
- formatting normalization
- missing xref line insertion (if deterministic)
- registry entry sync (if deterministic)

Never auto-fix:
- canon content decisions
- conflict resolution
- ownership boundary decisions

---

## 7) SYSTEM INTERFACE (MANDATORY)

## SYSTEM INTERFACE
- INPUTS:
  - artifacts: [validation targets]
  - sources: [standard law, registries, xref indexes, ctl policies]
- OUTPUTS:
  - artifacts: [validation report + issues]
  - target_path: <reports path rule>
- REGISTRY_UPDATES:
  - required: NO (validator reports may be registered optionally)
  - registries: []
  - entries_to_add: []
- XREF_UPDATES:
  - required: NO (validator demands xref, doesn't create canon links by default)
  - record_types: []
  - xref_targets: []
- GATES:
  - validators: []  # self
  - qa_checks: []
- ORCHESTRATION:
  - orc_owner: [<ORC ids that call this VAL>]
  - ctl_enforcers: [<CTL ids>]

---

## 8) RAW LINK (MANDATORY)

RAW: <raw github link to this validator file>

---

## FINAL RULE (LOCK)

> Validator PASS is a mandatory gate for promotion/canonization.  
> Any change to validator rules must be logged and versioned.

OWNER: Universe Engine  
LOCK: OPEN
