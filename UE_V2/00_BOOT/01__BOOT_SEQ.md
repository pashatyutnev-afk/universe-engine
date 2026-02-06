# 01__BOOT_SEQ

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: BOOT_SEQUENCE (CANON)
UID: UE.V2.BOOT.SEQ.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only (via INDEX_MANIFEST)
PURPOSE: Каноничная последовательность старта рантайма. Не даёт пропускать REG/XREF/KB/PIPE/NAV/LOG, включает трассу, ошибки и step-run.

---

## [M] PRIME LAW
- BOOT выполняется **всегда** перед любым доменным пайплайном.
- BOOT не “думает” о задаче — он **поднимает ядро**, проверяет входы и включает протоколы.
- Любая попытка “сразу сделать результат” без BOOT — нарушение.
- Навигация по путям запрещена. Только RAW из INDEX_MANIFEST.

---

## [M] REQUIRED INPUTS
- TASK_TEXT: строка задачи пользователя.
- OPTIONAL: MODE_HINT (FAST|RELEASE_READY|MASTERPIECE)
- OPTIONAL: constraints (platform, duration, style, references)

---

## [M] OUTPUTS (BOOT ARTIFACTS)
BOOT_OUTPUT:
- BOOT_STATUS: PASS | GAP | STOP
- FAIL_CODE (если STOP/FAIL)
- TRACE_ON: true/false
- ROUTE_TOKEN (после ROUTER стадии)
- NEXT_PROMPT: "го"

---

## [M] ERROR POLICY (STOP/GAP)
STOP только если:
- TASK_TEXT отсутствует
- любой MUST_LOAD файл не доступен по RAW или marker not confirmed (см. FAIL_CODES)
GAP если:
- доменный IDX/PIPE/обязательная сущность требуется по ROUTE_TOKEN, но отсутствует

---

## [M] ANTI-NOISE LOAD POLICY (ENFORCE)
ALWAYS LOAD (минимум):
- START (entrypoint)
- RUNTIME_MANIFEST
- TASK_ROUTER
- NAV_ROOT
THEN:
- один REQUIRED_IDX (по ROUTE_TOKEN)
- 1–3 target файла под задачу
NEVER:
- массовая загрузка деревьев
- обход IDX
- “догрузить на всякий случай”

---

# [S0] ENTRYPOINT CHECK
## Цель
Подтвердить, что это реально запуск задачи и есть TASK_TEXT.

## Steps
S0.1 Validate TASK_TEXT
- if missing -> STOP (FAIL_CODE: FC.INPUT.ABSENT.TASK_TEXT)

S0.2 Normalize MODE_HINT
- if missing -> MODE_HINT=RELEASE_READY (по умолчанию)

S0.3 Establish CONSTRAINTS object
- platform, duration, style, references (может быть пустым)

## Output
- ENTRYPOINT_OK: true

---

# [S1] BOOT CORE ENABLE
## Цель
Включить защитные протоколы: STOP/GAP, TRACE, FAIL_CODES.

## MUST_LOAD (by RAW from INDEX_MANIFEST)
- STOP_GAP
- TRACE
- FAIL_CODES

## Steps
S1.1 Load STOP_GAP rules
S1.2 Enable TRACE (TRACE_ON=true)
S1.3 Load FAIL_CODES mapping (для детерминированных ответов)
S1.4 Set BOOT_CONTEXT (минимальный):
- TASK_TEXT
- MODE_HINT
- CONSTRAINTS
- TRACE_ON
- BOOT_VERSION

## Output
- BOOT_CORE_ON: true

---

# [S2] MUST_LOAD RUNTIME MANIFEST
## Цель
Поднять минимальный MUST_LOAD_SET (только минимум), чтобы не засорять контекст.

## MUST_LOAD (by RAW)
- RUNTIME_MANIFEST

## Steps
S2.1 Load RUNTIME_MANIFEST
S2.2 Extract MUST_LOAD_SET
- только ключевые панели/правила, без доменных деревьев
S2.3 Validate markers in manifest
- if marker missing -> STOP (FAIL_CODE: FC.MUSTLOAD.MARKER.MISSING)

