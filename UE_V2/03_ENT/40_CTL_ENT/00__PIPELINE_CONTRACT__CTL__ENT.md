# 00__PIPELINE_CONTRACT__CTL__ENT
KIND: ENGINE
ROLE: CTL_CONTRACT
SCOPE: ENT.CTL
STATUS: CANON
VERSION: 1.0.0

## [M] PURPOSE
CTL (контроллер) — слой управления процессом и стандартами.
CTL обязан:
- применить политики (structure/variants/naming/release rules)
- энфорсить NO_GO (анти-мусор и запреты)
- нормализовать выходы под OUTPUT_CONTRACT
- выдать POLICY_REPORT как доказательство применённых правил

CTL не “создаёт заново” контент — он приводит результат ORC к канону и готовности к валидации.

---

## [M] HARD_RULES
1) NO_GO IS LAW
- Любой пункт NO_GO_LIST должен быть проверен.
- Нарушение NO_GO -> FAIL: SCOPE_VIOLATION (через STOP_GAP).

2) OUTPUT_CONTRACT FILTER
- CTL не добавляет лишние артефакты.
- Если ORC выдал больше — CTL помечает extras как IGNORED и не включает в PACK.

3) POLICY REPORT ALWAYS
- Если CTL required, POLICY_REPORT обязателен.

4) DETERMINISM
- Одинаковые входы -> одинаковые политики/правки (без “рандома”).

---

## [M] INPUTS (TOKENS)
REQUIRED:
- ROUTE_TOKEN
- NO_GO_LIST (из ROUTE_TOKEN.REQUIRED_SET.NO_GO_LIST или PROFILE)
- OUTPUT_CONTRACT (из ROUTE_TOKEN.REQUIRED_SET.OUTPUT_CONTRACT)
- ENG_OUTPUTS_TOKEN (из ORC)
- ENGINE_RUN_LEDGER (из ORC)

OPTIONAL:
- BRIEF_TOKEN
- CANON_TOKEN
- PROFILE_KEY
- KB_TOKEN

---

## [M] OUTPUTS (TOKENS)
REQUIRED:
- CONTROLLED_ARTIFACTS
- POLICY_REPORT

OPTIONAL:
- UPDATED_NO_GO_LIST (если CTL добавляет запреты)
- CTL_NOTES

---

## [M] CONTROLLED_ARTIFACTS (minimum schema)
CONTROLLED_ARTIFACTS:
  artifacts:
    - name: "<artifact_name>"
      source_eng_key: "KEY:ENG...."
      status: "kept|edited|ignored"
      notes: "<what was changed>"
  ignored:
    - name: "<artifact_name>"
      reason: "<why ignored>"
  summary:
    kept_count: <int>
    ignored_count: <int>

RULE:
- В kept идут только нужные артефакты под OUTPUT_CONTRACT (или под профиль).
- В ignored — всё лишнее, что создаёт мусор.

---

## [M] POLICY_REPORT (minimum schema)
POLICY_REPORT:
  profile_key: "<ROUTE_TOKEN.ROUTE.PROFILE_KEY>"
  policies_applied:
    - name: "<policy_name>"
      result: "applied|skipped"
      notes: "<one line>"
  no_go_checks:
    - rule: "<no_go_item>"
      status: "pass|fail"
      notes: "<one line>"
  contract_checks:
    - item: "<output_contract_item>"
      status: "present|missing|n/a"
      notes: "<one line>"
  violations:
    - type: "SCOPE_VIOLATION|OTHER"
      detail: "<one line>"
  next_actions:
    - "<minimal next step>"

---

## [M] CANON POLICIES (baseline, profile may extend)
CTL baseline policies:
- P0: Enforce NO_GO_LIST
- P1: Filter artifacts by OUTPUT_CONTRACT
- P2: Naming normalization (consistent names/keys, if applicable)
- P3: Variant policy hook (if profile requires variants)
- P4: Release packaging policy hook (if profile requires schedules)

NOTE:
- Доменные политики (музыка/видео) должны жить в CTL modules, а этот контракт — универсальный.

---

## [M] EXECUTION STEPS (CANON)
### STEP 0 — PRECHECK
- ensure required tokens exist
If missing -> FAIL: MARKER_NOT_CONFIRMED

### STEP 1 — NO_GO ENFORCEMENT
For each item in NO_GO_LIST:
- check compliance (using available tokens and artifact metadata)
- if violation -> add to POLICY_REPORT.violations and FAIL:SCOPE_VIOLATION

### STEP 2 — OUTPUT_CONTRACT FILTER
- Build keep-list from OUTPUT_CONTRACT
- Mark extra artifacts as ignored
- Ensure required contract items are targeted for presence downstream

### STEP 3 — NORMALIZATION (light)
- Normalize naming/structure to match templates
- Do NOT rewrite content deeply (that’s ORC job)

### STEP 4 — EMIT OUTPUTS
- CONTROLLED_ARTIFACTS
- POLICY_REPORT
- (optional) updated no-go list

---

## [M] FAIL / STOP POLICY
- Missing required token -> FAIL: MARKER_NOT_CONFIRMED
- NO_GO violation -> FAIL: SCOPE_VIOLATION
- Contract inconsistency (e.g. empty OUTPUT_CONTRACT on production) -> FAIL: MARKER_NOT_CONFIRMED

On FAIL:
- Provide FIX_LIST minimal:
  - "Remove forbidden artifact/step"
  - "Regenerate missing contract output via ORC"
  - "Tighten profile/no-go"

END.
