FILE: UE_V2/03_ENT/30_ORC_ENT/06_WEB_ORC_ENT/03__WEB__A11Y_QA__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 06_WEB_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: WEB_ORC_ENT
UID: UE.V2.ENT.ORC.WEB.A11Y_QA.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: WEB_A11Y_QA
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.WEB.A11Y_QA.001

## [M] PURPOSE
Проверяет доступность: семантика, порядок фокуса, клавиатурная навигация, aria, контраст как principle, reduced motion.
Возвращает A11Y_REPORT с PASS/FAIL и REQUIRED_FIXES.

## [M] INPUTS / OUTPUTS
- Inputs: [HTML_BUNDLE, WEB_BRIEF]
- Outputs: [A11Y_REPORT, FAIL_CODE?]

## [M] CHECKLIST (minimum)
- Semantic landmarks present
- Buttons/links accessible names
- Focus visible and logical order
- Keyboard-only nav possible
- No critical contrast violations (principle-based)
- Motion respects prefers-reduced-motion

## [M] GATES
- PASS: нет критических нарушений
- FAIL: есть REQUIRED_FIXES

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA, CTL]
- Handoff: report -> BLOCK_FACTORY (for fixes) / DEPLOY_HANDOFF

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
