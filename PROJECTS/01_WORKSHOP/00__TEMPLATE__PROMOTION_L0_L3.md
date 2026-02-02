# PROMOTION LAW TEMPLATE — L0→L3 (WORKSHOP)
FILE: 00__TEMPLATE__PROMOTION_L0_L3.md

SCOPE: Projects Workshop
LAYER: PRJ
DOC_TYPE: TEMPLATE
ENTITY_KIND: GENERIC
PROJECT_SCOPE: PROJECT_ONLY
OUTPUT_LEVEL: N/A
ID: PRJ.WORKSHOP.TEMPLATE.PROMOTION_L0_L3
STATUS: ACTIVE
VERSION: 2.0
ROLE: Universal promotion law for Workshop artifacts across levels L0_INTAKE → L1_DRAFT → L2_CANON → L3_OUTPUT. Defines mandatory gates, REG/XREF checkpoints, and exception policy.

---

## 0) PURPOSE (LAW)

Promotion — это контролируемый перевод артефакта вверх по уровням.
Цель:
- гарантировать трассируемость (откуда взялось)
- гарантировать канон-совместимость
- запретить скрытые зависимости и “прыжки” уровней
- обеспечить регистрацию существования (REG) и связей (XREF)

### NO SHOW WITHOUT CHAIN RULE
> Нельзя иметь L2_CANON или L3_OUTPUT без цепочки происхождения и записей в REG/XREF.

---

## 1) LEVEL DEFINITIONS (STANDARD)

### L0_INTAKE
- raw input: заметки, ссылки, фрагменты, сырьё
- не содержит утверждений “это канон”

### L1_DRAFT
- структурированный черновик, подготовка к канону
- допускаются варианты/конфликты/черновые решения

### L2_CANON
- утверждённый канон (единственная точка истины)
- должен пройти validators + QA + регистрацию

### L3_OUTPUT
- продакшн-выход (видео/арт/книга/музыка/шотлист и т.п.)
- должен ссылаться на L2_CANON (CANON_REF)

---

## 2) PROMOTION EVENTS (MANDATORY)

Promotion is an explicit event:
- EVENT_ID: <PROMO.<PROJECT_ID>.<YYYYMMDD>.<NN>>
- FROM_LEVEL: <L0|L1|L2>
- TO_LEVEL: <L1|L2|L3>
- TARGET_ID: <artifact/entity id>
- BY: <ORC.*|ENG.*|MANUAL>
- WHY: <one sentence>
- AT: <YYYY-MM-DD>

Rule:
> Каждый promotion event обязан создавать XREF provenance record.

---

## 3) MANDATORY CHECKPOINTS (HARD)

### 3.1 Registry checkpoint (existence)
When promoting to:
- L1: registry optional (project choice)
- L2: registry mandatory (canon registry)
- L3: registry mandatory (output registry)

### 3.2 XREF checkpoint (relationships)
When promoting:
- L0 → L1: create provenance
  - `L1_DRAFT -> L0_INTAKE | TYPE:DERIVED_FROM`
- L1 → L2: create provenance + producer
  - `L2_CANON -> L1_DRAFT | TYPE:DERIVED_FROM`
  - `L2_CANON -> ENG.* | TYPE:PRODUCED_BY` (or ORC.*)
- L2 → L3: create canon ref + provenance
  - `L3_OUTPUT -> L2_CANON | TYPE:CANON_REF`
  - `L3_OUTPUT -> L2_CANON | TYPE:DERIVED_FROM` (optional but recommended)

### 3.3 Dependency checkpoint (no hidden deps)
If any engine involved has DEPENDS_ON:
- XREF DEPENDS_ON records must exist in project dependency index

Fail if:
- dependency exists but is not mirrored in XREF

---

## 4) GATES (VAL/QA) — MANDATORY

### 4.1 Gate requirements by promotion
- L0 → L1:
  - VAL: optional
  - QA: optional
- L1 → L2:
  - VAL: mandatory (schema + canon consistency)
  - QA: mandatory (anti-stub + readability + links)
- L2 → L3:
  - VAL: mandatory (output traceability + canon ref)
  - QA: mandatory (production readiness)

### 4.2 Gate outcomes
- PASS: promotion allowed
- PASS_WITH_NOTES: allowed only for L0/L1 (recommended)
- FAIL: promotion blocked

---

## 5) CONTROLLER ENFORCEMENT (CTL) — MANDATORY

Controllers must enforce:
- correct path for target level folder
- no skip promotion
- mandatory registry entries for L2/L3
- mandatory xref links for provenance/canon_ref
- anti-duplicate entity roots

Recommended CTL pack:
- CTL.WORKSHOP.PATH_ENFORCER
- CTL.WORKSHOP.LEVEL_ENFORCER
- CTL.REG.ENTRY_ENFORCER
- CTL.XREF.NO_ORPHANS
- CTL.XREF.NO_HIDDEN_LINKS

---

## 6) PROMOTION PACKETS (STANDARD OUTPUT)

Each promotion should produce a “packet” summary:

PROMOTION_PACKET:
- TARGET: <id/path>
- FROM → TO: <...>
- REG_UPDATES: <what was added/updated>
- XREF_UPDATES: <which records were written>
- VALIDATION: <VAL result summary>
- QA: <QA result summary>
- NOTES: <optional>

---

## 7) EXCEPTIONS (STRICT POLICY)

Exceptions are allowed ONLY with governance approval.

### 7.1 Allowed exceptions
- Bootstrapping a project: initial canon seed
- Importing legacy canon artifacts
- Emergency hotfix outputs tied to stable canon

### 7.2 Exception record (mandatory)
EXCEPTION:
- ITEM: <id/path>
- RULE_BROKEN: <...>
- WHY: <...>
- APPROVED_BY: <ENG.GOV.07.DECISION_APPROVAL or MANUAL>
- AT: <YYYY-MM-DD>
- COMPENSATING_ACTION: <what will be done to repair traceability>

Rule:
> Exception must create XREF record with TYPE:EXCEPTION_FOR and link to the item.

---

## 8) SYSTEM INTERFACE (MANDATORY)

## SYSTEM INTERFACE
- INPUTS:
  - artifacts: [L0/L1/L2 candidates]
  - sources: [ORC pipeline steps, ENG outputs, REG/XREF]
- OUTPUTS:
  - artifacts: [promoted artifacts + promotion packets]
  - target_path: `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/.../<level_folder>/`
- REGISTRY_UPDATES:
  - required: YES (for L2/L3)
  - registries: [project canon registry, project output registry]
  - entries_to_add: [artifact existence records]
- XREF_UPDATES:
  - required: YES
  - record_types: [DERIVED_FROM, PRODUCED_BY, CANON_REF, DEPENDS_ON, EXCEPTION_FOR]
  - xref_targets: [project xref indexes]
- GATES:
  - validators: [project validators]
  - qa_checks: [project qa checks]
- ORCHESTRATION:
  - orc_owner: [project orchestrators]
  - ctl_enforcers: [project controllers]

---

## FINAL RULE (LOCK)

> Promotion — единственный легальный способ получить L2_CANON и L3_OUTPUT в проекте.  
> Любой обход = invalid unless exception approved and logged.

OWNER: Projects Workshop  
LOCK: FIXED
