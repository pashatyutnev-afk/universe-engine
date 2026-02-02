FILE: UE_V2/03_ENT/30_ORC_ENT/06_WEB_ORC_ENT/02__WEB__BLOCK_FACTORY__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 06_WEB_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: WEB_ORC_ENT
UID: UE.V2.ENT.ORC.WEB.BLOCK_FACTORY.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: WEB_BLOCK_FACTORY
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.WEB.BLOCK_FACTORY.001

## [M] PURPOSE
Производит self-contained HTML/CSS/JS блок (один файл) по WEB_BRIEF.
По умолчанию добавляет: аккуратные анимации, CTA эффекты, плавный скролл, доступность, адаптивность.

## [M] INPUTS / OUTPUTS
- Inputs: [WEB_BRIEF, WEB_CONSTRAINTS_LOCK]
- Outputs: [BLOCK_SPEC, HTML_BUNDLE, FAIL_CODE?]

## [M] CORE_RULES
- Один файл: HTML + CSS + JS внутри.
- Семантика: section/header/nav/main, кнопки/ссылки по смыслу.
- Доступность: focus-visible, aria-label where needed, reduced motion support.
- UX: hover/focus states, tap targets, keyboard.
- Без конкретных палитр: только принципы контраста, читаемости.
- Если есть бренд-стиль (например, MPS HERO) — применять как “style system”, но не как жёсткую палитру.

## [M] KB SCOPE
- KB Inputs: [brief, style constraints]
- KB Outputs: [html bundle]
- KB Boundaries: [не встраивать внешние библиотеки без запроса]
- KB RAW refs: []

## [M] GATES
- PASS: файл валиден, адаптив есть, базовый a11y ок
- FAIL: не хватает контента/структуры/платформенных ограничений

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA]
- Handoff: HTML_BUNDLE -> WEB_A11Y_QA / WEB_SEO_PACKAGER

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
