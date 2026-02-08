# 07__FAIL_CODES

SCOPE: UE_V2  
DOC_TYPE: FAIL_CODES (STOP / GAP CODEBOOK)  
UID: UE.V2.BOOT.FAILCODES.001  
VERSION: 1.1.0  
STATUS: ACTIVE  
MODE: REPO (USAGE-ONLY, NO-EDIT)  
NAV_RULE: Use RAW links only  

PURPOSE:  
Единый справочник кодов ошибок для BOOT/PIPE рантайма.
- STOP = нельзя продолжать (нет входа / нет MUST_LOAD / нет RAW / маркер не подтверждён)
- GAP  = можно продолжать после того, как добавят/починят отсутствующий обязательный элемент

RULE: коды короткие, детерминированные, без “лирики”.

---

## [M] CODE FORMAT
- STOP.<AREA>.<REASON>
- GAP.<AREA>.<MISSING>

AREA:
- ENTRY
- RAW
- BOOT
- MANIFEST
- ROUTER
- NAV
- IDX
- PIPE
- LOG
- ENT   (сущности/роли/орки/спц)
- KB

REASON / MISSING:
- NO_TASK_TEXT
- RAW_MISSING
- MARKER_MISSING
- MUST_LOAD_MISSING
- ROUTE_TOKEN_MISSING
- REQUIRED_IDX_MISSING
- PIPE_DEFAULT_MISSING
- LOG_SET_MISSING
- ENT_REQUIRED_MISSING
- KB_REQUIRED_MISSING
- CONTRACT_MISSING

---

## [M] STOP CODES (HARD STOP)

### ENTRY
- STOP.ENTRY.NO_TASK_TEXT  
TRIGGER: отсутствует TASK_TEXT на S0.  
ACTION: запросить TASK_TEXT (или вернуть "input absent").  

### RAW
- STOP.RAW.RAW_MISSING  
TRIGGER: обязательный RAW недоступен/404/нет ссылки.  
ACTION: останов, требовать RAW.

### BOOT
- STOP.BOOT.MARKER_MISSING  
TRIGGER: маркер [M] не найден в MUST_LOAD документе, который обязателен на этом шаге.  
ACTION: останов, требовать исправления маркера.

### MANIFEST
- STOP.MANIFEST.MUST_LOAD_MISSING  
TRIGGER: не подтверждён MUST_LOAD_SET или отсутствует манифест.  
ACTION: останов, починить RUNTIME_MANIFEST.

### ROUTER
- STOP.ROUTER.ROUTE_TOKEN_MISSING  
TRIGGER: ROUTE_TOKEN не собран (не удалось определить DOMAIN/ARTIFACT_TYPE/PIPE).  
ACTION: останов, починить TASK_ROUTER правила/маркеры.

### NAV / IDX
- STOP.NAV.NAV_ROOT_MISSING  
TRIGGER: NAV_ROOT недоступен.  
ACTION: останов, требовать NAV_ROOT RAW.

- STOP.IDX.REQUIRED_IDX_MISSING  
TRIGGER: REQUIRED_IDX из ROUTE_TOKEN не найден/не открывается.  
ACTION: останов, требовать индекс.

### PIPE
- STOP.PIPE.PIPE_DEFAULT_MISSING  
TRIGGER: PIPE_DEFAULT недоступен.  
ACTION: останов, требовать PIPE_DEFAULT.

### LOG
- STOP.LOG.LOG_SET_MISSING  
TRIGGER: LOG_RULES или обязательные логи недоступны.  
ACTION: останов, требовать LOG_RULES + пути.

---

## [M] GAP CODES (FIXABLE GAP)

### ENT (сущности/роли/оркестрация)
- GAP.ENT.ENT_REQUIRED_MISSING  
TRIGGER: по ROUTE_TOKEN требуется сущность (SPC/ORC/CTL/VAL/QA/XREF), но:
- нет файла сущности, или
- нет обязательного маркера роли, или
- нет привязки через IDX/REG.  
ACTION: добавить/починить сущность и её регистрацию (REG/IDX).

### KB
- GAP.KB.KB_REQUIRED_MISSING  
TRIGGER: требуется доменный KB/пример/гейт/рубрика, но отсутствует или не связан.  
ACTION: добавить KB элемент + связать через XREF/IDX.

### PIPE (доменный)
- GAP.PIPE.CONTRACT_MISSING  
TRIGGER: доменный PIPE выбран, но нет PIPELINE_CONTRACT/INDEX_MANIFEST в домене.  
ACTION: добавить контракт/манифест домена.

- GAP.PIPE.DOMAIN_PIPE_MISSING  
TRIGGER: ROUTE_TOKEN.PIPE_SELECTED указывает доменный пайп, но файла нет.  
ACTION: создать доменный PIPE или откатиться на PIPE_DEFAULT (только если разрешено TASK_ROUTER).

### IDX
- GAP.IDX.REQUIRED_CHECKS_MISSING  
TRIGGER: REQUIRED_CHECKS в ROUTE_TOKEN не подтверждены (нет файлов правил/чеков).  
ACTION: добавить missing checks или снять требование в ROUTER.

### LOG
- GAP.LOG.ARCHIVE_MISSING  
TRIGGER: TOKEN_ARCHIVE/DECISION_LOG отсутствуют.  
ACTION: добавить файлы логов и правила.

---

## [M] MAPPING TO BOOT STAGES

S0:
- STOP.ENTRY.NO_TASK_TEXT

S1:
- STOP.RAW.RAW_MISSING
- STOP.BOOT.MARKER_MISSING

S2:
- STOP.MANIFEST.MUST_LOAD_MISSING

S3:
- STOP.ROUTER.ROUTE_TOKEN_MISSING
- GAP.ENT.ENT_REQUIRED_MISSING (если ROUTER требует сущность для дефолтного хэнд-оффа)

S4:
- STOP.NAV.NAV_ROOT_MISSING
- STOP.IDX.REQUIRED_IDX_MISSING
- GAP.KB.KB_REQUIRED_MISSING
- GAP.IDX.REQUIRED_CHECKS_MISSING

S5:
- STOP.PIPE.PIPE_DEFAULT_MISSING
- GAP.PIPE.DOMAIN_PIPE_MISSING
- GAP.PIPE.CONTRACT_MISSING

S6:
- STOP.LOG.LOG_SET_MISSING
- GAP.LOG.ARCHIVE_MISSING

---

## [M] OUTPUT RULE (HOW TO REPORT)
При любом STOP/GAP:
- печатать CODE (один)
- печатать NOTE (одна строка: что конкретно missing)
- не печатать “как я думаю”, только факт

---

## [M] INTERFACES (RAW ONLY)
STOP/GAP POLICY:
https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/02__STOP_GAP.md

TRACE POLICY:
https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/06__TRACE.md

END.
