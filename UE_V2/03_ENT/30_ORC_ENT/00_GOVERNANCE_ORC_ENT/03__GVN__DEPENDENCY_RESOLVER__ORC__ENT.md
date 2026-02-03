# 03__GVN__DEPENDENCY_RESOLVER__ORC__ENT

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: ORC_ENTITY (GOVERNANCE)
UID: UE.V2.ORC.GVN.DEPENDENCY_RESOLVER.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)

---

## [M] NAME
GVN Dependency Resolver Orchestrator

## [M] PURPOSE
Детерминированно собрать и проверить минимально-нужный набор зависимостей для выполнения задачи.
Оркестратор обеспечивает:
- нулевой обход IDX (никаких “прямых” ходов мимо NAV)
- анти-шум (не грузить деревья, только минимальный MUST_LOAD + один доменный IDX + 1–3 target файла)
- предсказуемый порядок загрузки (stable sort и фиксированные tie-break)
- понятный статус: PASS / GAP / STOP с конкретным списком недостающих RAW/маркерных блоков

---

## [M] POSITION IN RUNTIME
Вызывается после ROUTER и перед PIPE_EXEC.

**Ориентир:**
- ROUTER сформировал ROUTE_TOKEN (DOMAIN, REQUIRED_IDX, REQUIRED_CHECKS, PIPE_SELECTED, EXEC_MODE)
- NAV_ROOT открыт/доступен
- дальше — резолв зависимостей и подтверждение доступа к REG/XREF/KB/PIPE/LOG через IDX

---

## [M] TRIGGERS
Запускать оркестратор, когда:
- сформирован ROUTE_TOKEN
- требуется открыть REQUIRED_IDX и подтвердить доступ к системным панелям (REG/XREF/KB/PIPE/LOG)
- планируется STEP-RUN исполнение (пошагово через “го”)

---

## [M] INPUTS
Обязательные:
- ROUTE_TOKEN
- NAV_ROOT_STATUS (доступен / недоступен)
- MUST_LOAD_SET (минимальный набор из RUNTIME_MANIFEST)

Опциональные:
- MODE_HINT (FAST | RELEASE_READY | MASTERPIECE)
- constraints (platform, duration, style, references)

---

## [M] OUTPUTS
Обязательные:
- DEP_RESOLVE_REPORT:
  - LOAD_ORDER (строгий порядок)
  - REQUIRED_PANELS_STATUS (REG/XREF/KB/PIPE/LOG)
  - MISSING (если есть)
  - ACTION (PASS/GAP/STOP) + причина
- REQUIRED_LOAD_SET (финальный минимальный набор файлов для открытия “сейчас”)

Опциональные:
- DECISION_NOTE (короткая запись для DECISION_LOG)
- TOKEN_PATCH (если нужно нормализовать ROUTE_TOKEN полями по правилам детерминизма)

---

## [M] CORE RULES (DETERMINISM + ANTI-NOISE)
1) **NO TREE SCAN**: никаких массовых обходов папок. Только через NAV_ROOT и доменный IDX.
2) **STABLE ORDER**: сортировка по фиксированному ключу:
   - первично: класс ресурса (MUST_LOAD → NAV → IDX → PANELS → TARGET)
   - вторично: строковый путь/имя (лексикографически)
3) **MINIMAL LOAD**:
   - ALWAYS: START + MANIFEST + ROUTER + NAV_ROOT
   - THEN: REQUIRED_IDX (ровно один доменный IDX)
   - THEN: 1–3 target файла (если уже известны из TASK_TEXT/PIPE)
4) **NO BYPASS**: если ресурс не обнаружен через IDX → это GAP/STOP, а не “пойду найду сам”.
5) **CLEAR FAILURE**: всегда отдавать конкретный список, что именно отсутствует.

---

## [M] RESOLVE STEPS (ALGORITHM)
### D0) Preconditions
- Если нет ROUTE_TOKEN → STOP (input absent)
- Если NAV_ROOT недоступен → STOP
- Если MUST_LOAD_SET недоступен → STOP

