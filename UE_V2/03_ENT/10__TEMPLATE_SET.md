# FILE: UE_V2/03_ENT/10__TEMPLATE_SET.md
SCOPE: UE_V2
LAYER: 03_ENT
DOC_TYPE: TEMPLATE_SET
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.ENT.TPL.SET.001
OWNER: STANDARDS_OWNER
TITLE: MINIMUM TEMPLATE SET (V2)

## MARKERS
- [M] INTENT
- [M] LIST
- [M] RULES
- [M] GATES

## [M] INTENT
Минимальный набор шаблонов, чтобы конвейер работал без “голого контента”.

## [M] LIST
- TPL.LAW
- TPL.STD
- TPL.ENT (entity passport/contract)
- TPL.PIPE
- TPL.REPORT (acceptance output)
- TPL.MANIFEST (pack/release)
- TPL.SOP (операционная процедура)
- TPL.CAL (календарь/график)

## [M] RULES
Если в системе появляется новый тип артефакта — сначала добавить шаблон.

## [M] GATES
- G.TPLSET.MISSING = GAP если нет шаблона под нужный артефакт
