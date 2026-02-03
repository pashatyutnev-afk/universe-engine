# 04__GVN__CHANGE_CONTROL__ORC__ENT

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: ORC_ENTITY (GOVERNANCE)
UID: UE.V2.ORC.GVN.CHANGE_CONTROL.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)

---

## [M] NAME
GVN Change Control Orchestrator

## [M] PURPOSE
Контролировать изменения в рантайме UE_V2 так, чтобы:
- любое изменение (ROUTE_TOKEN, PIPE, TARGET, constraints, outputs) фиксировалось и было объяснимым
- изменения не ломали детерминизм и анти-шум политику
- изменения не делались “молча” (всегда есть запись и причина)
- шаговый режим (“го”) оставался воспроизводимым

---

## [M] POSITION IN RUNTIME
Работает как “прослойка”:
- между шагами STEP-RUN
- между FOCUS-LOOP итерациями
- перед handoff в доменный PIPE (если меняется пайп/маршрут/цели)

Вызывается:
- после ROUTER (при формировании ROUTE_TOKEN)
- после DEPENDENCY_RESOLVER (если появился TOKEN_PATCH / LOAD_SET)
- перед PIPE_EXEC на каждом шаге, если входные/контекстные условия изменились

---

## [M] TRIGGERS
Запускать, когда обнаружено одно из:
- изменился TASK_TEXT (или его интерпретация)
- изменился MODE_HINT / constraints
- изменился ROUTE_TOKEN (DOMAIN/PIPE/IDX/CHECKS/EXEC_MODE)
- добавились/убрались target файлы (1–3 targets)
- требуется “перепрыгнуть” шаг или изменить порядок загрузки
- возник конфликт: анти-шум vs. требования задачи

---

## [M] INPUTS
Обязательные:
- ROUTE_TOKEN (current)
- STEP_STATE:
  - step_id
  - last_action (PASS/GAP/STOP)
  - last_outputs (summary)
- CHANGE_REQUEST (что меняем и зачем)

Опциональные:
- PREV_ROUTE_TOKEN (если есть)
- LOAD_ORDER / REQUIRED_LOAD_SET (если уже рассчитано)
- MODE_HINT (FAST | RELEASE_READY | MASTERPIECE)

---

## [M] OUTPUTS
Обязательные:
- CHANGE_DECISION:
  - decision: APPROVE | REJECT | DEFER
  - change_set: список атомарных изменений (field-level)
  - rationale: 1–3 строки (почему)
  - risk_notes: что может сломаться
  - required_rechecks: что надо перепроверить (IDX/панели/пайп)
- TOKEN_PATCH (если approve)
- LOG_INSTRUCTIONS (что записать в RUN_LOG / DECISION_LOG / TOKEN_ARCHIVE)

---

## [M] CHANGE TYPES (ATOMICS)
Все изменения должны быть выражены атомарно:
- TOKEN.FIELD_UPDATE (например ROUTE_TOKEN.PIPE_SELECTED)
- LOADSET.ADD / LOADSET.REMOVE (строго 1–3 target максимум)
- ORDER.SWAP / ORDER.APPEND (только по правилам anti-noise)
- CONSTRAINTS.UPDATE (platform/duration/style/references)
- STEP.MODE_SWITCH (FAST ↔ RELEASE_READY ↔ MASTERPIECE) — только с причиной

---

## [M] CORE RULES (NO SURPRISES)
1) **NO SILENT CHANGE**: любое approve = запись в логи.
2) **FIELD-LEVEL PATCH**: нельзя “пересобрать всё”, только минимальный патч.
3) **DETERMINISM FIRST**: при равных вариантах — выбираем тот, что следует правилам ROUTER/NAV/ANTI_NOISE.
4) **ANTI-NOISE ALWAYS ON**:
   - нельзя добавлять массовые загрузки “на всякий случай”
   - target файлы максимум 1–3 за итерацию
