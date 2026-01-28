# 17__VAL_CHAIN_COMPLETENESS

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: PIPE / VALIDATION
UID: UE.V2.PIPE.VAL.CHAIN_COMPLETENESS.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Валидация полноты цепочки и токенов. Нельзя "пройти мимо" обязательных стадий.

---

## [M] INTENT
Проверять не контент, а процесс: что шаги выполнены, контроль пройден, токены/решения зафиксированы, упаковка есть.

---

## [M] INPUTS
- TOKEN_ARCHIVE запись шага
- TRACE_TOKEN (участники и вклад-токены)
- PLAN_TOKEN (stages, coverage level)
- REQUIRED_TOKENS (по STD/15)

---

## [M] CHECKS (CANON)
C1) Есть ROUTE_TOKEN и PLAN_TOKEN.
C2) Если coverage level = release_ready/masterpiece -> есть REVIEW (CTL/VAL/QA) и REPORT_TOKEN.
C3) Если были OPTIONS -> есть DECISION_LOG запись.
C4) Если шаг завершён -> есть TOKEN_ARCHIVE запись.
C5) Если результат должен быть "готовый" -> есть PACK_TOKEN.
C6) Если был SIGNOFF -> есть BASELINE_TOKEN.

---

## [M] OUTPUTS
- REPORT_TOKEN (VAL): PASS/REWORK + список недостающих элементов

---

## [M] FAIL_CODES
- VAL.CHAIN.MISSING_PLAN
- VAL.CHAIN.MISSING_REVIEW
- VAL.CHAIN.MISSING_DECISION
- VAL.CHAIN.MISSING_ARCHIVE
- VAL.CHAIN.MISSING_PACK
- VAL.CHAIN.MISSING_BASELINE

---

## [M] GATES
PASS если:
- все обязательные элементы присутствуют
REWORK если:
- недостаёт токенов/решений/архива
STOP если:
- систематически обходятся контрольные стадии
