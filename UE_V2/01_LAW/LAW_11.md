# FILE: UE_V2/01_LAW/LAW_11.md
SCOPE: UE_V2
LAYER: 01_LAW
DOC_TYPE: LAW
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.LAW.11.001
OWNER: SYSTEM
TITLE: LOW-END ANCHOR (TIGHT LOW END)

## MARKERS
- [M] INTENT
- [M] RULES
- [M] DEFAULT_ANCHORS
- [M] GATES

## [M] INTENT
Низ должен быть управляемым, плотным, без расплыва. Это основа “удержания”.

## [M] RULES
- Низ не должен маскировать вокал и атаку бочки/снейра
- Саб-якорь фиксируется (частотный диапазон задаёт домен)
- Любой дроп (LAW_08/LAW_13) должен сохранять хотя бы один низовой якорь

## [M] DEFAULT_ANCHORS
- Sub Anchor: 30–60 Гц
- Tightness: контроль хвостов и лишней энергии ниже 120 Гц

## [M] GATES
- G.LOW.MUD = REWORK_REQUIRED если низ “размазывает” или забивает слова
- G.LOW.NO_ANCHOR = FAIL если в ключевых секциях нет якоря
