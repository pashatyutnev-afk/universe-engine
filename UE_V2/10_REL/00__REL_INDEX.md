# FILE: UE_V2/10_REL/00__REL_INDEX.md
SCOPE: UE_V2
LAYER: 10_REL
DOC_TYPE: INDEX
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.REL.IDX.001
OWNER: SYSTEM
TITLE: RELEASE DOMAIN INDEX

## MARKERS
- [M] REL_COMPONENTS
- [M] CALENDAR
- [M] READINESS
- [M] IMPACT_ARC
- [M] PACKAGING
- [M] QA_POST

## [M] REL_COMPONENTS
- 01__CAL_A            : Calendar A contract (42 days)
- 02__READINESS_MATRIX : rules for readiness scoring & flags
- 03__ARC_IMPACT       : resonance arc construction (phases)
- 04__SHEET_FMT        : Master Release Sheet format
- 05__UID_TRACK        : UID assignment rules for tracks
- 06__REWORK           : REWORK_REQUIRED rules and workflow
- 07__DROP_RULES       : drops/teasers/announcements rules
- 08__PACK_REL         : release bundle (audio+vis+lore) rules
- 09__POST_REL         : post-release control & regression

## [M] CALENDAR
Calendar A is a deterministic 42-step release pipeline.

## [M] READINESS
Readiness gates must be computed before scheduling.

## [M] PACKAGING
No release without a complete package (audio/visual/lore).
