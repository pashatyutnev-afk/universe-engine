FILE: UE_V2/03_ENT/40_CTL_ENT/30_WEB_CONTROLLERS_CTL_ENT/00__PIPELINE_CONTRACT__DOC__CTL__ENT.md
SCOPE: UE_V2 / 03_ENT / 40_CTL_ENT / 30_WEB_CONTROLLERS_CTL_ENT
DOC_TYPE: PIPELINE_CONTRACT
DOMAIN: WEB_CTL_ENT
UID: UE.V2.ENT.PIPE.WEB_CTL_ENT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: CTL_ENT
NAV_RULE: Contract has no RAW

---

## [M] PURPOSE
PIPELINE_CONTRACT — роутер WEB контроллеров CTL.
В этом реалме сейчас одна библиотека lint-правил (для веб-блоков и doc-like страниц).
RAW не хранит: работает через KEY и INDEX_MANIFEST.

## [M] HARD_RULES
- RAW запрещён внутри CONTRACT.
- Все ссылки: только KEYS.
- MODE REPO: никаких правок репозитория.
- Выход: CTL_CHAIN_PLAN (KEYS) + APPLY_NOTES.

## [M] REQUIRED_KEYS
- INDEX_MANIFEST
- PIPELINE_CONTRACT
- CTL.WEB.DOC_LINT_RULES_LIBRARY

## [M] DEFAULT_CHAIN_PLAN (keys)
- ALWAYS:
  - CTL.WEB.DOC_LINT_RULES_LIBRARY

## [M] APPLY_NOTES
- Применять lint-правила на уровне:
  - self-contained HTML bundle (один файл)
  - SEO meta / headings map
  - a11y минимум (keyboard/focus/semantics)
- Lint не добавляет контент. Он выявляет нарушения и возвращает REQUIRED_FIXES.

## [M] STEP-RUN
- STEP: S0
  GOAL: Return default chain keys
  INPUTS: [WEB_BRIEF?, HTML_BUNDLE?]
  TARGETS: [INDEX_MANIFEST]
  ACTIONS:
    - Output CTL_CHAIN_PLAN = [CTL.WEB.DOC_LINT_RULES_LIBRARY]
  OUTPUTS: [CTL_CHAIN_PLAN, APPLY_NOTES]
  CHECKS: [REQUIRED_KEYS_PRESENT]
  FAIL: UE.FAIL.MISSING_KEY
  NEXT: "го"

- STEP: S1
  GOAL: Aggregate lint findings into a single decision
  INPUTS: [LINT_FINDINGS?]
  TARGETS: []
  ACTIONS:
    - If critical violations -> FAIL
    - If missing required sections -> WARN/ASK
  OUTPUTS: [CTL_AGG_DECISION, REQUIRED_FIXES, FINDINGS]
  CHECKS: [DECISION_PRODUCED]
  FAIL: UE.FAIL.GATE_FAIL
  NEXT: "го"

## [M] FAIL_CODES
- UE.FAIL.MISSING_KEY
- UE.FAIL.GATE_FAIL
- UE.FAIL.RULE_VIOLATION
