# FILE: UE_V2/07_DOM_AUD/10__MIX_LOW.md
SCOPE: UE_V2
LAYER: 07_DOM_AUD
DOC_TYPE: SPEC
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.AUD.SPEC.LOW.001
OWNER: SYSTEM
TITLE: SPEC TIGHT LOW END (30–60 ANCHOR)

## MARKERS
- [M] INTENT
- [M] ANCHOR
- [M] CONTROL_ZONES
- [M] FAIL

## [M] INTENT
Дать “tight low end”: саб держит трек, но не мажет удар.

## [M] ANCHOR
- 30–60 Hz: суб-якорь (моно, стабильный, без дрожи)
- саб не должен исчезать в silence point (если FLAG.SUB_ANCHOR=true)

## [M] CONTROL_ZONES
- 60–90 Hz: конфликт кика/баса решать приоритетом “удар”
- 80–200 Hz: зона каши, резать/уплотнять аккуратно
- 200–500 Hz: не раздувать, иначе RI падает (mud)

## [M] FAIL
- если low-end “плавает”, проваливается или раздувает 80–200 → REWORK.AUD.LOW_END_LOOSE
