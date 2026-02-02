FILE: UE_V2/03_ENT/30_ORC_ENT/04_VIDEO_ORC_ENT/05__VID__QA_CHECKS__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 04_VIDEO_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: VID_ORC_ENT
UID: UE.V2.ENT.ORC.VID.QA_CHECKS.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: VID_QA_CHECKS
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.VID.QA_CHECKS.001

## [M] PURPOSE
QA чеклист видео-артефакта: соответствие brief, subject lock, непротиворечивость промптов, тайминг стилей, тех. параметры.
Выдаёт QA_REPORT с PASS/FAIL и REQUIRED_FIXES.

## [M] INPUTS / OUTPUTS
- Inputs: [VID_BRIEF, SHOT_PLAN, PROMPT_PACK, STYLE_PACK]
- Outputs: [QA_REPORT, FAIL_CODE?]

## [M] QA_CHECKLIST (minimum)
- Subject lock rules present and repeated in prompts
- Shot plan covers full duration
- Style timeline matches required switch count
- Prompts do not introduce new subjects/objects
- Params present (duration/resolution/fps)
- Constraints consistent, no contradictions

## [M] GATES
- PASS: нет блокирующих нарушений
- FAIL: есть REQUIRED_FIXES

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [CTL]
- Handoff: QA_REPORT -> EXPORT_HANDOFF

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
