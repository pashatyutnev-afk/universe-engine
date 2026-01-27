# FILE: UE_V2/01_LAW/LAW_10.md
SCOPE: UE_V2
LAYER: 01_LAW
DOC_TYPE: LAW
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.LAW.10.001
OWNER: SYSTEM
TITLE: NON-CLONE VARIANCE (DNA BUT NOT CLONES)

## MARKERS
- [M] INTENT
- [M] DEFINITIONS
- [M] RULES
- [M] GATES

## [M] INTENT
Треки одной сущности звучат как один массив данных, но не как частотные клоны.

## [M] DEFINITIONS
- DNA = общий “семейный” профиль (баланс, динамика, низ, характер)
- Variance = допустимые отклонения внутри семейства

## [M] RULES
- Семейные таргеты задаются доменом AUD (Master Targets)
- Допускается локальная вариативность, если RI сохраняется и нет прямого совпадения спектральных “отпечатков”
- Если треки слишком похожи → обязателен разнос ΔAIR/ΔLM или аранжа

## [M] GATES
- G.CLONE.SUSPECT = REWORK_REQUIRED если совпадение отпечатка слишком высокое
- G.VAR.NO_DNA = FAIL если трек вылетел из семейных таргетов
