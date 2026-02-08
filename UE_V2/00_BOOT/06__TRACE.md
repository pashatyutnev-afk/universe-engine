# 06__TRACE

SCOPE: UE_V2  
DOC_TYPE: BOOT_TRACE (RUNTIME TRACE POLICY)  
UID: UE.V2.BOOT.TRACE.001  
VERSION: 1.1.0  
STATUS: ACTIVE  
MODE: REPO (USAGE-ONLY, NO-EDIT)  
NAV_RULE: Use RAW links only  

PURPOSE:  
Включаем “тонкую трассу” рантайма, чтобы всегда было видно:
- на каком шаге BOOT мы находимся
- какие RAW открывали
- какой маркер подтвердили
- почему STOP или GAP
Без мусора и без длинных логов.

---

## [M] TRACE SWITCH
TRACE_MODE:
- OFF  = трасса выключена (только результат)
- ON   = печатаем TRACE_BLOCK на каждом шаге BOOT + при STOP/GAP
- AUTO = включается автоматически, если случился STOP или GAP

DEFAULT: AUTO

---

## [M] TRACE BLOCK (CANON FORMAT)
Если TRACE_MODE = ON или AUTO (и случился STOP/GAP), печатать блок:

TRACE:
- STAGE: <S0|S1|S2|S3|S4|S5|S6>
- ACTION: <OPEN|MARKER_CHECK|TOKEN_BUILD|IDX_CHECK|PIPE_ROUTE|LOG_INIT>
- RAW_OPENED: <raw_url_or_none>
- MARKER: <marker_name_or_none>
- MARKER_STATUS: <FOUND|MISSING|SKIP>
- RESULT: <OK|STOP|GAP>
- CODE: <FAIL_CODE|GAP_CODE|none>
- NOTE: <max 1 line>

HARD LIMIT:
- максимум 7 строк (как выше)
- NOTE строго 1 строка, без объяснялок

---

## [M] STAGES MAP
S0 ENTRYPOINT CHECK
- ACTION: MARKER_CHECK
- MARKER: TASK_TEXT_PRESENT

S1 BOOT SEQ
- ACTION: OPEN / MARKER_CHECK
- открываем BOOT_SEQ + STOP_GAP + FAIL_CODES

S2 MUST_LOAD ядро
- ACTION: OPEN / MARKER_CHECK
- открываем RUNTIME_MANIFEST и подтверждаем MUST_LOAD_SET

S3 ROUTING
- ACTION: OPEN / TOKEN_BUILD
- открываем TASK_ROUTER и собираем ROUTE_TOKEN

S4 NAV
- ACTION: OPEN / IDX_CHECK
- открываем NAV_ROOT + REQUIRED_IDX (из ROUTE_TOKEN)
- подтверждаем доступ к REG/XREF/KB/PIPE/LOG через IDX

S5 PIPE EXEC (STEP-RUN)
- ACTION: OPEN / PIPE_ROUTE
- открываем PIPE_DEFAULT и делаем handoff в доменный пайп (если выбран)

S6 LOG INIT
- ACTION: OPEN / MARKER_CHECK
- открываем LOG_RULES и подтверждаем доступ к RUN_LOG/TOKEN_ARCHIVE/DECISION_LOG

---

## [M] TRACE + STOP/GAP RULE
Если результат шага STOP:
- RESULT: STOP
- CODE: соответствующий STOP.* из FAIL_CODES
- NOTE: 1 строка (что отсутствует)

Если результат шага GAP:
- RESULT: GAP
- CODE: соответствующий GAP.* из STOP_GAP
- NOTE: 1 строка (что надо добавить/починить)

Запрещено:
- “предположения”
- “обходы”
- “длинные диагнозы”
TRACE = только факты.

---

## [M] LAST_OPENED_RAW RULE
Сохранять LAST_OPENED_RAW на каждом OPEN.
При STOP/GAP обязательно выводить RAW_OPENED = LAST_OPENED_RAW (если не none).

---

## [M] NOISE CONTROL
TRACE не должен:
- печатать содержимое файлов
- печатать списки деревьев
- печатать больше 1 IDX, кроме REQUIRED_IDX

---

## [M] OUTPUT INTEGRATION
BOOT (START) обязан печатать:
- ROUTE_TOKEN (после S3)
- FIRST_STEP_PROMPT: "го"
TRACE при этом печатается только если TRACE_MODE=ON или AUTO и был STOP/GAP.

---

## [M] INTERFACES (RAW ONLY)
STOP/GAP POLICY:
https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/02__STOP_GAP.md

FAIL CODES:
https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/07__FAIL_CODES.md

BOOT SEQ:
https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/01__BOOT_SEQ.md

END.
