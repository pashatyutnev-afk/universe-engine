FILE: UE_V2/03_ENT/30_ORC_ENT/04_VIDEO_ORC_ENT/03__VID__PROMPT_FACTORY__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 04_VIDEO_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: VID_ORC_ENT
UID: UE.V2.ENT.ORC.VID.PROMPT_FACTORY.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: VID_PROMPT_FACTORY
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.VID.PROMPT_FACTORY.001

## [M] PURPOSE
Строит PROMPT_PACK для выбранного генератора видео: общий промпт, промпты по шотам/сегментам, негативы, параметры.
Держит subject lock и не допускает противоречий.

## [M] INPUTS / OUTPUTS
- Inputs: [VID_BRIEF, SHOT_PLAN, STYLE_PACK?]
- Outputs: [PROMPT_PACK, FAIL_CODE?]

## [M] PROMPT_PACK (sections)
- GLOBAL_PROMPT
- SHOT_PROMPTS: [{beat_id, prompt}]
- NEGATIVE_PROMPT
- PARAMS (resolution, duration, fps, camera principles)
- LOCKS (subject lock phrases)

## [M] GATES
- PASS: промпты покрывают все биты и не конфликтуют
- FAIL: нет ключевых параметров или конфликт constraints

## [M] KB SCOPE
- KB Inputs: [brief/shot plan/style pack]
- KB Outputs: [prompt pack]
- KB Boundaries: [без “добавления объектов” вне входа]

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA]
- Handoff: PROMPT_PACK -> QA_CHECKS / EXPORT_HANDOFF

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
