FILE: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/15__MUS__METADATA_FACTORY__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 03_MUSIC_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: MUS_ORC_ENT
UID: UE.V2.ENT.ORC.MUS.METADATA_FACTORY.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_METADATA_FACTORY
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.MUS.METADATA_FACTORY.001

## [M] PURPOSE
Собирает METADATA_PACK: названия, артист, альбом, жанры, теги, кредиты, заметки к релизу, правила капитализации, языковая консистентность.

## [M] INPUTS / OUTPUTS
- Inputs: [ARTIST_ID_TOKEN, ALBUM_TOKEN, TRACK_PLAN, MUS_BRIEF]
- Outputs: [METADATA_PACK, FAIL_CODE?]

## [M] CORE_RULES
- Не добавлять лишние “факты” (лейблы, даты), если не задано.
- Имена и названия должны быть единообразны.
- Поддерживать формат под стриминги: artist/title/album/credits.

## [M] GATES
- PASS: обязательные поля заполнены
- FAIL: конфликт именования или нет базовых входов

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA]
- Handoff: METADATA_PACK -> RELEASE_ASSEMBLER / RELEASE_PACK

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
