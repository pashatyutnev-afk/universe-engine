# 01__PIPE_DEFAULT

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: PIPE
UID: UE.V2.PIPE.DEFAULT.001
VERSION: 1.2.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only

PURPOSE:
Универсальный пайп исполнения задач: маршрутизация -> шаги -> контроль -> упаковка.
Делает handoff в доменные пайпы по ROUTE_TOKEN.
Фиксирует правило: сначала SPC-INTAKE (первый спец), потом ORC и домены.

---

## [M] INTENT
Дать единый механизм исполнения любой задачи:
- выбрать домен и пайп (через ROUTE_TOKEN)
- работать пошагово (STEP-RUN) и итеративно (FOCUS-LOOP)
- выбирать сущности через REG+XREF+KB scope
- не выпускать результат без обязательных проверок и упаковки
- обеспечить, что первый контакт с задачей делает SPC-INTAKE (семейство GOV)

---

## [M] INPUTS
- ROUTE_TOKEN (обязателен):
  DOMAIN, ARTIFACT_TYPE, MODE, PIPE_SELECTED, DEFAULT_ORC, REQUIRED_IDX, REQUIRED_CHECKS, EXEC_MODE
- TASK_TEXT (обязателен)
- OPTIONAL: BRIEF_TOKEN (если уже сформирован)
- OPTIONAL: INTAKE_TOKEN (если уже сформирован)
- OPTIONAL: MODE_HINT (FAST|RELEASE_READY|MASTERPIECE)
- OPTIONAL: constraints (platform, duration, style, references)

---

## [M] OUTPUTS
- STEP tokens (STD/15)
- INTAKE_TOKEN (SPC intake result: goals, tone, constraints, risks, required specialists)
- BRIEF_TOKEN (минимум)
- PLAN_TOKEN (stages + budgets)
- KB_TOKEN (scope + boundaries)
- REPORT_TOKEN (CTL/VAL/QA)
- PACK_TOKEN (если требуется "готовый" результат)
- BASELINE_TOKEN (если требуется signoff)
- HANDOFF_TOKEN (куда передали и на каком основании)

---

## [M] PRECONDITIONS (MUST)
P0) Entry: запуск должен быть через START (LAW_17)
P1) MUST_LOAD ядро доступно (LAW_18)
P2) Доступны IDX: REG, XREF, KB, PIPE, LOG (через NAV_ROOT)
P3) NOISE_BUDGET включён (LAW_20)

Если любое P0–P3 не выполнено -> STOP или GAP по STOP_GAP.

---

## [M] ROUTING (PIPE DEFAULT)
R0) Если ROUTE_TOKEN.PIPE_SELECTED задан -> использовать его как PRIMARY_TARGET_PIPE.
R1) Иначе выбрать PRIMARY_TARGET_PIPE по DOMAIN:
- CORE -> PIPE_DEFAULT (текущий)
- MUSIC -> PIPE_MUSIC_TRACK или PIPE_MUSIC_LYRICS или PIPE_MUSIC_IDENTITY (по ARTIFACT_TYPE)
- VIS -> PIPE_VIS
- LOR -> PIPE_LOR
- REL -> PIPE_REL

R2) Если доменный пайп отсутствует -> GAP (создать пайп / IDX / обязательные сущности).

R3) Handoff:
- PIPE_DEFAULT исполняет только bootstrap-шаги (INTAKE/PLAN/KB/ROUTE) и передаёт управление доменному пайпу.
- Исключение: DOMAIN=CORE — остаёмся в PIPE_DEFAULT.

---

## [M] EXECUTION MODEL
E0) Всегда использовать STEP-RUN (один шаг -> токен -> "го").
E1) Если ROUTE_TOKEN.EXEC_MODE=FOCUS-LOOP -> вставить FOCUS-LOOP на текущем фокусе (через PIPE_FOCUS_LOOP протокол).
E2) Любой STEP обязан:
- выбрать партию сущностей через REG + XREF + KB_SCOPE
- соблюсти лимиты (LAW_20 + CTL budgets)
- записать токены в LOG (RUN_LOG + TOKEN_ARCHIVE + DECISION_LOG при необходимости)

---

## [M] BOOTSTRAP STEPS (ALWAYS)

