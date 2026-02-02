FILE: UE_V2/03_ENT/40_CTL_ENT/30_WEB_CONTROLLERS_CTL_ENT/90__DOC__LINT_RULES_LIBRARY__CTL__ENT.md
SCOPE: UE_V2 / 03_ENT / 40_CTL_ENT / 30_WEB_CONTROLLERS_CTL_ENT
DOC_TYPE: CTL_ENTITY
DOMAIN: WEB_CTL_ENT
UID: UE.V2.ENT.CTL.WEB.DOC_LINT_RULES_LIBRARY.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: CTL_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: WEB_DOC_LINT_RULES_LIBRARY_CTL
- ENTITY_CLASS: CTL
- UID: UE.V2.ENT.CTL.WEB.DOC_LINT_RULES_LIBRARY.001

## [M] PURPOSE
Библиотека lint-правил для WEB артефактов (блоки/страницы/встраиваемые HTML).
Проверяет структуру, самодостаточность, базовый a11y и SEO-минимум, чтобы не выпускать “кривые” блоки.

## [M] SCOPE
- TARGET_DOMAIN: WEB
- APPLIES_TO: [HTML_BUNDLE, WEB_BRIEF, SEO_PACK?, A11Y_REPORT?]
- NON_GOALS: [дизайн-палитры, монтажные решения, написание контента вместо пользователя]

## [M] INPUTS / OUTPUTS
- Inputs:
  - HTML_BUNDLE?: self-contained html/css/js
  - WEB_BRIEF?: цель/секции/CTA/ограничения платформы
  - SEO_PACK?: meta suggestions / headings
- Outputs:
  - CTL_DECISION: PASS|WARN|ASK|FAIL
  - CTL_FINDINGS: [findings]
  - REQUIRED_FIXES: [fixes]
  - FAIL_CODE?: UE.FAIL.RULE_VIOLATION|UE.FAIL.INPUT_ABSENT

## [M] RULESET (lint checks library)

### [L] STRUCTURE_MIN
- R.S1: Есть понятная секционная структура (section/header/main) или эквивалент.
- R.S2: Есть один главный заголовок (H1) или явная причина его отсутствия.
- R.S3: CTA присутствует, если он заявлен в brief.

### [L] SELF_CONTAINED_MIN
- R.C1: Один файл: HTML+CSS+JS внутри (без внешних библиотек), если не задано иначе.
- R.C2: Нет ссылок на локальные ассеты, которые не переданы (если есть — дать список).

### [L] A11Y_MIN
- R.A1: Все интерактивные элементы доступны с клавиатуры.
- R.A2: Есть видимый focus state (focus-visible).
- R.A3: У кнопок/ссылок есть доступные имена (текст/aria-label).
- R.A4: Уважать prefers-reduced-motion (если есть анимации).

### [L] SEO_MIN
- R.E1: Title/description предложения не противоречат brief (без “обещаний”).
- R.E2: Заголовки идут по логике (H1->H2->H3), без хаоса.
- R.E3: Нет keyword stuffing.

### [L] POLICY_MIN
- R.P1: Не вставлять “гарантия/гарантийные обещания” как факт, если это не целевой блок «Почему покупают у нас».
- R.P2: Не добавлять ссылки/источники в итоговый пользовательский вывод, если не запрошено.

## [M] DECISION_MATRIX
- IF HTML_BUNDLE отсутствует -> ASK (нужен HTML_BUNDLE)
- IF нарушен SELF_CONTAINED_MIN (критично) -> FAIL (UE.FAIL.RULE_VIOLATION)
- IF нарушен A11Y_MIN (критично: клавиатура/фокус) -> FAIL (UE.FAIL.RULE_VIOLATION)
- IF нарушен STRUCTURE_MIN -> WARN (дать REQUIRED_FIXES)
- IF нарушен SEO_MIN -> WARN
- ELSE -> PASS

## [M] VIOLATIONS
- V.WEB.NO_BUNDLE — нет HTML_BUNDLE
- V.WEB.NOT_SELF_CONTAINED — внешние зависимости без указания
- V.WEB.A11Y_CRITICAL — критический a11y провал
- V.WEB.STRUCTURE — нарушена структура секций/заголовков
- V.WEB.SEO_MIN — SEO минимум не соблюдён
- V.WEB.POLICY_COPY — добавлены неподтверждённые обещания

## [M] FAIL_CODES
- UE.FAIL.INPUT_ABSENT
- UE.FAIL.RULE_VIOLATION
- UE.FAIL.GATE_FAIL

## [M] KB SCOPE
- KB Inputs: [brief/bundle/seo hints]
- KB Outputs: [lint findings + required fixes]
- KB Boundaries: [не придумывать факты/обещания; не добавлять внешние ссылки]
- KB RAW refs: []

## [M] GATES
- PASS if:
  - self-contained минимум соблюдён
  - критические a11y проверки пройдены
- FAIL if:
  - нет bundle или есть критические нарушения self-contained/a11y

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, QA_ENT, VAL_ENT]
- Handoff rules:
  - WARN -> вернуть REQUIRED_FIXES и дать патч-пункты
  - ASK -> запросить минимальный вход (bundle/brief)
  - FAIL -> стоп до исправления
