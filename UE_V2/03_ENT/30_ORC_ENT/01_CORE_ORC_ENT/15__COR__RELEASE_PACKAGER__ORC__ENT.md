FILE: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/15__COR__RELEASE_PACKAGER__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 01_CORE_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: COR_ORC_ENT
UID: UE.V2.ENT.ORC.COR.RELEASE_PACKAGER.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: COR_RELEASE_PACKAGER
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.COR.RELEASE_PACKAGER.001

## [M] PURPOSE
Упаковывает выдачу в OUTPUT_PACK: кратко что сделано, outputs, логи, gates.
Формат стабильный и детерминированный.

## [M] INPUTS / OUTPUTS
- Inputs: [FINAL_STATUS, PIPE_OUTPUTS, RUN_LOG, DECISION_LOG?]
- Outputs: [OUTPUT_PACK]

## [M] CORE_RULES
- OUTPUT_PACK должен включать: SUMMARY, OUTPUTS, GATES, LOGS.
- Без RAW внутри, только KEYS и токены.

## [M] INTERFACES (RAW only)
- Entry points (RAW):
- Dependencies (RAW):

## [M] KB SCOPE
- KB Inputs: [output pack template]
- KB Outputs: [OUTPUT_PACK]
- KB Boundaries: [no extra content]

## [M] GATES
- PASS: OUTPUT_PACK сформирован

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA]
- Handoff: output -> caller realm

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
