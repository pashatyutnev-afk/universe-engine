# 21__RESUME_TOKEN
SCOPE: Universe Engine (UE_V2)
DOC_TYPE: TOKEN_SPEC
UID: UE.V2.TOKEN.RESUME.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)

## [M] PURPOSE
RESUME_TOKEN фиксирует точку продолжения, чтобы:
- не перепроходить весь пайп
- чинить только WORK_UNIT
- возвращаться в нужный шаг

## [M] TOKEN SHAPE (CANON)
RESUME_TOKEN v1:
- RUN_ID: <id исходного прогона или связанного>
- PARENT_RUN_ID: <optional, если patch-run>
- ROUTE_TOKEN_REF: <id/ключ маршрута>
- DOMAIN: <domain из ROUTE_TOKEN>
- ARTIFACT_ID: <UID артефакта или artifact key>
- ARTIFACT_VERSION: <optional>
- WORK_UNIT_ID: <см. WORK_UNITS_STANDARD>
- ISSUE_CLASS: FLOW|RHYME|LOGIC|STYLE|COMPLIANCE|LINK_MISSING|UID_COLLISION|STRUCTURE
- ISSUE_NOTE: <кратко>
- PATCH_MODE: PATCH_ONLY|PATCH_THEN_VALIDATE|PATCH_THEN_REGEN
- LOAD_MIN_SET:
  - REQUIRED_INDEX_KEYS: [ ... ]
  - REQUIRED_DOC_KEYS: [ ... ]
  - REQUIRED_ENTITY_KEYS: [ ... ]
- GATES_REQUIRED: [ ... ]
- NEXT_STEP:
  - RETURN_TO: PIPE_STEP|USER_REVIEW|FINAL_EXPORT
  - PIPE_STEP_REF: <optional>
- TRACE_LEVEL: MIN|STD|MAX

## [M] LOAD POLICY (RESUME)
- LOAD_MIN_SET обязателен.
- В RESUME запрещено массово грузить деревья.
- Разрешена загрузка только:
  - INDEX_MANIFEST домена
  - PIPELINE_CONTRACT домена
  - target файл/блок WORK_UNIT
  - обязательные правила для ISSUE_CLASS (если указаны в REQUIRED_DOC_KEYS)

## [M] LAW: WHEN TO CREATE
RESUME_TOKEN создаётся всегда, когда:
- пользователь просит точечную правку
- найден FAIL валидации на конкретном WORK_UNIT
- требуется вернуться к месту ошибки без перегона всего

## [M] GATES
PASS если:
- WORK_UNIT_ID задан и адресуем
- PATCH_MODE определён
- LOAD_MIN_SET определён
- GATES_REQUIRED заданы
FAIL если:
- отсутствует WORK_UNIT_ID
- PATCH_MODE отсутствует
- LOAD_MIN_SET пуст
