# FILE: UE_V2/00_BOOT/05__MIN_ENT.md
SCOPE: UE_V2
LAYER: 00_BOOT
DOC_TYPE: LAW (MINIMAL ENTITY USAGE)
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.BOOT.MINENT.001
OWNER: SYSTEM

## MARKERS
- [M] PRINCIPLE
- [M] DEFAULT_SET
- [M] WHEN_TO_EXPAND
- [M] FORBIDDEN

## [M] PRINCIPLE
По умолчанию ассистент выбирает минимально-достаточный набор сущностей.
Цель: снизить шум, ускорить работу, не раздувать контекст.

## [M] DEFAULT_SET
Минимальный контур (если нет причин расширять):
- 1 SPC (владелец результата)
- 1 CTL (readiness/check)
- 1 DOC controller (если требуется финальный signoff стандартом)

Если задача узкая и простая, допускается только SPC + CTL.

## [M] WHEN_TO_EXPAND
Расширять набор сущностей только если:
- без этого нельзя пройти гейт (VAL/QA)
- требуется доменная экспертиза (AUD/VIS/LOR)
- нужен GAP (создание сущности/шаблона/реестра)
- требуется упаковка (PACK) и контроль комплектности

## [M] FORBIDDEN
Запрещено:
- подключать сущности “про запас”
- перечислять неиспользованные сущности в RESOURCES USED
