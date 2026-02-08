# 03__STR_PNT__QA_FAIL

SCOPE: UE_V2 / 13_STR_PNT
DOC_TYPE: START_POINT
UID: UE.V2.STR_PNT.QA_FAIL.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW via INDEX_MANIFEST only

---

## [M] ROLE
PRIMARY: STR_PNT (главный стартовый специалист)
MISSION: принимать фейлы/замечания QA/VAL/CTL и переводить их в управляемый ремонтный цикл:
triage → pinpoint → patch batch (full files) → re-checks → accept/reject, строго через ROUTER/IDX и по шагам через "го".

---

## [M] INTENT
Запуск обработки QA_FAIL так, чтобы:
- фейл был классифицирован (тип/критичность/локализация)
- источник фейла был связан с конкретным файлом/маркером/правилом
- выдача была “фулл-версия файла” (замена целиком)
- работало пошагово через "го" без шума контекста
- не было обходов IDX/REG/XREF/KB/PIPE/LOG

---

## [M] REQUIRED_INPUTS
- TASK_TEXT (обязателен; должен содержать описание фейла или ссылку/идентификатор)
- OPTIONAL: FAIL_CONTEXT (что именно упало: QA_ACCEPT / VAL_* / CTL_* / PIPE step)
- OPTIONAL: MODE_HINT (FAST|RELEASE_READY|MASTERPIECE)
- OPTIONAL: constraints (scope, forbidden zones, references, batch size)

---

## [M] QA_FAIL DEFINITIONS
QA_FAIL = событие, когда:
- документ/артефакт не проходит QA_ACCEPT
- не выполнены обязательные маркеры/секция/контракт
- нарушены NAV/RAW/IDX правила
- есть конфликт UID/VERSION/STATUS/MODE
- нарушены стандарты пайпа (PIPE contract, STEP_RUN, FOCUS_LOOP)

---

## [M] DEFAULTS
- MODE_HINT: RELEASE_READY (если не задан)
- constraints:
  - BATCH_SIZE: 1 doc per step (default)
  - MAX_TARGET_FILES_PER_ITER: 5
  - NO_TREE_LOAD: true

---

## [M] START_POINT_TOKEN (OUTPUT)
Emit once at S0:
- START_POINT_KEY: STR_PNT.QA_FAIL
- TASK_TEXT: <as provided>
- FAIL_CONTEXT: <provided or "UNKNOWN">
- MODE_HINT: <provided or RELEASE_READY>
- constraints: <provided or defaults>
- QUALITY_TARGET: "FULL_VERSION_FILES"
- NEXT_STEP: S1
- NEXT_PROMPT: "го"

---

## [M] ANTI_NOISE_LOAD_POLICY
ALWAYS (minimal boot path):
- UE_V2/00_BOOT/01__BOOT_SEQ.md
- UE_V2/00_BOOT/02__STOP_GAP.md
- UE_V2/00_BOOT/06__TRACE.md
- UE_V2/00_BOOT/07__FAIL_CODES.md
- UE_V2/00_BOOT/08__RUNTIME_MANIFEST.md (MUST_LOAD_SET only)
- UE_V2/00_BOOT/09__TASK_ROUTER.md
- UE_V2/04_NAV/00__NAV_ROOT.md
- UE_V2/06_PIPE/01__PIPE_DEFAULT.md
- UE_V2/14_LOG/00__PIPELINE_CONTRACT__LOG.md

THEN (strict):
- 1 domain IDX (from ROUTE_TOKEN.REQUIRED_IDX)
- 1–3 target files for current fail (prefer 1)
- 0–2 helper files (KB/XREF) only if REQUIRED_CHECKS asks

NEVER:
- обход IDX
- массовая загрузка дерева
- “починить всё сразу” без triage
- выдавать только советы без полной версии файла

---

## [M] STEP-RUN (CANON)

### S0) ENTRY CHECK
IF no TASK_TEXT:
- STOP: INPUT_ABSENT
ELSE:
- Emit START_POINT_TOKEN
- Ask: "го"

### S1) BOOT MIN
Open (RAW):
- UE_V2/00_BOOT/01__BOOT_SEQ.md
Apply:
- UE_V2/00_BOOT/02__STOP_GAP.md
Enable:
- UE_V2/00_BOOT/06__TRACE.md
- UE_V2/00_BOOT/07__FAIL_CODES.md
Output:
- BOOT_MIN_READY = true
- Ask: "го"

### S2) MUST_LOAD ядро (MIN)
Open (RAW):
- UE_V2/00_BOOT/08__RUNTIME_MANIFEST.md
Load:
- MUST_LOAD_SET (minimum only)
Output:
- MUST_LOAD_READY = true
- Ask: "го"

### S3) ROUTING (QA_FAIL aware)
Open (RAW):
- UE_V2/00_BOOT/09__TASK_ROUTER.md

