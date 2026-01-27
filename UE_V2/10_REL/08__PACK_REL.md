# FILE: UE_V2/10_REL/08__PACK_REL.md
SCOPE: UE_V2
LAYER: 10_REL
DOC_TYPE: PACK_SPEC
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.REL.PACK.001
OWNER: SYSTEM
TITLE: RELEASE PACKAGE (AUDIO + VISUAL + LORE)

## MARKERS
- [M] INTENT
- [M] REQUIRED
- [M] STRUCTURE
- [M] QA_GATES

## [M] INTENT
Запрет “релиза без комплекта”. Релиз = связанный пакет трёх слоёв.

## [M] REQUIRED
- AUDIO:
  - final mix/master reference
  - metrics report (RI/CF/LRA + optional WTI/Δ)
- VIS:
  - prompt set (chunked if needed)
  - generated assets refs
- LOR:
  - LOR_STATE + trigger note
  - canon lock level

## [M] STRUCTURE
- folder per track UID
- within: /AUDIO /VIS /LOR /LOG

## [M] QA_GATES
- readiness gates PASS
- visual + lore fail specs PASS
- package completeness PASS
