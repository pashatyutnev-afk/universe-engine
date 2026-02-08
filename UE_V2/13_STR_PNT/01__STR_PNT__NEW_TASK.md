# 01__STR_PNT__NEW_TASK

SCOPE: UE_V2 / 13_STR_PNT
DOC_TYPE: START_POINT
UID: UE.V2.STR_PNT.NEW_TASK.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW via INDEX_MANIFEST only

---

## [M] ROLE
PRIMARY: STR_PNT (главный стартовый специалист рантайма)
MISSION: принять новую задачу, сформировать стартовый токен, запустить BOOT→ROUTER→NAV→PIPE пошагово через "го" без обходов и без засора контекста.

---

## [M] INTENT
Запуск новой задачи так, чтобы:
- не пройти мимо REG/XREF/KB/PIPE/NAV/LOG
- не засорить контекст массовыми загрузками
- работать пошагово через "го"
- выбирать путь детерминированно через ROUTER
- не угадывать сущности и не обходить IDX

---

## [M] REQUIRED_INPUTS
- TASK_TEXT (обязателен)
- OPTIONAL: MODE_HINT (FAST|RELEASE_READY|MASTERPIECE)
- OPTIONAL: constraints (platform, duration, style, references)

---

## [M] DEFAULTS
- MODE_HINT: FAST (если не задан)
- constraints: none (если не задан)

---

## [M] START_POINT_TOKEN (OUTPUT)
Emit once at S0:
- START_POINT_KEY: STR_PNT.NEW_TASK
- TASK_TEXT: <as provided>
- MODE_HINT: <provided or FAST>
- constraints: <provided or none>
- NEXT_STEP: S1
- NEXT_PROMPT: "го"

---

## [M] ANTI_NOISE_LOAD_POLICY
- ALWAYS (minimal boot path):
  - BOOT_SEQ
  - STOP_GAP
  - TRACE
  - FAIL_CODES
  - RUNTIME_MANIFEST (MUST_LOAD_SET only)
  - TASK_ROUTER
  - NAV_ROOT
  - PIPE_DEFAULT
  - LOG_RULES
- THEN:
  - 1 domain IDX (from ROUTE_TOKEN.REQUIRED_IDX)
  - 1–3 target files only (based on TASK_TEXT & ROUTE_TOKEN)
- NEVER:
  - обход IDX
  - массовая загрузка деревьев/папок
  - “пробежаться по всему репо”

---

## [M] STEP-RUN (CANON)
### S0) ENTRY CHECK
IF no TASK_TEXT:
- STOP: INPUT_ABSENT
ELSE:
- Emit START_POINT_TOKEN
- Ask: "го"

### S1) BOOT SEQ (MIN)
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
- MUST_LOAD_SET (minimum only, per manifest)
Output:
- MUST_LOAD_READY = true
- Ask: "го"

### S3) ROUTING
Open (RAW):
- UE_V2/00_BOOT/09__TASK_ROUTER.md
Build ROUTE_TOKEN (deterministic, no guessing):
- DOMAIN
- ARTIFACT_TYPE
- MODE (from MODE_HINT)
- PIPE_SELECTED
- DEFAULT_ORC
- REQUIRED_IDX
- REQUIRED_CHECKS
- EXEC_MODE
Output:
- ROUTE_TOKEN (mandatory)
- Ask: "го"

### S4) NAV CHECK
Open (RAW):
- UE_V2/04_NAV/00__NAV_ROOT.md
Open (RAW):
- IDX from ROUTE_TOKEN.REQUIRED_IDX
Confirm (via IDX only) access paths exist for:
- REG
- XREF
- KB
- PIPE
- LOG
Output:
- NAV_OK = true OR GAP with missing item list
- Ask: "го"

### S5) PIPE EXEC (STEP-RUN)
Open (RAW):
- UE_V2/06_PIPE/01__PIPE_DEFAULT.md
Routing rule:
- If ROUTE_TOKEN.PIPE_SELECTED is domain pipe -> handoff via PIPE_DEFAULT routing
Enable protocols (RAW):
- UE_V2/00_BOOT/10__STEP_RUN_PROTOCOL.md
- UE_V2/00_BOOT/12__FOCUS_LOOP_PROTOCOL.md
- UE_V2/00_BOOT/13__COMMANDS.md
Output:
- PIPE_HANDOFF_READY = true OR GAP with missing pipe
- Ask: "го"

### S6) LOG INIT
Open (RAW):
- UE_V2/14_LOG/00__PIPELINE_CONTRACT__LOG.md (or LOG rules root if contract points there)
Then confirm availability (RAW):
- UE_V2/14_LOG/01__RUN_LOG.md
- UE_V2/14_LOG/03__TOKEN_ARCHIVE.md
- UE_V2/14_LOG/04__DECISION_LOG.md
Output:
- LOG_READY = true OR GAP with missing log assets
- Ask: "го"

---

## [M] STOP / GAP
STOP only if:
- INPUT_ABSENT (no TASK_TEXT)
- MUST_LOAD missing raw
- marker not confirmed for MUST_LOAD (if manifest requires marker checks)

GAP if:
- missing domain PIPE
- missing REQUIRED_IDX or IDX cannot confirm REG/XREF/KB/PIPE/LOG
- required checks/entities referenced by ROUTE_TOKEN are absent

---

## [M] FAIL CODES (LOCAL)
- INPUT_ABSENT
- MUST_LOAD_MISSING
- MARKER_NOT_CONFIRMED
- IDX_MISSING
- NAV_ACCESS_NOT_CONFIRMED
- PIPE_MISSING
- LOG_MISSING

---

## [M] OUTPUT CONTRACT (THIS FILE)
On successful S0, always output:
- START_POINT_TOKEN
- "го"