Build ROUTE_TOKEN (deterministic):
- DOMAIN
- ARTIFACT_TYPE
- MODE (from MODE_HINT)
- PIPE_SELECTED
- DEFAULT_ORC
- REQUIRED_IDX
- REQUIRED_CHECKS
- EXEC_MODE

QA_FAIL override intent:
- ARTIFACT_TYPE resolves to DOC/POLICY/TEMPLATE/INDEX (one)
- EXEC_MODE resolves to STEP_RUN
- REQUIRED_CHECKS should include QA/VAL/CTL checks relevant to FAIL_CONTEXT
Output:
- ROUTE_TOKEN (mandatory)
- Ask: "го"

### S4) NAV CHECK (IDX-only)
Open (RAW):
- UE_V2/04_NAV/00__NAV_ROOT.md
Open (RAW):
- IDX from ROUTE_TOKEN.REQUIRED_IDX

Confirm (via IDX only) access exists for:
- REG
- XREF
- KB (if REQUIRED_CHECKS says so)
- PIPE
- LOG

IF any missing:
- GAP: NAV_ACCESS_NOT_CONFIRMED
ELSE:
- NAV_OK = true
- Ask: "го"

### S5) TRIAGE (FAIL CLASSIFICATION)
Goal: превратить “фейл” в точные targets.

Produce TRIAGE_CARD:
- FAIL_ID (если есть) else generate local: QAFAIL.<date>.<seq>
- FAIL_CONTEXT
- SEVERITY: BLOCKER | MAJOR | MINOR
- TYPE:
  - MARKER_MISSING
  - SECTION_CONTRACT_BROKEN
  - UID_OR_VERSION_CONFLICT
  - NAV_RAW_VIOLATION
  - IDX_MISSING_OR_WRONG
  - PIPE_CONTRACT_VIOLATION
  - LOG_CONTRACT_VIOLATION
  - STYLE_GUIDE_VIOLATION
  - OTHER
- SUSPECT_TARGETS: list of 1–5 files max (paths)
- REQUIRED_EVIDENCE: what to open next (1–3 files)
Output:
- TRIAGE_CARD
- Ask: "го"

### S6) PINPOINT (MIN READ)
Open (RAW) only what TRIAGE requires:
- 1 target file (prefer)
- plus helper XREF/KB if REQUIRED_EVIDENCE says

Produce PINPOINT_REPORT:
- TARGET_FILE
- WHERE: section / marker / line-range concept (no need exact lines)
- WHAT: contract breach description
- WHY: rule/source pointer (REG/XREF/KB/PIPE reference path)
- FIX_STRATEGY: replace-ready full file rewrite OR minimal full rewrite
Output:
- PINPOINT_REPORT
- Ask: "го"

### S7) PATCH BATCH (FULL FILES)
Rules:
- Output FULL content for each patched file (complete replacement)
- Preserve required header fields and markers
- Keep changes minimal but sufficient to pass REQUIRED_CHECKS
- 1 file per step by default

Output:
- PATCHED_FILE_FULL
- Ask: "го"

### S8) RE-CHECKS (DECLARATIVE)
Without doing heavy loads:
- Declare which REQUIRED_CHECKS are satisfied and why (based on patched doc structure)
- If a required check needs another doc: GAP and list needed path(s)

Output:
- CHECKS_STATUS: PASS|GAP per check
- Ask: "го"

### S9) LOG INIT / TRACE HOOK
Open (RAW):
- UE_V2/14_LOG/00__PIPELINE_CONTRACT__LOG.md
Confirm availability (RAW):
- UE_V2/14_LOG/01__RUN_LOG.md
- UE_V2/14_LOG/03__TOKEN_ARCHIVE.md
- UE_V2/14_LOG/04__DECISION_LOG.md
If missing:
- GAP: LOG_MISSING
Else:
- LOG_READY = true
- Ask: "го"

---

## [M] STOP / GAP
STOP only if:
- INPUT_ABSENT
- MUST_LOAD missing raw
- marker not confirmed for MUST_LOAD (if required)

GAP if:
- ROUTER cannot resolve route
- REQUIRED_IDX missing
- NAV cannot confirm access via IDX
- need extra file(s) beyond load limits to prove check
- LOG contract/assets missing

---

## [M] FAIL CODES (LOCAL)
- INPUT_ABSENT
- MUST_LOAD_MISSING
- MARKER_NOT_CONFIRMED
- ROUTER_UNRESOLVED_QA_FAIL
- IDX_MISSING
- NAV_ACCESS_NOT_CONFIRMED
- TRIAGE_NO_TARGETS
- PINPOINT_INSUFFICIENT_EVIDENCE
- PATCH_BATCH_LIMIT_EXCEEDED
- LOG_MISSING

---

## [M] OUTPUT CONTRACT (THIS FILE)
On successful S0, always output:
- START_POINT_TOKEN
- "го"
