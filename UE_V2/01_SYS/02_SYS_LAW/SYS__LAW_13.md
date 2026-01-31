# FILE: UE_V2/01_LAW/LAW_13.md
SCOPE: UE_V2
LAYER: 01_LAW
DOC_TYPE: LAW
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.LAW.13.001
OWNER: SYSTEM
TITLE: SILENCE POINT

## MARKERS
- [M] INTENT
- [M] TRIGGER
- [M] RECOGNITION
- [M] FAIL_CASES
- [M] GATES

## [M] INTENT
Провал в тишину может быть целевым драматургическим событием, а не браком.

## [M] TRIGGER
Silence Point активен, если заданы условия проекта (в домене AUD/PIPE):
- RMS drop ≥ 12 dB (или эквивалент)
- сохранён удерживающий якорь: суб/шёпот/пульс
- соблюдён RI gate для ключевого сообщения

## [M] RECOGNITION
Система обязана различать:
- Intentional Silence (LAW_13) vs Technical Dropout (брак)
Критерий: наличие якоря + наличие объявления режима в профиле/пайплайне.

## [M] FAIL_CASES
Брак, если:
- дроп случайный и ломает структуру
- пропадает якорь
- падает RI ниже допустимого

## [M] GATES
- G.SP.INTENT.MISSING = REWORK_REQUIRED если дроп есть, но режим не объявлен
- G.SP.NO_ANCHOR = FAIL если нет удержания
