SCOPE: Universe Engine (UE_V2)
DOC_TYPE: LAW / STANDARD
UID: UE.V2.LAW.NAV.STACK.014
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only

---

## [M] PURPOSE
Зафиксировать канон навигации UE_V2 так, чтобы:
- система стартовала детерминированно через START→ROUTER→NAV→PIPE
- контекст не засорялся
- ссылки (RAW) жили только в контролируемых местах
- локальные “точки старта” существовали по всей пирамиде, но вход был один

---

## [M] DEFINITIONS
ROOT_LINK_BASE — глобальная база RAW ссылок (вне рантайма).
START (BOOT) — единая точка входа в рантайм.
ROUTER — сущность, формирующая ROUTE_TOKEN.
NAV_ROOT — навигационный корень, который открывает нужные индексы по ROUTE_TOKEN.
INDEX_MANIFEST — адресная книга папки: KEY → RAW + краткий смысл + мета.
PIPELINE_CONTRACT — контракт действий: шаги, роли, токены. RAW не хранит.
START_NODE — локальная старт-капсула домена/папки. RAW не хранит.

---

## [M] CANON: NAV STACK (PYRAMID)
### L0: GLOBAL ENTRY
1) TASK_TEXT → START (BOOT)
2) START включает: TRACE, FAIL_CODES, LOG_INIT, MUST_LOAD минимумы
3) START вызывает ROUTER → получает ROUTE_TOKEN

### L1: NAV
4) NAV_ROOT открывает REQUIRED_IDX из ROUTE_TOKEN
5) Проверка доступа к REG/XREF/KB/PIPE/LOG через IDX

### L2: LOCAL ENTRY (START_NODE)
6) По ROUTE_TOKEN.DOMAIN открывается START_NODE (локальный старт)
7) START_NODE добавляет REQUIRED_IDX_LOCAL и выбирает DEFAULT_PIPE_ID

### L3: PIPE
8) PIPE_DEFAULT делает handoff в доменный PIPE по DEFAULT_PIPE_ID
9) PIPE исполняется в STEP-RUN, отдавая управление через “го”

---

## [M] LINK PLACEMENT POLICY (VERY IMPORTANT)
RAW ссылки разрешены только в местах навигации.

### ALLOWED (где RAW живут)
- ROOT_LINK_BASE (вне рантайма)
- START (BOOT)
- INDEX_MANIFEST (адресная книга папки)

### FORBIDDEN (где RAW запрещены)
- PIPELINE_CONTRACT (только KEY/ID)
- START_NODE (только KEY/ID)
- сущности (SPC/ORC/CTL/VAL/QA/ENG/XREF): RAW запрещены
- любые прочие документы: RAW запрещены

Смысл:
- адреса = INDEX_MANIFEST
- действия = PIPELINE_CONTRACT
- старт локальный = START_NODE
- сущности = знания/обязанности без навигационного мусора

---

## [M] INTERACTION CANON (INDEX_MANIFEST ↔ PIPELINE_CONTRACT ↔ START_NODE)
### INDEX_MANIFEST
- хранит: KEY, RAW, TYPE, SCOPE, STATUS, BRIEF
- отвечает на вопрос “где файл и что это”

### PIPELINE_CONTRACT
- хранит только KEY целевых объектов (SPC/KB/PANELS/etc)
- при выполнении: резолвит RAW через INDEX_MANIFEST
- отвечает на вопрос “что делать и кто участвует”

### START_NODE
- хранит DEFAULT_PIPE_ID, REQUIRED_IDX_LOCAL, EXEC_MODE_DEFAULT
- отвечает на вопрос “как стартовать тут быстро и правильно”

---

## [M] ANTI-NOISE LOAD POLICY (RECONFIRMED)
- ALWAYS: START + MANIFEST + ROUTER + NAV_ROOT
- THEN: 1 доменный IDX + 1 PIPELINE_CONTRACT + 1–3 target файла
- NEVER: массовая загрузка деревьев и обход индексов
- OUTPUT-FIRST: максимум контекста под результат, не под справку

---

## [M] GATES
PASS если:
- ROUTE_TOKEN сформирован
- NAV_ROOT доступен
- REQUIRED_IDX открыт
- найден и открыт START_NODE домена
- найден и открыт доменный PIPELINE_CONTRACT

STOP если:
- нет TASK_TEXT
- missing MUST_LOAD (как в START)

GAP если:
- нет START_NODE или PIPELINE_CONTRACT для домена
- нет INDEX_MANIFEST папки (нельзя резолвить адреса)

---

## [M] MIGRATION RULE (когда переименовываешь/чистишь)
- Сначала правится INDEX_MANIFEST (ключи и RAW)
- Потом правится START_NODE (DEFAULT_PIPE_ID и REQUIRED_IDX_LOCAL)
- Потом правится PIPELINE_CONTRACT (ключи целей)
- Сущности не трогаем ссылками, только смысл/обязанности
