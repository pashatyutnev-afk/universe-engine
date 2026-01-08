# CHANGE CONTROL ENGINE (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
LAYER: 03_SYSTEM_ENTITIES
FAMILY: 00_GOVERNANCE_ENGINES
DOC_TYPE: ENGINE
CLASS: GOVERNANCE (L1)
LEVEL: L1
STATUS: ACTIVE
VERSION: 1.0.0
UID: <UE.ENG.GOV.CHANGE_CONTROL.001>
OWNER: SYSTEM
ROLE: Canonical change workflow controller (proposal → checks → decision → apply → audit → verify → close)
LOCK: FIXED

---

## 0) PURPOSE (LAW)

Этот движок задаёт **единственный допустимый процесс** изменения канона.

What this engine is for:
- стандартизировать “Change Package” (набор обязательных артефактов изменения)
- управлять стадиями: propose → validate → decide → apply → audit → verify → close
- запрещать “грязные правки” без пакета, без отката и без аудита
- обеспечивать совместимость с фиксированными индексами (LOCK: FIXED)

Primary outcome:
- любое канон-изменение имеет полный Change Package и проходит через обязательные шаги.

Non-goals (hard):
- НЕ принимает решение approve/reject (это Canon Authority)
- НЕ делает глубокую проверку логики контента (это Consistency + Validators)
- НЕ подменяет dependency registry (но требует обновлять его при изменениях зависимостей)

---

## 1) BOUNDARY (ANTI-DUPLICATION)

### 1.1 Owned area
- формат и стадии Change Package
- правила “no direct canon edit without package”
- требования к rollback/backout
- требования к проверкам до и после

### 1.2 Forbidden overlap
- не заменяет Audit Log (только требует запись)
- не заменяет Rule Hierarchy (использует как reference)
- не заменяет Scope/Risk engines (может требовать их outputs как условия)

### 1.3 Interface contract
- Inputs: proposal + affected list + change note + optional reports
- Outputs: change package record + stage statuses
- Enforcement: cannot close change without decision + audit + post-verify

---

## 2) MINI-CONTRACT (MANDATORY)

CONSUMES:
- <ARTIFACT: CHANGE_PROPOSAL>
- <ARTIFACT: CHANGE_NOTE>                 # summary/reason/impact
- <ARTIFACT: AFFECTED_FILES_LIST>
- <ARTIFACT: DIFF_SUMMARY?>
- <ARTIFACT: SCOPE_IMPACT_REPORT?>
- <ARTIFACT: RISK_ASSESSMENT?>
- <ARTIFACT: CONSISTENCY_REPORT?>
- <ARTIFACT: DEPENDENCY_RECORDS?>         # если затрагивает зависимости

PRODUCES:
- <ARTIFACT: CHANGE_PACKAGE_RECORD>       # обязательный “паспорт” изменения
- <ARTIFACT: STAGE_CHECKLIST>             # шаги и отметки
- <ARTIFACT: ROLLBACK_PLAN>               # обязателен для средних/больших правок
- <ARTIFACT: CLOSEOUT_REPORT>             # итог: что сделано, что проверено
- <ARTIFACT: AUDIT_RECORD_REF>            # ссылка на audit record (обязательная)

DEPENDS_ON:
- [00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG]
- [00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG]

OUTPUT_TARGET:
- `99_LOGS/LOG__CHANGES.md` + `99_LOGS/LOG__AUDIT.md` (refs)

---

## 3) CHANGE PACKAGE (REQUIRED) — STANDARD

### 3.1 Change Package must include
REQUIRED (always):
- CHANGE_ID
- DATE
- AUTHOR
- CHANGE_TYPE (PATCH/MINOR/MAJOR/HARD-RESET/HOTFIX/DEPRECATION/RENAMING/MOVE/DELETE/ADD)
- CANON_IMPACT (YES/NO)
- AFFECTED_FILES_LIST (concrete)
- SUMMARY / REASON / IMPACT
- DECISION_REF (from Canon Authority)
- AUDIT_RECORD_REF (from Audit Log)
- POST_VERIFY_RESULT (PASS/FAIL)

REQUIRED (conditional):
- ROLLBACK_PLAN — required if:
  - CHANGE_TYPE in {MAJOR, HARD-RESET, MOVE, DELETE}
  - or if any affected file has LOCK: FIXED
- DEPENDENCY_UPDATES — required if:
  - any engine DEPENDS_ON changed
  - any registry/index order changed
- SCOPE_IMPACT_REPORT — required if:
  - global indexes / fixed indexes changed
  - cross-layer entrypoints changed
- RISK_ASSESSMENT — required if:
  - change touches law/standards/registries in a way that can break navigation

---

## 4) WORKFLOW (MANDATORY STAGES)

### Stage S0 — PROPOSE
Inputs:
- CHANGE_PROPOSAL + CHANGE_NOTE + AFFECTED_FILES_LIST
Outputs:
- CHANGE_PACKAGE_RECORD (draft) + stage checklist

