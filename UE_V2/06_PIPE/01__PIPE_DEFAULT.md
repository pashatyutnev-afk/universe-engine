# 01__PIPE_DEFAULT
KIND: ENGINE
ROLE: PIPE
SCOPE: SYSTEM
STATUS: CANON
VERSION: 1.0.0

## 0) PURPOSE
Единый исполнительный конвейер.
PIPE принимает ROUTE_TOKEN и:
- резолвит требуемые модули (IDX/KEY)
- энфорсит REQUIRED_SET (roles/outputs/gates)
- запускает стадии SPC → ORC → CTL → VAL → (QA) → PACK
- останавливает выполнение при GAP/FAIL (STOP_GAP)
- выдаёт артефакты (FULL_PATCH / KB_PATCH / PATCH_OUTPUT) и отчёты

PIPE НЕ “думает” вместо ROUTER и НЕ расширяет scope.

---

## 1) INPUTS
REQUIRED:
- ROUTE_TOKEN (из 00_BOOT/09__TASK_ROUTER)

OPTIONAL:
- USER_FILES
- USER_CONTEXT
- RUNTIME_MANIFEST (если есть)

---

## 2) OUTPUTS
PIPE всегда возвращает:
- PACK_OUTPUT (итоговые артефакты)
- VAL_REPORT (PASS/FAIL + причины)
- EXEC_LEDGER (что реально запускалось)
- (optional) QA_REPORT
- (for repo patching) CHANGELOG_ENTRY + NEXT_POINTER

---

## 3) CORE LAWS (ENFORCEMENT)
### 3.1 Required Set is law
PIPE обязан исполнять только то, что указано в:
- ROUTE_TOKEN.REQUIRED_SET
И ничего сверх (иначе FAIL:SCOPE_VIOLATION).

### 3.2 No silent skipping
Если REQUIRED_ROLES/OUTPUT_CONTRACT/REQUIRED_VAL_KEYS не выполнены:
- STOP_GAP + FAIL_CODE
Никаких “ну ок”.

### 3.3 KEY-first resolution
Любой модуль/движок/валидатор подключается только через:
- KEY → (MANIFEST) → LOCAL_PATH
Прямые пути и RAW навигация запрещены.

---

## 4) EXECUTION LEDGERS (доказательство работы)
PIPE ведёт 3 леджера:

### 4.1 ROLE_LEDGER
Для каждой роли из REQUIRED_ROLES:
- status: ran/skipped/failed
- outputs_produced: []

### 4.2 ENGINE_RUN_LEDGER
Для каждого eng_key из ENGINE_PLAN_TOKEN.required_eng_keys:
- status: ran/skipped/failed
- outputs_produced: []
- notes

### 4.3 OUTPUT_LEDGER
Для каждого output из OUTPUT_CONTRACT:
- present: true/false
- source: SPC/ORC/CTL/VAL/QA/PACK

Эти леджеры потом проверяет VAL.COVERAGE.

---

## 5) STAGES (CANON ORDER)
### STAGE 0 — PRECHECK (ROUTE_TOKEN sanity)
Check:
- ROUTE_TOKEN exists
- REQUIRED_SET exists
- REQUIRED_ROLES exists (for production)
- OUTPUT_CONTRACT exists
- REQUIRED_VAL_KEYS includes:
  - KEY:VAL.ENGINE_COVERAGE_GATE
  - KEY:VAL.OUTPUT_CONTRACT_GATE
If missing -> STOP_GAP (FAIL:MARKER_NOT_CONFIRMED)

### STAGE 1 — RESOLVE (IDX + MODULES)
1) Resolve REQUIRED_IDX via manifests
2) Resolve PIPE_SELECTED key
3) Resolve REQUIRED_VAL_KEYS
If any key cannot be resolved -> STOP_GAP (FAIL:ENTRYPOINT_MISSING / FAIL:FILE_NOT_FOUND)

### STAGE 2 — SPC (INTAKE → PLAN)
SPC обязан выдать минимум:
- BRIEF_TOKEN
- ENGINE_PLAN_TOKEN
- OUTPUT_CONTRACT (если ROUTER не задал — но в каноне ROUTER задаёт)

PIPE rules:
- If "SPC" in REQUIRED_ROLES and BRIEF_TOKEN missing -> FAIL
- If "SPC" in REQUIRED_ROLES and ENGINE_PLAN_TOKEN missing -> FAIL

