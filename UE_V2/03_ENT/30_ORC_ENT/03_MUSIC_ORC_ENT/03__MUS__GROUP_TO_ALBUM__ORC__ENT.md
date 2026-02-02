FILE: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/03__MUS__GROUP_TO_ALBUM__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 03_MUSIC_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: MUS_ORC_ENT
UID: UE.V2.ENT.ORC.MUS.GROUP_TO_ALBUM.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_GROUP_TO_ALBUM
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.MUS.GROUP_TO_ALBUM.001

## [M] PURPOSE
Преобразует identity/группу в ALBUM_TOKEN: концепт релиза, настроение, смысловая ось, правила названий, позиционирование.

## [M] INPUTS / OUTPUTS
- Inputs: [ARTIST_ID_TOKEN, MUS_BRIEF, STYLE_ROUTE_TOKEN]
- Outputs: [ALBUM_TOKEN, FAIL_CODE?]

## [M] CORE_RULES
- Не выдумывать “биографию артиста”, если не дано.
- Описывать обложку/визуал как принципы и ограничения, без монтажных решений.
- Держать единый тон и ключевые образы.

## [M] GATES
- PASS: концепт ясен, конфликтов нет
- FAIL: нет достаточных входов для концепта

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA]
- Handoff: ALBUM_TOKEN -> ALBUM_TO_TRACK / METADATA_FACTORY

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
