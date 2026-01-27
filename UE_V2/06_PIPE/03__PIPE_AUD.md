# FILE: UE_V2/06_PIPE/03__PIPE_AUD.md
SCOPE: UE_V2
LAYER: 06_PIPE
DOC_TYPE: PIPELINE
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.PIPE.AUD.001
OWNER: SYSTEM
TITLE: PIPE AUDIO

## MARKERS
- [M] INTENT
- [M] REQUIRED_KB
- [M] STEPS
- [M] ACCEPT_RULES
- [M] OUTPUTS

## [M] INTENT
Производство аудио-артефакта: сохранить DNA семьи + обеспечить читаемость + допустить “износ” без брака.

## [M] REQUIRED_KB
Нужны определения/пороги:
- AUD.RI, AUD.WTI, AUD.CF, AUD.LRA, AUD.DAIR, AUD.DLM
- THR.RI.MIN, THR.CF.REL, THR.DAIR.FLOOR, THR.DLM.MONO
Если нет → GAP (в 05_KB/05__KB_AUD).

## [M] STEPS
1) PROFILE PICK
   - выбрать “семейный” профиль (targets) или создать новый (GAP)
2) ORUM-A PASS
   - вокальный контраст/читаемость: держать RI >= THR.RI.MIN
3) ORUM-B PASS
   - энергия/пики: CF target по задаче; контролировать LRA режимы
4) DELTA CONTROL
   - ΔAIR/ΔLM: единая сущность, но не клоны (см. VAL_AUD)
5) MIX LOW-END
   - tight low end: саб 30–60 Hz якорь, без каши в 80–200
6) PRE-ACCEPT
   - собрать метрики: RI_t, WTI_t, CF_3s_P50, LRA, ΔAIR%, ΔLM%
7) QA_ACCEPT
   - PASS или REWORK_REQUIRED

## [M] ACCEPT_RULES
- RI_t < 0.62 → REWORK_REQUIRED (если не спец-режим с явным допуском)
- CF_3s_P50 < 11.5 → REWORK_REQUIRED
- LRA > 12 LU → допустимо только при явном LAW-13
- клоны Δ (слишком одинаковые) → REWORK_REQUIRED

## [M] OUTPUTS
- AUDIO_PROFILE (targets + допуски)
- ACCEPT_REPORT (метрики + решение)
- VIS/LOR hooks (если LAW-15/канон-триггеры включены)
