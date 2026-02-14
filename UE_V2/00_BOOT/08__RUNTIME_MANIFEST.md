# 08__RUNTIME_MANIFEST
KIND: ENGINE
ROLE: RUNTIME_STATE
SCOPE: SYSTEM
STATUS: CANON
VERSION: 1.0.0

## [M] PURPOSE
RUNTIME_MANIFEST — единая “истина текущего состояния” выполнения.
Нужен, чтобы:
- не терять контекст между шагами
- воспроизводимо продолжать работу (resume)
- доказуемо видеть: профиль, required_set, что реально запускалось, и итог PASS/FAIL

---

## [M] HARD_RULES
1) SINGLE SOURCE OF RUNTIME TRUTH
- Текущее состояние фиксируется только здесь (плюс TRACE/CHANGELOG).

2) STEP-SCOPED
- Один STEP = одна запись CURRENT_STEP + обновление LAST_RESULT.
- Продолжение возможно только через RESUME_TOKEN / signal "го".

3) NO FAKE EXECUTION
- Если нет ledgers/val_report — manifest не должен утверждать PASS.

---

## [M] STRUCTURE (FIELDS)
### 1) SESSION
SESSION:
  SESSION_ID: "<runtime>"
  STARTED_AT: "0000-00-00"
  UPDATED_AT: "0000-00-00"
  OWNER: "USER|TEAM"
  MODE: "REPO"

### 2) CURRENT_STEP
CURRENT_STEP:
  STEP_ID: "<incremental or runtime>"
  STEP_STATUS: "RUNNING|STOP_GAP|FAIL|PASS"
  STEP_GOAL: "<one line>"
  NEXT_SIGNAL_REQUIRED: true
  USER_SIGNAL: "<expected: го>"
  ACTIVE_FOLDER: "<e.g. 00_BOOT>"
  ACTIVE_FILE: "<e.g. 00_BOOT/08__RUNTIME_MANIFEST.md>"

### 3) ROUTING (from ROUTE_TOKEN)
ROUTING:
  DOMAIN: "<SYS|MUSIC|...>"
  ARTIFACT_TYPE: "<FULL_PATCH|KB_PATCH|...>"
  PROFILE_KEY: "<PROFILE.* or NONE>"
  PIPE_SELECTED: "<KEY:PIPE.*>"
  REQUIRED_IDX: []
  REQUIRED_ROLES: []
  REQUIRED_ENG_KEYS: []
  REQUIRED_KB_KEYS: []
  REQUIRED_VAL_KEYS: []
  OUTPUT_CONTRACT: []
  NO_GO_LIST: []

### 4) EXECUTION LEDGERS (proof)
LEDGERS:
  ROLE_LEDGER:
    - role: "SPC"
      status: "ran|skipped|failed"
      outputs_produced: []
      notes: ""
    - role: "ORC"
      status: "ran|skipped|failed"
      outputs_produced: []
      notes: ""
    - role: "CTL"
      status: "ran|skipped|failed"
      outputs_produced: []
      notes: ""
    - role: "VAL"
      status: "ran|skipped|failed"
      outputs_produced: []
      notes: ""
    - role: "QA"
      status: "ran|skipped|failed"
      outputs_produced: []
      notes: ""

  ENGINE_RUN_LEDGER:
    run_id: "<runtime>"
    entries:
      - eng_key: "KEY:ENG...."
        status: "ran|skipped|failed"
        outputs_produced: []
        notes: ""

  OUTPUT_LEDGER:
    - output: "BRIEF_TOKEN"
      present: false
      source: "<SPC|ORC|CTL|VAL|QA|PACK>"
      ref: "<optional>"
    - output: "ENGINE_PLAN_TOKEN"
      present: false
      source: ""
      ref: ""
    - output: "ENGINE_RUN_LEDGER"
      present: false
      source: ""
      ref: ""
    - output: "VAL_REPORT"
      present: false
      source: ""
      ref: ""
    - output: "PACK_OUTPUT"
      present: false
      source: ""
      ref: ""

### 5) LAST_RESULT (what happened in previous step)
LAST_RESULT:
  STATUS: "NONE|PASS|FAIL|STOP_GAP"
  FAIL_CODE: "<optional>"
  FAIL_REASONS: []
  FIX_LIST: []
  VAL_REPORT_REF: "<optional>"
  PACK_OUTPUT_REF: "<optional>"

### 6) PATCHSET TRACKING (for repo edits)
PATCH_TRACKING:
  LAST_PATCHSET_ID: "<e.g. PATCHSET_0007>"
  LAST_FILES_CHANGED: []
  CHANGELOG_REF: "<path or key>"
  NEXT_POINTER: "<what file is next>"

### 7) RESUME CONTROL
RESUME:
  RESUME_TOKEN: "<optional>"
  RESUME_ALLOWED: false
  RESUME_REQUIREMENTS:
    - "<e.g. provide missing file content>"
  RESUME_TARGET:
    FILE: "<next file to patch>"
    GOAL: "<one line>"

---

## [M] UPDATE RULES (how to use this file)
On every STEP:
1) Write CURRENT_STEP fields (goal, active file)
2) Copy ROUTING from ROUTE_TOKEN
3) Update LEDGERS as roles/engines/outputs are produced
4) Write LAST_RESULT (PASS/FAIL/STOP_GAP)
5) Update PATCH_TRACKING if files changed
6) If STOP_GAP/FAIL: set RESUME_ALLOWED=false and fill RESUME_REQUIREMENTS
7) If PASS: set RESUME_ALLOWED=true and set RESUME_TARGET to NEXT file

---

## [M] DEFAULT TEMPLATE (blank instance)
SESSION:
  SESSION_ID: ""
  STARTED_AT: ""
  UPDATED_AT: ""
  OWNER: "USER"
  MODE: "REPO"

CURRENT_STEP:
  STEP_ID: ""
  STEP_STATUS: "RUNNING"
  STEP_GOAL: ""
  NEXT_SIGNAL_REQUIRED: true
  USER_SIGNAL: "го"
  ACTIVE_FOLDER: ""
  ACTIVE_FILE: ""

ROUTING:
  DOMAIN: ""
  ARTIFACT_TYPE: ""
  PROFILE_KEY: ""
  PIPE_SELECTED: ""
  REQUIRED_IDX: []
  REQUIRED_ROLES: []
  REQUIRED_ENG_KEYS: []
  REQUIRED_KB_KEYS: []
  REQUIRED_VAL_KEYS: []
  OUTPUT_CONTRACT: []
  NO_GO_LIST: []

LEDGERS:
  ROLE_LEDGER: []
  ENGINE_RUN_LEDGER:
    run_id: ""
    entries: []
  OUTPUT_LEDGER: []

LAST_RESULT:
  STATUS: "NONE"
  FAIL_CODE: ""
  FAIL_REASONS: []
  FIX_LIST: []
  VAL_REPORT_REF: ""
  PACK_OUTPUT_REF: ""

PATCH_TRACKING:
  LAST_PATCHSET_ID: ""
  LAST_FILES_CHANGED: []
  CHANGELOG_REF: ""
  NEXT_POINTER: ""

RESUME:
  RESUME_TOKEN: ""
  RESUME_ALLOWED: false
  RESUME_REQUIREMENTS: []
  RESUME_TARGET:
    FILE: ""
    GOAL: ""

END.
