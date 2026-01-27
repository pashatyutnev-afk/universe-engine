# FILE: UE_V2/10_REL/09__POST_REL.md
SCOPE: UE_V2
LAYER: 10_REL
DOC_TYPE: SPEC
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.REL.POST.001
OWNER: SYSTEM
TITLE: POST-RELEASE CONTROL (REGRESSION / FIXES)

## MARKERS
- [M] INTENT
- [M] INPUTS
- [M] CHECKS
- [M] ACTIONS
- [M] LIMITS

## [M] INTENT
После релиза проверяем регресс и фиксируем отклонения без реткона канона.

## [M] INPUTS
- audience signals (if available)
- internal QC re-check: RI/CF/LRA spot check
- packaging integrity check

## [M] CHECKS
- regression: did key metrics drift in later masters?
- continuity: visual/lore consistency
- compliance: forbidden items not present

## [M] ACTIONS
- log issue in QA_LOG or CHANGE_LOG
- hotfix allowed only if it does not break CANON_LOCK
- if breaks canon → requires change protocol

## [M] LIMITS
- no rewriting triggers post-release unless declared as migration
