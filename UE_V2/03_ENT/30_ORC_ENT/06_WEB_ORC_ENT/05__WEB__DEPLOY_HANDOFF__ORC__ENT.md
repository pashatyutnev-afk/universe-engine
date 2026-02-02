FILE: UE_V2/03_ENT/30_ORC_ENT/06_WEB_ORC_ENT/05__WEB__DEPLOY_HANDOFF__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 06_WEB_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: WEB_ORC_ENT
UID: UE.V2.ENT.ORC.WEB.DEPLOY_HANDOFF.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: WEB_DEPLOY_HANDOFF
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.WEB.DEPLOY_HANDOFF.001

## [M] PURPOSE
Готовит DEPLOY_HANDOFF_TOKEN: куда вставить блок, что проверить, как откатить, какие устройства протестить, как валидировать SEO/a11y.
В режиме no-edit — только инструкция и структура.

## [M] INPUTS / OUTPUTS
- Inputs: [HTML_BUNDLE, A11Y_REPORT, SEO_PACK, PLATFORM_HINT?]
- Outputs: [DEPLOY_HANDOFF_TOKEN, OUTPUT_PACK, FAIL_CODE?]

## [M] DEPLOY_HANDOFF_TOKEN (minimum)
- INSERT_INSTRUCTIONS
- TEST_CHECKLIST (desktop/mobile, keyboard, performance)
- ROLLBACK_PLAN
- SEO_VERIFICATION (basic)
- A11Y_VERIFICATION (basic)
- NEXT_ACTION

## [M] GATES
- PASS: handoff полный и нет блокирующих QA
- FAIL: критический a11y fail или отсутствует bundle

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA, CTL]
- Handoff: OUTPUT_PACK -> user / caller realm

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