## Output
- MUST_LOAD_OK: true
- MUST_LOAD_SET: (ids only)

---

# [S3] ROUTING (TASK → ROUTE_TOKEN)
## Цель
Детерминированно выбрать путь выполнения задачи через ROUTER.

## MUST_LOAD (by RAW)
- TASK_ROUTER

## Steps
S3.1 Load TASK_ROUTER
S3.2 Build ROUTE_TOKEN fields (minimum required):
- DOMAIN
- ARTIFACT_TYPE
- MODE (resolved from MODE_HINT)
- PIPE_SELECTED (default or domain)
- DEFAULT_ORC
- REQUIRED_IDX
- REQUIRED_CHECKS
- EXEC_MODE (STEP_RUN)

S3.3 Validate ROUTE_TOKEN completeness
- if REQUIRED fields missing -> STOP (FAIL_CODE: FC.ROUTER.TOKEN.INCOMPLETE)

## Output
- ROUTE_TOKEN

---

# [S4] NAV (ACCESS CHECK)
## Цель
Подтвердить доступ к NAV_ROOT и обязательным панелям через REQUIRED_IDX.

## MUST_LOAD (by RAW)
- NAV_ROOT
- REQUIRED_IDX (из ROUTE_TOKEN)

## Steps
S4.1 Load NAV_ROOT
S4.2 Load REQUIRED_IDX
S4.3 Confirm that REG/XREF/KB/PIPE/LOG are reachable:
- либо прямыми RAW панелями
- либо через IDX ссылки (RAW only)
If something is required by REQUIRED_CHECKS but missing -> GAP (не STOP)

## Output
- NAV_OK: true | GAP
- NAV_GAP_LIST (если GAP)

---

# [S5] PIPE EXEC SETUP (STEP-RUN)
## Цель
Подключить PIPE_DEFAULT и протоколы пошагового исполнения.

## MUST_LOAD (by RAW)
- PIPE_DEFAULT
- STEP_RUN_PROTOCOL
- FOCUS_LOOP_PROTOCOL
- COMMANDS

## Steps
S5.1 Load PIPE_DEFAULT
S5.2 If ROUTE_TOKEN.PIPE_SELECTED is domain pipe:
- handoff via PIPE_DEFAULT routing rules
- if domain pipe missing -> GAP
S5.3 Enable protocols:
- STEP_RUN_PROTOCOL
- FOCUS_LOOP_PROTOCOL
- COMMANDS
S5.4 Force EXEC_MODE=STEP_RUN
- единая команда продолжения: "го"

## Output
- PIPE_READY: true | GAP
- NEXT_PROMPT: "го"

---

# [S6] LOG INIT
## Цель
Подтвердить доступ к лог-панелям и правилам логирования.

## MUST_LOAD (by RAW)
- LOG_RULES
- RUN_LOG
- TOKEN_ARCHIVE
- DECISION_LOG

## Steps
S6.1 Load LOG_RULES
S6.2 Confirm panels are accessible
- if any missing -> GAP (если не MUST_LOAD), STOP (если MUST_LOAD задан как required в manifest)
S6.3 Initialize session log headers (in-memory, not writing):
- RUN_ID
- ROUTE_TOKEN hash
- timestamp
- EXEC_MODE
- TRACE_ON

## Output
- LOG_READY: true | GAP

---

## [M] FINAL BOOT GATES
PASS если:
- ENTRYPOINT_OK
- BOOT_CORE_ON
- MUST_LOAD_OK
- ROUTE_TOKEN built
- NAV_OK != STOP
- PIPE_READY != STOP
- LOG_READY != STOP

STOP если:
- TASK_TEXT отсутствует
- MUST_LOAD missing/marker missing

GAP если:
- требуется доменный IDX/PIPE/панель по ROUTE_TOKEN, но не найдено

---

## [M] BOOT COMPLETE OUTPUT TEMPLATE
BOOT_OUTPUT:
- BOOT_STATUS: PASS|GAP|STOP
- FAIL_CODE: (optional)
- TRACE_ON: true
- ROUTE_TOKEN: (present if PASS/GAP after routing)
- NEXT_PROMPT: "го"
