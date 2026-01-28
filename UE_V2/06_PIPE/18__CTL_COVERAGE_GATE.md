# 18__CTL_COVERAGE_GATE

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: PIPE / CONTROL
UID: UE.V2.PIPE.CTL.COVERAGE_GATE.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Контроллер покрытия Pillars/Topics. Гарантия "шедевр со всех сторон".

---

## [M] INTENT
Не дать системе выпускать "однобокий" результат: проверять, что обязательные Pillars закрыты участниками и их вклад-токенами.

---

## [M] INPUTS
- PLAN_TOKEN (coverage level, список обязательных Pillars)
- TRACE_TOKEN (участники и их contribution токены)
- MAP__COVERAGE_TO_ENTITIES (XREF)
- REG_ENTITY_CATALOG (роль/cap каждого участника)

---

## [M] CHECKS
K1) Для каждого обязательного Pillar есть хотя бы 1 участник, подходящий по карте (роль/cap).
K2) Для каждого Pillar есть хотя бы 1 CONTRIBUTION_TOKEN (вклад реальный).
K3) Нет "лишних" участников без вкладов (LAW_20).
K4) Если coverage=MASTERPIECE -> обязательны FOCUS-LOOP на ключевых компонентах домена (доменно задаётся пайпом).

---

## [M] OUTPUTS
- REPORT_TOKEN (CTL): PASS/REWORK + что не закрыто + рекомендация кого вызвать

---

## [M] GATES
PASS если:
- покрытие выполнено
REWORK если:
- не закрыты обязательные Pillars или нет вкладов
STOP если:
- попытка signoff без покрытия (дл
