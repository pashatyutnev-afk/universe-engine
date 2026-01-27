# FILE: UE_V2/09_DOM_LOR/02__RI_TO_LANG.md
SCOPE: UE_V2
LAYER: 09_DOM_LOR
DOC_TYPE: SPEC
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.LOR.RI.LANG.001
OWNER: SYSTEM
TITLE: RI → LANGUAGE/COMMUNICATION COLLAPSE

## MARKERS
- [M] INTENT
- [M] STATES
- [M] THRESHOLDS
- [M] OUTPUT_RULES
- [M] FAIL

## [M] INTENT
Закрепить: падение читаемости (RI) = распад языка/связи в каноне.

## [M] STATES
- LANG_OK
- LANG_NOISE
- LANG_FRACTURE
- LANG_SILENCE (ZP coupling)

## [M] THRESHOLDS
- RI_t ≥ 0.70 → LANG_OK
- 0.62 ≤ RI_t < 0.70 → LANG_NOISE
- RI_t < 0.62 → LANG_FRACTURE
- LAW-13 + RMS drop ≥ 12 dB → LANG_SILENCE (overrides)

## [M] OUTPUT_RULES
- LANG_NOISE: фразы короче, смысл “скользит”, но связь есть
- LANG_FRACTURE: обрывки, повтор ключевых слов, невозможность договориться
- LANG_SILENCE: язык временно прекращается, коммуникация через “сигналы” (точка/пульс)

## [M] FAIL
- if lore claims “language collapse” but RI_t is high → REWORK.LOR.RI_MISMATCH
