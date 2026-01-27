# FILE: UE_V2/06_PIPE/08__VAL_DOC.md
SCOPE: UE_V2
LAYER: 06_PIPE
DOC_TYPE: VALIDATOR
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.VAL.DOC.001
OWNER: SYSTEM
TITLE: VAL DOC

## MARKERS
- [M] INTENT
- [M] REQUIRED_FIELDS
- [M] MARKER_RULES
- [M] FAIL_CODES

## [M] INTENT
Проверка документа-артефакта: минимальная валидность и пригодность для машины.

## [M] REQUIRED_FIELDS
- FILE path line
- SCOPE, LAYER, DOC_TYPE, MODE
- STATUS, VERSION, UID, OWNER
- MARKERS block

## [M] MARKER_RULES
- каждый [M] marker должен существовать в тексте
- marker names stable (без творчества)
- запрещены “мертвые маркеры” без секции

## [M] FAIL_CODES
- REWORK.DOC.MISSING_FIELD
- REWORK.DOC.MARKER_BROKEN
- REWORK.DOC.NOISE_EXCEEDED (если CTL_NOISE триггернул)
