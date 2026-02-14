# 02__STOP_GAP
KIND: ENGINE
ROLE: BOOT_GUARD
SCOPE: SYSTEM
STATUS: CANON
VERSION: 1.0.0

## [M] PURPOSE
STOP_GAP — протокол немедленной остановки.
Срабатывает, когда система не может гарантировать корректность/качество из-за:
- отсутствия обязательных входов/модулей/токенов
- провала обязательных гейтов (mandatory validators)
- нарушения scope (подключили лишнее / обошли правила)

STOP_GAP предотвращает “мусорные финалы” и принудительно возвращает систему в управляемый режим.

---

## [M] HARD_RULES
1) NO-SILENT-SKIP
- Нельзя “пропустить” required роль/движок/гейт ради скорости.

2) NO-FINAL-ON-FAIL
- Если любой mandatory gate FAIL → запрещено выдавать результат как “финал/готово”.
- Разрешено выдавать только:
  - FAIL_CODE
  - что отсутствует/сломано
  - минимальный FIX_LIST
  - (опционально) частичный черновик с явной меткой DRAFT

3) MINIMAL NEXT ACTION
- В ответе при STOP_GAP указывается только 1 минимальное действие, которое нужно сделать дальше.

4) DETERMINISM
- STOP_GAP должен всегда выдавать одинаковый FAIL_CODE при одинаковой причине.

---

## [M] TRIGGERS (WHEN TO STOP)
STOP_GAP обязателен при любом из:

### A) Missing Inputs
- TASK_TEXT отсутствует
- ROUTE_TOKEN отсутствует

=> FAIL: INPUT_ABSENT

### B) Missing Entry Points / Keys
- KEY из REQUIRED_SET не резолвится в PATH (IDX/PIPE/ENG/VAL/KB)
=> FAIL: ENTRYPOINT_MISSING

### C) Missing Files
- PATH указан, но файла нет / недоступен
=> FAIL: FILE_NOT_FOUND

### D) Marker / Contract Missing
- отсутствует обязательное поле/токен:
  - REQUIRED_ROLES
  - OUTPUT_CONTRACT
  - ENGINE_PLAN_TOKEN.required_eng_keys (как поле)
  - ENGINE_RUN_LEDGER
  - OUTPUT_LEDGER
=> FAIL: MARKER_NOT_CONFIRMED

### E) Scope Violations
- запущен engine вне allowed list
- запущен engine из no-go list
- PIPE/ORC подключили модули не из REQUIRED_SET
=> FAIL: SCOPE_VIOLATION

### F) Mandatory Validation Failed
- mandatory валидатор FAIL, например:
  - VAL_ENG.COVERAGE_AND_OUTPUT_CONTRACT
  - VAL_ENG.ERROR_DETECTION
=> FAIL: <propagate validator FAIL_CODE> (обычно MARKER_NOT_CONFIRMED / ENTRYPOINT_MISSING / SCOPE_VIOLATION)

### G) Web insufficient (если web был разрешён)
=> FAIL: WEB_INSUFFICIENT

---

## [M] STOP_GAP OUTPUT (MANDATORY FORMAT)
When STOP_GAP triggers, output MUST contain:
1) MODE
2) RESOURCES USED (что реально использовано)
3) DELIVERABLES:
   - STATUS: STOP_GAP
   - FAIL_CODE: <...>
   - MISSING: [<item1>, <item2>...]
   - FIX_LIST: [<minimal steps>]
   - SAFE_PARTIALS (optional): [DRAFT artifacts if they help]
4) GATES:
   - FAIL

---

## [M] SPECIAL RULE — PRODUCTION LOCK
For production tasks (content factory):
- If VAL_REPORT=FAIL → STOP_GAP is mandatory
- PACK_OUTPUT may be produced ONLY as DRAFT (no “final” label)

---

## [M] EXAMPLES (short)
Example 1:
- Missing ENGINE_RUN_LEDGER
=> FAIL: MARKER_NOT_CONFIRMED
=> FIX_LIST: ["ORC must generate ENGINE_RUN_LEDGER for required_eng_keys"]

Example 2:
- required_eng_key not resolvable
=> FAIL: ENTRYPOINT_MISSING
=> FIX_LIST: ["Add eng_key mapping to 00__INDEX_MANIFEST__ENG__ENT"]

END.
