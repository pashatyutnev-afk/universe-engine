FILE: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/16__MUS__IDENTITY_BUILD__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 03_MUSIC_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: MUS_ORC_ENT
UID: UE.V2.ENT.ORC.MUS.IDENTITY_BUILD.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_IDENTITY_BUILD
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.MUS.IDENTITY_BUILD.001

## [M] PURPOSE
Строит ARTIST_ID_TOKEN: правила имени, тональность бренда, словарь образов, запреты, формат кредитов.
Нужен, чтобы релизы разных настроений оставались частью одной рамки.

## [M] INPUTS / OUTPUTS
- Inputs: [MUS_BRIEF, CREATIVE_HINTS?]
- Outputs: [ARTIST_ID_TOKEN, FAIL_CODE?]

## [M] GATES
- PASS: рамка ясна, без противоречий
- FAIL: недостаточно входа для консистентного identity

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA]
- Handoff: ARTIST_ID_TOKEN -> GROUP_TO_ALBUM / METADATA_FACTORY

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
