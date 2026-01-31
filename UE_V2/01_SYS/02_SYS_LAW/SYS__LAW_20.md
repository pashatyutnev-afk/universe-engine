# LAW_20

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: LAW
UID: UE.V2.LAW.20.NOISE_BUDGET.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Жёсткие лимиты на контекст, участников и варианты. Контент важнее мусора.

---

## [M] INTENT
Сделать систему жизнеспособной при лимите контекста: максимум места — под результат, минимум — под служебку.

---

## [M] RULES
1) В одном STEP активны максимум:
   - 1 Lead SPC
   - 1 ORC
   - 1 CTL
   - 1 VAL или 1 QA
   - 0–5 узких вкладчиков
2) В одном STEP максимум:
   - OPTIONS_MAX: 5
   - QUESTIONS_MAX: 3
3) Длинные обсуждения заменяются FOCUS-LOOP.
4) Любая сущность без CONTRIBUTION_TOKEN считается шумом → исключить (REWORK).
5) Если нужно больше участия, делаем несколько прогонов (STEP-RUN), а не расширяем один прогон.

---

## [M] GATES
PASS если:
- лимиты соблюдены
REWORK если:
- превышение лимитов без причины
STOP если:
- систематическое нарушение лимитов (несоблюдение протоколов)
