# FILE: UE_V2/08_DOM_VIS/09__PACK_VIS.md
SCOPE: UE_V2
LAYER: 08_DOM_VIS
DOC_TYPE: PACK_SPEC
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.VIS.PACK.001
OWNER: SYSTEM
TITLE: PACK VIS (RELEASE BUNDLE)

## MARKERS
- [M] INTENT
- [M] REQUIRED_ASSETS
- [M] NAMING
- [M] QA_NOTES

## [M] INTENT
Упаковать визуал так, чтобы релиз был воспроизводим и проверяем.

## [M] REQUIRED_ASSETS
- prompts: 5s chunks (text)
- state timeline (VIS_STATE)
- negative list (global)
- continuity sheet (location, character, wardrobe, lens)
- final render(s) references (ids/paths)

## [M] NAMING
- use track UID as prefix
- chunk numbering: _VIS_05S_0001, _0002, ...
- keep short names, no long prose

## [M] QA_NOTES
- must pass FAIL_VIS checks
- sync events documented: CF impacts, LAW-13 ZP mode, AIR mapping
