# 11__IDX_LOG

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: NAV / INDEX
UID: UE.V2.NAV.IDX_LOG.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Вход в LOG слой (трейс, токены, решения, изменения).

---

## [M] INTENT
Сделать фиксацию прогонов и решений стандартной: чтобы ничего не "плыло" и не терялось.

---

## [M] LINKS (PATH)
LOG ядро:
- UE_V2/12_LOG/00__LOG_RULES.md
- UE_V2/12_LOG/01__RUN_LOG.md
- UE_V2/12_LOG/02__CHANGE_LOG.md
- UE_V2/12_LOG/03__TOKEN_ARCHIVE.md
- UE_V2/12_LOG/04__DECISION_LOG.md

---

## [M] RULES
1) Каждый STEP обязан оставить запись в RUN_LOG (кратко).
2) Каждый выбор вариантов обязан оставить DECISION_LOG запись.
3) Токены старых шагов выносятся в TOKEN_ARCHIVE, а не держатся в контексте.
4) Любое изменение правил/словари/карт фиксируется в CHANGE_LOG.

---

## [M] GATES
PASS если:
- RUN_LOG доступен
GAP если:
- отсутствуют 02–04 (CHANGE/TOKEN/DECISION)
STOP если:
- отсутствует LOG_RULES или RUN_LOG
