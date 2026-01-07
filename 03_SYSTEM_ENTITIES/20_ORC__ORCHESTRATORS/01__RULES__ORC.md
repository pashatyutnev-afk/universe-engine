# ORCHESTRATORS (ORC) — RULES
FILE: 03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/01__RULES__ORC.md

SCOPE: Universe Engine / ORC Rules
ENTITY_GROUP: ENT
CATEGORY: ORC
LEVEL: L1
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
OWNER: SYSTEM
ROLE: Правила для ORC: UID, контракт, структура пайплайнов, связи и анти-конфликты.

SOURCE OF TRUTH:
- UID Standard: `02_STANDARDS/01_SPECIFICATIONS/UID_AND_MARKING_SPEC.md`

---

## 0) ORC CORE LAW
ORC отвечает только за:
- ORDER (порядок шагов)
- ROUTING (кто выполняет шаг)
- INPUT/OUTPUT (что нужно и что считается результатом)
- CHECKPOINTS (контрольные точки)

ORC НЕ делает:
- доменные решения (SPC/ENG)
- законы/валидации (VAL/QA)
- хранение контента (KB/PRJ/AST/OUT)

---

## 1) UID FORMAT (ORC)
`UE.ENT.ORC.<FAMILY>.<NAME>`

Пример:
`UE.ENT.ORC.PROD.SCENE_BUILD_PIPELINE`

FAMILY рекомендуется:
- PROD (production)
- GOV (governance)
- QLT (quality routing)
- GEN (общий)

---

## 2) ORC MINI-CONTRACT (MANDATORY)
Каждый ORC обязан иметь:

CONSUMES:
- 1–5 типов входов (например PRJ_SCENE_UID, KB_REFS, TARGET_OUT_TYPES)

PRODUCES:
- 1–5 выходов (PIPELINE_PLAN, ROUTING, CHECKPOINTS, OUTPUT_TARGETS)

DEPENDS_ON:
- список ENG/SPC/CTL/VAL/QA сущностей или []

OUTPUT_TARGET:
- куда кладётся результат (обычно PRJ/OUT, реже KB)

Если mini-contract отсутствует — ORC incomplete.

---

## 3) PIPELINE STEP FORMAT (MANDATORY)
Каждый ORC имеет список STEPS, где каждый STEP:

STEP_ID: <01..NN>
NAME: <UPPER_SNAKE_CASE>
EXECUTOR_UID: <UE.ENT.(ENG|SPC|CTL|VAL|QA)...>
CONSUMES: [...]
PRODUCES: [...]
GATE: <NONE|VAL|QA|CTL>
FAIL_SEVERITY: <S0|S1|S2|S3>
HANDOFF_TARGET: <KB|PRJ|AST|OUT>
NOTES: <optional>

---

## 4) CONFLICT RULE
Если ORC пытается делать работу ENG/SPC/VAL/QA — это нарушение (S0).

---

## 5) REGISTRY RULE
ORC существует только после записи в ORC Global Registry.

---
END.