### STEP_00 (S0 INTAKE, FIRST SPECIALIST)
Цель: первый контакт с задачей делает SPC-INTAKE, а не ORC/PIPE.

S0.0) Ensure inputs:
- TASK_TEXT должен существовать, иначе STOP (UE.FAIL.INPUT_ABSENT)

S0.1) ROUTE_TOKEN presence:
- если ROUTE_TOKEN отсутствует -> сформировать через TASK_ROUTER (детерминированно)

S0.2) Mandatory SPC-INTAKE:
- если INTAKE_TOKEN отсутствует -> выполнить SPC intake через SPC_ENT PIPELINE_CONTRACT
- FAMILY_HINT: GOV (обязателен)
- вход: TASK_TEXT + MODE_HINT? + constraints?
- выход: INTAKE_TOKEN (goals, tone, constraints, risks, required specialists, suggested DOMAIN/ARTIFACT_TYPE)

S0.3) Sync ROUTE_TOKEN with INTAKE_TOKEN:
- если INTAKE_TOKEN предлагает DOMAIN/ARTIFACT_TYPE и это не конфликтует с ROUTER -> уточнить ROUTE_TOKEN (без эвристик: только явные поля из INTAKE_TOKEN)
- DEFAULT_ORC: берётся из INTAKE_TOKEN (если задан), иначе из ROUTE_TOKEN

S0.4) BRIEF_TOKEN:
- если BRIEF_TOKEN отсутствует -> собрать BRIEF_TOKEN (минимум) на основе TASK_TEXT + INTAKE_TOKEN

Выход STEP_00:
- ROUTE_TOKEN (подтверждён)
- INTAKE_TOKEN (если требовался)
- BRIEF_TOKEN (минимум)
NEXT: "го"

---

### STEP_01 (S2 PLAN)
- сформировать PLAN_TOKEN:
  - coverage level
  - budgets (FAST/RELEASE_READY/MASTERPIECE)
  - список стадий доменного пайпа
  - required checks (CTL/VAL/QA) из ROUTE_TOKEN
NEXT: "го"

---

### STEP_02 (S3 KB)
- сформировать KB_TOKEN:
  - KB_SCOPE_ID
  - правила и запреты (do_not)
  - allowed sources (KB_SOURCES)
  - подтвердить, что KB в границах (KB_BOUNDARIES)
NEXT: "го"

---

## [M] DOMAIN HANDOFF MAP (PATH)
MUSIC:
- TRACK -> UE_V2/06_PIPE/20__PIPE_MUSIC_TRACK.md
- LYRICS -> UE_V2/06_PIPE/21__PIPE_MUSIC_LYRICS.md
- IDENTITY -> UE_V2/06_PIPE/22__PIPE_MUSIC_IDENTITY.md
- MIX/HOOK -> PIPE_MUSIC_TRACK (как focus steps) или FOCUS-ORC, если задано в ROUTE_TOKEN

REL:
- UE_V2/06_PIPE/14__PIPE_REL.md

VIS:
- UE_V2/06_PIPE/04__PIPE_VIS.md

LOR:
- UE_V2/06_PIPE/05__PIPE_LOR.md

CORE:
- остаётся в PIPE_DEFAULT (текущий)

---

## [M] REQUIRED CONTROL (DEFAULT)
На уровне PIPE_DEFAULT (bootstrap):
- CTL readiness + noise budget (минимум)
- VAL doc format (минимум)
- QA accept (минимум)

Доменные проверки берутся из ROUTE_TOKEN.REQUIRED_CHECKS и доменного пайпа.

---

## [M] EXIT RULES (WHEN TO FINISH IN PIPE_DEFAULT)
PIPE_DEFAULT завершается, если:
- DOMAIN != CORE и handoff успешно выполнен (дальше работает доменный пайп)
- DOMAIN = CORE и выполнены: REVIEW -> PACK -> SIGNOFF (если требуется)

---

## [M] GATES
PASS если:
- выполнены bootstrap steps и handoff выполнен (для доменных задач)
- или для CORE задач завершены нужные стадии с токенами и логами

REWORK если:
- нет токенов/логов
- нарушены лимиты или пропущены контрольные стадии

GAP если:
- отсутствует доменный пайп/IDX/обязательные сущности

STOP если:
- нарушены P0–P3 (entrypoint/manifest/idx/noise) или нет задачи
