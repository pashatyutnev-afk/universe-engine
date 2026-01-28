# 04__DECISION_LOG

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: LOG / DECISIONS
UID: UE.V2.LOG.DECISION_LOG.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Лог решений пользователя и системы (выбор вариантов, компромиссы, закрепления baseline).

---

## [M] INTENT
Сделать процесс воспроизводимым: почему выбрали A, почему отвергли B, что закрепили как эталон.

---

## [M] RULES
1) Любой выбор из OPTIONS обязан фиксироваться DECISION_ENTRY.
2) Любой "дефолтный выбор" (когда пользователь не выбирал) тоже фиксируется.
3) Любое "закрепи" создаёт baseline decision.
4) Решения должны быть короткими и конкретными: 3–10 строк.
5) Решение должно ссылаться на соответствующие TOKEN_ID (OPTIONS/REPORT/DELTA).

---

## [M] DECISION_ENTRY_TEMPLATE
DECISION_ENTRY:
- DECISION_ID:
- DATE:
- RUN_ID:
- STEP_ID:
- FOCUS_ID: (optional)
- DOMAIN:
- ARTIFACT:
- OPTIONS_REF: (TOKEN_ID)
- CHOSEN: (A|B|C|custom mix)
- WHY (3–10 строк):
- TRADEOFFS (0–5 bullets):
- BASELINE: (YES|NO)
- NEXT_ACTION:

---

## [M] DECISIONS (APPEND ONLY)
| DECISION_ID | DATE | RUN_ID | STEP_ID | DOMAIN | ARTIFACT | CHOSEN | BASELINE |
|---|---|---|---|---|---|---|---|

---

## [M] GATES
PASS если:
- есть решение на каждый OPTIONS_TOKEN
REWORK если:
- применены изменения без решения
STOP если:
- противоречивые решения без фиксации baseline/отката
