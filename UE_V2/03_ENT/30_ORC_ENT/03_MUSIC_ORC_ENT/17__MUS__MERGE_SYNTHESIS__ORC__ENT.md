FILE: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/17__MUS__MERGE_SYNTHESIS__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 03_MUSIC_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: MUS_ORC_ENT
UID: UE.V2.ENT.ORC.MUS.MERGE_SYNTHESIS.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_MERGE_SYNTHESIS
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.MUS.MERGE_SYNTHESIS.001

## [M] PURPOSE
Сводит варианты в один финал: выбирает лучшие элементы (хук, интро, плотность, эмоция) и формирует MERGE_TOKEN.
Работает только по заметкам/критериям, не “на вкус без входа”.

## [M] INPUTS / OUTPUTS
- Inputs: [VARIANT_NOTES, ACCEPT_CRITERIA, STYLE_ROUTE_TOKEN]
- Outputs: [MERGE_TOKEN, FAIL_CODE?]

## [M] GATES
- PASS: критерии выбора ясны, конфликтов нет
- FAIL: нет критериев, нет данных о вариантах

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA]
- Handoff: MERGE_TOKEN -> RELEASE_ASSEMBLER / RELEASE_PACK

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
