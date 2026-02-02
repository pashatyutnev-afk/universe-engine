FILE: UE_V2/03_ENT/40_CTL_ENT/00_TEMPLATES_CTL_ENT/00__PIPELINE_CONTRACT__TPL__CTL__ENT.md
SCOPE: UE_V2 / 03_ENT / 40_CTL_ENT / 00_TEMPLATES_CTL_ENT
DOC_TYPE: PIPELINE_CONTRACT
DOMAIN: TPL_CTL_ENT
UID: UE.V2.ENT.PIPE.TPL_CTL_ENT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: CTL_ENT
NAV_RULE: Contract has no RAW

---

## [M] PURPOSE
PIPELINE_CONTRACT — навигатор шаблонов CTL.
Принимает запрос “какой документ нужен” и возвращает TEMPLATE_KEY (KEYS only).
RAW не хранит: резолвится через INDEX_MANIFEST.

## [M] HARD_RULES
- RAW запрещён внутри CONTRACT.
- Все ссылки: только KEYS.
- Любое открытие: KEY -> INDEX_MANIFEST -> RAW -> open.
- MODE REPO: никаких правок репозитория.

## [M] REQUIRED_KEYS
- INDEX_MANIFEST
- PIPELINE_CONTRACT
- TPL.CTL_ENTITY
- TPL.CTL_BLOCKER
- TPL.INDEX_MANIFEST_CTL

## [M] ROUTES (keys only)
- IF need "CTL entity/controller doc" -> TPL.CTL_ENTITY
- IF need "hard stop / blocker / violation policy doc" -> TPL.CTL_BLOCKER
- IF need "INDEX_MANIFEST for a CTL realm" -> TPL.INDEX_MANIFEST_CTL

## [M] STEP-RUN
- STEP: S0
  GOAL: Determine template type
  INPUTS: [TASK_TEXT]
  TARGETS: [INDEX_MANIFEST]
  ACTIONS:
    - Classify TASK_TEXT into TEMPLATE_INTENT:
      - ctl entity -> TPL.CTL_ENTITY
      - ctl blocker -> TPL.CTL_BLOCKER
      - ctl index-manifest -> TPL.INDEX_MANIFEST_CTL
  OUTPUTS: [TEMPLATE_KEY]
  CHECKS: [TEMPLATE_KEY_RESOLVABLE]
  FAIL: UE.FAIL.ROUTE_UNRESOLVED
  NEXT: "го"

- STEP: S1
  GOAL: Return template key and minimal usage notes
  INPUTS: [TEMPLATE_KEY]
  TARGETS: [TEMPLATE_KEY]
  ACTIONS:
    - Return TEMPLATE_KEY and minimal usage hints (no RAW)
  OUTPUTS: [TEMPLATE_KEY, USAGE_HINTS?]
  CHECKS: []
  FAIL: UE.FAIL.GATE_FAIL
  NEXT: "го"

## [M] FAIL_CODES
- UE.FAIL.ROUTE_UNRESOLVED
- UE.FAIL.GATE_FAIL
- UE.FAIL.RULE_VIOLATION

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
