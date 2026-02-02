FILE: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/11__MUS__MIX_FOCUS_LOOP__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 03_MUSIC_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: MUS_ORC_ENT
UID: UE.V2.ENT.ORC.MUS.MIX_FOCUS_LOOP.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_MIX_FOCUS_LOOP
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.MUS.MIX_FOCUS_LOOP.001

## [M] PURPOSE
Цикл улучшения микса как принципов: баланс, читаемость вокала, динамика, плотность, удар, ширина.
Не задаёт точные значения, только направляющие и риски.

## [M] INPUTS / OUTPUTS
- Inputs: [STYLE_ROUTE_TOKEN, GEN_OUTPUT_NOTES?]
- Outputs: [MIX_LOOP_NOTES, MIX_TARGETS_UPDATE?, FAIL_CODE?]

## [M] GATES
- PASS: есть конкретные рекомендации и критерии “лучше/хуже”
- FAIL: отсутствуют данные о текущем результате

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA]
- Handoff: notes -> TRACK_BUILD_STEP / MERGE_SYNTHESIS

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
