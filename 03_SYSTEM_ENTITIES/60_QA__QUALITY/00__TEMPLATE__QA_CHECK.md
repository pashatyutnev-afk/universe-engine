# QA CHECK TEMPLATE — UNIVERSAL QUALITY GATE
FILE: 00__TEMPLATE__QA_CHECK.md

SCOPE: Universe Engine
LAYER: QA
DOC_TYPE: TEMPLATE
ENTITY_KIND: GENERIC
PROJECT_SCOPE: GLOBAL
OUTPUT_LEVEL: N/A
ID: QA.TEMPLATE.UNIVERSAL
STATUS: ACTIVE
VERSION: 2.0
ROLE: Universal template for QA checks. Defines quality gates for readability, completeness, navigation, link integrity, anti-stub rules, and system compatibility (REG/XREF/WORKSHOP).

---

## 0) PURPOSE (LAW)

QA Check — это “врата качества”:
- документ может быть формально валиден (VAL PASS),
  но быть непригоден (нечитабелен, пустой, без навигации, без ссылок, без примеров)
- QA проверяет usability и каноничность “как артефакта”

### ANTI-STUB LAW
> Заглушки, пустые списки “без изменений”, и документы без примеров/выходов запрещены для L2_CANON и L3_OUTPUT.

---

## 1) QA CHECK IDENTITY (MANDATORY)

QA_NAME: <UPPER_SNAKE_CASE>
QA_ID: <QA.<DOMAIN>.<NN>.<QA_NAME>>

DOMAIN: <ENG|REG|XREF|ORC|CTL|VAL|PRJ|WORKSHOP|CANON|OUTPUT|GENERIC>
APPLIES_TO:
- SCOPE: <GLOBAL|PRJ:<PROJECT_ID>>
- ENTITY_KIND: <CHR|LOC|OBJ|SYS|FAC|EVT|CPT|REL|ARC|STY|EXP|GENERIC>
- LEVELS: [L0_INTAKE, L1_DRAFT, L2_CANON, L3_OUTPUT, N/A]
- DOC_TYPES: [ENGINE, README, REGISTRY, XREF_INDEX, ORCHESTRATOR, CONTROLLER, VALIDATOR, QA_CHECK, ENTITY, INDEX, ...]

OWNER: Universe Engine
LOCK: OPEN

---

## 2) INPUT / OUTPUT (MANDATORY)

INPUTS:
- artifacts: [<paths/ids>]
- validation_results: [<VAL reports>]
- references: [REG, XREF indexes]

OUTPUTS:
- result: <PASS|FAIL|PASS_WITH_NOTES>
- notes: [<qa notes>]
- required_fixes: [<fix items>]

---

## 3) QA NOTE SCHEMA (MANDATORY)

QA_NOTE:
- NOTE_ID: <QA...N001>
- SEVERITY: <NOTE|WARN|BLOCKER>
- CATEGORY: <READABILITY|COMPLETENESS|NAVIGATION|LINKS|ANTI_STUB|CONSISTENCY|TRACEABILITY|STYLE>
- TARGET: <id/path/section>
- MESSAGE: <short>
- REQUIRED_FIX: <what to change>
- ACCEPTANCE: <how we know it is fixed>

Rule:
- BLOCKER = FAIL
- WARN = PASS_WITH_NOTES (allowed for lower levels)
- NOTE = informational

---

## 4) CORE QUALITY CHECKLIST (MANDATORY)

### 4.1 Readability (minimum)
- Headings are structured (H1/H2/H3), not a wall of text
- Lists are properly formatted (no one-line dump)
- Uses consistent naming for sections (Purpose / Contract / Interface / Process / Quality)
- Includes at least one minimal example where applicable

BLOCKER if:
- content is mostly on one line / unreadable diff
- ambiguous naming, unclear outputs

### 4.2 Completeness (minimum per doc type)
ENGINE:
- has Mini-contract + System Interface + Failure modes + Raw link
README (family):
- has OWNS/DOES NOT OWN + Role map + Required REG/XREF + Canon order + Templates block
REGISTRY:
- has entry format + at least one example entry
XREF INDEX:
- uses normalized line format + has sections + has at least one record (if ACTIVE)
ORC:
- has pipeline steps + promotion rules + checkpoints
CTL:
- has enforceable rules + fail messages + exception policy
VAL:
- has rules + issue schema + pass/fail logic

BLOCKER if:
- required section missing for that doc type

### 4.3 Navigation
- Must include direct raw links (where required)
- Must include “where outputs go” (workshop routing) when producing artifacts
- Must include pointers to dependent engines (DEPENDS_ON mirrored via XREF)

BLOCKER if:
- user cannot use it without opening repository tree
- no pointers to required indexes/registries

### 4.4 Link integrity
- Raw links must be correct format
- No broken placeholders like `NN__ _ENG.md` with missing name
- No double slashes in canonical paths (`//`)

BLOCKER if:
- raw link missing where mandated
- canonical path formatting broken

### 4.5 Anti-stub rule (hard)
- No “TBD only” documents in L2_CANON or any ACTIVE doc that claims to be canonical
- Any ACTIVE canonical doc must have:
  - at least one example OR
  - at least one produced artifact spec OR
  - at least one filled record/table/flow

BLOCKER if:
- ACTIVE doc contains only empty sections/placeholders

### 4.6 Traceability (REG + XREF)
- If artifact is L2_CANON or L3_OUTPUT:
  - registry entry exists
  - xref canon/provenance links exist

BLOCKER if:
- L3 output exists without CANON_REF
- L2 canon exists without provenance link

---

## 5) PASS/FAIL POLICY (MANDATORY)

PASS if:
- no BLOCKER notes

PASS_WITH_NOTES if:
- only WARN/NOTE and level allows it (L0/L1)

FAIL if:
- any BLOCKER

Level constraints (recommended):
- L0_INTAKE: WARN ok
- L1_DRAFT: WARN ok
- L2_CANON: WARN allowed only rarely; prefer none
- L3_OUTPUT: no WARN; must be clean

---

## 6) SYSTEM INTERFACE (MANDATORY)

## SYSTEM INTERFACE
- INPUTS:
  - artifacts: [targets + val reports]
  - sources: [standard law, registries, xref indexes]
- OUTPUTS:
  - artifacts: [qa report + required fixes]
  - target_path: <QA reports path or project workshop notes>
- REGISTRY_UPDATES:
  - required: NO (optional for QA reports)
  - registries: []
  - entries_to_add: []
- XREF_UPDATES:
  - required: NO
  - record_types: []
  - xref_targets: []
- GATES:
  - validators: []
  - qa_checks: [] # self
- ORCHESTRATION:
  - orc_owner: [<ORC ids that call this QA>]
  - ctl_enforcers: [<CTL ids>]

---

## 7) RAW LINK (MANDATORY)

RAW: <raw github link to this QA check file>

---

## FINAL RULE (LOCK)

> QA gates protect canon usability and production readiness.  
> FAIL blocks promotion/canonization until fixed.

OWNER: Universe Engine  
LOCK: OPEN
