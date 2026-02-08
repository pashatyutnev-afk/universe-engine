# 01__PIPE_DEFAULT

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: PIPE
UID: UE.V2.PIPE.DEFAULT.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Универсальный пайп исполнения задач: маршрутизация -> шаги -> контроль -> упаковка. Делает handoff в доменные пайпы по ROUTE_TOKEN.

---

## [M] INTENT
Дать единый механизм исполнения любой задачи:
- выбрать домен и пайп (через ROUTE_TOKEN)
- работать пошагово (STEP-RUN) и итеративно (FOCUS-LOOP)
- выбирать сущности через REG+XREF+KB scope
- не выпускать результат без обязательных проверок и упаковки

---
# 01__PIPE_DEFAULT

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: PIPE
UID: UE.V2.PIPE.DEFAULT.001
VERSION: 1.2.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Универсальный пайп исполнения задач: SPC intake -> маршрутизация -> шаги -> контроль -> упаковка. Делает handoff в доменные пайпы по ROUTE_TOKEN.

---

## [M] INTENT
Дать единый механизм исполнения любой задачи:
- выбрать домен и пайп (через ROUTE_TOKEN)
- работать пошагово (STEP-RUN) и итеративно (FOCUS-LOOP)
- **обязательный SPC intake до ORC** (главный спец принимает задачу первым)
- выбирать сущности через REG + XREF + KB scope
- не выпускать результат без обязательных проверок и упаковки

---

## [M] INPUTS
- ROUTE_TOKEN (обязателен):
  DOMAIN, ARTIFACT_TYPE, MODE, PIPE_SELECTED, DEFAULT_ORC, REQUIRED_IDX, REQUIRED_CHECKS, EXEC_MODE
- TASK_TEXT (обязателен)
- OPTIONAL:
  - BRIEF_TOKEN (если уже сформирован)
  - MODE_HINT (FAST|RELEASE_READY|MASTERPIECE)
  - constraints (platform, duration, style, references)

---

## [M] OUTPUTS
- SPC_TOKEN (STD/15) — результат первичного приёма задачи главным SPC
- BRIEF_TOKEN (STD/15) — минимальный бриф (если не был дан)
- PLAN_TOKEN (STD/15)
- KB_TOKEN (STD/15)
- STEP tokens (STD/15)
- REPORT_TOKEN (CTL/VAL/QA)
- PACK_TOKEN (если требуется "готовый" результат)
- BASELINE_TOKEN (если требуется signoff)

---

## [M] PRECONDITIONS (MUST)
P0) Entry: запуск должен быть через START (LAW_17)
P1) MUST_LOAD ядро доступно (LAW_18)
P2) Доступны IDX: REG, XREF, KB, PIPE, LOG (через NAV_ROOT)
P3) NOISE_BUDGET включён (LAW_20)

Если любое P0–P3 не выполнено → STOP или GAP по STOP_GAP.

---

## [M] ROUTING (PIPE DEFAULT)
R0) Если ROUTE_TOKEN.PIPE_SELECTED задан → использовать его как PRIMARY_TARGET_PIPE.
R1) Иначе выбрать PRIMARY_TARGET_PIPE по DOMAIN:
- CORE -> PIPE_DEFAULT (текущий)
- MUSIC -> PIPE_MUSIC_TRACK или PIPE_MUSIC_LYRICS или PIPE_MUSIC_IDENTITY (по ARTIFACT_TYPE)
- VIS -> PIPE_VIS
- LOR -> PIPE_LOR
- REL -> PIPE_REL
R2) Если доменный пайп отсутствует → GAP (создать пайп / IDX / обязательные сущности).
R3) Handoff:
- PIPE_DEFAULT исполняет только bootstrap-шаги (SPC/INTAKE/PLAN/KB/ROUTE) и передаёт управление доменному пайпу.
- Исключение: DOMAIN=CORE — остаёмся в PIPE_DEFAULT.

---