5) **RECHECK POLICY**:
   - если изменили REQUIRED_IDX / DOMAIN / PIPE_SELECTED → обязателен повтор DEPENDENCY_RESOLVER
   - если изменили только constraints текста (style/duration) без смены домена → DEP может быть пропущен (если REQUIRED_CHECKS не затронуты)

---

## [M] APPROVAL MATRIX
### APPROVE если:
- изменение минимально и объяснимо
- не нарушает NAV_RULE (только через IDX)
- не нарушает anti-noise
- не противоречит MUST_LOAD

### REJECT если:
- изменение требует обхода IDX / “дай я сам найду”
- изменение размывает маршрут (несколько доменов одновременно)
- изменение тянет массовую загрузку деревьев
- изменение ломает step-run (невозможно воспроизвести)

### DEFER если:
- не хватает входа (CHANGE_REQUEST туманный)
- требуется доменный IDX/PIPE, которого нет → сначала GAP resolution

---

## [M] PROCESS (ALGORITHM)
### C0) Preconditions
- Если нет CHANGE_REQUEST → DEFER (input absent)
- Если нет ROUTE_TOKEN → STOP (нельзя менять то, чего нет)

### C1) Diff Build
Собрать diff:
- PREV_ROUTE_TOKEN vs ROUTE_TOKEN (если prev есть)
- Запрошенные изменения vs разрешённые атомики

### C2) Validate Against Policies
Проверить:
- NAV_RULE ok (все ссылки/ресурсы только через IDX)
- ANTI_NOISE ok (не расширяем загрузку сверх лимитов)
- STEP_RUN ok (есть понятный следующий шаг)
- REQUIRED_CHECKS impact (нужно ли ре-резолвить зависимости)

### C3) Decide
- APPROVE → сформировать TOKEN_PATCH + required_rechecks
- REJECT → дать минимальную альтернативу (какой change_set нужен вместо)
- DEFER → перечислить, чего не хватает (1 строка, без шума)

### C4) Emit Logs
Сформировать LOG_INSTRUCTIONS:
- TOKEN_ARCHIVE: сохранить новый ROUTE_TOKEN (и patch)
- DECISION_LOG: decision + rationale + risk_notes
- RUN_LOG: короткая строка “CHANGE_CONTROL: APPROVE/REJECT/DEFER”

---

## [M] REQUIRED_RECHECKS (DEFAULT)
- Если изменили DOMAIN / PIPE_SELECTED / REQUIRED_IDX → вызвать GVN_DEPENDENCY_RESOLVER снова
- Если изменили REQUIRED_CHECKS → вызвать NAV подтверждения панелей снова
- Если изменили только текстовые constraints → recheck не обязателен

---

## [M] ERROR CODES (LOCAL)
- STOP.GVN.CHG.001 = ROUTE_TOKEN missing
- DEFER.GVN.CHG.010 = CHANGE_REQUEST missing
- REJECT.GVN.CHG.020 = violates NAV_RULE (IDX bypass)
- REJECT.GVN.CHG.021 = violates ANTI_NOISE (tree load / too many targets)
- REJECT.GVN.CHG.022 = violates DETERMINISM (multi-domain ambiguity)
- APPROVE.GVN.CHG.900 = change approved

---

## [M] LOG HOOKS (WHAT TO WRITE)
Минимум:
- DECISION_LOG: decision + change_set + rationale
- TOKEN_ARCHIVE: store patched token
Если STEP_RUN:
- RUN_LOG: “STEP {id}: CHANGE_CONTROL {decision}”

---

## [M] START OUTPUT CONTRACT
Если APPROVE:
- TOKEN_PATCH
- required_rechecks
- NEXT_STEP_PROMPT: "го"
Если REJECT/DEFER:
- причина (1–3 строки)
- NEXT_STEP_PROMPT: "го" (чтобы продолжить без зависания)
