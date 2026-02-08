# 02__STOP_GAP

SCOPE: UE_V2  
DOC_TYPE: POLICY (STOP / GAP)  
UID: UE.V2.BOOT.STOPGAP.001  
VERSION: 1.1.0  
STATUS: ACTIVE  
MODE: REPO (USAGE-ONLY, NO-EDIT)  
NAV_RULE: Use RAW links only  

PURPOSE:  
Жёстко определить, когда рантайм обязан остановиться (STOP) и когда он обязан выдать “дыру” (GAP).
Политика защищает от обходов, гаданий и засорения контекста.

---

## [M] DEFINITIONS

### STOP
HARD STOP: продолжать нельзя.
Причины:
- нет входа (TASK_TEXT)
- нет RAW для MUST_LOAD
- обязательный маркер не подтверждён
- отсутствует обязательный системный файл шага (MANIFEST/ROUTER/NAV/PIPE_DEFAULT/LOG_RULES)

### GAP
FIXABLE GAP: продолжать можно только после добавления/починки отсутствующего элемента.
Причины:
- нет доменного PIPE/IDX/контракта
- нет обязательной сущности/панели/проверки по ROUTE_TOKEN
- нет KB/примеров/гейтов, требуемых маршрутом

---

## [M] ABSOLUTE RULES (NO BYPASSES)
1) НЕЛЬЗЯ:
- обходить IDX (никаких “прямых” открытий доменных файлов мимо REQUIRED_IDX)
- массово грузить деревья/папки “для ориентации”
- строить маршрут без ROUTE_TOKEN
- выполнять пайплайн без PIPE_DEFAULT
- “угадывать” сущности или их RAW

2) МОЖНО:
- открывать только MUST_LOAD + REQUIRED_IDX + 1–3 целевых файла
- отвечать шагами через STEP-RUN (“го”)
- выдавать только один STOP или один GAP код на шаг

---

## [M] STOP CONDITIONS (CANON)

### S0 ENTRYPOINT CHECK
STOP если:
- отсутствует TASK_TEXT  
CODE: STOP.ENTRY.NO_TASK_TEXT

### RAW AVAILABILITY (любая стадия)
STOP если:
- любой MUST_LOAD файл не открывается по RAW / 404 / нет ссылки  
CODE: STOP.RAW.RAW_MISSING

### MARKER CONFIRMATION (любая стадия)
STOP если:
- в MUST_LOAD документе не найден обязательный [M] блок (маркер)  
CODE: STOP.BOOT.MARKER_MISSING

### S2 MUST_LOAD ядро
STOP если:
- RUNTIME_MANIFEST не доступен или MUST_LOAD_SET не подтверждён  
CODE: STOP.MANIFEST.MUST_LOAD_MISSING

### S3 ROUTING
STOP если:
- ROUTE_TOKEN не сформирован полностью (нет DOMAIN/ARTIFACT_TYPE/MODE/PIPE_SELECTED/REQUIRED_IDX/REQUIRED_CHECKS/EXEC_MODE)  
CODE: STOP.ROUTER.ROUTE_TOKEN_MISSING

### S4 NAV
STOP если:
- NAV_ROOT не доступен  
CODE: STOP.NAV.NAV_ROOT_MISSING
STOP если:
- REQUIRED_IDX не доступен или не найден  
CODE: STOP.IDX.REQUIRED_IDX_MISSING

### S5 PIPE EXEC
STOP если:
- PIPE_DEFAULT не доступен  
CODE: STOP.PIPE.PIPE_DEFAULT_MISSING

### S6 LOG INIT
STOP если:
- LOG_RULES не доступен или отсутствует обязательный набор логов  
CODE: STOP.LOG.LOG_SET_MISSING

---

## [M] GAP CONDITIONS (CANON)

GAP объявляется ТОЛЬКО после того, как:
- MUST_LOAD пройден
- ROUTE_TOKEN сформирован
- NAV_ROOT + REQUIRED_IDX доступны

### DOMAIN PIPE / CONTRACT
GAP если:
- выбран доменный PIPE (PIPE_SELECTED), но файла нет  
CODE: GAP.PIPE.DOMAIN_PIPE_MISSING

GAP если:
- в домене отсутствует PIPELINE_CONTRACT или INDEX_MANIFEST, требуемые маршрутом  
CODE: GAP.PIPE.CONTRACT_MISSING

### REQUIRED CHECKS / PANELS
GAP если:
- REQUIRED_CHECKS перечислены, но соответствующие файлы/правила не доступны  
CODE: GAP.IDX.REQUIRED_CHECKS_MISSING

### ENTITIES (SPC/ORC/CTL/VAL/QA/XREF)
GAP если:
- ROUTE_TOKEN требует сущность/роль/дефолтный хэнд-офф, но:
  - файл отсутствует, или
  - маркеры роли отсутствуют, или
  - нет связки через IDX/REG  
CODE: GAP.ENT.ENT_REQUIRED_MISSING

### KB
GAP если:
- маршрут требует KB элемент (пример/гейт/рубрику), но его нет или он не связан через XREF/IDX  
CODE: GAP.KB.KB_REQUIRED_MISSING

### LOG (архив/решения)
GAP если:
- RUN_LOG есть, но TOKEN_ARCHIVE/DECISION_LOG отсутствуют  
CODE: GAP.LOG.ARCHIVE_MISSING

---

## [M] SINGLE-CODE RULE (ONE STEP → ONE CODE)
На каждом шаге (S0–S6) допускается:
- либо PASS (продолжаем)
- либо ровно один STOP code
- либо ровно один GAP code

Если обнаружено несколько проблем:
- выбирать самую раннюю по sequence (S0→S6)
- внутри шага выбирать самый “жёсткий” (STOP приоритетнее GAP)

---

## [M] REPORT TEMPLATE (MANDATORY)
Если STOP:
- CODE: <STOP.*>
- NOTE: <что missing, 1 строка>
- NEXT: <что требуется от пользователя, 1 строка>

Если GAP:
- CODE: <GAP.*>
- NOTE: <что missing, 1 строка>
- REQUIRED: <какой файл/сущность/контракт добавить, 1 строка>

PASS:
- OK: <шаг выполнен>
- NEXT: "го"

---

## [M] ANTI-NOISE LOAD POLICY (REPEAT)
ALWAYS:
- START
- RUNTIME_MANIFEST
- TASK_ROUTER
- NAV_ROOT

THEN:
- один REQUIRED_IDX
- 1–3 целевых файла по задаче

NEVER:
- обход IDX
- загрузка папок
- “на всякий случай” загрузка десятков документов

---

## [M] INTERFACES (RAW ONLY)
FAIL CODES:
https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/07__FAIL_CODES.md

STEP RUN:
https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/10__STEP_RUN_PROTOCOL.md

FOCUS LOOP:
https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/12__FOCUS_LOOP_PROTOCOL.md

END.
