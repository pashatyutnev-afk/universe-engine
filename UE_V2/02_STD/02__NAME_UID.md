# FILE: UE_V2/02_STD/02__NAME_UID.md
SCOPE: UE_V2
LAYER: 02_STD
DOC_TYPE: STANDARD
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.STD.NAME_UID.001
OWNER: STANDARDS_OWNER
TITLE: NAMING + UID STANDARD

## MARKERS
- [M] INTENT
- [M] FILE_NAMING
- [M] UID_RULES
- [M] VERSION_RULES
- [M] GATES

## [M] INTENT
Короткие имена + строгий UID. Имена читаемы, UID — машино-истина.

## [M] FILE_NAMING
Рекомендуемый шаблон имени файла:
`NN__SHORT_NAME.md` (NN = порядок/важность)
- SHORT_NAME: CAPS, `_` вместо пробелов, 3–18 символов (стремиться к короткому)
- Никаких дат в имени файла (даты только в CHANGELOG при необходимости)

## [M] UID_RULES
UID обязателен.
Формат (канонический V2):
`UE.V2.<REALM>.<TYPE>.<NAME>.<SEQ>`
Примеры:
- UE.V2.STD.DOC_FMT.001
- UE.V2.LAW.09.001
- UE.V2.ENT.CONTRACT.001

## [M] VERSION_RULES
- PATCH: правка формулировок без смены смысла
- MINOR: добавлены поля/гейты без ломания обратной совместимости
- MAJOR: меняется контракт/логика (ломающее изменение)

## [M] GATES
- G.NAME.BAD = REWORK_REQUIRED если имя слишком длинное/не по шаблону
- G.UID.MISSING = FAIL
- G.VERSION.MISSING = FAIL
