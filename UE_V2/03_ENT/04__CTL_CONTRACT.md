# FILE: UE_V2/03_ENT/04__CTL_CONTRACT.md
SCOPE: UE_V2
LAYER: 03_ENT
DOC_TYPE: CONTRACT
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.ENT.CTL.CONTRACT.001
OWNER: GOVERNANCE_OWNER
TITLE: CTL CONTRACT (CONTROLLER)

## MARKERS
- [M] PURPOSE
- [M] POWERS
- [M] STOP_ONLY
- [M] OUTPUTS
- [M] GATES

## [M] PURPOSE
CTL применяет политики/лимиты и запускает гейты. CTL не “придумывает” контент.

## [M] POWERS
CTL может:
- требовать Boot Trace / Resource Trace
- ограничивать шум (NOISE_BUDGET)
- блокировать “лишние сущности”
- требовать доменную валидацию

## [M] STOP_ONLY
CTL имеет право на STOP только при:
- RAW missing
- marker not confirmed
- input absent

## [M] OUTPUTS
- Gate Report (PASS/REWORK/FAIL/STOP/GAP)
- Requirements list для исправления

## [M] GATES
- G.CTL.BAD_STOP = FAIL если STOP без допустимой причины
- G.CTL.NO_TRACE = FAIL если нет требуемого Trace
