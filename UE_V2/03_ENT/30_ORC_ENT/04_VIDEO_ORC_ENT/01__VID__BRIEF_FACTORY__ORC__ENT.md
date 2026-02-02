FILE: UE_V2/03_ENT/30_ORC_ENT/04_VIDEO_ORC_ENT/01__VID__BRIEF_FACTORY__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 04_VIDEO_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: VID_ORC_ENT
UID: UE.V2.ENT.ORC.VID.BRIEF_FACTORY.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: VID_BRIEF_FACTORY
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.VID.BRIEF_FACTORY.001

## [M] PURPOSE
Строит VID_BRIEF: цель клипа, сюжет/сцена, субъект, требования к качеству, длительность, ограничения камеры, стиль-слоты.
Определяет “subject lock” (один и тот же герой/объект) и “visual constraints”.

## [M] INPUTS / OUTPUTS
- Inputs: [TASK_TEXT, USER_CONSTRAINTS?]
- Outputs: [VID_BRIEF, VID_CONSTRAINTS_LOCK, FAIL_CODE?]

## [M] VID_BRIEF (minimum fields)
- DURATION_SEC
- RESOLUTION
- FPS_HINT
- SUBJECT (who/what) + SUBJECT_LOCK_RULES
- SCENE (where/when)
- ACTION (what happens)
- STYLE_SWITCHES (count + timing) optional
- CAMERA_RULES (movement, framing, DoF principles)
- NEGATIVE (what must not appear)
- OUTPUT_TARGET (tool/platform hints)

## [M] GATES
- PASS: brief полный, subject lock ясен
- FAIL: нет ключевых параметров (subject/duration/resolution)

## [M] KB SCOPE
- KB Inputs: [user constraints]
- KB Outputs: [VID_BRIEF]
- KB Boundaries: [без “монтажных решений”]

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA, CTL]
- Handoff: VID_BRIEF -> SHOT_PLANNER / PROMPT_FACTORY

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
