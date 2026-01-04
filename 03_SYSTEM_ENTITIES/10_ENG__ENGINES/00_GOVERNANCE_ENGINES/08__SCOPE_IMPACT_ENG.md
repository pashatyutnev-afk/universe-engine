# Scope Impact Engine
FILE: 08__SCOPE_IMPACT_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 00_GOVERNANCE_ENGINES
CLASS: GOVERNANCE (L1)
LEVEL: L1
STATUS: ACTIVE
VERSION: 2.0
ROLE: Evaluates scope of any proposed change across ENG; predicts blast radius, affected families/contracts/dependencies/terminology, and produces an Impact Report used by Change Control and Canon Authority

---

## PURPOSE

Этот движок отвечает на главный вопрос перед изменением:

> “Что именно сломается/изменится, если мы это тронем?”

Он нужен, чтобы:
- изменения не делались “вслепую”
- было видно, какие семьи/движки будут затронуты
- было понятно, нужны ли CR/DG/waivers и какой уровень решения (D0–D3)
- governance pipeline работал предсказуемо

---

## SCOPE (WHAT IT ANALYZES)

Scope Impact анализирует изменения по направлениям:

1) **Registry impact**
- затрагивает ли INDEX / нумерацию / naming / ссылки

2) **Contract impact**
- меняется ли mini-contract
- меняются ли outputs/inputs/handoff

3) **Dependency impact**
- добавляются/убираются edges
- риск циклов, скрытых зависимостей

4) **Terminology impact**
- меняются ли термины, определения, “style locks”, canonical fields

5) **Level/Class impact**
- меняется ли уровень семейства/движка (L1–L4)
- меняется ли CLASS (DOMAIN/PRODUCTION/META…)

6) **Downstream impact**
- какие движки потребляют outputs изменяемого движка
- какие инструменты/проекты зависят от этого

---

## NON-GOALS

- не утверждает решения (Canon Authority)
- не управляет изменениями (Change Control)
- не проверяет целостность после правки (Consistency)
- не строит официальный граф зависимостей (Dependency Registry)
Он делает “предсказание воздействия” до правки.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- change proposal summary (CHG draft)
- target files list
- mini-contract blocks of touched engines
- index registry sections related to target files
- dependency notes (current edges) if exist

### PRODUCES
- IMPACT REPORT (mandatory artifact)
- severity estimation (D-level suggestion)
- required artifacts list (CR/DG/CY/waiver)
- ordered affected files list (blast radius)

### DEPENDS_ON
- 00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md
- 00_GOVERNANCE_ENGINES/06__DEPENDENCY_REGISTRY_ENG.md
- 00_GOVERNANCE_ENGINES/03__RULE_HIERARCHY_ENG.md
- 00_GOVERNANCE_ENGINES/07__DECISION_APPROVAL_ENG.md

### OUTPUT_TARGET
- Used at Change Control gate G2 (Impact)
- Attached to CHG packet for Canon Authority review

---

## IMPACT CLASSIFICATION (BLAST RADIUS)

### I0 — Local
- 1 file
- no contract change
- no index change
- no downstream consumers

### I1 — Family-local
- several files inside one family
- minor contract clarifications
- downstream impact limited to same family

### I2 — Cross-family
- affects multiple families
- contract/handoff changed
- requires dependency edges update

### I3 — System-wide
- index restructuring
- level/class changes
- new global rules/terms
- risk of cycles or role redefinition

---

## REQUIRED CANON ARTIFACT: IMPACT REPORT

### IMPACT_REPORT SCHEMA (CANON)

- IR_ID: IR-ENG-0001
- DATE:
- TRIGGER:
  - new_engine | edit_engine | restructure | fix_drift | resolve_conflict
- CHANGE_TYPE (expected):
  - PATCH | MINOR | MAJOR
- IMPACT_LEVEL:
  - I0 | I1 | I2 | I3
- TARGET:
  - primary files (list)
- AFFECTED_SCOPE:
  - families affected
  - engines affected
- DIMENSIONS:
  - INDEX_IMPACT: yes/no
  - CONTRACT_IMPACT: yes/no
  - DEP_IMPACT: yes/no
  - TERMS_IMPACT: yes/no
  - LEVEL_IMPACT: yes/no
- DOWNSTREAM:
  - consumers (known)
  - degraded mode allowed? yes/no
- RISKS:
  - top risks (3–7 bullets)
- REQUIRED ARTIFACTS:
  - CR required? yes/no
  - DG required? yes/no
  - CY required? yes/no
  - waiver likely? yes/no
- DECISION LEVEL SUGGESTION:
  - D0 | D1 | D2 | D3
- REQUIRED UPDATES (ORDERED):
  - file-by-file plan
- STOP CONDITIONS:
  - what would block approval (S0 triggers)
- NOTES (optional)

---

## STOP CONDITIONS (S0 BLOCKERS PREDICTION)

Если предсказано хотя бы одно:
- индексный дрейф (file/index mismatch)
- level/class mismatch
- renumbering without full propagation
- dependency cycle risk without break mechanism
- role overlap without owner plan

→ change must be treated as D2/D3 and cannot be “quick patch”.

---

## PROCEDURE (HOW TO RUN IMPACT)

1) Identify the primary change target
- which file is the source of change

2) Determine rule level affected (P0–P3)
- index? governance? README? engine?

3) Read mini-contract of the target
- list produces/consumes/depends_on

4) Map consumers (downstream)
- from known edges / handoff / family expectations

5) Decide blast radius I0–I3

6) Suggest decision level D0–D3

7) Generate Impact Report
- include ordered updates list

8) Route to Change Control (G2) and attach IR

---

## VALIDATION CHECKLIST

- SI1: IR has DIMENSIONS flags
- SI2: IR lists affected files explicitly
- SI3: IR includes decision level suggestion
- SI4: IR lists required artifacts (CR/DG/CY)
- SI5: IR includes stop conditions

---

## INTEGRATION NOTES

- Change Control uses IR at gate G2 (Impact)
- Decision Approval uses IR to set decision level (D0–D3)
- Canon Authority uses IR to understand blast radius before verdict
- Dependency Registry uses IR to pre-plan edge updates

---

OWNER: Universe Engine
LOCK: FIXED
CHANGE_GATE: GOVERNANCE_PIPELINE
