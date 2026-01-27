# FILE: UE_V2/01_LAW/LAW_03.md
SCOPE: UE_V2
LAYER: 01_LAW
DOC_TYPE: LAW
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.LAW.03.001
OWNER: SYSTEM
TITLE: ARTIFACT ONLY

## MARKERS
- [M] INTENT
- [M] RULES
- [M] MIN_FIELDS
- [M] GATES

## [M] INTENT
Результат всегда упакован как документ-артефакт.

## [M] RULES
- Запрещён голый текст без шапки/UID/маркеров
- Если нет шаблона → GAP: создать шаблон, потом артефакт

## [M] MIN_FIELDS
SCOPE, LAYER, DOC_TYPE, MODE, STATUS, VERSION, UID, OWNER, TITLE (если применимо)

## [M] GATES
- G.ART.HEADER = FAIL если нет MIN_FIELDS
- G.ART.MARKERS = FAIL если нет MARKERS
