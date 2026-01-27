# FILE: UE_V2/06_PIPE/12__QA_PACK.md
SCOPE: UE_V2
LAYER: 06_PIPE
DOC_TYPE: QA
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.QA.PACK.001
OWNER: SYSTEM
TITLE: QA PACK

## MARKERS
- [M] INTENT
- [M] REQUIRED_ITEMS
- [M] FAIL_CODES

## [M] INTENT
Проверка комплектности пакета релиза: ничего не забыто.

## [M] REQUIRED_ITEMS
Минимальный пакет:
- audio artifact + audio profile + acceptance report
- visual prompts (если LAW-15 включен)
- lore trigger artifact (если релизный режим/канон)
- UID mapping (track UID)

## [M] FAIL_CODES
- REWORK.PACK.MISSING_ITEM
- REWORK.PACK.NAME_UID_MISMATCH
