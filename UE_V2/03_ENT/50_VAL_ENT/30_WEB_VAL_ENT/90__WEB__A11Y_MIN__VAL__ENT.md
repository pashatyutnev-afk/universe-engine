FILE: UE_V2/03_ENT/50_VAL_ENT/30_WEB_VAL_ENT/90__WEB__A11Y_MIN__VAL__ENT.md
SCOPE: UE_V2 / 03_ENT / 50_VAL_ENT / 30_WEB_VAL_ENT
DOC_TYPE: VAL_ENTITY
DOMAIN: WEB_VAL_ENT
UID: UE.V2.ENT.VAL.WEB.A11Y_MIN.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: VAL_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: WEB_A11Y_MIN_VAL
- ENTITY_CLASS: VAL
- UID: UE.V2.ENT.VAL.WEB.A11Y_MIN.001

## [M] PURPOSE
Проверяет минимальный a11y для web артефактов (self-contained HTML блок/страница):
- клавиатурная доступность интерактивов,
- видимый фокус,
- корректные роли/семантика,
- доступные имена кнопок/ссылок,
- базовое уважение prefers-reduced-motion.

## [M] SCOPE
- TARGET_DOMAIN: WEB
- APPLIES_TO: [HTML_BUNDLE, WEB_BRIEF?]
- NON_GOALS: [полный WCAG аудит, дизайн-палитры, контент вместо автора]

## [M] INPUTS / OUTPUTS
- Inputs:
  - HTML_BUNDLE?: html/css/js (самодостаточно)
  - WEB_BRIEF?: секции/CTA/ограничения
- Outputs:
  - VAL_DECISION: PASS|FAIL|WARN|ASK
  - VAL_FINDINGS: [short findings]
  - REQUIRED_FIXES: [minimal fixes]
  - VIOLATIONS: [violation ids]
  - FAIL_CODE?: UE.FAIL.INPUT_ABSENT|UE.FAIL.GATE_FAIL|UE.FAIL.RULE_VIOLATION

## [M] CHECKS
- C1: Есть интерактивы? Если да — доступны с клавиатуры (Evidence: semantic elements or tabindex usage).
- C2: Есть видимый focus state (Evidence: :focus-visible styles or equivalent).
- C3: У кнопок/ссылок есть доступные имена (Evidence: visible text or aria-label).
- C4: Семантика не сломана (no div-button без роли/aria).
- C5: Если есть анимации — уважать prefers-reduced-motion (Evidence: media query guard).

## [M] EVIDENCE_REQUIREMENTS
- E1: PASS возможен только при наличии HTML_BUNDLE.
- E2: Если нет HTML_BUNDLE -> ASK.
- E3: Критические нарушения (клавиатура/фокус/имена) -> FAIL.
- E4: Некритические (неидеальная семантика) -> WARN.

## [M] DECISION_MATRIX
- IF HTML_BUNDLE отсутствует -> ASK (V.WEB.A11Y.NO_BUNDLE)
- IF интерактивы не доступны с клавиатуры -> FAIL (UE.FAIL.RULE_VIOLATION; V.WEB.A11Y.KEYBOARD_FAIL)
- IF нет focus-visible -> FAIL (UE.FAIL.RULE_VIOLATION; V.WEB.A11Y.NO_FOCUS)
- IF у кнопок нет имени -> FAIL (UE.FAIL.RULE_VIOLATION; V.WEB.A11Y.NO_NAME)
- IF семантика слабая -> WARN (V.WEB.A11Y.SEMANTICS_WARN)
- IF нет reduced-motion guards при тяжёлой анимации -> WARN (V.WEB.A11Y.MOTION_WARN)
- ELSE -> PASS

## [M] VIOLATIONS
- V.WEB.A11Y.NO_BUNDLE — нет HTML_BUNDLE
- V.WEB.A11Y.KEYBOARD_FAIL — интерактивы недоступны с клавиатуры
- V.WEB.A11Y.NO_FOCUS — нет видимого фокуса
- V.WEB.A11Y.NO_NAME — нет доступных имён
- V.WEB.A11Y.SEMANTICS_WARN — слабая семантика/роли
- V.WEB.A11Y.MOTION_WARN — нет prefers-reduced-motion защиты

## [M] FAIL_CODES
- UE.FAIL.INPUT_ABSENT
- UE.FAIL.RULE_VIOLATION
- UE.FAIL.GATE_FAIL

## [M] KB SCOPE
- KB Inputs: [html bundle, brief]
- KB Outputs: [a11y findings + fixes]
- KB Boundaries: [не придумывать контент; не навязывать стиль]
- KB RAW refs: []

## [M] GATES
- PASS if:
  - интерактивы доступны с клавиатуры
  - видимый фокус присутствует
  - имена элементов доступны
- FAIL if:
  - любой критический a11y минимум нарушен

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, CTL_ENT, QA_ENT]
- Handoff rules:
  - ASK -> запросить HTML_BUNDLE
  - WARN -> вернуть REQUIRED_FIXES и продолжить
  - FAIL -> стоп до исправления
