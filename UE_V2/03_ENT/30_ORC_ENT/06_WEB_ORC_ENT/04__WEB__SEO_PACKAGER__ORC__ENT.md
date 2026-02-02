FILE: UE_V2/03_ENT/30_ORC_ENT/06_WEB_ORC_ENT/04__WEB__SEO_PACKAGER__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 06_WEB_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: WEB_ORC_ENT
UID: UE.V2.ENT.ORC.WEB.SEO_PACKAGER.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: WEB_SEO_PACKAGER
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.WEB.SEO_PACKAGER.001

## [M] PURPOSE
Формирует SEO_PACK: meta title/description (как предложения), структура H1-H3, json-ld рекомендации, внутренние ссылки.
Без keyword-stuffing и без обещаний, которые не подтверждены входом.

## [M] INPUTS / OUTPUTS
- Inputs: [WEB_BRIEF, HTML_BUNDLE?]
- Outputs: [SEO_PACK, FAIL_CODE?]

## [M] SEO_PACK (minimum)
- TITLE_SUGGESTIONS
- META_DESCRIPTION_SUGGESTIONS
- HEADING_MAP
- INTERNAL_LINK_NOTES
- JSON_LD_HINTS (type suggestions, fields list)

## [M] GATES
- PASS: пакет не противоречит brief и не “врет”
- FAIL: не хватает информации о странице/товаре/услуге

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA]
- Handoff: SEO_PACK -> DEPLOY_HANDOFF

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