### Stage S1 — PRE-CHECK
Do:
- header compliance check (status/lock/version/uid single instance)
- naming/numbering check (NN matches)
- identify required conditional artifacts (rollback/risk/scope/dependency)
Outputs:
- PRECHECK_RESULT: PASS or REQUIRED_ADDITIONS

### Stage S2 — DECISION
Do:
- request Canon Authority decision
Outputs:
- DECISION_REF

### Stage S3 — APPLY
Do:
- apply changes (out of scope who applies; this stage records that it happened)
Outputs:
- DIFF_SUMMARY (optional), updated affected list if changed

### Stage S4 — AUDIT
Do:
- create audit record for the applied change
Outputs:
- AUDIT_RECORD_REF

### Stage S5 — POST-VERIFY
Do:
- run Consistency checks and registry integrity checks (as available)
- confirm that navigation entrypoints still resolve (existence rule)
Outputs:
- POST_VERIFY_RESULT: PASS/FAIL + notes

### Stage S6 — CLOSE
Do:
- write closeout report
- mark change package as closed
Outputs:
- CLOSEOUT_REPORT

Rule:
- No CLOSE without DECISION_REF + AUDIT_RECORD_REF + POST_VERIFY_RESULT=PASS.

---

## 5) HARD GATES (ENFORCEMENT)

- G1: No change without affected list  
  FAIL → stop at S0

- G2: No canon-impacting change without decision  
  FAIL → cannot pass S2

- G3: No canon-impacting change without audit  
  FAIL → cannot pass S4 / cannot close

- G4: Fixed index safety  
  If any affected LOCK: FIXED and no rollback plan → FAIL

- G5: Dependency transparency  
  If DEPENDS_ON changed and no dependency record → FAIL

- G6: Post-verify required  
  If POST_VERIFY missing or FAIL → cannot close

---

## 6) OUTPUT ARTIFACTS (STANDARD FORMS)

### 6.1 CHANGE_PACKAGE_RECORD (REQUIRED)
FORMAT:

- CHANGE_ID: <UE.CHANGE.YYYY-MM-DD.NNN>
- DATE:
- AUTHOR:
- CHANGE_TYPE:
- CANON_IMPACT:
- SCOPE:
- AFFECTED:
  - ITEM: <DOC|INDEX|TEMPLATE|ENGINE|REGISTRY|MAP>
    PATH:
    UID: <optional>
- SUMMARY:
- REASON:
- IMPACT:
- REQUIRED_ARTIFACTS:
  - <rollback_plan?> <scope_impact?> <risk_assessment?> <dependency_updates?> <consistency_report?>
- STAGES:
  - S0: <DONE|PENDING>
  - S1:
  - S2:
  - S3:
  - S4:
  - S5:
  - S6:
- DECISION_REF:
- AUDIT_RECORD_REF:
- POST_VERIFY_RESULT:
- NOTES:

### 6.2 STAGE_CHECKLIST (REQUIRED)
- S0 propose: done when ...
- S1 pre-check: done when ...
- ...
- S6 close: done when ...

### 6.3 ROLLBACK_PLAN (CONDITIONAL)
- What to revert
- How to revert
- What signals success
- What to do if revert fails

### 6.4 CLOSEOUT_REPORT (REQUIRED)
- What was changed
- What was verified
- Remaining risks (if any)
- Links/refs to decision + audit + checks

---

## 7) EXAMPLES (GOOD / BAD)

### 7.1 Good example
Change:
- PATCH: обновили шаблон governance движка, не трогая порядок и индексы.
Flow:
- S0 propose + affected list
- S1 precheck pass
- S2 decision accept
- S3 apply
- S4 audit created
- S5 post-verify pass
- S6 close complete

### 7.2 Bad example
Change:
- “удалил индексы и переименовал файлы” без списка и без rollback.
Fail:
- G1 (no affected list) + G4 (no rollback) + G3 (no audit)

Fix:
- собрать package, добавить rollback, пройти decision/audit.

---

## 8) FAILURE MODES & EDGE CASES

- Emergency hotfix  
  → allowed, but must still produce: decision + audit (можно post-facto, но обязательно)

- Rename/move breaking raw links  
  → require rollback plan + explicit mapping OLD→NEW + decision conditions

- Partial application  
  → post-verify fails; change cannot be closed; must either complete or rollback

---

## 9) REL / XREF (UID-FIRST)

REL:
- REL: REQUIRES | TARGET_UID: <UE.ENG.GOV.CANON_AUTHORITY.001> | WHY: canon changes need decision
- REL: REQUIRES | TARGET_UID: <UE.ENG.GOV.AUDIT_LOG.001> | WHY: canon changes must be audited
- REL: USES | TARGET_UID: <UE.ENG.GOV.RULE_HIERARCHY.001> | WHY: conflicts resolved by precedence
- REL: REQUESTS | TARGET_UID: <UE.ENG.GOV.CONSISTENCY.###> | WHY: post-verify integrity check
- REL: REQUESTS | TARGET_UID: <UE.ENG.GOV.DEPENDENCY_REGISTRY.###> | WHY: dependency updates must be recorded

RULE:
- RAW links в индексах/реестрах.
- Здесь — UID-first.

--- END.
