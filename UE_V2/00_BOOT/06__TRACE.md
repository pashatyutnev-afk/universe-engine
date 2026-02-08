# 06__TRACE

SCOPE: UE_V2  
DOC_TYPE: BOOT_TRACE (RUNTIME TRACE)  
UID: UE.V2.BOOT.TRACE.001  
VERSION: 1.1.0  
STATUS: ACTIVE  
MODE: REPO (USAGE-ONLY, NO-EDIT)  
NAV_RULE: RAW only  
PURPOSE: Включает минимальную трассу исполнения рантайма без засорения контекста. Фиксирует: что открывали, почему, какие маркеры подтвердили, какие решения приняли, какой следующий шаг.

---

## [M] TRACE PRINCIPLES
- TRACE IS LIGHT: трасса короткая, только “критические точки”.
- OUTPUT-FIRST: контент/результат важнее справки.
- DETERMINISTIC: одинаковый вход → одинаковые решения/путь.
- NO TREE LOAD: нельзя массово грузить папки/индексы; только MUST_LOAD + IDX из ROUTE_TOKEN + 1–3 target файла.
- RAW ONLY: каждый “открытый” ресурс должен иметь RAW ссылку.

---

## [M] TRACE LEVELS
- TRACE_OFF: трасса выключена (запрещено для BOOT по START).
- TRACE_MIN: минимум (по умолчанию).
- TRACE_FULL: расширенная (только при MODE_HINT=MASTERPIECE или при QA/VAL расследовании).

По START_SEQUENCE активировать: TRACE_MIN.

---

## [M] TRACE EVENTS (CANON)
Трасса ведётся событиями. Каждое событие — 1 блок.

### E0: ENTRYPOINT
Фиксируем:
- TASK_PRESENT: yes/no
- TASK_HASH: короткий отпечаток (например первые 12 символов безопасного хеша)  
- MODE_HINT: FAST | RELEASE_READY | MASTERPIECE | none
- CONSTRAINTS_PRESENT: yes/no

---

### E1: BOOT_LOAD
Фиксируем:
- MUST_LOAD_OPENED: список PATH (не больше 12 строк)
- MUST_LOAD_MARKERS: marker ok / missing (по каждому MUST_LOAD)
- STOP/GAP: triggered? (код/нет)

---

### E2: ROUTING
Фиксируем:
- ROUTER_OPENED: PATH
- ROUTE_TOKEN: значения (см. формат ниже)
- DECISION: почему выбран DOMAIN/PIPE_SELECTED (1 строка)

---

### E3: NAV_CONFIRM
Фиксируем:
- NAV_ROOT_OPENED: PATH
- REQUIRED_IDX_OPENED: PATH
- ACCESS_CONFIRMED: REG/XREF/KB/PIPE/LOG (ok/missing)

---

### E4: PIPE_HANDOFF
Фиксируем:
- PIPE_DEFAULT_OPENED: PATH
- PIPE_SELECTED_OPENED: PATH (если доменный)
- STEP_RUN_PROTOCOL_ON: yes/no
- FOCUS_LOOP_PROTOCOL_ON: yes/no
- COMMANDS_ON: yes/no

---

### E5: LOG_INIT
Фиксируем:
- LOG_RULES_OPENED: PATH
- RUN_LOG_AVAILABLE: yes/no
- TOKEN_ARCHIVE_AVAILABLE: yes/no
- DECISION_LOG_AVAILABLE: yes/no

---

### E6: STEP_RESULT (per step)
Фиксируем на каждый STEP-RUN:
- STEP_ID: Sx
- OPENED_TARGETS: 1–3 PATH
- OUTPUT_SUMMARY: 1–3 строки (что выдали)
- NEXT_PROMPT: обычно “го”
- STATUS: PASS | GAP | STOP

---

## [M] ROUTE_TOKEN FORMAT (TRACE)
В трассе ROUTE_TOKEN пишется одним блоком:

ROUTE_TOKEN:
- DOMAIN:
- ARTIFACT_TYPE:
- MODE:
- PIPE_SELECTED:
- DEFAULT_ORC:
- REQUIRED_IDX:
- REQUIRED_CHECKS:
- EXEC_MODE:

Правило: если поле пустое — это риск STOP_05 (или GAP по ROUTER).

---

## [M] ANTI-NOISE RULES (TRACE)
Запрещено в TRACE:
- длинные объяснения, “почему так в философии”
- повторять содержимое открытых файлов
- писать “все файлы были проверены” без перечисления
- включать внешние ссылки кроме RAW

Разрешено:
- короткие списки PATH
- коды STOP/GAP/FAIL
- 1 строка rationales для routing decisions

---

## [M] TRACE OUTPUT TEMPLATE (MIN)
Использовать этот шаблон, когда трасса включена:

TRACE:
- LEVEL: TRACE_MIN
- E0_ENTRYPOINT: ...
- E1_BOOT_LOAD: ...
- E2_ROUTING: ...
- E3_NAV_CONFIRM: ...
- E4_PIPE_HANDOFF: ...
- E5_LOG_INIT: ...
- E6_STEP_RESULT: ...

---

## [M] FAIL / GAP IN TRACE
Если STOP:
- обязательно добавить:
  - FAIL_CODE
  - MISSING (PATH/marker)
  - NEXT (1 действие)

Если GAP:
- обязательно добавить:
  - GAP_CODE
  - AFFECTED
  - ALLOWED / BLOCKED
  - NEXT

---

## [M] DEFAULTS
- DEFAULT_TRACE_LEVEL: TRACE_MIN
- MAX_MUST_LOAD_LIST_LINES: 12
- MAX_OPENED_TARGETS_PER_STEP: 3
- MAX_OUTPUT_SUMMARY_LINES: 3
