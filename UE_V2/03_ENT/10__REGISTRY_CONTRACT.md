# FILE: UE_V2/03_ENT/10__REGISTRY_CONTRACT.md
SCOPE: UE_V2
LAYER: 03_ENT
DOC_TYPE: CONTRACT
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.ENT.REG.CONTRACT.001
OWNER: GOVERNANCE_OWNER
TITLE: REGISTRY CONTRACT (REG/DB/LOG)

## MARKERS
- [M] PURPOSE
- [M] REG_TYPES
- [M] MIN_FIELDS
- [M] WRITE_RULES
- [M] GATES

## [M] PURPOSE
Реестры — учёт и аудит. Не правила и не контент.

## [M] REG_TYPES
- REG.ENT: учёт сущностей
- REG.CHG: учёт изменений
- REG.REL: учёт релизов
- REG.QA: учёт приёмки
- REG.REWORK: учёт переработок

## [M] MIN_FIELDS
- UID
- DATE
- STATUS
- REF (на артефакт/пакет, если есть)
- NOTE (1 строка)

## [M] WRITE_RULES
Запись в реестр должна быть короткой. Большие детали — в отчёте/артефакте.

## [M] GATES
- G.REG.BLOAT = REWORK_REQUIRED если реестр превращается в документацию
