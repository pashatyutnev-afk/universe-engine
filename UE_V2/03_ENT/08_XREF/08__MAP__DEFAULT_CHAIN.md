# 08__MAP__DEFAULT_CHAIN

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: XREF / MAP
UID: UE.V2.XREF.DEFAULT_CHAIN.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Базовая цепочка ролей и обязательных артефактов (токенов) для любой задачи.

---

## [M] INTENT
Сделать так, чтобы система всегда проходила через контроль и не выпускала результат без CTL/VAL/QA/PACK/SIGNOFF.

---

## [M] DEFAULT_CHAIN (ROLE ORDER)
1) SPC (Lead) -> output: BRIEF_TOKEN / критерии
2) ORC -> output: PLAN_TOKEN + TRACE_TOKEN
3) CTL (readiness/noise/coverage) -> output: REPORT_TOKEN(CTL)
4) ENG/SPC contributors (batch) -> output: CONTRIBUTION_TOKEN set + OPTIONS_TOKEN
5) USER DECISION -> output: DECISION_TOKEN
6) VAL -> output: REPORT_TOKEN(VAL)
7) QA -> output: REPORT_TOKEN(QA)
8) ORC/CTL FIX pass (optional, via FOCUS-LOOP) -> output: DELTA_TOKEN
9) PACK -> output: PACK_TOKEN
10) SIGNOFF (SPC) -> output: BASELINE_TOKEN

---

## [M] REQUIRED_TOKENS (MIN)
- ROUTE_TOKEN
- PLAN_TOKEN
- TRACE_TOKEN
- at least one CONTRIBUTION_TOKEN (если был production/варианты)
- REPORT_TOKEN (если была REVIEW стадия)
- PACK_TOKEN (если это релиз-уровень или результат должен быть “готовый”)

---

## [M] RULES
1) Если отсутствуют REQUIRED_TOKENS — REWORK (или GAP если нет шаблона/правила).
2) Если отсутствует CTL/VAL/QA на S6 REVIEW (release_ready+) — STOP/REWORK по политике пайпа.
3) DEFAULT_CHAIN может уточняться доменными пайпами (PIPE_MUSIC_TRACK и т.д.), но не нарушать базовый контроль.

---

## [M] GATES
PASS если:
- цепочка и обязательные токены соблюдены
REWORK если:
- пропущен контроль или отсутствуют обязательные токены
