# 00__PIPELINE_CONTRACT__VAL_ENG__VAL__ENT
SCOPE: UE_V2 / 03_ENT / 50_VAL_ENT / 11_VALIDATION_ENGINES
DOC_TYPE: PIPELINE_CONTRACT
DOMAIN: VAL_ENG_VAL_ENT
UID: UE.V2.ENT.PIPE.VAL_ENG_VAL_ENT.001
VERSION: 1.1.0
STATUS: ACTIVE
OWNER: VAL_ENT
MODE: REPO (USAGE-ONLY, NO-EDIT)

---

## [M] PURPOSE
PIPELINE_CONTRACT — протокол вызова валидирующих engines (VAL_ENG).
Определяет:
- какие валидаторы существуют (через KEY)
- порядок прогонов (stages)
- обязательные валидаторы для production
- входы/выходы (tokens + reports)
- stop/fail правила

---

## [M] HARD_RULES
1) KEY-FIRST
- Этот контракт ссылается только на KEY (из INDEX_MANIFEST).
- PATH/RAW не используются для исполнения.

2) MANDATORY COVERAGE
- Для production задач обязательны:
  - VAL_ENG.COVERAGE_AND_OUTPUT_CONTRACT (нельзя пропускать роли/движки/выходы)

3) STOP ON FAIL
- Если mandatory валидатор FAIL → STOP_GAP. Никакого “финала”.

4) NO TRASH
- Валидаторы не добавляют новый scope. Они только проверяют то, что уже произведено.

---

## [M] INPUTS (EXPECTED TOKENS)
REQUIRED (for production):
- ROUTE_TOKEN
- ROLE_LEDGER
- OUTPUT_LEDGER
- ENGINE_PLAN_TOKEN
- ENGINE_RUN_LEDGER

OPTIONAL:
- BRIEF_TOKEN
- CANON_TOKEN
- POLICY_REPORT
- PROFILE_KEY
- RUNTIME_MANIFEST

---

## [M] OUTPUTS
REQUIRED:
- VAL_REPORT (aggregated)
  - STATUS: PASS|FAIL
  - FAIL_CODE (if FAIL)
  - FAIL_REASONS[]
  - FIX_LIST[]
  - SUBREPORTS[] (per-engine)
- VAL_LEDGER (what validators ran)
  - entries: [{ key, status, notes }]

---

## [M] STAGES (ORDER)
### STAGE 0 — PRECHECK (always)
Goal: проверить наличие базовых токенов и контрактов, чтобы дальше не было мусора.

MANDATORY_ENGINES:
- VAL_ENG.ERROR_DETECTION

### STAGE 1 — COVERAGE + OUTPUT CONTRACT (production lock)
Goal: не дать пропускать роли/движки/обязательные выходы.

MANDATORY_ENGINES (production):
- VAL_ENG.COVERAGE_AND_OUTPUT_CONTRACT

### STAGE 2 — CONSISTENCY (optional by profile)
Goal: консистентность фактов/структуры/контекста.

OPTIONAL_ENGINES:
- VAL_ENG.FACT_CONSISTENCY

### STAGE 3 — LANGUAGE (optional by profile)
OPTIONAL_ENGINES:
- VAL_ENG.LANGUAGE_LINGUISTICS

### STAGE 4 — CULTURE/HISTORY/SCIENCE (optional by profile)
OPTIONAL_ENGINES:
- VAL_ENG.CULTURAL_ACCURACY
- VAL_ENG.HISTORICAL_ACCURACY
- VAL_ENG.SCIENTIFIC_PLAUSIBILITY

NOTE:
- Какие optional валидаторы включать — решает PROFILE/REQUIRED_VAL_KEYS из ROUTE_TOKEN.
- PIPE/VAL обязаны запускать только разрешённые ключи из REQUIRED_VAL_KEYS (+ mandatory из этого контракта).

---

## [M] REQUIRED ENGINE SET (by execution class)
### CLASS: PRODUCTION (content factory)
MANDATORY_KEYS:
- VAL_ENG.ERROR_DETECTION
- VAL_ENG.COVERAGE_AND_OUTPUT_CONTRACT

### CLASS: SYS_PATCH (system maintenance)
MANDATORY_KEYS:
- VAL_ENG.ERROR_DETECTION
OPTIONAL_KEYS (if needed):
- VAL_ENG.FACT_CONSISTENCY

---

## [M] EXECUTION RULES
1) Resolve engine files:
- All VAL_ENG keys resolve via:
  11_VALIDATION_ENGINES/00__INDEX_MANIFEST__VAL_ENG__VAL__ENT

2) Run list:
- Build RUN_LIST =
  mandatory for class + ROUTE_TOKEN.REQUIRED_SET.REQUIRED_VAL_KEYS (mapped to VAL_ENG keys if you use that layer)
- Deduplicate while preserving stage order.

3) Collect reports:
- Each validator returns SUBREPORT:
  - KEY
  - STATUS
  - FAIL_CODE (if FAIL)
  - REASONS[]
  - FIX_LIST[]

4) Aggregate:
- If any MANDATORY validator FAIL -> overall FAIL and STOP_GAP.

---

## [M] FAIL / STOP POLICY
- If required input token missing -> FAIL: MARKER_NOT_CONFIRMED
- If required validator key not resolvable -> FAIL: ENTRYPOINT_MISSING
- If mandatory validator FAIL -> FAIL (propagate its FAIL_CODE) + STOP_GAP

---

## [M] REFERENCES (KEYS)
INDEX:
- INDEX_MANIFEST (SELF): 00__INDEX_MANIFEST__VAL_ENG__VAL__ENT

MANDATORY ENGINES:
- VAL_ENG.ERROR_DETECTION
- VAL_ENG.COVERAGE_AND_OUTPUT_CONTRACT

OPTIONAL ENGINES:
- VAL_ENG.FACT_CONSISTENCY
- VAL_ENG.LANGUAGE_LINGUISTICS
- VAL_ENG.CULTURAL_ACCURACY
- VAL_ENG.HISTORICAL_ACCURACY
- VAL_ENG.SCIENTIFIC_PLAUSIBILITY

END.
