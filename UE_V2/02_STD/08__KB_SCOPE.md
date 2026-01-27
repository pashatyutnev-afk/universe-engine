# FILE: UE_V2/02_STD/08__KB_SCOPE.md
SCOPE: UE_V2
LAYER: 02_STD
DOC_TYPE: STANDARD
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.STD.KB_SCOPE.001
OWNER: STANDARDS_OWNER
TITLE: KB SCOPE STANDARD

## MARKERS
- [M] INTENT
- [M] REQUIRED_FIELDS
- [M] BOUNDARIES
- [M] RAW_REFERENCES
- [M] GATES

## [M] INTENT
KB фиксирует: что считается знанием, какие входы/выходы допустимы, где границы.

## [M] REQUIRED_FIELDS
KB-док обязан иметь:
- KB_INPUTS
- KB_OUTPUTS
- KB_BOUNDARIES
- KB_SOURCES (RAW/refs если применимо)

## [M] BOUNDARIES
- Что KB включает
- Что KB НЕ включает (запреты/игнор)
- Уровень доверия (если есть)

## [M] RAW_REFERENCES
Если KB опирается на внешнее — указывать RAW ссылки.
Если RAW нет → либо GAP, либо “LOCAL KB ONLY”.

## [M] GATES
- G.KB.SCOPE_MISSING = FAIL
- G.KB.BOUNDARY_MISSING = FAIL
