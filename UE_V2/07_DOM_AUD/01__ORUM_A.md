# FILE: UE_V2/07_DOM_AUD/01__ORUM_A.md
SCOPE: UE_V2
LAYER: 07_DOM_AUD
DOC_TYPE: ENGINE_CONTRACT
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.AUD.ORUMA.001
OWNER: SYSTEM
TITLE: ORUM-A (READABILITY / VOCAL SIGNATURE)

## MARKERS
- [M] INTENT
- [M] INPUTS
- [M] OUTPUTS
- [M] RULES
- [M] GATES

## [M] INTENT
Сделать вокал “читаемым” без убийства характера. Это микроконтур: артикуляция, маскировка, близость/воздух.

## [M] INPUTS
- vocal stem or vocal target description
- arrangement context (rap vs melodic sections)
- required RI threshold (default 0.62)

## [M] OUTPUTS
- section map (A/B)
- readability plan (freq control + dynamics + space)
- RI_t estimate per section (target/accept)

## [M] RULES
- rap (B): сухо/близко, минимум хвостов, артикуляция впереди
- melodic (A): больше “air”, ширина/хорал, но без маскировки текста
- конфликт зона: 250–500 Hz (low-mid mud). вокал не должен тонуть в гитарах
- “clean mix”: separation > saturation; грязь допускается только как WTI (LAW-07) и только по правилам профиля
- если “silence point” (LAW-13) активен: тишина считается художественным режимом при наличии маркера (см. CAL_ANOM)

## [M] GATES
- RI_t >= THR.RI.MIN (default 0.62) в секциях с текстом
- маскировка вокала 250–500 → запрещено (см. FAIL_AUD)
