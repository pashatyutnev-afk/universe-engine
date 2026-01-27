# FILE: UE_V2/09_DOM_LOR/04__CANON_LOCK.md
SCOPE: UE_V2
LAYER: 09_DOM_LOR
DOC_TYPE: RULES
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.LOR.CANON.LOCK.001
OWNER: SYSTEM
TITLE: CANON LOCK RULES

## MARKERS
- [M] INTENT
- [M] LOCK_LEVELS
- [M] WHAT_CAN_CHANGE
- [M] WHAT_CANNOT_CHANGE
- [M] ENTRY_RULES

## [M] INTENT
Фиксация канона: что считается “закрытым” после релиза/триггера.

## [M] LOCK_LEVELS
- LOCK0: draft (всё можно менять)
- LOCK1: released track (мелкие уточнения, без реткона причин)
- LOCK2: trigger-locked (после событий ZERO_POINT/LANG_FRACTURE)
- LOCK3: core law locked (законы/конвейер)

## [M] WHAT_CAN_CHANGE
- wording, формулировки, стилистика
- второстепенные детали, если не ломают причины/следствия

## [M] WHAT_CANNOT_CHANGE
- причина события, если оно триггерилось метриками
- базовые определения LAW-13/LAW-15
- итоговый LOR_STATE финала сезона

## [M] ENTRY_RULES
- lock level must be declared in release package
- any retcon requires CHANGE protocol (outside this doc)
