# FILE: UE_V2/01_LAW/LAW_14.md
SCOPE: UE_V2
LAYER: 01_LAW
DOC_TYPE: LAW
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.LAW.14.001
OWNER: SYSTEM
TITLE: ACCEPTANCE & RELEASE

## MARKERS
- [M] INTENT
- [M] STATES
- [M] MIN_ACCEPT_SET
- [M] GATES

## [M] INTENT
Единые правила приёмки: PASS, REWORK_REQUIRED, FAIL.

## [M] STATES
- PASS: допуски соблюдены, можно выпускать
- REWORK_REQUIRED: можно исправить без смены сущности/UID
- FAIL: нарушены базовые законы, требуется переработка/пересборка

## [M] MIN_ACCEPT_SET
Минимум проверок для домена AUD:
- RI gate (LAW_09)
- WTI control (LAW_07)
- non-clone variance (LAW_10)
- low-end anchor (LAW_11)
- если есть Silence Point, проверка LAW_13

## [M] GATES
- G.ACCEPT.MINSET.MISSING = REWORK_REQUIRED если нет части MIN_ACCEPT_SET
- G.ACCEPT.LAW_BREACH = FAIL если нарушен любой LAW_01..LAW_06
