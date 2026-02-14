# 07__VAL_ENG__COVERAGE_AND_OUTPUT_CONTRACT__ENG__VAL__ENT
KIND: ENGINE
ROLE: VAL
SCOPE: ENT.VAL
STATUS: CANON
VERSION: 1.0.0

VAL_KEYS:
- KEY:VAL.ENGINE_COVERAGE_GATE
- KEY:VAL.OUTPUT_CONTRACT_GATE

## 0) PURPOSE
Два обязательных гейта, которые делают систему “непропускаемой”:
1) ENGINE_COVERAGE_GATE:
   - доказывает, что все required роли и required движки реально отработали
2) OUTPUT_CONTRACT_GATE:
   - доказывает, что выданы все обязательные артефакты (output contract)

Если любой гейт FAIL → STOP_GAP (нельзя считать результат “готовым/финальным”).

---

## 1) INPUTS
REQUIRED:
- ROUTE_TOKEN
- ROLE_LEDGER
- OUTPUT_LEDGER
- ENGINE_PLAN_TOKEN
- ENGINE_RUN_LEDGER

OPTIONAL:
- PROFILE (если используется)
- NO_GO_LIST
- POLICY_REPORT
- RUNTIME_MANIFEST

---

## 2) OUTPUTS
VAL_REPORT:
  STATUS: "<PASS|FAIL>"
  FAIL_CODE: "<optional>"
  FAIL_REASONS: []
  FIX_LIST: []
  COVERAGE_SUMMARY: {}
  OUTPUT_SUMMARY: {}

---

## 3) GATE 1 — KEY:VAL.ENGINE_COVERAGE_GATE
### 3.1 Checks
A) REQUIRED ROLES coverage
- ROUTE_TOKEN.REQUIRED_SET.REQUIRED_ROLES должен существовать и быть списком
- для каждой роли из REQUIRED_ROLES должна быть запись в ROLE_LEDGER
- статус каждой required роли должен быть "ran"
- у каждой required роли должны быть outputs_produced (минимум baseline ниже)

B) REQUIRED ENGINE coverage
- ENGINE_PLAN_TOKEN.required_eng_keys поле MUST exist (как поле, даже если список пустой на SYS-задачах)
- для каждого required_eng_key должна быть запись в ENGINE_RUN_LEDGER.entries
- статус каждой required eng должен быть "ran" (если профиль не разрешил skip)

C) Allowed/No-Go constraints
- если ENGINE_PLAN_TOKEN.allowed_eng_keys присутствует:
  - любой engine со статусом "ran" должен входить в allowed_eng_keys
- если ENGINE_PLAN_TOKEN.no_go_eng_keys присутствует:
  - ни один из no_go_eng_keys не может иметь статус "ran"

### 3.2 Baseline outputs per role (minimum)
Эти ожидания можно ужесточать профилем, но ниже — минимум:
- SPC: BRIEF_TOKEN, ENGINE_PLAN_TOKEN
- ORC: ENGINE_RUN_LEDGER, ENG_OUTPUTS_TOKEN (или эквивалент)
- CTL: CONTROLLED_ARTIFACTS (или POLICY_REPORT)
- VAL: VAL_REPORT (от этого валидатора)
- QA (если required): QA_REPORT

Если роль "ran", но baseline outputs не присутствуют → FAIL: MARKER_NOT_CONFIRMED

### 3.3 PASS conditions
PASS если:
- REQUIRED_ROLES покрыты: у всех status=ran и есть baseline outputs
- ENGINE_PLAN_TOKEN.required_eng_keys поле существует
- каждый required_eng_key имеет ledger entry и status=ran
- нет нарушений allowed/no-go

### 3.4 FAIL behavior (codes)
- FAIL: MARKER_NOT_CONFIRMED
  - отсутствуют REQUIRED_ROLES / ledgers / required_eng_keys как поле / baseline outputs
- FAIL: ENTRYPOINT_MISSING
  - required_eng_key нет в ENGINE_RUN_LEDGER (не доказано исполнение)
- FAIL: SCOPE_VIOLATION
  - engine ran вне allowed или из no-go

### 3.5 FIX_LIST (minimal actions)
При FAIL валидатор обязан вернуть FIX_LIST вида:
- "Add missing ledger entry for <ROLE/ENG_KEY>"
- "Provide <missing output> from <ROLE>"
- "Remove/forbid <ENG_KEY> (violates allowed/no-go)"
- "Add required_eng_keys field to ENGINE_PLAN_TOKEN"

---

## 4) GATE 2 — KEY:VAL.OUTPUT_CONTRACT_GATE
### 4.1 Checks
- ROUTE_TOKEN.REQUIRED_SET.OUTPUT_CONTRACT должен существовать и быть списком
- OUTPUT_LEDGER должен содержать запись для каждого пункта контракта
- для каждого пункта: present=true

### 4.2 PASS conditions
PASS если:
- OUTPUT_CONTRACT существует
- все пункты контракта present=true

### 4.3 FAIL behavior (codes)
- FAIL: MARKER_NOT_CONFIRMED
  - OUTPUT_CONTRACT отсутствует или OUTPUT_LEDGER отсутствует
- FAIL: ENTRYPOINT_MISSING
  - обязательный output отсутствует (present=false)

### 4.4 FIX_LIST examples
- "Add missing contract output: <OUTPUT_NAME>"
- "Update OUTPUT_LEDGER to include: <OUTPUT_NAME>"

---

## 5) REPORT TEMPLATE (recommended structure)
VAL_REPORT:
  STATUS: "<PASS|FAIL>"
  FAIL_CODE: "<optional>"
  FAIL_REASONS:
    - "<reason>"
  FIX_LIST:
    - "<minimal fix>"
  COVERAGE_SUMMARY:
    required_roles: []
    roles_ran: []
    missing_roles: []
    required_eng_keys: []
    eng_ran: []
    missing_eng: []
    scope_violations: []
  OUTPUT_SUMMARY:
    contract: []
    present: []
    missing: []

---

## 6) STOP RULE
Если любой гейт FAIL:
- STATUS=FAIL
- PACK не имеет права маркировать результат как “финал”.
END.
