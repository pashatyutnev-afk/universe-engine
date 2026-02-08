# 01__BOOT_SEQ

SCOPE: UE_V2  
DOC_TYPE: BOOT_SEQ  
UID: UE.V2.BOOT.SEQ.001  
VERSION: 1.1.0  
STATUS: ACTIVE  
MODE: REPO (USAGE-ONLY, NO-EDIT)  
NAV_RULE: RAW only  
PURPOSE: Каноническая последовательность запуска рантайма. Гарантирует, что первым включается “главный спец” (SPC_PRIME), затем ROUTER, затем NAV/IDX и только потом PIPE.

---

## [M] PRINCIPLES
- FIRST-SPECIALIST: перед любым ORC/PIPE должен включиться SPC_PRIME (главный спец входа).
- ROUTER-DRIVEN: домен, пайп, обязательные индексы и проверки выбираются только ROUTER-ом.
- ANTI-NOISE: грузим минимум (START + MANIFEST + ROUTER + NAV_ROOT), затем 1 доменный IDX + 1–3 целевых файла.
- STEP-RUN: работа только пошагово через команду “го”.
- NO-BYPASS: запрещён обход IDX, запрещена массовая загрузка деревьев.

---

## [M] INPUTS
- TASK_TEXT (обязателен): что нужно сделать
- OPTIONAL: MODE_HINT (FAST | RELEASE_READY | MASTERPIECE)
- OPTIONAL: constraints (platform, duration, style, references)

---

## [M] OUTPUTS
- START_TOKEN:
  - ROUTE_TOKEN (обязателен)
  - FIRST_STEP_PROMPT: "го"
- TRACE ON
- FAIL CODES ON

---

## [M] BOOT SEQUENCE (CANON)

### S0) ENTRYPOINT CHECK
PASS если:
- TASK_TEXT присутствует и не пустой

STOP если:
- TASK_TEXT отсутствует

---

### S1) BOOT CORE ON
Цель: включить минимальные системные предохранители и трассу.

MUST:
- STOP_GAP rules applied
- TRACE enabled
- FAIL_CODES enabled

Результат:
- система готова к детерминированному роутингу
- контекст не засоряется

---

### S2) MUST_LOAD MINIMUM (RUNTIME MANIFEST)
Открыть RUNTIME_MANIFEST и взять только MUST_LOAD_SET (минимум), без “всего подряд”.

MUST_LOAD_SET обязан включать как минимум:
- START (ENTRYPOINT)
- BOOT_SEQ (этот файл)
- STOP_GAP
- TRACE
- FAIL_CODES
- TASK_ROUTER
- NAV_ROOT
- PIPE_DEFAULT
- STEP_RUN_PROTOCOL
- FOCUS_LOOP_PROTOCOL
- COMMANDS

STOP если:
- любой MUST_LOAD отсутствует по RAW
- marker не подтверждён внутри MUST_LOAD

---

### S3) SPC_PRIME HANDSHAKE (FIRST-SPECIALIST)
Цель: “главный спец” принимает задачу раньше оркестраторов и пайпов.

Правило:
- SPC_PRIME не исполняет доменную работу.
- SPC_PRIME делает только:
  1) проверку MIN_INPUTS,
  2) нормализацию TASK_TEXT,
  3) формирование PRE_ROUTE_HINT (если нужно),
  4) передачу в ROUTER.

SPC_PRIME выбирается детерминированно:
- либо из RUNTIME_MANIFEST (DEFAULT_SPC_PRIME),
- либо из NAV/IDX (REG index), без угадывания.

GAP если:
- SPC_PRIME не найден в доступных IDX/manifest

---

### S4) ROUTING (TASK_ROUTER)
ROUTER обязан сформировать ROUTE_TOKEN:

ROUTE_TOKEN fields (обязательные):
- DOMAIN
- ARTIFACT_TYPE
- MODE
- PIPE_SELECTED
- DEFAULT_ORC
- DEFAULT_SPC (если домен требует спеца до ORC)
- REQUIRED_IDX
- REQUIRED_CHECKS
- EXEC_MODE

ROUTER запрещено:
- выбирать пайп без указания REQUIRED_IDX
- пропускать REQUIRED_CHECKS
- включать “массовую загрузку” (anti-noise)

---

### S5) NAV + IDX CONFIRMATION
Цель: подтвердить доступ к REG/XREF/KB/PIPE/LOG строго через индексы.

Шаги:
1) открыть NAV_ROOT
2) открыть REQUIRED_IDX из ROUTE_TOKEN
3) подтвердить, что через IDX доступны:
   - REG
   - XREF
   - KB
   - PIPE
   - LOG

STOP если:
- NAV_ROOT missing по RAW
- REQUIRED_IDX missing по RAW
GAP если:
- IDX открыт, но не даёт доступа к одному из обязательных сегментов (REG/XREF/KB/PIPE/LOG)

---

### S6) PIPE EXEC (STEP-RUN)
1) открыть PIPE_DEFAULT
2) если ROUTE_TOKEN.PIPE_SELECTED доменный — выполнить handoff через PIPE_DEFAULT routing
3) включить протоколы:
   - STEP_RUN_PROTOCOL
   - FOCUS_LOOP_PROTOCOL
   - COMMANDS

Правило STEP-RUN:
- система отвечает коротко, выдаёт результат шага и снова предлагает “го”
- без длинных справок и без загрузки лишнего

---

### S7) LOG INIT
Цель: включить журналирование решений и токенов.

MUST:
- LOG_RULES доступны
- RUN_LOG доступен
- TOKEN_ARCHIVE доступен
- DECISION_LOG доступен

GAP если:
- LOG сегмент недоступен через IDX

---

## [M] STOP / GAP RULES (SUMMARY)
STOP только если:
- input absent (нет TASK_TEXT)
- RAW missing для MUST_LOAD
- marker not confirmed для MUST_LOAD

GAP если:
- SPC_PRIME не найден
- отсутствует доменный PIPE/IDX/обязательная сущность/панель по ROUTE_TOKEN
- IDX не подтверждает доступ к REG/XREF/KB/PIPE/LOG

---

## [M] FIRST STEP PROMPT
Если S0–S7 PASS:
- вывести ROUTE_TOKEN
- вывести: "го"