## [M] EXECUTION MODEL
E0) Всегда использовать STEP-RUN (один шаг -> токен -> "го").
E1) Если ROUTE_TOKEN.EXEC_MODE=FOCUS-LOOP → вставить FOCUS-LOOP на текущем фокусе (через PIPE_FOCUS_LOOP протокол).
E2) Любой STEP обязан:
- **сначала подтвердить SPC_TOKEN (или сформировать)**
- выбрать партию сущностей через REG + XREF + KB_SCOPE
- соблюсти лимиты (LAW_20 + CTL budgets)
- записать токены в LOG (RUN_LOG + TOKEN_ARCHIVE + DECISION_LOG при необходимости)

---

## [M] BOOTSTRAP STEPS (ALWAYS)

### STEP_00 (S0 INTAKE)
- если BRIEF_TOKEN отсутствует -> собрать BRIEF_TOKEN (минимум)
- подтвердить ROUTE_TOKEN (или сформировать через TASK_ROUTER)
- нормализовать MODE_HINT/constraints (если даны)

### STEP_00A (S1 SPC INTAKE — MUST)
Цель: “главный SPC” принимает задачу **перед** любым ORC/доменным пайпом.

- открыть SPC слой через NAV/IDX:
  - REQUIRED: SPC_ENT INDEX_MANIFEST + SPC_ENT PIPELINE_CONTRACT
- сформировать SPC_TOKEN:
  - SPC_OWNER (кто главный SPC для этой задачи)
  - SPC_FAMILY_KEY (если применимо)
  - INTAKE_SUMMARY (1–3 строки)
  - REQUIRED_SPECIALISTS (какие роли/сущности обязаны участвовать)
  - BRIEF_UPDATES (что уточнили/нормализовали)
  - CONSTRAINTS_LOCK (что запрещено/обязательно)
- если SPC слой/контракт отсутствует → GAP (не игнорировать; именно GAP, не обход)
- после SPC_TOKEN:
  - если BRIEF_TOKEN был пуст/слабый → обновить BRIEF_TOKEN по SPC_TOKEN
  - разрешить запуск ORC/доменного пайпа

### STEP_01 (S2 PLAN)
- сформировать PLAN_TOKEN:
  - coverage level
  - budgets (FAST/RELEASE_READY/MASTERPIECE)
  - список стадий доменного пайпа
  - required checks (CTL/VAL/QA) из ROUTE_TOKEN
- учесть REQUIRED_SPECIALISTS из SPC_TOKEN (не выкидывать)

### STEP_02 (S3 KB)
- сформировать KB_TOKEN:
  - KB_SCOPE_ID
  - правила и запреты (do_not)
  - allowed sources (KB_SOURCES)
  - подтвердить, что KB в границах (KB_BOUNDARIES)

После STEP_02:
- handoff в доменный пайп (PRIMARY_TARGET_PIPE), если DOMAIN != CORE

---

## [M] DOMAIN HANDOFF MAP (RAW PREFERRED)
MUSIC:
- TRACK   -> (RAW) UE_V2/06_PIPE/20__PIPE_MUSIC_TRACK.md
- LYRICS  -> (RAW) UE_V2/06_PIPE/21__PIPE_MUSIC_LYRICS.md
- IDENTITY-> (RAW) UE_V2/06_PIPE/22__PIPE_MUSIC_IDENTITY.md
REL:
- (RAW) UE_V2/06_PIPE/14__PIPE_REL.md
VIS:
- (RAW) UE_V2/06_PIPE/04__PIPE_VIS.md
LOR:
- (RAW) UE_V2/06_PIPE/05__PIPE_LOR.md
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
- выполнены STEP_00, STEP_00A, STEP_01, STEP_02 и handoff выполнен (для доменных задач)
- или для CORE задач завершены нужные стадии с токенами и логами

REWORK если:
- нет токенов/логов
- нарушены лимиты или пропущены контрольные стадии
- SPC_TOKEN не сформирован/не подтверждён до ORC

