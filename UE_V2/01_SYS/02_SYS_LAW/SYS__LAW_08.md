# FILE: UE_V2/01_LAW/LAW_08.md
SCOPE: UE_V2
LAYER: 01_LAW
DOC_TYPE: LAW
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.LAW.08.001
OWNER: SYSTEM
TITLE: INVERSE CONTRAST

## MARKERS
- [M] INTENT
- [M] RULES
- [M] CONDITIONS
- [M] GATES

## [M] INTENT
Контраст “громко→тихо” является формой, если удерживает внимание опорой (саб/шёпот/ритм).

## [M] RULES
- Падение плотности допускается, если задан удерживающий якорь
- Тишина не считается браком автоматически (связка с LAW_13)

## [M] CONDITIONS
Inverse Contrast VALID если:
- сохранён саб- или ритм-якорь
- читаемость ключевого сообщения не разрушена (RI gate)

## [M] GATES
- G.IC.NO_ANCHOR = FAIL если после дропа нет якоря
- G.IC.RI_DROP = REWORK_REQUIRED если RI падает ниже порога домена
