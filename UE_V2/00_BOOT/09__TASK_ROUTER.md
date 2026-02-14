# 09__TASK_ROUTER
KIND: ENGINE
ROLE: ROUTER
SCOPE: SYSTEM
STATUS: CANON
VERSION: 1.0.0

## 0) PURPOSE
Детерминированно маршрутизировать любую задачу:
- выбрать DOMAIN
- выбрать ARTIFACT_TYPE
- выбрать PROFILE_KEY
- сформировать REQUIRED_SET (IDX/ROLES/ENG/KB/VAL/OUTPUTS/NO_GO)
- выдать ROUTE_TOKEN, пригодный для PIPE исполнения

ROUTER НЕ создаёт контент и НЕ “гуглит”. Он только выбирает маршрут и обязательные компоненты.

---

## 1) INPUTS
REQUIRED:
- TASK_TEXT (текст пользователя)

OPTIONAL:
- USER_FILES (архивы/скрины/доки)
- USER_CONTEXT (внутренний контекст/прошлые решения, если есть)
- USER_CONSTRAINTS (язык, формат, сроки, стиль)

---

## 2) OUTPUTS
ROUTER всегда выдаёт один объект: ROUTE_TOKEN

### 2.1 ROUTE_TOKEN (schema)
ROUTE_TOKEN:
  META:
    ROUTER_VERSION: "1.0.0"
    TIMESTAMP: "<runtime>"
    TRACE_ID: "<runtime>"
  TASK:
    TASK_TEXT_HASH: "<runtime>"
    USER_INTENT: "<detected>"
  ROUTE:
    DOMAIN: "<SYS|MUSIC|VIDEO|COPY|DESIGN|KB|OTHER>"
    ARTIFACT_TYPE: "<PATCH|FULL_PATCH|KB_PATCH|PLAN|AUDIT|SPEC|OTHER>"
    MODE: "<REPO|WEB_ALLOWED|FAIL>"
    PROFILE_KEY: "<PROFILE.* or NONE>"
    PIPE_SELECTED: "<KEY:PIPE.*>"
  REQUIRED_SET:
    REQUIRED_IDX: ["KEY:IDX.*", "..."]
    REQUIRED_ROLES: ["SPC","ORC","CTL","VAL"]   # default for production
    REQUIRED_ENG_KEYS: ["KEY:ENG.*", "..."]    # may be empty at early stage
    REQUIRED_KB_KEYS:  ["KEY:KB.*",  "..."]    # may be empty at early stage
    REQUIRED_VAL_KEYS: ["KEY:VAL.*", "..."]    # must include coverage gate for production
    OUTPUT_CONTRACT:   ["BRIEF_TOKEN","ENGINE_PLAN_TOKEN","ENGINE_RUN_LEDGER","VAL_REPORT","PACK_OUTPUT"]
    NO_GO_LIST:        ["..."]                 # anti-trash
  GATES:
    STOP_CONDITIONS: ["FAIL:INPUT_ABSENT","FAIL:ENTRYPOINT_MISSING","FAIL:FILE_NOT_FOUND","FAIL:MARKER_NOT_CONFIRMED","FAIL:SCOPE_VIOLATION"]
    QUALITY_MINIMUM: ["VAL.ENGINE_COVERAGE_GATE","VAL.OUTPUT_CONTRACT_GATE"]

ROUTER must be deterministic: same task + same context -> same ROUTE_TOKEN.

---

## 3) ROUTING RULES (DETERMINISTIC)
### 3.1 LANGUAGE DETECTION (light)
- if TASK_TEXT contains mostly Cyrillic -> LANG=RU else LANG=EN/OTHER
LANG affects PROFILE selection only (not DOMAIN by itself).

### 3.2 DOMAIN DETECTION (priority order)
DOMAIN=MUSIC if any of:
- "трек/песня/альбом/релиз/саунд/бит/вокал/дуэт/лейбл/чарты"

DOMAIN=SYS if any of:
- "архитектура/папки/манифест/контракт/роутер/нав/пайп/гейты/протокол"

DOMAIN=KB if any of:
- "база знаний/KB/модуль знаний/правила/метрики/чеклисты"

Else DOMAIN=OTHER.