Update ROLE_LEDGER[SPC].

#### ENGINE_PLAN_TOKEN (minimum schema)
ENGINE_PLAN_TOKEN:
- required_eng_keys: []
- allowed_eng_keys: [] (optional)
- no_go_eng_keys: [] (optional)
- expected_outputs: [] (optional)

If required_eng_keys missing (field absent) -> FAIL:MARKER_NOT_CONFIRMED
(пустой список допустим только на SYS-патчах, не на контент-производстве)

### STAGE 3 — ENG RESOLVE + ORC (RUN ENGINES → DRAFT)
If "ORC" in REQUIRED_ROLES:
- Resolve each eng_key from ENGINE_PLAN_TOKEN.required_eng_keys
- Run engines according to ENG pipeline contract
- Produce ENG_OUTPUTS_TOKEN
- Produce ENGINE_RUN_LEDGER (proof)

Update ROLE_LEDGER[ORC].

Rules:
- If any required_eng_key cannot be resolved -> FAIL:ENTRYPOINT_MISSING
- If engine fails -> mark failed; continue only if profile allows (default: FAIL)

### STAGE 4 — CTL (POLICIES → CONTROLLED)
If "CTL" in REQUIRED_ROLES:
- Apply policies (NO_GO, naming, variants, structure)
- Produce CONTROLLED_ARTIFACTS + POLICY_REPORT
Update ROLE_LEDGER[CTL].

Rules:
- If CTL produces outputs outside OUTPUT_CONTRACT and not requested -> ignore (do not add)
- If required policy outputs missing -> FAIL

### STAGE 5 — VAL (QUALITY + COVERAGE)
If "VAL" in REQUIRED_ROLES:
VAL runs at least:
- VAL.ENGINE_COVERAGE_GATE (required engines executed)
- VAL.OUTPUT_CONTRACT_GATE (all outputs present)
Plus any domain gates in REQUIRED_VAL_KEYS.

VAL produces:
- VAL_REPORT (PASS/FAIL, reasons, fix list)

Update ROLE_LEDGER[VAL].

Rules:
- If FAIL -> STOP_GAP (do not PACK as final, only provide fix instructions)
- If PASS -> proceed

### STAGE 6 — QA (OPTIONAL BUT SUPPORTED)
If "QA" in REQUIRED_ROLES or profile requires:
- Run regression checks
- Produce QA_REPORT
Update ROLE_LEDGER[QA].

### STAGE 7 — PACK (DELIVERABLES)
PACK must:
- compile PACK_OUTPUT according to ARTIFACT_TYPE:
  - FULL_PATCH -> output files for replacement
  - KB_PATCH -> KB module(s)
  - PLAN/AUDIT -> structured doc
- attach EXEC_LEDGER (ledgers summary)
- update CHANGELOG_ENTRY and NEXT_POINTER if patching repo

PACK is allowed only if VAL_REPORT=PASS for production outputs.

---

## 6) STOP_GAP / FAIL CODES (MANDATORY)
If any condition triggers STOP:
- emit FAIL_CODE
- emit what is missing (single smallest next action)
- do not fabricate missing modules

Common FAIL triggers:
- INPUT_ABSENT
- ENTRYPOINT_MISSING
- FILE_NOT_FOUND
- MARKER_NOT_CONFIRMED
- SCOPE_VIOLATION
- WEB_INSUFFICIENT (if web was allowed and insufficient)

---

## 7) OUTPUT CONTRACT (STRICT)
OUTPUT_CONTRACT is a list. PIPE must ensure every item is present in OUTPUT_LEDGER.
Default expectations:
- SYS patches: PATCH_OUTPUT, VAL_REPORT, CHANGELOG_ENTRY, NEXT_POINTER
- Content production: BRIEF_TOKEN, ENGINE_PLAN_TOKEN, ENGINE_RUN_LEDGER, VAL_REPORT, PACK_OUTPUT

If any missing -> FAIL (VAL.OUTPUT_CONTRACT_GATE).

---

## 8) NOTES
- PIPE_DEFAULT is universal.
- Domain-specific behavior must be expressed via PROFILE + REQUIRED_SET (not by editing PIPE_DEFAULT per domain).
END.
