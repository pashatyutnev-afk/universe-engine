# 06__REG_STAGE_RULES

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: REGISTRY / RULES
UID: UE.V2.REG.STAGE_RULES.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Правила обязательных ролей по стадиям пайпа и допустимые участники.

---

## [M] INTENT
Гарантировать, что система не "проскочит" мимо контроля: на нужных стадиях обязаны участвовать нужные роли.

---

## [M] STAGE_TO_ROLE (MIN REQUIRED)
S0 INTAKE:
- REQUIRED: SPC, ORC
- OPTIONAL: CTL (noise), ENG (brief), XREF (route hints)

S1 ROUTE:
- REQUIRED: ORC, XREF
- OPTIONAL: SPC (goal fit), CTL (readiness)

S2 PLAN:
- REQUIRED: SPC, ORC, CTL
- OPTIONAL: XREF, REG (index), ENG (coverage suggestions)

S3 KB:
- REQUIRED: ORC, CTL
- OPTIONAL: SPC, XREF, KB managers

S4 OPTIONS:
- REQUIRED: ORC
- OPTIONAL: SPC, ENG, QA(score)

S5 PRODUCTION:
- REQUIRED: ORC
- OPTIONAL: ENG/SPC contributors

S6 REVIEW:
- REQUIRED: CTL, VAL, QA
- OPTIONAL: SPC (final call), XREF (checks), ORC

S7 FIX:
- REQUIRED: ORC
- OPTIONAL: ENG/SPC contributors, VAL (spot check)

S8 PACK:
- REQUIRED: SPC, ORC
- OPTIONAL: CTL (compliance), VAL (pack ready), QA (pack QA)

S9 SIGNOFF:
- REQUIRED: SPC
- OPTIONAL: CTL, QA, VAL

S10 POST:
- REQUIRED: CTL (regression), ORC
- OPTIONAL: XREF, KB scope updates, REG updates

---

## [M] RULES
1) Любой PLAN_TOKEN обязан указать стадии, которые будут выполнены.
2) На RELEASE_READY и выше стадии S6 и S8 обязательны.
3) Если стадия требует роль, а роль не присутствует → REWORK (или GAP, если сущности нет).
4) Внутри STEP-RUN активный набор сущностей должен быть минимальным (LAW_20).

---

## [M] GATES
PASS если:
- для каждой стадии присутствуют REQUIRED роли
REWORK если:
- стадия пропущена без разрешения пайпа
STOP если:
- нет CTL/VAL/QA на стадии REVIEW (S6) при релиз-уровне
