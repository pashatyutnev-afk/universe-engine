# 02__STOP_GAP

SCOPE: UE_V2  
DOC_TYPE: BOOT_GUARD (STOP/GAP POLICY)  
UID: UE.V2.BOOT.GUARD.STOPGAP.001  
VERSION: 1.1.0  
STATUS: ACTIVE  
MODE: REPO (USAGE-ONLY, NO-EDIT)  
NAV_RULE: Use RAW links only  

PURPOSE:  
Единая политика, которая объясняет, когда рантайм обязан остановиться (STOP),  
а когда должен продолжить в режиме “пробел” (GAP) и запросить недостающие сущности/индексы/пайпы.  
Главная цель: не “молчать”, не “обходить”, не “пропускать” REG/XREF/KB/PIPE/NAV/LOG.

---

## [M] DEFINITIONS
STOP = немедленная остановка, без “го”, потому что продолжение даст неверный рантайм.  
GAP  = продолжение возможно, но требуется один или несколько обязательных элементов;  
       рантайм фиксирует что отсутствует и формирует запрос/маркер на добавление.

---

## [M] HARD LAW (NON-NEGOTIABLE)
L1) RAW-ONLY ACCESS  
- если файл должен быть открыт, но RAW ссылка недоступна → это missing.

L2) MUST_LOAD IS STOP  
- любые missing в MUST_LOAD_SET = STOP.

L3) MARKER NOT CONFIRMED (MUST_LOAD) = STOP  
- если MUST_LOAD файл открылся, но в нём нет маркера/секции, которую требует BOOT → STOP.

L4) DOMAIN INFRA MISSING = GAP  
- доменные IDX/PIPE/сущности/панели — это GAP, если они не входят в MUST_LOAD.

L5) NO SILENT BYPASS  
- нельзя “перепрыгнуть” отсутствующий IDX/PIPE/сущность и продолжить как будто всё ок.

---

## [M] INPUT ABSENCE RULE
Если нет TASK_TEXT → STOP (ENTRYPOINT invalid).

---

## [M] MUST_LOAD (BOOT MINSET)
MUST_LOAD_SET для запуска UE_V2 (минимальный, канонический):
- UE_V2/00_BOOT/01__BOOT_SEQ.md
- UE_V2/00_BOOT/02__STOP_GAP.md
- UE_V2/00_BOOT/06__TRACE.md
- UE_V2/00_BOOT/07__FAIL_CODES.md
- UE_V2/00_BOOT/08__RUNTIME_MANIFEST.md
- UE_V2/00_BOOT/09__TASK_ROUTER.md
- UE_V2/04_NAV/00__NAV_ROOT.md
- UE_V2/06_PIPE/01__PIPE_DEFAULT.md
- UE_V2/00_BOOT/10__STEP_RUN_PROTOCOL.md
- UE_V2/00_BOOT/12__FOCUS_LOOP_PROTOCOL.md
- UE_V2/00_BOOT/13__COMMANDS.md

NOTE:
- Логи и доменные панели по умолчанию GAP (если отдельно не объявлены MUST_LOAD в манифесте).

---

## [M] STOP MATRIX (WHEN TO HALT)
STOP, если выполняется хотя бы одно:

S0) INPUT ABSENT
- TASK_TEXT отсутствует / пустой

S1) MUST_LOAD RAW MISSING
- любой файл из MUST_LOAD_SET не открывается по RAW

S2) MUST_LOAD MARKER NOT CONFIRMED
- файл открылся, но требуемый маркер/секция отсутствует
  пример: ROUTER не содержит выдачу ROUTE_TOKEN

S3) NAV RULE BROKEN
- попытка перейти не по RAW (обход правила)

S4) ROUTER LAW BROKEN
- выбор домена/пайпа/оркестратора сделан “руками”, без ROUTE_TOKEN

S5) STEP-RUN LAW BROKEN
- переход шагов без команды “го” (в режиме STEP_RUN)

---

## [M] GAP MATRIX (WHEN TO CONTINUE WITH A GAP)
GAP, если отсутствует, но не является MUST_LOAD:

G1) DOMAIN PIPE MISSING
- ROUTE_TOKEN.PIPE_SELECTED указывает на доменный пайп, но RAW недоступен

G2) REQUIRED IDX MISSING
- ROUTE_TOKEN.REQUIRED_IDX отсутствует или не открывается по RAW

G3) GOVERNANCE SPC ENTITY NOT RESOLVED
- система должна начать со SPC-FIRST (governance SPC), но сущность не найдена через ENT IDX/manifest

G4) REG/XREF/KB/PIPE/LOG REACHABILITY NOT CONFIRMED
- NAV_ROOT открыт, но через REQUIRED_IDX нельзя подтвердить доступ к нужным панелям

G5) OPTIONAL TARGET FILES MISSING
- 1–3 “target” файла, которые ROUTER попросил для задачи, отсутствуют

G6) CHECKS PANEL MISSING
- ROUTE_TOKEN.REQUIRED_CHECKS указаны, но соответствующие файлы не доступны

---

## [M] GAP OUTPUT FORMAT (WHAT TO PRINT)
Если GAP:
- печатаем коротко:
  - GAP_CODE
  - MISSING_ITEMS (PATH + RAW if known)
  - HOW_TO_FIX (1 строка)
  - FIRST_STEP_PROMPT: го

Запрещено:
- длинные объяснения
- загрузка дерева “вдруг поможет”

---

## [M] TRACE INTEGRATION
Если TRACE=ON:
- при STOP или GAP печатаем:
  - FAIL_CODE или GAP_CODE
  - STAGE (S0..S9)
  - LAST_OPENED_RAW (если был)

Если TRACE=OFF:
- печатаем только:
  - STOP/GAP + код + 1 строка причины

---

## [M] CODES (MIN SET)
STOP codes:
- STOP.INPUT.ABSENT
- STOP.MUSTLOAD.MISSING
- STOP.MARKER.MISSING
- STOP.NAV.RULE
- STOP.ROUTER.LAW
- STOP.STEPRUN.LAW

GAP codes:
- GAP.PIPE.MISSING
- GAP.IDX.MISSING
- GAP.SPC.NOT_RESOLVED
- GAP.REACHABILITY.NOT_CONFIRMED
- GAP.TARGET.MISSING
- GAP.CHECKS.MISSING

---

## [M] INTERFACES (RAW ONLY)
BOOT SEQ:
https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/01__BOOT_SEQ.md

TRACE:
https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/06__TRACE.md

FAIL CODES:
https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/07__FAIL_CODES.md

RUNTIME MANIFEST:
https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/08__RUNTIME_MANIFEST.md

TASK ROUTER:
https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/09__TASK_ROUTER.md

NAV ROOT:
https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/04_NAV/00__NAV_ROOT.md

PIPE DEFAULT:
https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/06_PIPE/01__PIPE_DEFAULT.md

STEP RUN PROTOCOL:
https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/10__STEP_RUN_PROTOCOL.md

FOCUS LOOP:
https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/12__FOCUS_LOOP_PROTOCOL.md

COMMANDS:
https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/13__COMMANDS.md

END.
