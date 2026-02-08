# 04__STR_PNT__RELEASE_READY

SCOPE: UE_V2 / 13_STR_PNT
DOC_TYPE: START_POINT
UID: UE.V2.STR_PNT.RELEASE_READY.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW via INDEX_MANIFEST only

---

## [M] ROLE
PRIMARY: STR_PNT (главный стартовый специалист)
MISSION: запуск режима RELEASE_READY как “боевой сборки результата”.
Фокус: минимальный шум, детерминированный роутинг, строгие гейты, упаковка артефакта под релиз.

---

## [M] INTENT
Запустить работу так, чтобы:
- система поднялась строго через START, MANIFEST, ROUTER, NAV_ROOT
- был сформирован ROUTE_TOKEN с MODE=RELEASE_READY
- был выбран PIPE (default или доменный) детерминированно
- выполнялись только обязательные проверки и упаковка, без лишней справки
- выдача шла пошагово через "го", 1 документ за итерацию, “фулл-версиями”

---

## [M] REQUIRED_INPUTS
- TASK_TEXT (обязателен)
- OPTIONAL: DOMAIN_HINT (AUD|VIS|LOR|REL|KB|PIPE|LEX|LOG|NAV|BOOT)
- OPTIONAL: ARTIFACT_HINT (DOC|TEMPLATE|INDEX|TRACK|LYRICS|PROMPT|PACK)
- OPTIONAL: constraints (platform, duration, style, references, forbidden zones)

---

## [M] DEFAULTS
- MODE_HINT: RELEASE_READY (locked)
- EXEC_MODE: STEP_RUN
- constraints defaults:
  - BATCH_SIZE: 1 doc per step
  - MAX_TARGET_FILES_PER_ITER: 5
  - NO_TREE_LOAD: true
  - OUTPUT_FULL_FILES: true
  - NO_INDEX_BYPASS: true
  - NO_SIDEQUESTS: true

---

## [M] START_POINT_TOKEN (OUTPUT)
Emit once at S0:
- START_POINT_KEY: STR_PNT.RELEASE_READY
- TASK_TEXT: <as provided>
- DOMAIN_HINT: <provided or "AUTO">
- ARTIFACT_HINT: <provided or "AUTO">
- MODE_HINT: RELEASE_READY
- constraints: <provided or defaults>
- QUALITY_TARGET: "RELEASE_READY"
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

THEN:
- 1 domain IDX (from ROUTE_TOKEN.REQUIRED_IDX)
- 1–3 target files needed to build deliverable for current step
- 0–2 helper files (KB/XREF) only if REQUIRED_CHECKS requires them

NEVER:
- обход IDX
- массовая загрузка деревьев
- создание пачки документов без STEP_RUN
- выдача результата без гейтов

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

### S3) ROUTING (RELEASE_READY forced)
Open (RAW):
- UE_V2/00_BOOT/09__TASK_ROUTER.md

Build ROUTE_TOKEN (deterministic):
- DOMAIN
- ARTIFACT_TYPE
- MODE = RELEASE_READY
- PIPE_SELECTED
- DEFAULT_ORC
- REQUIRED_IDX
- REQUIRED_CHECKS
- EXEC_MODE = STEP_RUN

Routing hints:
- If DOMAIN_HINT provided, use it as primary signal
- If ARTIFACT_HINT provided, use it as primary signal
- Else infer from TASK_TEXT via ROUTER rules (no guessing outside ROUTER)

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

### S5) PIPE SELECT + PROTOCOLS
Open (RAW):
- UE_V2/06_PIPE/01__PIPE_DEFAULT.md

If ROUTE_TOKEN.PIPE_SELECTED is domain:
- Handoff via PIPE_DEFAULT rules (deterministic)
Else:
- Use PIPE_DEFAULT

Enable protocols (RAW):
- UE_V2/00_BOOT/10__STEP_RUN_PROTOCOL.md
- UE_V2/00_BOOT/12__FOCUS_LOOP_PROTOCOL.md
- UE_V2/00_BOOT/13__COMMANDS.md

Output:
- PIPE_READY = true
- PIPE_IN_USE = <PIPE_SELECTED or DEFAULT>
- Ask: "го"

### S6) TARGET SET (RELEASE_READY minimal)
Goal: определить минимальный набор файлов для релизного результата.

Produce TARGET_SET:
- PRIMARY_TARGETS: 1–3 files (paths)
- SUPPORT_TARGETS: 0–2 files (paths) only if REQUIRED_CHECKS requires
- PACK_TARGETS: 0–2 files (paths) for packaging if pipe requires

Rules:
- respect MAX_TARGET_FILES_PER_ITER
- if cannot fit:
  - GAP: TARGET_SET_TOO_LARGE

Output:
- TARGET_SET
- Ask: "го"

### S7) BUILD STEP (FULL OUTPUT)
For current step:
- Open (RAW) only files in TARGET_SET needed now
- Produce deliverable output in one of forms:
  - FULL_FILE_REPLACEMENT (complete document)
  - PACK_SECTION (if pipe defines pack format) but prefer full file when possible

Rules:
- Output must be “release ready”:
  - correct headers (SCOPE/DOC_TYPE/UID/VERSION/STATUS/MODE/NAV_RULE)
  - required markers present
  - no placeholders
  - minimal but complete

Output:
- DELIVERABLE (full)
- Ask: "го"

### S8) REQUIRED_CHECKS (DECLARATIVE)
Run check-list as declared statuses (no tree scans):
- For each REQUIRED_CHECK in ROUTE_TOKEN:
  - PASS if structure satisfied by deliverable and loaded sources
  - GAP if requires opening additional doc(s) outside load limits
  - FAIL if rule clearly violated

Output:
- CHECKS_STATUS table (PASS|GAP|FAIL per check)
- Ask: "го"

### S9) PACK + SIGNOFF (if pipe)
If PIPE requires PACK or SIGNOFF:
- produce PACK output (full file if pack is a doc)
- produce SIGNOFF note (structured, short)

Output:
- PACK_OUTPUT (optional)
- SIGNOFF_NOTE (optional)
- Ask: "го"

### S10) LOG INIT / TRACE HOOK
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
- TARGET_SET too large for limits
- PACK required but pack doc missing
- LOG contract/assets missing

---

## [M] FAIL CODES (LOCAL)
- INPUT_ABSENT
- MUST_LOAD_MISSING
- MARKER_NOT_CONFIRMED
- ROUTER_UNRESOLVED_RELEASE_READY
- IDX_MISSING
- NAV_ACCESS_NOT_CONFIRMED
- TARGET_SET_TOO_LARGE
- REQUIRED_CHECKS_NEED_MORE_SOURCES
- PACK_MISSING
- LOG_MISSING

---

## [M] OUTPUT CONTRACT (THIS FILE)
On successful S0, always output:
- START_POINT_TOKEN
- "го"
