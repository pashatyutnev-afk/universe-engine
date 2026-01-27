# FILE: UE_V2/10_REL/04__SHEET_FMT.md
SCOPE: UE_V2
LAYER: 10_REL
DOC_TYPE: SPEC
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.REL.SHEET.001
OWNER: SYSTEM
TITLE: MASTER RELEASE SHEET FORMAT

## MARKERS
- [M] INTENT
- [M] REQUIRED_COLUMNS
- [M] OPTIONAL_COLUMNS
- [M] VALIDATION_RULES

## [M] INTENT
Единый формат “Master Release Sheet” для календаря A.

## [M] REQUIRED_COLUMNS
- Day
- Track_UID
- Track_Title
- RI_t
- CF_3s_P50
- LRA
- Ready_Status (OK/REWORK_REQUIRED/HOLD/ANOMALY_ALLOWED)
- Visual_Prompt_Ref (LAW-15)
- Lore_Trigger_Ref
- Notes

## [M] OPTIONAL_COLUMNS
- WTI_t
- ΔAIR%
- ΔLM%
- Alienation%
- Rage%
- Hope%
- Package_Status (AUDIO/VIS/LORE)

## [M] VALIDATION_RULES
- Track_UID must be unique per sheet
- Days must be 1..42, no gaps unless explicitly HOLD
- Any REWORK_REQUIRED cannot be scheduled unless overridden with explicit waiver (discouraged)
