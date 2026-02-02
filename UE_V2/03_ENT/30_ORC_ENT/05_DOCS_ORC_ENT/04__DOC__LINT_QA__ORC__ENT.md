FILE: UE_V2/03_ENT/30_ORC_ENT/05_DOCS_ORC_ENT/04__DOC__LINT_QA__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 05_DOCS_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: DOC_ORC_ENT
UID: UE.V2.ENT.ORC.DOC.LINT_QA.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: DOC_LINT_QA
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.DOC.LINT_QA.001

## [M] PURPOSE
Прогоняет линтер и QA по документу: хедер, секции, RAW-only интерфейсы, KB SCOPE, чистота ролей, отсутствие противоречий.
Возвращает QA_REPORT с REQUIRED_FIXES.

## [M] INPUTS / OUTPUTS
- Inputs: [DOC_DRAFT, KB_SCOPE_TOKEN]
- Outputs: [QA_REPORT, DOC_FINAL, FAIL_CODE?]

## [M] LINT_CHECKLIST (minimum)
- Header fields present and ordered
- REQUIRED_SECTIONS present
- INTERFACES contain RAW only (no PATH links)
- KB SCOPE present and aligned
- SPC PEER ROLES present (NON-ENG) and not mixed into ENG sections
- VISUAL section has constraints/risks only
- Color described as principles, not palette

## [M] GATES
- PASS: QA_REPORT PASS
- FAIL: QA_REPORT FAIL + REQUIRED_FIXES

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA, CTL]
- Handoff: DOC_FINAL -> RELEASE_PACKAGER

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
