# 02__STR_PNT__PATCH_FIX

SCOPE: UE_V2 / 13_STR_PNT
DOC_TYPE: START_POINT
UID: UE.V2.STR_PNT.PATCH_FIX.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW via INDEX_MANIFEST only

---

## [M] ROLE
PRIMARY: STR_PNT (главный стартовый специалист)
MISSION: принимать задачи типа “исправить документацию/шаблоны/индексы”, вести их по безопасному пайпу: диагностика → патч → валидация → QA → релиз/сайнофф, строго через ROUTER и IDX, пошагово через "го".

---

## [M] INTENT
Запуск задач PATCH/FIX так, чтобы:
- работа была детерминированной (через ROUTER)
- не было обходов IDX/REG/XREF/KB/PIPE/LOG
- не было “массовой загрузки дерева”
- изменения готовились как “фулл-версия файла” (replace-ready)
- можно было идти по шагам через "го"

---

## [M] REQUIRED_INPUTS
- TASK_TEXT (обязателен; должен явно содержать, что исправляем)
- OPTIONAL: MODE_HINT (FAST|RELEASE_READY|MASTERPIECE)
- OPTIONAL: constraints (scope, files list, forbidden zones, style rules, refs)

---

## [M] PATCH/FIX DEFINITIONS
PATCH/FIX = любые задачи, где цель:
- исправить/нормализовать документ(ы) UE_V2
- исправить контракт/маркер/шаблон
- убрать конфликт путей/UID/версий/секций
- сделать документ self-contained и пригодный для “сделал и забыл”

---

## [M] DEFAULTS
- MODE_HINT: RELEASE_READY (если не задан)
- constraints: none (если не задан)

---

## [M] START_POINT_TOKEN (OUTPUT)
Emit once at S0:
- START_POINT_KEY: STR_PNT.PATCH_FIX
- TASK_TEXT: <as provided>
- MODE_HINT: <provided or RELEASE_READY>
- constraints: <provided or none>
- QUALITY_TARGET: "FULL_VERSION_FILES"
- NEXT_STEP: S1
- NEXT_PROMPT: "го"

---

## [M] ANTI_NOISE_LOAD_POLICY
ALWAYS (minimal boot path, no exceptions):
- UE_V2/00_BOOT/01__BOOT_SEQ.md
- UE_V2/00_BOOT/02__STOP_GAP.md
- UE_V2/00_BOOT/06__TRACE.md
- UE_V2/00_BOOT/07__FAIL_CODES.md
- UE_V2/00_BOOT/08__RUNTIME_MANIFEST.md (MUST_LOAD_SET only)
- UE_V2/00_BOOT/09__TASK_ROUTER.md
- UE_V2/04_NAV/00__NAV_ROOT.md
- UE_V2/06_PIPE/01__PIPE_DEFAULT.md
- UE_V2/14_LOG/00__PIPELINE_CONTRACT__LOG.md

THEN (strictly limited):
- 1 domain IDX (from ROUTE_TOKEN.REQUIRED_IDX)
- 1–5 target files max per iteration (patch batch)
- 0–2 XREF/KB helper files max, only if ROUTE_TOKEN says required

NEVER:
- обход IDX
- массовая загрузка папок/деревьев
- “прочитать всё и потом решить”
- неконкретные правки без выдачи полной версии файла

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

### S3) ROUTING (PATCH/FIX aware)
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

PATCH/FIX override rules (only if router supports, else GAP):
- ARTIFACT_TYPE should resolve to DOC/POLICY/TEMPLATE/INDEX (one of)
- EXEC_MODE should resolve to STEP_RUN
- PIPE_SELECTED should resolve to PIPE_GAP or domain pipe that includes doc validation
Output:
- ROUTE_TOKEN (mandatory)
- Ask: "го"

### S4) NAV CHECK (IDX-only)
Open (RAW):
- UE_V2/04_NAV/00__NAV_ROOT.md
Open (RAW):
- IDX from ROUTE_TOKEN.REQUIRED_IDX

Confirm (via IDX only) access exists for:
- REG (registries / manifests)
- XREF (cross refs)
- KB (knowledge base if needed)
- PIPE (pipeline docs)
- LOG (log contract + logs)

IF any missing:
- GAP: NAV_ACCESS_NOT_CONFIRMED
- Provide missing list (paths/keys)
ELSE:
- NAV_OK = true
- Ask: "го"

### S5) PIPE HANDOFF (PATCH/FIX)
Open (RAW):
- UE_V2/06_PIPE/01__PIPE_DEFAULT.md

Routing:
- If ROUTE_TOKEN.PIPE_SELECTED is domain pipe -> handoff via PIPE_DEFAULT
- Else use PIPE_GAP for missing/repair paths (if defined by router)

Enable protocols (RAW):
- UE_V2/00_BOOT/10__STEP_RUN_PROTOCOL.md
- UE_V2/00_BOOT/12__FOCUS_LOOP_PROTOCOL.md
- UE_V2/00_BOOT/13__COMMANDS.md

Output:
- PIPE_HANDOFF_READY = true OR GAP: PIPE_MISSING
- Ask: "го"

### S6) PATCH OUTPUT CONTRACT (FULL FILES)
For each target file in current batch:
- Output must be the FULL content of the file (complete replacement)
- Include header block: SCOPE / DOC_TYPE / UID / VERSION / STATUS / MODE / NAV_RULE
- Include [M] markers where required by standards
- No partial snippets, no “diff-only” as primary output

Batch rules:
- 1 doc per step by default (can be 2–3 only if tiny and strongly related)
- End each step with: "го"

Output:
- PATCH_BATCH_READY = true
- Ask: "го"

### S7) LOG INIT (recordability)
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
- marker not confirmed for MUST_LOAD (if required by manifest)

GAP if:
- router cannot resolve PATCH/FIX route
- missing REQUIRED_IDX
- NAV cannot confirm required panels via IDX
- missing PIPE_SELECTED
- missing LOG contract/assets

---

## [M] FAIL CODES (LOCAL)
- INPUT_ABSENT
- MUST_LOAD_MISSING
- MARKER_NOT_CONFIRMED
- ROUTER_UNRESOLVED_PATCH_FIX
- IDX_MISSING
- NAV_ACCESS_NOT_CONFIRMED
- PIPE_MISSING
- LOG_MISSING

---

## [M] OUTPUT CONTRACT (THIS FILE)
On successful S0, always output:
- START_POINT_TOKEN
- "го"
