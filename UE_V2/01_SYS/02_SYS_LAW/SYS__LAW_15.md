# FILE: UE_V2/01_LAW/LAW_15.md
SCOPE: UE_V2
LAYER: 01_LAW
DOC_TYPE: LAW
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.LAW.15.001
OWNER: SYSTEM
TITLE: VISUAL-AUDIO LINK

## MARKERS
- [M] INTENT
- [M] REQUIRED_LINKS
- [M] MIN_OUTPUT
- [M] GATES

## [M] INTENT
Аудио-параметры управляют визуальными состояниями. Визуал синхронизирован с метриками.

## [M] REQUIRED_LINKS
Минимальные связи:
- CF high → glitch artifacts intensity
- LAW_13 active + RMS drop → режим “Zero Point” (white dot on black)
- AIR band energy (8–16k) → transparency/DOF depth

## [M] MIN_OUTPUT
Для каждого трека, если визуал присутствует:
- VIS_STATE map (коды состояний)
- PROMPT chunks (например 5s blocks)
- NEGATIVE constraints
- sync notes: какие метрики дергают какие события

## [M] GATES
- G.VISLINK.MISSING = REWORK_REQUIRED если нет маппинга при наличии визуала
- G.VISLINK.CONFLICT = FAIL если визуал нарушает канон/условия (LAW_01)
