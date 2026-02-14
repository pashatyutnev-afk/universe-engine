# 07__FAIL_CODES
KIND: LAW
ROLE: FAIL_CODES
SCOPE: SYSTEM
STATUS: CANON
VERSION: 1.0.0

## [M] PURPOSE
Единый список FAIL кодов для всей системы.
Каждый FAIL:
- детерминированный
- краткий
- указывает 1 минимальное действие (FIX_LIST)

STOP_GAP использует эти коды как закон.

---

## [M] HARD_RULES
1) NO GUESSING
- При нехватке данных -> FAIL, а не “примерно так”.

2) MINIMAL NEXT ACTION
- FIX_LIST содержит 1–3 минимальных шага, не больше.

3) PROPAGATION
- Если FAIL пришёл из валидатора/движка — его FAIL_CODE переносится наверх (не затирать).

4) CONSISTENCY
- Один тип проблемы -> один и тот же FAIL_CODE во всех модулях.

---

## [M] FAIL CODES (CANON)

### FAIL: INPUT_ABSENT
WHEN:
- отсутствует TASK_TEXT или обязательный пользовательский ввод
- отсутствует критичный артефакт от пользователя (например текст файла для точного патча)

OUTPUT MUST INCLUDE:
- MISSING: что именно отсутствует
- FIX_LIST: "Provide <missing input>"

---

### FAIL: RAW_MISSING
WHEN:
- система по старой логике ожидает RAW ссылку как обязательную (deprecated case)
NOTE:
- В vNext KEY-first RAW_MISSING должен встречаться редко. Использовать только если правило реально требует RAW.

FIX_LIST example:
- "Add RAW field (or migrate reference to KEY-first)"

---

### FAIL: FILE_NOT_FOUND
WHEN:
- указан PATH, но файла нет / не читается / недоступен

FIX_LIST example:
- "Create file at <PATH> or correct manifest mapping"

---

### FAIL: ENTRYPOINT_MISSING
WHEN:
- отсутствует ключевой entrypoint/KEY (не резолвится KEY → PATH)
- required_eng_key / required_val_key / required_pipe_key не найден в манифесте
- отсутствует обязательный системный модуль (router/pipe/manifest)

FIX_LIST example:
- "Add KEY mapping to INDEX_MANIFEST: <KEY> -> <PATH>"

---

### FAIL: MARKER_NOT_CONFIRMED
WHEN:
- отсутствуют обязательные маркеры/поля/токены/контракты, например:
  - REQUIRED_ROLES
  - OUTPUT_CONTRACT
  - ENGINE_PLAN_TOKEN.required_eng_keys (как поле)
  - ENGINE_RUN_LEDGER
  - OUTPUT_LEDGER
  - VAL_REPORT
- формат не соответствует ENTRY_SCHEMA/contract

FIX_LIST example:
- "Add missing field <FIELD_NAME> to <TOKEN/FILE>"

---

### FAIL: SCOPE_VIOLATION
WHEN:
- подключены модули вне REQUIRED_SET
- запущен engine вне allowed list
- запущен engine из no-go list
- PIPE/ORC расширили задачу за пределы профиля/контракта

FIX_LIST example:
- "Remove forbidden module/engine <KEY> or update profile allow-list"

---

### FAIL: WEB_INSUFFICIENT
WHEN:
- WEB был разрешён политикой, но источников не хватило/они конфликтуют
- нет надёжных источников для ключевого утверждения

FIX_LIST example:
- "Provide additional sources or tighten requirements"

---

### FAIL: SCOPE_VIOLATION (SAFETY)
WHEN:
- запрос нарушает правила безопасности/политики (если применимо)
NOTE:
- Если у тебя отдельный safety код — вынеси туда. Если нет, оставляем как подтип SCOPE_VIOLATION.

---

## [M] FAIL RESPONSE TEMPLATE (MANDATORY)
Every FAIL response must include:
1) MODE
2) RESOURCES USED
3) DELIVERABLES:
   - STATUS: FAIL or STOP_GAP
   - FAIL_CODE: <...>
   - MISSING: [ ... ]
   - FIX_LIST: [ ... ]
4) GATES:
   - FAIL

---

## [M] MAPPING TO STOP_GAP
- Любой FAIL_CODE может активировать STOP_GAP.
- Для production задач: FAIL от mandatory validators -> STOP_GAP обязателен.

END.