GAP если:
- отсутствует SPC слой/контракт/IDX/обязательные сущности
- отсутствует доменный пайп/IDX/обязательные сущности

STOP если:
- нарушены P0–P3 (entrypoint/manifest/idx/noise) или нет задачи

## [M] INPUTS
- ROUTE_TOKEN (обязателен): DOMAIN, ARTIFACT_TYPE, MODE, PIPE_SELECTED, DEFAULT_ORC, REQUIRED_IDX, REQUIRED_CHECKS, EXEC_MODE
- TASK_TEXT (обязателен)
- OPTIONAL: BRIEF_TOKEN (если уже сформирован)

---

## [M] OUTPUTS
- STEP tokens (STD/15)
- REPORT_TOKEN (CTL/VAL/QA)
- PACK_TOKEN (если требуется "готовый" результат)
- BASELINE_TOKEN (если требуется signoff)

---

## [M] PRECONDITIONS (MUST)
P0) Entry: запуск должен быть через START (LAW_17)
P1) MUST_LOAD ядро доступно (LAW_18)
P2) Доступны IDX: REG, XREF, KB, PIPE, LOG (через NAV_ROOT)
P3) NOISE_BUDGET включён (LAW_20)
Если любое P0–P3 не выполнено → STOP или GAP по STOP_GAP.

---

## [M] ROUTING (PIPE DEFAULT)
R0) Если ROUTE_TOKEN.PIPE_SELECTED задан → использовать его как PRIMARY_TARGET_PIPE.
R1) Иначе выбрать PRIMARY_TARGET_PIPE по DOMAIN:
- CORE -> PIPE_DEFAULT (текущий)
- MUSIC -> PIPE_MUSIC_TRACK или PIPE_MUSIC_LYRICS или PIPE_MUSIC_IDENTITY (по ARTIFACT_TYPE)
- VIS -> PIPE_VIS
- LOR -> PIPE_LOR
- REL -> PIPE_REL
R2) Если доменный пайп отсутствует → GAP (создать пайп / IDX / обязательные сущности).
R3) Handoff:
- PIPE_DEFAULT исполняет только bootstrap-шаги (INTAKE/PLAN/KB/ROUTE) и передаёт управление доменному пайпу.
- Исключение: DOMAIN=CORE — остаёмся в PIPE_DEFAULT.

---

## [M] EXECUTION MODEL
E0) Всегда использовать STEP-RUN (один шаг -> токен -> "го").
E1) Если ROUTE_TOKEN.EXEC_MODE=FOCUS-LOOP → вставить FOCUS-LOOP на текущем фокусе (через PIPE_FOCUS_LOOP протокол).
E2) Любой STEP обязан:
- выбрать партию сущностей через REG + XREF + KB_SCOPE
- соблюсти лимиты (LAW_20 + CTL budgets)
- записать токены в LOG (RUN_LOG + TOKEN_ARCHIVE + DECISION_LOG при необходимости)

---

## [M] BOOTSTRAP STEPS (ALWAYS)
STEP_00 (S0 INTAKE):
- если BRIEF_TOKEN отсутствует -> собрать BRIEF_TOKEN (минимум)
- подтвердить ROUTE_TOKEN (или сформировать через TASK_ROUTER)

STEP_01 (S2 PLAN):
- сформировать PLAN_TOKEN:
  - coverage level
  - budgets (FAST/RELEASE_READY/MASTERPIECE)
  - список стадий доменного пайпа
  - required checks (CTL/VAL/QA) из ROUTE_TOKEN

STEP_02 (S3 KB):
- сформировать KB_TOKEN:
  - KB_SCOPE_ID
  - правила и запреты (do_not)
  - allowed sources (KB_SOURCES)
- подтвердить, что KB в границах (KB_BOUNDARIES)

После STEP_02:
- handoff в доменный пайп (PRIMARY_TARGET_PIPE), если DOMAIN != CORE

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
