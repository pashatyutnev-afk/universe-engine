FILE: UE_V2/03_ENT/30_ORC_ENT/06_WEB_ORC_ENT/01__WEB__BRIEF_FACTORY__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 06_WEB_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: WEB_ORC_ENT
UID: UE.V2.ENT.ORC.WEB.BRIEF_FACTORY.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: WEB_BRIEF_FACTORY
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.WEB.BRIEF_FACTORY.001

## [M] PURPOSE
Строит WEB_BRIEF: цель блока/страницы, аудитория, сообщение, секции, CTA, ограничения платформы, требования к адаптиву и UX.

## [M] INPUTS / OUTPUTS
- Inputs: [TASK_TEXT, PLATFORM_HINT?, CONTENT_HINTS?]
- Outputs: [WEB_BRIEF, WEB_CONSTRAINTS_LOCK, FAIL_CODE?]

## [M] WEB_BRIEF (minimum fields)
- GOAL
- AUDIENCE
- SECTIONS (ordered)
- CTA (label + intent)
- PLATFORM_CONSTRAINTS (e.g. builder, embed rules)
- RESPONSIVE_RULES (breakpoints as principles)
- UX_DEFAULTS (smooth scroll, microinteractions, motion limits)
- ACCESSIBILITY_MIN (keyboard/focus/aria)
- SEO_HINTS (keywords as hints, not stuffing)

## [M] KB SCOPE
- KB Inputs: [task + platform hints]
- KB Outputs: [web brief token]
- KB Boundaries: [не добавлять “факты о бизнесе”, если не дано]
- KB RAW refs: []

## [M] GATES
- PASS: brief ясен и выполним
- FAIL: отсутствует цель/платформа/контент

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA, CTL]
- Handoff: WEB_BRIEF -> WEB_BLOCK_FACTORY

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
