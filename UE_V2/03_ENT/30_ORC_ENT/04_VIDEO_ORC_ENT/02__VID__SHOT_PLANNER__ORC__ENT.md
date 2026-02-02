FILE: UE_V2/03_ENT/30_ORC_ENT/04_VIDEO_ORC_ENT/02__VID__SHOT_PLANNER__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 04_VIDEO_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: VID_ORC_ENT
UID: UE.V2.ENT.ORC.VID.SHOT_PLANNER.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: VID_SHOT_PLANNER
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.VID.SHOT_PLANNER.001

## [M] PURPOSE
Создаёт SHOT_PLAN: beats по времени, движения камеры как принципы, переходы, места переключения стиля.
Делает план так, чтобы генератор удержал одного героя и не “рассыпался”.

## [M] INPUTS / OUTPUTS
- Inputs: [VID_BRIEF, VID_CONSTRAINTS_LOCK]
- Outputs: [SHOT_PLAN, FAIL_CODE?]

## [M] SHOT_PLAN (schema)
- BEATS: [{t_start, t_end, action, framing, camera_motion_principle, transition}]
- STYLE_TIMELINE: [{t, style_slot}]
- SUBJECT_LOCK_CHECKS
- RISK_NOTES

## [M] GATES
- PASS: тайминг покрывает всю длительность, style switches корректны
- FAIL: конфликт длительности/кол-ва стилей/ограничений

## [M] KB SCOPE
- KB Inputs: [brief + constraints]
- KB Outputs: [shot plan]
- KB Boundaries: [без конкретного монтажа и палитр]

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA]
- Handoff: SHOT_PLAN -> PROMPT_FACTORY / STYLE_PACKAGER

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
