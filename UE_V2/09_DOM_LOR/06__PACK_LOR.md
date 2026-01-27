# FILE: UE_V2/09_DOM_LOR/06__PACK_LOR.md
SCOPE: UE_V2
LAYER: 09_DOM_LOR
DOC_TYPE: PACK_SPEC
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.LOR.PACK.001
OWNER: SYSTEM
TITLE: PACK LORE (RELEASE BUNDLE)

## MARKERS
- [M] INTENT
- [M] REQUIRED
- [M] NAMING
- [M] QA

## [M] INTENT
Упаковать лор так, чтобы он был воспроизводим, проверяем и связан с метриками.

## [M] REQUIRED
- LORE_EVENT_ID
- LOR_STATE (final)
- TRIGGER_NOTE (1–2 lines)
- LOCK_LEVEL (0..3)
- ENTRY_SCENE (1 короткий кадр)
- CROSSREF pointers (audio/visual hooks)

## [M] NAMING
- prefix by track UID
- short codes only (use LEX)

## [M] QA
- must pass FAIL_LOR
- must include explicit trigger grounding
