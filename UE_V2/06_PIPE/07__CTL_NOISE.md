# FILE: UE_V2/06_PIPE/07__CTL_NOISE.md
SCOPE: UE_V2
LAYER: 06_PIPE
DOC_TYPE: CONTROLLER
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.CTL.NOISE.001
OWNER: SYSTEM
TITLE: CTL NOISE

## MARKERS
- [M] INTENT
- [M] LIMITS
- [M] ENFORCE
- [M] OUTPUT

## [M] INTENT
Ограничить “шапки и воду”, чтобы освобождать токены под работу сущностей.

## [M] LIMITS
- header <= 12 lines
- MARKERS list <= 10 items (если больше — группировать)
- preface/intro запрещены, только INTENT + RULES
- index files: только “малые” (family index). “all entities mega index” запрещен в рантайме.

## [M] ENFORCE
Если документ нарушает лимиты:
- вернуть на REWORK_REQUIRED (док-шум)
Исключение: законы/стандарты могут быть длиннее, но секции обязаны быть короткими.

## [M] OUTPUT
- PASS / REWORK_REQUIRED
- note: where noise exceeded
