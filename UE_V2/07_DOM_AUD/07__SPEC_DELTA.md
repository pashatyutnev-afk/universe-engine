# FILE: UE_V2/07_DOM_AUD/07__SPEC_DELTA.md
SCOPE: UE_V2
LAYER: 07_DOM_AUD
DOC_TYPE: SPEC
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.AUD.SPEC.DELTA.001
OWNER: SYSTEM
TITLE: SPEC ΔAIR% / ΔLM% (CLONE-SAFETY)

## MARKERS
- [M] INTENT
- [M] DEFINITION
- [M] DEFAULT_LIMITS
- [M] CLONE_RULE
- [M] NOTES

## [M] INTENT
Держать “одна сущность/одна ДНК”, но не делать частотных клонов.

## [M] DEFINITION
- ΔAIR%: относительное отклонение энергии полосы 8–16 kHz от семейного таргета
- ΔLM%: относительное отклонение “low-mid body” (примерно 250–500 Hz) от семейного таргета

Знак:
- отрицательное ΔAIR → меньше воздуха (клаустрофобия)
- положительное ΔLM → больше монолитности/тела вокала (но риск muddy)

## [M] DEFAULT_LIMITS
- ΔAIR floor (claustro mode): -18% (как requested)
- ΔLM target: +5…+8% (как requested)

## [M] CLONE_RULE
Чтобы не быть клонами:
- между треками держать различия по Δ:
  - |ΔAIR_i - ΔAIR_j| >= 3%
  - |ΔLM_i - ΔLM_j| >= 2%
если одновременно меньше обоих → REWORK (clone risk)

## [M] NOTES
Δ не отменяет RI: если ΔLM растит mud и RI падает <0.62 → REWORK.
