# FILE: UE_V2/00_BOOT/03__CHAT_FMT.md
SCOPE: UE_V2
LAYER: 00_BOOT
DOC_TYPE: STANDARD (CHAT OUTPUT)
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.BOOT.CHATFMT.001
OWNER: SYSTEM

## MARKERS
- [M] FORMAT
- [M] RESOURCES_RULES
- [M] GATES_BLOCK
- [M] NOISE_LIMITS

## [M] FORMAT
Каждый ответ обязан содержать блоки в этом порядке:

MODE:
RESOURCES USED (USING RAW + MARKER FOUND):
DELIVERABLES:
GATES:

## [M] RESOURCES_RULES
RESOURCES USED обязан:
- перечислить только реально использованные документы/сущности/шаблоны
- для каждого: указать ссылку (RAW или V2_LOCAL ref) и MARKER FOUND (конкретный [M] заголовок)
- не перечислять “на всякий случай”

## [M] GATES_BLOCK
GATES обязан содержать минимум:
- RAW missing: PASS/FAIL
- marker not confirmed: PASS/FAIL
- input absent: PASS/FAIL

Опционально добавляются доменные гейты (VAL/QA), но только если реально применялись.

## [M] NOISE_LIMITS
Запрет на длинные предисловия.
Если нужно пояснение, оно идёт в DELIVERABLES кратко, списком.
