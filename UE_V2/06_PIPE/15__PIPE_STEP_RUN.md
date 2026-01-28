# 15__PIPE_STEP_RUN

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: PIPE / PROTOCOL
UID: UE.V2.PIPE.STEP_RUN.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Как любой PIPE исполняется в режиме STEP-RUN (один шаг за раз + "го").

---

## [M] INTENT
Гарантировать, что сложные задачи выполняются сериями коротких прогонов с фиксацией токенов и без перегруза контекста.

---

## [M] RULES
1) PIPE исполняется последовательностью STEP_ID: STEP_00, STEP_01...
2) Каждый STEP заканчивается USER_PROMPT = "го".
3) Каждый STEP обязан создать минимум один STEP_TOKEN из STD/15.
4) STEP хранит только текущий контекст + ссылки на архив токенов.
5) Любой PIPE может вставлять FOCUS-LOOP на любой стадии (см. 16__PIPE_FOCUS_LOOP).

---

## [M] STEP_LAYOUT (CANON)
STEP_00 INTAKE:
- BRIEF_TOKEN + ROUTE_TOKEN

STEP_01 PLAN:
- PLAN_TOKEN (stages, budgets, coverage, participants)

STEP_02 KB:
- KB_TOKEN (scope + rules + do_not)

STEP_03 OPTIONS / DRAFT:
- OPTIONS_TOKEN или DRAFT_v1 (по типу задачи)

STEP_04 REVIEW:
- REPORT_TOKEN (CTL/VAL/QA)

STEP_05 FIX:
- DELTA_TOKEN v2

STEP_06 REVIEW_2 (optional):
- REPORT_TOKEN(QA/VAL) spot-check

STEP_07 PACK + SIGNOFF:
- PACK_TOKEN + BASELINE_TOKEN

---

## [M] GATES
PASS если:
- соблюдён порядок и есть токены
REWORK если:
- шаги сливаются в один большой "комок"
STOP если:
- нет USER_PROMPT "го" в конце шага
