# 01__GVN__ENTRY_GUARD__ORC__ENT

SCOPE: UE_V2 / ORC_ENT / GOVERNANCE
DOC_TYPE: ORC_ENTITY (GOVERNANCE)
UID: UE.V2.ORC.GVN.ENTRY_GUARD.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
ROLE: входной страж рантайма. Валидирует вход, включает трассу, запрещает обходы, переводит задачу в ROUTE_TOKEN.

---

## [M] INTENT
Сделать так, чтобы любая задача:
- не стартовала без TASK_TEXT
- не проходила мимо BOOT → ROUTER → NAV → PIPE → LOG
- не грузила лишнее (ANTI_NOISE_LOAD_POLICY)
- работала пошагово через STEP-RUN ("го")
- не допускала неявных/не детерминированных решений

---

## [M] MIN_INPUTS
REQUIRED:
- TASK_TEXT

OPTIONAL:
- MODE_HINT: FAST | RELEASE_READY | MASTERPIECE
- constraints: platform, duration, style, references, guardrails

---

## [M] OUTPUTS
ENTRY_GUARD_OUTPUT:
- ENTRY_STATUS: PASS | STOP | GAP
- ENTRY_NOTES: кратко, что принято/что отсутствует
- REQUIRED_ACTION: что именно нужно открыть/подтвердить дальше
- START_OUTPUT (если PASS):
  - ROUTE_TOKEN (обязателен)
  - FIRST_STEP_PROMPT: "го"

---

## [M] GUARDED CONDITIONS (что обязано быть выполнено)
G0) Task presence:
- TASK_TEXT exists and not empty

G1) Mandatory boot chain must be respected:
- BOOT_SEQ applied
- STOP_GAP applied
- TRACE enabled
- FAIL_CODES enabled

G2) MUST_LOAD ядро:
- RUNTIME_MANIFEST доступен
- MUST_LOAD_SET подхвачен (минимум)

G3) Routing:
- TASK_ROUTER доступен
- ROUTE_TOKEN сформирован (DOMAIN, ARTIFACT_TYPE, MODE, PIPE_SELECTED, DEFAULT_ORC, REQUIRED_IDX, REQUIRED_CHECKS, EXEC_MODE)

G4) Nav proof:
- NAV_ROOT доступен
- IDX из REQUIRED_IDX доступен
- подтвержден доступ к REG/XREF/KB/PIPE/LOG через IDX (хотя бы “есть ссылки”)

G5) Pipe proof:
- PIPE_DEFAULT доступен
- STEP_RUN_PROTOCOL, FOCUS_LOOP_PROTOCOL включаемы
- COMMANDS доступны

G6) Log proof:
- LOG_RULES доступны
- RUN_LOG, TOKEN_ARCHIVE, DECISION_LOG доступны

---

## [M] PROCEDURE (ENTRY FLOW)
E0) Normalize input
- trim TASK_TEXT
- set MODE = MODE_HINT else default RELEASE_READY
- constraints = {} if absent

E1) Entrypoint check
IF TASK_TEXT отсутствует → STOP
- FAIL_CODE: STOP.INPUT_ABSENT.TASK_TEXT
- ENTRY_NOTES: "нет TASK_TEXT, старт невозможен"

E2) Enforce canonical start sequence
- обязать открыть BOOT_SEQ, STOP_GAP, TRACE, FAIL_CODES
IF любой из MUST_LOAD для старта недоступен → STOP
- FAIL_CODE: STOP.MUST_LOAD.MISSING

E3) Require runtime manifest
- обязать открыть RUNTIME_MANIFEST и взять MUST_LOAD_SET (минимум)
IF manifest/must_load_set недоступен → STOP
- FAIL_CODE: STOP.MUST_LOAD.MISSING

E4) Require routing
- обязать открыть TASK_ROUTER
- сформировать ROUTE_TOKEN (детерминированно)
IF ROUTE_TOKEN не сформирован → GAP
- FAIL_CODE: GAP.ROUTER.MISSING_OR_UNCONFIRMED

E5) Require NAV proof
- открыть NAV_ROOT
- открыть REQUIRED_IDX из ROUTE_TOKEN
- подтвердить наличие путей/ссылок на REG/XREF/KB/PIPE/LOG
IF отсутствует REQUIRED_IDX или панели в нем → GAP
- FAIL_CODE: GAP.NAV.IDX_OR_PANEL_MISSING

E6) Require PIPE + STEP-RUN protocols
- открыть PIPE_DEFAULT
- включить STEP_RUN_PROTOCOL + FOCUS_LOOP_PROTOCOL + COMMANDS
IF PIPE_DEFAULT отсутствует → STOP
- FAIL_CODE: STOP.PIPE_DEFAULT.MISSING

E7) Require LOG init
- открыть LOG_RULES
- подтвердить RUN_LOG, TOKEN_ARCHIVE, DECISION_LOG
IF логи недоступны → GAP (не стопим, но запрещаем “длинные прогоны”)
- FAIL_CODE: GAP.LOG.PANELS_MISSING
- REQUIRED_ACTION: "разрешить только короткий шаг до восстановления логов"

E8) PASS
- ENTRY_STATUS = PASS
- START_OUTPUT:
  - ROUTE_TOKEN = сформированный
  - FIRST_STEP_PROMPT = "го"
- ENTRY_NOTES: "вход валиден, цепочка старта соблюдена, можно step-run"

---

## [M] ANTI-NOISE POLICY (ENFORCED)
ALWAYS LOAD (минимум):
- START
- RUNTIME_MANIFEST
- TASK_ROUTER
- NAV_ROOT

THEN:
- 1 доменный IDX (из ROUTE_TOKEN.REQUIRED_IDX)
- 1–3 target файла (строго по PIPE шагу)

NEVER:
- обход IDX
- массовая загрузка деревьев
- “угадывание” сущностей без подтверждения в IDX/REG

---

## [M] TRACE EVENTS (минимальный словарь)
TRACE_KEYS:
- ENTRY.START
- ENTRY.INPUT_OK
- ENTRY.BOOT_OK
- ENTRY.MANIFEST_OK
- ENTRY.ROUTE_TOKEN_READY
- ENTRY.NAV_OK
- ENTRY.PIPE_OK
- ENTRY.LOG_OK
- ENTRY.PASS
- ENTRY.STOP(code)
- ENTRY.GAP(code)

---

## [M] FAIL / GAP RULES
STOP только если:
- нет TASK_TEXT
- MUST_LOAD missing (boot/manifest/pipe_default)

GAP если:
- отсутствует доменный PIPE/IDX/панель (REG/XREF/KB/LOG)
- ROUTE_TOKEN не сформирован или не подтвержден

---

## [M] DEFAULT DECISION
По умолчанию:
- если не можем подтвердить обязательные ссылки через IDX → GAP, не “придумываем”
- если лог-панели отсутствуют → GAP и ограничиваемся коротким шагом
