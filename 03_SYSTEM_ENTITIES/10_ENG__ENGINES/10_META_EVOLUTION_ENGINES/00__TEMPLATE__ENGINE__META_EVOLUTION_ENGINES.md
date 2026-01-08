# ENGINE TEMPLATE — META EVOLUTION ENGINES (ENG)
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/10_META_EVOLUTION_ENGINES/00__TEMPLATE__ENGINE__META_EVOLUTION_ENGINES.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: TEMPLATE
ENGINE_FAMILY: 10_META_EVOLUTION_ENGINES
LEVEL: L4
STATUS: ACTIVE
VERSION: 1.0.1
ROLE: Canonical template for META evolution engines (learning, pattern extraction, optimization, creative mutation, future projection)

LOCK: FIXED
UID: <UE.TPL.ENG.META.ENGINE.###>            # MUST follow 01_SYSTEM_LAW/02__UID_RULES.md

---

## 0) IDENTITY (REQUIRED)
ENGINE_NAME: <DISPLAY_NAME>
ENGINE_CODE: <SHORT_CODE>                     # LEARNING | PATTERN_EXTRACTION | OPTIMIZATION | CREATIVE_MUTATION | FUTURE_PROJECTION
ENGINE_NUMBER: <NN>                           # must match filename NN__
ENGINE_FILE_NAME: <NN__NAME_ENG.md>
ENGINE_UID: <UE.ENG.META.<CODE>.###>          # MUST follow UID_RULES

FAMILY: 10_META_EVOLUTION_ENGINES
CLASS: META (L4)

---

## 1) PURPOSE (LAW)
Зачем этот мета-движок существует:
- что улучшает (правила/процессы/качество/масштабирование)
- какие типовые ошибки предотвращает
- какие изменения допустимы (границы)

---

## 2) CRITICAL BOUNDARY (ANTI-DUP) — ABSOLUTE
OWNED HERE (META):
- learning from history / logs / outputs
- extracting reusable patterns
- optimizing pipelines, constraints, ordering, checklists
- proposing controlled experiments (mutations)
- forecasting / scenarios / risk projections

NOT OWNED HERE (DOMAIN FINAL OUTPUT):
- финальный сюжет/сцены/лора/персонажи/миры/музыка/визуал как “готовый продукт”
Если движок всё же генерит “кусок контента”, он обязан пометить его как INPUT для доменных движков, не как финальный артефакт.

---

## 3) MINI-CONTRACT (MANDATORY)
CONSUMES:
- <1–5 input artifact types>
- ...

PRODUCES:
- <1–5 output artifact types>
- ...

DEPENDS_ON:
- []
# либо список UID движков:
# - <UE.ENG....>

OUTPUT_TARGET:
- <куда кладётся результат в проектах/артефактах>

OUTPUT_ARTIFACT_RULE:
- Любой PRODUCES-тип должен быть совместим с реестром типов артефактов
  (см. 01_SYSTEM_LAW/05__ARTIFACT_SCHEMA_REGISTRY.md / DB__ARTIFACT_TYPES при наличии).

---

## 4) METHOD (REQUIRED)
EVIDENCE SOURCES:
- <logs / audit / outputs / QA / metrics>

EXTRACTION:
- <как вычленяем паттерн/проблему>

OBJECTIVE:
- <что оптимизируем и как меряем>

RISK MODEL:
- <что может сломать, как страхуем>

ROLLOUT (SAFE):
- propose → test → validate → adopt

BACKOUT PLAN:
- <как откатить>

DEFAULT SAFE MODE:
- если неопределённость высокая → выдаём варианты/предложения, не “обязательное изменение”.

---

## 5) META GATES (HARD) — REQUIRED
- GATE: evidence grounded
  CHECK: inputs существуют и указаны
  FAIL: нет ссылок на входные данные
  FIX: добавить источники/входы

- GATE: scope safety
  CHECK: не ломает канон по умолчанию
  FAIL: требует изменения канона без governance
  FIX: перевести в proposal + через governance pipeline

- GATE: reversibility
  CHECK: есть backout plan
  FAIL: отката нет
  FIX: добавить откат/rollback

- GATE: impact clarity
  CHECK: что меняем + зачем + ожидаемый эффект
  FAIL: “улучшили” без меры
  FIX: добавить метрику/критерий

- GATE: boundary compliance
  CHECK: не выдаёт доменный “финал”
  FAIL: создаёт готовый доменный продукт
  FIX: пометить как INPUT или вынести в доменное семейство

---

## 6) EXAMPLES (REQUIRED)
GOOD:
- <пример meta-output и почему проходит gates>

BAD:
- <пример нарушения и почему>

---

## 7) REL / XREF (UID-FIRST)
REL:
- REL: <REL_TYPE> | TARGET_UID: <UID> | WHY: <reason>

XREF:
- XREF_UID: <UID> | WHY: <reason>

RULE:
- RAW links обязательны в INDEX/REGISTRY.
- Внутри engine-файлов — UID-first (чтобы не плодить “навигацию путями”).

--- END.
