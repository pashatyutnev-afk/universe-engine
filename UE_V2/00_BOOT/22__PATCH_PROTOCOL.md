# 22__PATCH_PROTOCOL
SCOPE: Universe Engine (UE_V2)
DOC_TYPE: PROTOCOL
UID: UE.V2.PROTO.PATCH.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)

## [M] PURPOSE
Заставить рантайм чинить строго WORK_UNIT, не переписывая артефакт целиком.

## [M] INPUTS
- RESUME_TOKEN (обязателен)
- TARGET_CONTENT (только WORK_UNIT или минимальный контекст вокруг него)
- DOMAIN_INDEX_MANIFEST (обязателен)
- DOMAIN_PIPELINE_CONTRACT (обязателен)

## [M] STEPS (CANON)
P0) RESUME ENTRY CHECK
- verify RESUME_TOKEN поля: WORK_UNIT_ID, PATCH_MODE, LOAD_MIN_SET, GATES_REQUIRED

P1) MIN_LOAD
- load INDEX_MANIFEST по ключам REQUIRED_INDEX_KEYS
- load PIPELINE_CONTRACT (только разделы: steps, gates, interfaces)
- load TARGET_CONTENT (WORK_UNIT)

P2) PATCH EXEC
- выполнить правку только внутри WORK_UNIT
- запрет: менять другие WORK_UNITS, кроме случаев PATCH_THEN_REGEN (и только указанные)

P3) VALIDATE (по GATES_REQUIRED)
- прогнать минимальные проверки домена
- прогнать compliance для ISSUE_CLASS
- если FAIL → создать новый RESUME_TOKEN (следующий чекпоинт) и остановить на FIX_REQUIRED

P4) LOG WRITE
- RUN_LOG: записать PATCH_EVENT
- DECISION_LOG: почему выбран PATCH_MODE
- TOKEN_ARCHIVE: сохранить RESUME_TOKEN v1 и новый v1 (если создан)

P5) RETURN
- перейти в NEXT_STEP.RETURN_TO

## [M] PATCH_EVENT SHAPE
PATCH_EVENT:
- RUN_ID
- ARTIFACT_ID
- WORK_UNIT_ID
- ISSUE_CLASS
- PATCH_MODE
- BEFORE_SUMMARY
- AFTER_SUMMARY
- GATES_RESULT: PASS|FAIL
- NEXT_STEP

## [M] GATES
PASS если:
- изменён только WORK_UNIT
- GATES_REQUIRED = PASS
FAIL если:
- изменено вне WORK_UNIT без разрешения
- отсутствует логирование PATCH_EVENT
