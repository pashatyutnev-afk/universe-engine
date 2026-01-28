# 18__PIPELINE_STAGE_MODEL

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: STD
UID: UE.V2.STD.PIPELINE_STAGE_MODEL.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Единая модель стадий для любых пайпов и шагов STEP-RUN.

---

## [M] INTENT
Чтобы все пайпы и сущности говорили одинаковыми стадиями, и чтобы CTL/VAL/QA могли проверять полноту.

---

## [M] STAGE_LIST (CANON)
S0 INTAKE
- сбор минимального ввода

S1 ROUTE
- выбор DOMAIN/ARTIFACT/PIPE, обязательных IDX и гейтов

S2 PLAN
- разбиение на шаги, бюджеты, coverage, участие

S3 KB
- подтянуть нужные знания и ограничения, не таща мусор

S4 OPTIONS
- варианты решений A/B/C

S5 PRODUCTION
- создание/изменение артефакта (draft v1/v2)

S6 REVIEW
- CTL/VAL/QA проверки и отчёты

S7 FIX
- правки по отчётам

S8 PACK
- упаковка, метаданные, экспорт, чеклисты

S9 SIGNOFF
- финальное утверждение и фиксация baseline

S10 POST
- пост-контроль, регрессия, обновление канона/KB

---

## [M] RULES
1) Любой пайп обязан указать, какие STAGE он использует.
2) Любой STEP-RUN шаг обязан указывать текущий STAGE.
3) На релиз-уровне (release_ready/masterpiece) обязательны S6 и S8.

---

## [M] GATES
PASS если:
- STAGE указан в каждом STEP
REWORK если:
- используется стадия вне списка
STOP если:
- стадия не определена и пайп не может продолжаться
