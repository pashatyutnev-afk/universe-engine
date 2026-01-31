FILE: UE_V2/04_NAV/00__NAV__PIPELINE_CONTRACT.md
SCOPE: UE_V2 / 04_NAV
DOC_TYPE: PIPELINE_CONTRACT
DOMAIN: NAV
UID: UE.V2.NAV.PIPELINE_CONTRACT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: Contract has no RAW

---

## [M] PURPOSE
NAV PIPELINE_CONTRACT — навигатор работы с навигационными панелями (IDX) в 04_NAV.
Не хранит RAW. Работает через KEY и резолвит адреса в NAV INDEX_MANIFEST.
Основная задача: по ROUTE_TOKEN / NAV_HINT выбрать нужный IDX и подтвердить, что он доступен.

## [M] HARD_RULES
- Запрещено хранить RAW внутри CONTRACT (без исключений).
- Все обращения: TARGET_KEY -> resolve via NAV INDEX_MANIFEST -> open.
- STEP-RUN: один шаг = одна пачка действий.
- Никаких догадок: NAV_HINT обязателен, если ROUTE_TOKEN не содержит REQUIRED_IDX_KEY.
- CONTRACT не проверяет “содержимое мира”, только детерминированно открывает нужный IDX и фиксирует доступность.

## [M] REQUIRED_KEYS (must exist in NAV INDEX_MANIFEST)
- INDEX_MANIFEST
- PIPELINE_CONTRACT
- NAV.IDX.BOOT
- NAV.IDX.ENT
- NAV.IDX.PIPE
- NAV.IDX.KB
- NAV.IDX.AUD
- NAV.IDX.VIS
- NAV.IDX.LEX
- NAV.IDX.REG
- NAV.IDX.XREF
- NAV.IDX.OPERATIONS
- NAV.IDX.LOG
- NAV.IDX.MUSIC

## [M] NAV_SELECTOR (no guessing)
# RULE: NAV_HINT must map to a NAV.IDX.* key (unless ROUTE_TOKEN provides REQUIRED_IDX_KEY)
- BOOT: NAV.IDX.BOOT
- ENT:  NAV.IDX.ENT
- PIPE: NAV.IDX.PIPE
- KB:   NAV.IDX.KB
- AUD:  NAV.IDX.AUD
- VIS:  NAV.IDX.VIS
- LEX:  NAV.IDX.LEX
- REG:  NAV.IDX.REG
- XREF: NAV.IDX.XREF
- OPS:  NAV.IDX.OPERATIONS
- LOG:  NAV.IDX.LOG
- MUSIC: NAV.IDX.MUSIC

## [M] FAIL_CODES
- UE.FAIL.INPUT_ABSENT
- UE.FAIL.MISSING_KEY
- UE.FAIL.INVALID_NAV_HINT
- UE.FAIL.GATE_FAIL

## [M] CONTRACT_HEADER
- REALM_ID: UE_V2/04_NAV
- DOMAIN: NAV
- ARTIFACT_TYPES: [IDX, NAV_TOKEN, ROUTE_TOKEN, LOG]
- DEFAULT_MODE: FAST

## [M] EXEC_MODEL (how it runs)
1) Resolve NAV INDEX_MANIFEST via KEY: INDEX_MANIFEST
2) Validate REQUIRED_KEYS exist
3) Determine IDX_KEY:
   - If ROUTE_TOKEN provides REQUIRED_IDX_KEY -> use it
   - else map NAV_HINT via NAV_SELECTOR
4) Open IDX doc by IDX_KEY (via INDEX_MANIFEST)
5) Emit NAV_TOKEN (opened IDX + summary) and NEXT prompt "го"

## [M] STEP-RUN (canonical)
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
  GOAL: Entry sanity and IDX selection framing
  INPUTS: [TASK_TEXT, ROUTE_TOKEN?, NAV_HINT?, MODE_HINT?]
  TARGETS: [INDEX_MANIFEST]
  ACTIONS:
    - Ensure TASK_TEXT exists, else FAIL
    - If ROUTE_TOKEN exists and has REQUIRED_IDX_KEY -> select IDX_KEY = REQUIRED_IDX_KEY
    - Else ensure NAV_HINT exists, else FAIL
    - Validate NAV_HINT is supported, else FAIL
  OUTPUTS: [TASK_TOKEN, IDX_KEY]
  CHECKS: [TASK_PRESENT, IDX_SELECTED]
  FAIL: UE.FAIL.INPUT_ABSENT
  NEXT: "го"

- STEP: S1
  GOAL: Load NAV layer and validate keys
  INPUTS: [TASK_TOKEN]
  TARGETS: [INDEX_MANIFEST, PIPELINE_CONTRACT]
  ACTIONS:
    - Resolve INDEX_MANIFEST via KEY: INDEX_MANIFEST
    - Validate ALL REQUIRED_KEYS exist in NAV INDEX_MANIFEST
  OUTPUTS: [NAV_READY]
  CHECKS: [REQUIRED_KEYS_OK]
  FAIL: UE.FAIL.MISSING_KEY
  NEXT: "го"

- STEP: S2
  GOAL: Open the selected IDX
  INPUTS: [IDX_KEY]
  TARGETS: [INDEX_MANIFEST]
  ACTIONS:
    - Resolve IDX_KEY via NAV INDEX_MANIFEST and open it
    - Confirm at least one [M] marker present in IDX doc (MARKER FOUND)
  OUTPUTS: [IDX_DOC_OPENED, NAV_TOKEN]
  CHECKS: [IDX_OPEN_OK]
  FAIL: UE.FAIL.GATE_FAIL
  NEXT: "го"

- STEP: S3
  GOAL: Emit NAV_TOKEN and continue
  INPUTS: [NAV_TOKEN]
  TARGETS: [INDEX_MANIFEST]
  ACTIONS:
    - Output NAV_TOKEN: IDX_KEY + short note what it enables
    - Provide NEXT prompt
  OUTPUTS: [NAV_TOKEN]
  CHECKS: [NAV_COMPLETE]
  FAIL: UE.FAIL.GATE_FAIL
  NEXT: "го"
