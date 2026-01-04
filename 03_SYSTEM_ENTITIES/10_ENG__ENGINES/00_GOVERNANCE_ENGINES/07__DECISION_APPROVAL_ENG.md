# Decision Approval Engine
FILE: 07__DECISION_APPROVAL_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 00_GOVERNANCE_ENGINES
CLASS: GOVERNANCE (L1)
LEVEL: L1
STATUS: ACTIVE
VERSION: 2.0
ROLE: Standardizes how canonical decisions are proposed, reviewed, approved, and recorded for ENG; provides decision schema, severity levels, required approvals, and linkage to audit/version/lock

---

## PURPOSE

Этот движок вводит единый стандарт:
- как формулировать “решение”
- какие решения требуют утверждения
- как фиксировать решение в канон
- как связывать решение с CHG / CV / AUDIT / VERSION / LOCK

Без него решения будут “в чате” и система потеряет управляемость.

---

## SCOPE (WHAT IS A "DECISION")

Решением считается любая фиксация выбора, которая влияет на систему ENG:

### A) Structural decisions
- добавление/удаление движка
- изменение нумерации/переезд по папкам
- изменение состава семейств

### B) Canon law decisions
- изменение governance правил
- изменение иерархии правил/терминов

### C) Contract decisions
- изменение mini-contract полей
- изменение handoff или dependency edges
- разрешение/запрет циклов

### D) Conflict decisions
- кто owner при role overlap
- какой термин “истинный”
- какой документ побеждает (по Rule Hierarchy)

### E) Lock & Waiver decisions
- FIXED/UNFIXED
- waiver scope + expiry

---

## NON-GOALS

- не определяет истину канона (это Canon Authority)
- не проводит аудит (Consistency)
- не ведёт журнал (Audit Log)
- не управляет процессом изменений (Change Control)
Он задаёт **стандарт**, по которому эти процессы фиксируют решения.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- decision proposals (from authors / governance gates)
- conflict reports (role/term/dep)
- consistency report findings that need a call
- change packets that require decisions

### PRODUCES
- DECISION RECORD (DR) — canonical artifact
- approval matrix outcome (who approved)
- routing instructions (what must be updated: index/deps/audit/version/lock)

### DEPENDS_ON
- 00_GOVERNANCE_ENGINES/03__RULE_HIERARCHY_ENG.md
- 00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md
- 00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG.md
- 00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG.md
- 00_GOVERNANCE_ENGINES/10__VERSIONING_MEMORY_ENG.md

### OUTPUT_TARGET
- Any decision that affects canon must be written as DR and referenced from CHG/AUDIT/CV as applicable

---

## DECISION LEVELS (SEVERITY)

### D0 — Local / low impact
- wording, formatting, minor clarifications
- no contract change
- no index impact
Approval: optional (can be implicit via Change Control PATCH)

### D1 — Minor canon impact
- adds rules but backward-compatible
- minor dependency edge additions (soft)
Approval: required (Canon Authority)

### D2 — System impact
- contract changes
- role boundary changes
- index edits (add/rename/move)
Approval: required (Canon Authority) + must attach CR report

### D3 — Breaking / major
- renumbering families
- removing engines
- changing LEVEL/CLASS
- approving dependency cycles
Approval: required (Canon Authority) + CR + DG/Cycle report + explicit lock plan

---

## APPROVAL MATRIX (WHO MUST SIGN)

Default (until you introduce more roles):

- D0: author + (optional) governance
- D1: Canon Authority
- D2: Canon Authority + Consistency verification (CR)
- D3: Canon Authority + CR + DG/CY + explicit major version bump plan

Все утверждения проходят через:
- Canon Verdict (CV) when it is a canon change
- Audit entry (AL) always when canon changes

---

## CANON ARTIFACT: DECISION RECORD (DR)

### DECISION_RECORD SCHEMA (CANON)

- DR_ID: DR-ENG-0001
- DATE:
- LEVEL: D0 | D1 | D2 | D3
- TOPIC:
  - short title
- CONTEXT:
  - what problem triggered it
- OPTIONS:
  - A:
  - B:
  - (C optional)
- DECISION:
  - chosen option
- RATIONALE:
  - 3–7 bullets
- IMPACT:
  - INDEX: yes/no
  - CONTRACT: yes/no
  - DEP_GRAPH: yes/no
  - LEVEL/CLASS: yes/no
- REQUIRED UPDATES (ORDERED):
  - exact file list + what changes
- VALIDATION REQUIRED:
  - CR required? yes/no
  - DG required? yes/no
  - Cycle report required? yes/no
- APPROVALS:
  - approver(s) + decision (approve/reject/return)
- REFERENCES:
  - CHG_ID (if any)
  - CV_ID (if any)
  - AL_ID (once logged)
  - CR_ID (if any)
  - DG_ID/CY_ID (if any)
- LOCK PLAN:
  - FIXED/UNFIXED + conditions
- NOTES (optional):
  - max 5 bullets

---

## ROUTING RULES (WHAT MUST HAPPEN AFTER DECISION)

If IMPACT.INDEX = yes:
- update `00__INDEX_ALL_ENGINES.md`
- run consistency scan for drift
- log in audit

If IMPACT.CONTRACT = yes:
- update engine mini-contract sections
- update handoff blocks
- update dependency edges (DG snapshot)
- log in audit

If IMPACT.DEP_GRAPH = yes:
- generate DG artifact and attach
- check cycles; produce CY if needed

If IMPACT.LEVEL/CLASS = yes:
- update INDEX + family README + all engines in family
- treat as D3 by default

---

## PROCEDURE (HOW TO USE)

1) Write DR proposal in schema
2) Assign decision level D0–D3
3) Collect required artifacts (CR/DG/CY) if needed
4) Route to Canon Authority for final decision (CV)
5) Execute required updates list
6) Log in Audit Log (AL)
7) Apply LOCK decision when done

---

## VALIDATION CHECKLIST

- DA1: DR has level and approvals
- DA2: DR lists required updates (file-by-file)
- DA3: If index impact → index updated + audit logged
- DA4: If contract/dep impact → DG snapshot exists
- DA5: Any D3 decision has explicit lock plan and version bump plan

---

OWNER: Universe Engine
LOCK: FIXED
CHANGE_GATE: GOVERNANCE_PIPELINE
