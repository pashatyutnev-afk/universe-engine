# 01__BOOT_SEQ

SCOPE: UE_V2  
DOC_TYPE: BOOT_SEQUENCE (ENTRYPOINT)  
UID: UE.V2.BOOT.SEQ.001  
VERSION: 1.1.0  
STATUS: ACTIVE  
MODE: REPO (USAGE-ONLY, NO-EDIT)  
NAV_RULE: Use RAW links only  

PURPOSE:  
Каноническая последовательность загрузки рантайма.  
Гарантирует: REG/XREF/KB/PIPE/NAV/LOG не пропущены, контекст не засорён, система идёт пошагово через “го”, маршрутизация детерминирована через ROUTER, и управление всегда начинается с SPC-FIRST.

---

## [M] ENTRYPOINT RULE
ENTRYPOINT = валиден, если:
- есть TASK_TEXT (не пустой)

Если TASK_TEXT отсутствует → STOP.

---

## [M] BOOT PRINCIPLES (HARD)
P1) SPC-FIRST HANDOFF (ALWAYS)  
- Первым активируется “главный управляющий SPC” (governance SPC).  
- Он НЕ пишет результат задачи, он поднимает правила, запускает ROUTER и отдаёт управление PIPE/ORC по ROUTE_TOKEN.

P2) NO MASS LOAD  
- запрещено грузить папки/деревья “на всякий случай”  
- после BOOT грузим только REQUIRED_IDX (один доменный + always) и 1–3 target файла

P3) RAW-ONLY  
- любые переходы только по RAW ссылкам  
- PATH в тексте допускается как подпись, но реальный доступ — RAW

P4) STEP-RUN  
- исполнение пайпа строго шагами  
- шаг двигается только командой: го

P5) ROUTER IS LAW  
- ни один доменный пайп/оркестратор не выбирается “вручную”  
- всё через ROUTE_TOKEN

---

## [M] BOOT STAGES (CANON)
STAGES:
S0) ENTRYPOINT_CHECK
S1) STOP_GAP_ARM
S2) TRACE_ON
S3) FAIL_CODES_ON
S4) MUST_LOAD ядро
S5) SPC-FIRST DISPATCH
S6) ROUTER_BUILD_ROUTE_TOKEN
S7) NAV_CONFIRM_REQUIRED_IDX
S8) PIPE_DEFAULT_STEP_RUN_ARM
S9) LOG_INIT_CONFIRM

---

## [M] S0 — ENTRYPOINT_CHECK
ACTIONS:
- подтвердить, что TASK_TEXT присутствует

OUTPUT:
- PASS или STOP

STOP CONDITION:
- TASK_TEXT отсутствует

---

## [M] S1 — STOP_GAP_ARM
ACTIONS:
- открыть и применить правила STOP/GAP:
  - UE_V2/00_BOOT/02__STOP_GAP.md

OUTPUT:
- STOP/GAP policy armed

---

## [M] S2 — TRACE_ON
ACTIONS:
- включить трассу:
  - UE_V2/00_BOOT/06__TRACE.md

OUTPUT:
- TRACE = ON

---

## [M] S3 — FAIL_CODES_ON
ACTIONS:
- включить коды ошибок:
  - UE_V2/00_BOOT/07__FAIL_CODES.md

OUTPUT:
- FAIL_CODES = ON

---

## [M] S4 — MUST_LOAD ядро (MINSET)
ACTIONS (минимально-достаточно):
- открыть:
  - UE_V2/00_BOOT/08__RUNTIME_MANIFEST.md
- загрузить только MUST_LOAD_SET (строго минимум, как в манифесте)

HARD RULE:
- если любой MUST_LOAD missing по RAW → STOP

OUTPUT:
- MUST_LOAD_READY = true

---

## [M] S5 — SPC-FIRST DISPATCH (FIX “сущности не участвуют”)
INTENT:
Сделать так, чтобы система всегда начинала с главного SPC и далее уже раздавала управление.

ACTIONS:
- активировать GOVERNANCE SPC как первый исполнитель BOOT:
  - DOMAIN: SYS_ENT_STD
  - ROLE: TOP_GOVERNANCE_SPC (SPC-FIRST)
- правило: SPC не “делает задачу”, SPC запускает ROUTER и PIPE, и фиксирует “что будет грузиться”.

OUTPUT:
- ACTIVE_SPC = TOP_GOVERNANCE_SPC
- SPC_DISPATCH_READY = true