### D1) Build Required Set
Собрать список:
- MUST_LOAD_SET (минимум)
- REQUIRED_IDX из ROUTE_TOKEN
- REQUIRED_CHECKS из ROUTE_TOKEN (панели/проверки)
- PIPE_DEFAULT + PIPE_SELECTED (если указан)

### D2) Confirm Access via NAV / IDX
- Открыть REQUIRED_IDX
- Через REQUIRED_IDX подтвердить доступ к:
  - REG
  - XREF
  - KB
  - PIPE
  - LOG
Если любая панель не подтверждается через IDX → GAP (панель missing)

### D3) Compute Minimal Load Order
Сформировать LOAD_ORDER:
1) MUST_LOAD_SET (как есть)
2) NAV_ROOT
3) REQUIRED_IDX
4) минимальные панельные файлы, строго необходимые для следующего шага:
   - PIPE_DEFAULT (для handoff)
   - LOG_RULES (для лог-инициализации, если следующий шаг — LOG_INIT)
5) 1–3 target файла (если ROUTE_TOKEN/PIPE уже вычислили конкретику)

### D4) Missing Detection
MISSING считается:
- RAW отсутствует
- маркерный блок/обязательная секция не подтверждена (если правило задано REQUIRED_CHECKS)

Результат:
- если missing ∈ MUST_LOAD → STOP
- если missing ∈ доменном IDX/PIPE/панелях → GAP
- иначе PASS

### D5) Emit Report
Сформировать DEP_RESOLVE_REPORT, пригодный для логов и для показа пользователю.
В PASS — вернуть REQUIRED_LOAD_SET и FIRST_STEP_PROMPT: “го”.

---

## [M] REQUIRED_CHECKS (DEFAULT)
Минимальный набор проверок по умолчанию:
- NAV_ROOT доступен
- REQUIRED_IDX доступен
- PIPE_DEFAULT доступен
- LOG_RULES доступен
- подтверждён доступ к REG/XREF/KB/PIPE/LOG через IDX

Примечание: доменные пайпы/индексы добавляются ROUTER-ом в REQUIRED_CHECKS.

---

## [M] FAIL / GAP BEHAVIOR
### STOP conditions
- input absent: нет ROUTE_TOKEN или MUST_LOAD_SET
- MUST_LOAD missing (RAW missing)
- NAV_ROOT missing

### GAP conditions
- REQUIRED_IDX отсутствует
- любая из панелей REG/XREF/KB/PIPE/LOG не подтверждается через IDX
- доменный PIPE отсутствует/не подтверждён

---

## [M] ERROR CODES (LOCAL)
- STOP.GVN.DEP.001 = ROUTE_TOKEN missing
- STOP.GVN.DEP.002 = NAV_ROOT missing
- STOP.GVN.DEP.003 = MUST_LOAD missing
- GAP.GVN.DEP.010 = REQUIRED_IDX missing
- GAP.GVN.DEP.020 = PANEL access not confirmed (REG/XREF/KB/PIPE/LOG)
- GAP.GVN.DEP.030 = PIPE selected missing
- PASS.GVN.DEP.900 = dependencies resolved

---

## [M] LOG HOOKS (WHAT TO WRITE)
Если LOG доступен:
- RUN_LOG: записать короткую строку “DEP_RESOLVE: PASS/GAP/STOP” + список missing
- DECISION_LOG: зафиксировать LOAD_ORDER и причину выбора (anti-noise)
- TOKEN_ARCHIVE: сохранить ROUTE_TOKEN (если есть нормализация — сохранить patch)

---

## [M] SECURITY / COMPLIANCE NOTES
- Не пытаться “угадывать” файлы вне IDX.
- Не подменять ROUTER.
- Не расширять REQUIRED_LOAD_SET без причины.
- При любом GAP отдавать список missing, не “решать молча”.

---

## [M] START OUTPUT CONTRACT
Если PASS:
- ROUTE_TOKEN (как есть или с TOKEN_PATCH)
- DEP_RESOLVE_REPORT
- FIRST_STEP_PROMPT: "го"
