FILE: UE_V2/03_ENT/60_QA_ENT/30_WEB_QA_ENT/90__WEB__A11Y_AUDIT__QA__ENT.md
SCOPE: UE_V2 / 03_ENT / 60_QA_ENT / 30_WEB_QA_ENT
DOC_TYPE: QA_ENTITY
DOMAIN: WEB_QA_ENT
UID: UE.V2.ENT.QA.WEB.A11Y_AUDIT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: QA_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: WEB_A11Y_AUDIT_QA
- ENTITY_CLASS: QA
- UID: UE.V2.ENT.QA.WEB.A11Y_AUDIT.001

## [M] PURPOSE
Аудит a11y для web bundles (self-contained HTML блок/страница):
проверяет клавиатуру, фокус, доступные имена, семантику и motion-guard.
Работает по тексту/структуре bundle и notes, без внешних инструментов.

## [M] SCOPE
- TARGET_DOMAIN: WEB
- APPLIES_TO: [HTML_BUNDLE, WEB_BRIEF?]
- NON_GOALS: [полный WCAG аудит, дизайн-палитры]

## [M] INPUTS / OUTPUTS
- Inputs:
  - HTML_BUNDLE?: html/css/js
  - WEB_BRIEF?: цель/CTA/ограничения
- Outputs:
  - QA_DECISION: PASS|WARN|ASK|FAIL
  - QA_FINDINGS: [findings]
  - REQUIRED_FIXES: [fixes]
  - ISSUES?: [issue tokens]
  - FAIL_CODE?: UE.FAIL.INPUT_ABSENT|UE.FAIL.GATE_FAIL|UE.FAIL.RULE_VIOLATION

## [M] CHECKS (minimum)
- C1: Keyboard access
  - All interactive elements reachable and usable via keyboard.
- C2: Visible focus
  - Focus indicator visible (:focus-visible or equivalent).
- C3: Accessible names
  - Buttons/links have text or aria-label.
- C4: Semantics
  - Avoid div-button without role/aria; headings are logical.
- C5: Motion guard
  - If animations exist, respect prefers-reduced-motion.

## [M] DECISION_MATRIX
- IF HTML_BUNDLE отсутствует -> ASK (V.WEB.A11Y.NO_BUNDLE)
- IF keyboard fail -> FAIL (UE.FAIL.RULE_VIOLATION; V.WEB.A11Y.KEYBOARD_FAIL)
- IF no focus visible -> FAIL (UE.FAIL.RULE_VIOLATION; V.WEB.A11Y.NO_FOCUS)
- IF no accessible names -> FAIL (UE.FAIL.RULE_VIOLATION; V.WEB.A11Y.NO_NAME)
- IF semantics weak -> WARN (V.WEB.A11Y.SEMANTICS_WARN)
- IF motion guard missing -> WARN (V.WEB.A11Y.MOTION_WARN)
- ELSE -> PASS

## [M] VIOLATIONS
- V.WEB.A11Y.NO_BUNDLE
- V.WEB.A11Y.KEYBOARD_FAIL
- V.WEB.A11Y.NO_FOCUS
- V.WEB.A11Y.NO_NAME
- V.WEB.A11Y.SEMANTICS_WARN
- V.WEB.A11Y.MOTION_WARN

## [M] FAIL_CODES
- UE.FAIL.INPUT_ABSENT
- UE.FAIL.RULE_VIOLATION
- UE.FAIL.GATE_FAIL

## [M] REQUIRED_FIXES (style)
- 1–7 пунктов, каждый “что исправить” + “где”.
- Без лишней лирики, только действия.

## [M] KB SCOPE
- KB Inputs: [html bundle, brief]
- KB Outputs: [a11y audit findings + fixes]
- KB Boundaries: [не добавлять внешний контент]
- KB RAW refs: []

## [M] GATES
- PASS if: keyboard+focus+names ok
- FAIL if: any critical minimum violated

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, CTL_ENT, VAL_ENT]
- Handoff rules:
  - ASK -> запросить bundle
  - WARN -> вернуть fixes и recheck
  - FAIL -> стоп до исправления
