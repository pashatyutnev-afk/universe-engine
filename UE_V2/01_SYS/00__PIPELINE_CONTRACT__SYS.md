FILE: UE_V2/01_SYS/00__PIPELINE_CONTRACT__SYS.md
SCOPE: UE_V2 / 01_SYS
DOC_TYPE: PIPELINE_CONTRACT
DOMAIN: SYS
UID: UE.V2.SYS.PIPELINE_CONTRACT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: Contract has no RAW

---

## [M] PURPOSE
PIPELINE_CONTRACT — навигатор действий для реалма 01_SYS.
Не хранит RAW-адреса. Работает через KEY и резолвит адреса в INDEX_MANIFEST.
Роутит в SYS под-реалмы через их INDEX_MANIFEST и дальше передаёт управление их PIPELINE_CONTRACT.

## [M] HARD_RULES
- Запрещено хранить RAW внутри CONTRACT (без исключений).
- Все обращения: TARGET_KEY -> resolve via INDEX_MANIFEST -> open.
- Выполнение по STEP-RUN: один шаг = одна пачка действий.
- Никаких догадок: SUBREALM_HINT обязателен.
- Под-реалмовый PIPELINE_CONTRACT обязателен и резолвится внутри под-реалмового INDEX_MANIFEST.

## [M] REQUIRED_KEYS (must exist in SYS INDEX_MANIFEST)
- INDEX_MANIFEST
- PIPELINE_CONTRACT
- SYS.TPL_SYS.INDEX_MANIFEST
- SYS.SYS_LAW.INDEX_MANIFEST

## [M] SUBREALM_SELECTOR (no guessing)
# RULE: SUBREALM_HINT must be one of these tokens.
- TPL_SYS: SYS.TPL_SYS.INDEX_MANIFEST
- SYS_LAW: SYS.SYS_LAW.INDEX_MANIFEST

## [M] FAIL_CODES
- UE.FAIL.INPUT_ABSENT
- UE.FAIL.MISSING_KEY
- UE.FAIL.INVALID_SUBREALM_HINT
- UE.FAIL.SUBREALM_PIPELINE_MISSING

## [M] CONTRACT_HEADER
- REALM_ID: UE_V2/01_SYS
- DOMAIN: SYS
- ARTIFACT_TYPES: [INDEX, PIPE, TPL, LAW, OUTPUT_PACK, LOG]
- DEFAULT_MODE: FAST

## [M] EXEC_MODEL (how it runs)
1) Resolve SYS INDEX_MANIFEST via KEY: INDEX_MANIFEST
2) Validate REQUIRED_KEYS exist
3) Resolve SUBREALM_INDEX_KEY via SUBREALM_SELECTOR(SUBREALM_HINT)
4) Open SUBREALM INDEX_MANIFEST (resolved from SYS index)
5) Inside subrealm index, resolve KEY: PIPELINE_CONTRACT and open it
6) Handoff: continue execution in subrealm pipeline

## [M] STEP-RUN (canonical)
Each step block format:
- STEP: S<n>
  GOAL: <one line>
  INPUTS: [<tokens>]
  TARGETS: [<KEYS_ONLY>]
  ACTIONS:
    - <imperative action>
  OUTPUTS: [<tokens/artifacts>]
  CHECKS: [<gates>]
  FAIL: <FAIL_CODE_IF_ANY>
  NEXT: "го"

## [M] STEPS

- STEP: S0
  GOAL: Entry sanity and deterministic subrealm selection
  INPUTS: [TASK_TEXT, SUBREALM_HINT, MODE_HINT?]
  TARGETS: [INDEX_MANIFEST]
  ACTIONS:
    - Ensure TASK_TEXT exists, else FAIL
    - Ensure SUBREALM_HINT exists, else FAIL
    - Validate SUBREALM_HINT is one of SUBREALM_SELECTOR tokens, else FAIL
    - Decide EXEC_MODE using MODE_HINT or DEFAULT_MODE
  OUTPUTS: [TASK_TOKEN, EXEC_MODE, SUBREALM_HINT]
  CHECKS: [TASK_PRESENT, SUBREALM_HINT_VALID]
  FAIL: UE.FAIL.INVALID_SUBREALM_HINT
  NEXT: "го"

- STEP: S1
  GOAL: Load SYS navigation layer and validate readiness
  INPUTS: [TASK_TOKEN]
  TARGETS: [INDEX_MANIFEST, PIPELINE_CONTRACT]
  ACTIONS:
    - Resolve INDEX_MANIFEST via KEY: INDEX_MANIFEST
    - Validate ALL REQUIRED_KEYS exist in SYS INDEX_MANIFEST ENTRIES
  OUTPUTS: [SYS_READY]
  CHECKS: [REQUIRED_KEYS_OK]
  FAIL: UE.FAIL.MISSING_KEY
  NEXT: "го"

- STEP: S2
  GOAL: Enter subrealm via subrealm index and open subrealm pipeline
  INPUTS: [TASK_TOKEN, SUBREALM_HINT]
  TARGETS: [INDEX_MANIFEST]
  ACTIONS:
    - Map SUBREALM_HINT -> SUBREALM_INDEX_KEY via SUBREALM_SELECTOR
    - Resolve and open SUBREALM INDEX_MANIFEST using SUBREALM_INDEX_KEY
    - Inside SUBREALM INDEX_MANIFEST, resolve KEY: PIPELINE_CONTRACT
    - Open SUBREALM PIPELINE_CONTRACT
  OUTPUTS: [SUBREALM_INDEX_KEY, SUBREALM_PIPELINE_KEY]
  CHECKS: [SUBREALM_INDEX_OK, SUBREALM_PIPELINE_OK]
  FAIL: UE.FAIL.SUBREALM_PIPELINE_MISSING
  NEXT: "го"

- STEP: S3
  GOAL: Handoff summary (KEYS only) and continue
  INPUTS: [SUBREALM_INDEX_KEY, SUBREALM_PIPELINE_KEY]
  TARGETS: [INDEX_MANIFEST]
  ACTIONS:
    - Return route summary (which subrealm, which keys opened)
    - Continue in subrealm pipeline
  OUTPUTS: [ROUTE_SUMMARY]
  CHECKS: [TRACE_PRESENT]
  FAIL: UE.FAIL.MISSING_KEY
  NEXT: "го"
