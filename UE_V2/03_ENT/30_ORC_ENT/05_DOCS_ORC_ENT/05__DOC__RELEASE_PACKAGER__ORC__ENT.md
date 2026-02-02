FILE: UE_V2/03_ENT/30_ORC_ENT/05_DOCS_ORC_ENT/05__DOC__RELEASE_PACKAGER__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 05_DOCS_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: DOC_ORC_ENT
UID: UE.V2.ENT.ORC.DOC.RELEASE_PACKAGER.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: DOC_RELEASE_PACKAGER
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.DOC.RELEASE_PACKAGER.001

## [M] PURPOSE
Пакует DOC_FINAL в OUTPUT_PACK: summary, outputs, gates, QA, next action.
В режиме no-edit — без записи в репо, только готовый блок для вставки/публикации.

## [M] INPUTS / OUTPUTS
- Inputs: [DOC_FINAL, QA_REPORT, KB_SCOPE_TOKEN]
- Outputs: [OUTPUT_PACK, FAIL_CODE?]

## [M] OUTPUT_PACK (required)
- SUMMARY
- OUTPUTS (doc content reference)
- GATES (pass/fail + reasons)
- QA_REPORT (short)
- NEXT_ACTION

## [M] GATES
- PASS: QA_PASS и output pack сформирован
- FAIL: QA_FAIL или отсутствуют артефакты

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA, CTL]
- Handoff: OUTPUT_PACK -> user / caller realm

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
