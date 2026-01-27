# FILE: UE_V2/07_DOM_AUD/11__MASTER_TARGETS.md
SCOPE: UE_V2
LAYER: 07_DOM_AUD
DOC_TYPE: TARGETS
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.AUD.TGT.MASTER.001
OWNER: SYSTEM
TITLE: MASTER TARGETS (FAMILY DNA)

## MARKERS
- [M] INTENT
- [M] FAMILY_BASELINE
- [M] VARIATION_BUDGET
- [M] DEFAULT_GATES

## [M] INTENT
Единые таргеты для группы: ощущение “одной сущности”, но с вариативностью.

## [M] FAMILY_BASELINE
Базовый профиль (по умолчанию, если не задано иначе):
- RI_t >= 0.62 (lyric sections)
- CF_3s_P50: 12.5–14.0 (big chorus capable)
- LRA: 9–12 (legal), >12 только с LAW-13
- ΔAIR: [-18% .. +10%] (внутри семейного окна)
- ΔLM:  [+3% .. +9%] (не уходить в mud)

## [M] VARIATION_BUDGET
Чтобы не стать клонами:
- ΔAIR spread across album: минимум 3% между соседями
- ΔLM spread across album: минимум 2% между соседями
- WTI can vary by sections (verse higher, chorus lower)

## [M] DEFAULT_GATES
- CF < 11.5 → REWORK_REQUIRED
- RI < 0.62 (lyric sections) → REWORK_REQUIRED
- LRA > 12 без LAW-13 → REWORK_REQUIRED
