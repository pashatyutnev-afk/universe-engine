# 24__CHECKPOINT_RULES
SCOPE: Universe Engine (UE_V2)
DOC_TYPE: LAW
UID: UE.V2.LAW.CHECKPOINTS.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)

## [M] PURPOSE
Гарантировать, что система никогда не теряет место работы и не уходит в полный переген без нужды.

## [M] CHECKPOINT TYPES
- AUTO_CHECKPOINT: создаётся системой на FAIL или перед рискованным шагом
- USER_CHECKPOINT: создаётся по команде пользователя (например "зафиксируй тут")
- PATCH_CHECKPOINT: создаётся при любой точечной правке

## [M] MANDATORY CHECKPOINT MOMENTS
Создавать RESUME_TOKEN обязательно:
- при FAIL любого gate, если можно локализовать WORK_UNIT
- при запросе пользователя на частичную правку
- перед шагами, которые могут изменить структуру артефакта (REGEN, NORMALIZE, MIGRATE)

## [M] STORAGE
- TOKEN_ARCHIVE хранит:
  - RESUME_TOKEN
  - ROUTE_TOKEN snapshot ref
  - связанный RUN_ID
- RUN_LOG хранит:
  - список checkpoint refs по RUN_ID
- DECISION_LOG хранит:
  - почему не PATCH_ONLY, а REGEN

## [M] LAW: NO FULL REWRITE
Если ISSUE локализуется в WORK_UNIT, то:
- PATCH_ONLY является default
- FULL_REGEN запрещён без записи Decision: WHY_REGEN

## [M] GATES
PASS если:
- любой FAIL имеет чекпоинт и адресуемый WORK_UNIT
FAIL если:
- произошёл полный переген при локализуемом ISSUE без Decision
