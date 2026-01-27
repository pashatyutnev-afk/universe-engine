# FILE: UE_V2/11_LEX/05__ABBR_RULES.md
SCOPE: UE_V2
LAYER: 11_LEX
DOC_TYPE: RULES
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.LEX.ABBR.001
OWNER: SYSTEM
TITLE: ABBREVIATION RULES (STABILITY)

## MARKERS
- [M] PRINCIPLES
- [M] FORMAT
- [M] DO_NOT

## [M] PRINCIPLES
- token must be short, unique, stable
- 1 token = 1 meaning (no overload)
- avoid synonyms (choose one canonical token)

## [M] FORMAT
- uppercase A–Z, digits, underscore
- recommended length 2–6 chars
- compound tokens use dot hierarchy:
  - UE.V2.<AREA>.<NAME>.<NNN>
- domain prefixes: AUD/VIS/LOR/REL/LEX/LOG

## [M] DO_NOT
- do not change token meaning after adoption
- do not use long phrases as tokens
- do not create duplicates with different spelling