### 3.3 ARTIFACT_TYPE DETECTION
If user asks to "переписать/исправить файл/дать текст файла/патч" -> ARTIFACT_TYPE=FULL_PATCH
If user asks "план/список/порядок" -> ARTIFACT_TYPE=PLAN
If user asks "добавить знания/модуль KB" -> ARTIFACT_TYPE=KB_PATCH
Else ARTIFACT_TYPE=SPEC

### 3.4 PROFILE SELECTION (anti-trash)
PROFILE_KEY is mandatory for DOMAIN content-production (MUSIC/VIDEO/COPY/DESIGN).
If DOMAIN=SYS -> PROFILE_KEY=PROFILE.SYS.CORE_MAINTENANCE
If DOMAIN=MUSIC and LANG=RU and mentions "хиты/топ/2 релиза/дуэт" -> PROFILE_KEY=PROFILE.MUSIC.HIT_FACTORY.RU.DUO
If DOMAIN=MUSIC but no details -> PROFILE_KEY=PROFILE.MUSIC.GENERAL
If DOMAIN=KB -> PROFILE_KEY=PROFILE.KB.BUILD_MODULE
Else PROFILE_KEY=PROFILE.GENERAL

### 3.5 PIPE SELECTION (KEY-based)
PIPE_SELECTED is a KEY, resolved later by NAV/INDEX:
- SYS -> KEY:PIPE.SYS.MAINTENANCE
- MUSIC -> KEY:PIPE.MUSIC.FACTORY
- KB -> KEY:PIPE.KB.BUILD
- OTHER -> KEY:PIPE.GENERAL

---

## 4) REQUIRED_SET DEFAULTS (IMPORTANT)
### 4.1 REQUIRED_ROLES defaults
If ARTIFACT_TYPE in [FULL_PATCH, PLAN, AUDIT] and DOMAIN=SYS:
- REQUIRED_ROLES = ["SPC","ORC","CTL","VAL"]   # still required for consistency

If DOMAIN in [MUSIC,VIDEO,COPY,DESIGN]:
- REQUIRED_ROLES = ["SPC","ORC","CTL","VAL"]

### 4.2 OUTPUT_CONTRACT defaults
For SYS patches:
- OUTPUT_CONTRACT = ["PATCH_OUTPUT","VAL_REPORT","CHANGELOG_ENTRY","NEXT_POINTER"]

For content production (MUSIC etc.):
- OUTPUT_CONTRACT = ["BRIEF_TOKEN","ENGINE_PLAN_TOKEN","ENGINE_RUN_LEDGER","VAL_REPORT","PACK_OUTPUT"]

### 4.3 REQUIRED_VAL_KEYS defaults (coverage is mandatory)
Always include:
- KEY:VAL.ENGINE_COVERAGE_GATE
- KEY:VAL.OUTPUT_CONTRACT_GATE

Optionally (domain-specific later):
- KEY:VAL.MUS.ABSOLUTE_SCORECARD
- KEY:VAL.MUS.ANTI_COPY
etc.

### 4.4 REQUIRED_IDX defaults (layer access)
Minimal:
- KEY:IDX.CORE.BOOT
- KEY:IDX.CORE.SYS
- KEY:IDX.CORE.NAV
- KEY:IDX.CORE.PIPE
If DOMAIN=MUSIC:
- + KEY:IDX.SUBSYSTEM.MUSIC
- + KEY:IDX.ENT.ENG
- + KEY:IDX.KB.MUSIC (может быть пусто, но ключ должен существовать)

---

## 5) FAIL BEHAVIOR (NO GUESSING)
If TASK_TEXT missing -> FAIL: INPUT_ABSENT
If PROFILE_KEY cannot be selected deterministically -> FAIL: MARKER_NOT_CONFIRMED
If PIPE_SELECTED key is undefined -> FAIL: ENTRYPOINT_MISSING

ROUTER must output FAIL with minimal next action required, not “best-effort guesses”.

---

## 6) ROUTER OUTPUT TEMPLATE (what PIPE expects)
When emitting ROUTE_TOKEN, include:
- DOMAIN, ARTIFACT_TYPE, PROFILE_KEY, PIPE_SELECTED
- REQUIRED_SET fully populated (even if some lists are empty)
- STOP_CONDITIONS and minimum quality gates

END.
