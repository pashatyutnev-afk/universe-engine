# 08__RUNTIME_MANIFEST

SCOPE: UE_V2  
DOC_TYPE: BOOT / RUNTIME_MANIFEST  
VERSION: 1.2.0  
STATUS: ACTIVE  
MODE: REPO (USAGE-ONLY, NO-EDIT)  
NAV_RULE: Use RAW links only  
PURPOSE: Минимальный манифест MUST_LOAD. Поднимает “ядро” и гарантирует доступ к NAV/PIPE/LOG без массовой загрузки.

---

## [M] MUST_LOAD_SET (MIN)

### A) BOOT ядро (обязательно)
- UE_V2/00_BOOT/01__BOOT_SEQ.md
- UE_V2/00_BOOT/02__STOP_GAP.md
- UE_V2/00_BOOT/06__TRACE.md
- UE_V2/00_BOOT/07__FAIL_CODES.md
- UE_V2/00_BOOT/08__RUNTIME_MANIFEST.md
- UE_V2/00_BOOT/09__TASK_ROUTER.md
- UE_V2/00_BOOT/10__STEP_RUN_PROTOCOL.md
- UE_V2/00_BOOT/12__FOCUS_LOOP_PROTOCOL.md
- UE_V2/00_BOOT/13__COMMANDS.md

### B) NAV ядро (обязательно)
- UE_V2/04_NAV/00__NAV_ROOT.md

### C) PIPE ядро (обязательно)
- UE_V2/06_PIPE/00__INDEX_MANIFEST__PIPE.md
- UE_V2/06_PIPE/00__PIPELINE_CONTRACT__PIPE.md
- UE_V2/06_PIPE/01__PIPE_DEFAULT.md

### D) LOG ядро (обязательно)
- UE_V2/14_LOG/00__INDEX_MANIFEST__LOG.md
- UE_V2/14_LOG/00__PIPELINE_CONTRACT__LOG.md
- UE_V2/14_LOG/01__RUN_LOG.md
- UE_V2/14_LOG/03__TOKEN_ARCHIVE.md
- UE_V2/14_LOG/04__DECISION_LOG.md
- UE_V2/14_LOG/05__START_POINT_LOG.md

---

## [M] LOAD_RULES
- Загружаем строго MUST_LOAD_SET и ничего лишнего.
- Любые доменные сущности/пайпы подключаются ТОЛЬКО после ROUTE_TOKEN и через NAV IDX.
- Если любой файл из MUST_LOAD_SET недоступен по RAW → STOP.

---

## [M] MARKERS (REQUIRED)
Каждый MUST_LOAD файл обязан содержать:
- SCOPE
- DOC_TYPE
- VERSION
- STATUS
- NAV_RULE

Если marker not confirmed → STOP.

---

## [M] OUTPUT CONTRACT (для BOOT)
BOOT должен вернуть:
- ROUTE_TOKEN (из TASK_ROUTER)
- FIRST_STEP_PROMPT: "го"