GAP CONDITION:
- если GOVERNANCE SPC сущность не находится через ENT IDX/manifest → GAP (не STOP)

---

## [M] S6 — ROUTER_BUILD_ROUTE_TOKEN
ACTIONS:
- открыть:
  - UE_V2/00_BOOT/09__TASK_ROUTER.md
- сформировать ROUTE_TOKEN из:
  - TASK_TEXT
  - MODE_HINT (optional)
  - constraints (optional)

OUTPUT:
- ROUTE_TOKEN (обязателен)
- FIRST_STEP_PROMPT = го

GAP CONDITION:
- если ROUTER файл недоступен по RAW → STOP (это MUST_LOAD для запуска)

---

## [M] S7 — NAV_CONFIRM_REQUIRED_IDX
ACTIONS:
- открыть:
  - UE_V2/04_NAV/00__NAV_ROOT.md
- открыть REQUIRED_IDX из ROUTE_TOKEN:
  - always set + один доменный IDX
- подтвердить доступность REG/XREF/KB/PIPE/LOG через IDX (reachability)

OUTPUT:
- NAV_OK = true
- IDX_OK = true

GAP CONDITION:
- доменный IDX отсутствует → GAP
- любой ALWAYS IDX отсутствует → GAP (если это не MUST_LOAD; MUST_LOAD решается на S4)

---

## [M] S8 — PIPE_DEFAULT_STEP_RUN_ARM
ACTIONS:
- открыть:
  - UE_V2/06_PIPE/01__PIPE_DEFAULT.md
- применить протоколы управления шагами:
  - UE_V2/00_BOOT/10__STEP_RUN_PROTOCOL.md
  - UE_V2/00_BOOT/12__FOCUS_LOOP_PROTOCOL.md
  - UE_V2/00_BOOT/13__COMMANDS.md
- подготовить handoff:
  - если ROUTE_TOKEN.PIPE_SELECTED доменный → передать в него через PIPE_DEFAULT routing

OUTPUT:
- PIPE_READY = true
- EXEC_MODE = STEP_RUN

GAP CONDITION:
- PIPE_DEFAULT отсутствует → GAP
- ROUTE_TOKEN.PIPE_SELECTED отсутствует/недоступен → GAP

---

## [M] S9 — LOG_INIT_CONFIRM
ACTIONS:
- открыть правила логирования:
  - UE_V2/14_LOG/00__INDEX_MANIFEST__LOG.md
  - (или если используется отдельный файл правил) UE_V2/14_LOG/00__PIPELINE_CONTRACT__LOG.md
- подтвердить доступность лог-панелей:
  - UE_V2/14_LOG/01__RUN_LOG.md
  - UE_V2/14_LOG/03__TOKEN_ARCHIVE.md
  - UE_V2/14_LOG/04__DECISION_LOG.md

OUTPUT:
- LOG_READY = true

GAP CONDITION:
- отсутствует доступ к любому из LOG файлов → GAP

---

## [M] START_OUTPUT (WHAT TO PRINT AT THE END)
При успешном BOOT печатается только:
- ROUTE_TOKEN
- FIRST_STEP_PROMPT: го

---

## [M] STOP / GAP SUMMARY
STOP:
- TASK_TEXT отсутствует
- MUST_LOAD missing по RAW

GAP:
- нет GOVERNANCE SPC сущности (SPC-FIRST не может стартовать)
- нет доменного IDX/PIPE/обязательных панелей
- NAV reachability не подтверждена

---

## [M] INTERFACES (RAW ONLY)
- STOP/GAP:
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/02__STOP_GAP.md

- TRACE:
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/06__TRACE.md

- FAIL CODES:
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/07__FAIL_CODES.md

- RUNTIME MANIFEST:
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/08__RUNTIME_MANIFEST.md

- TASK ROUTER:
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/09__TASK_ROUTER.md

- NAV ROOT:
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/04_NAV/00__NAV_ROOT.md

- PIPE DEFAULT:
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/06_PIPE/01__PIPE_DEFAULT.md

- STEP RUN PROTOCOL:
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/10__STEP_RUN_PROTOCOL.md

- FOCUS LOOP:
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/12__FOCUS_LOOP_PROTOCOL.md

- COMMANDS:
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/13__COMMANDS.md

- LOG INDEX MANIFEST:
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/14_LOG/00__INDEX_MANIFEST__LOG.md

END.
