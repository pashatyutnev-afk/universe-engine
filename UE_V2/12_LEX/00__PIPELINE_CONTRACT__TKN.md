# FILE: UE_V2/11_LEX/00__LEX.md
SCOPE: UE_V2
LAYER: 11_LEX
DOC_TYPE: DICTIONARY
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.LEX.MAIN.001
OWNER: SYSTEM
TITLE: UE_V2 LEXICON (CORE)

## MARKERS
- [M] PURPOSE
- [M] TOKENS_CORE
- [M] STATES
- [M] RUNTIME
- [M] DOMAINS

## [M] PURPOSE
Short tokens replace long meanings. 1 token = 1 meaning. Stable.

## [M] TOKENS_CORE
- UE      : Universe Engine system scope
- V2      : optimized version set
- DOC     : document artifact
- ENT     : entity artifact
- IDX     : index doc (small)
- TPL     : template doc
- REG     : registry/log store
- RAW     : raw link navigation only

## [M] STATES
- OK      : pass gate
- HOLD    : blocked by missing inputs/package
- FAIL    : gate failed
- GAP     : missing entity/template/doc → must propose/create
- STOP    : hard stop condition met
- REWORK  : rework required

## [M] RUNTIME
- BOOT    : mandatory boot sequence
- TRACE   : run trace contract
- SIGNOFF : final approval stage

## [M] DOMAINS
- AUD     : audio domain (ORUM, metrics)
- VIS     : visual domain (LAW-15 mapping)
- LOR     : lore domain (canon triggers)
- REL     : release domain (calendar, packaging)
