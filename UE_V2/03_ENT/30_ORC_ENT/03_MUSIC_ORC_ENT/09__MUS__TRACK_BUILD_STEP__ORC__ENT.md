FILE: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/09__MUS__TRACK_BUILD_STEP__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 03_MUSIC_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: MUS_ORC_ENT
UID: UE.V2.ENT.ORC.MUS.TRACK_BUILD_STEP.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_TRACK_BUILD_STEP
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.MUS.TRACK_BUILD_STEP.001

## [M] PURPOSE
Определяет итерационный шаг сборки трека: generate -> review notes -> adjust prompt -> regenerate.
Не генерирует сам, а формирует STEP_TOKEN и критерии принятия.

## [M] INPUTS / OUTPUTS
- Inputs: [PROMPT_PACK, QA_TARGETS?]
- Outputs: [STEP_TOKEN, ACCEPT_CRITERIA, FAIL_CODE?]

## [M] CORE_RULES
- Один шаг — один вывод генератора и одно решение accept/retry.
- Не менять constraints lock без нового входа пользователя.

## [M] GATES
- PASS: step токен сформирован, критерии ясны
- FAIL: отсутствует PROMPT_PACK

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA, CTL]
- Handoff: STEP_TOKEN -> HOOK_FOCUS_LOOP / MIX_FOCUS_LOOP / MERGE_SYNTHESIS

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
