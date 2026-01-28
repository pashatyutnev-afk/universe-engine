# 16__COVERAGE_RULES

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: STD
UID: UE.V2.STD.COVERAGE_RULES.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Правила "шедевр со всех сторон" через покрытие Pillars/Topics.

---

## [M] INTENT
Гарантировать, что результат проработан с нескольких углов, и что участие сущностей не случайное, а закрывает реальные стороны качества.

---

## [M] PILLARS (CANON)
P0 GOAL_FIT (цель/аудитория/формат)
P1 CORE_CRAFT (основное ремесло: структура/логика/композиция)
P2 EMOTION_PSYCH (эмоция/психология/вовлечение)
P3 UNIQUENESS (дифференциация/анти-коллизии/новизна)
P4 TECH_QUALITY (тех качество: чистота, стабильность, отсутствие дефектов)
P5 PACKAGING (упаковка: метаданные, оформление, экспорт)
P6 COMPLIANCE (правила/канон/ограничения/права)
P7 DELIVERY (публикация/дистрибуция/пост-контроль)

---

## [M] COVERAGE_LEVELS
- L1 BASIC: минимум 3 Pillars
- L2 RELEASE_READY: минимум 5 Pillars
- L3 MASTERPIECE: минимум 7 Pillars + обязательные FOCUS-LOOP на ключевых местах

---

## [M] COVERAGE_BY_ARTIFACT (DEFAULT)
MUSIC.TRACK:
- BASIC: P0, P1, P4
- RELEASE_READY: P0, P1, P3, P4, P5
- MASTERPIECE: P0, P1, P2, P3, P4, P5, P6

MUSIC.LYRICS:
- BASIC: P0, P1, P6
- RELEASE_READY: P0, P1, P2, P3, P6
- MASTERPIECE: P0, P1, P2, P3, P4, P6, P5

VIS.PROMPT_SPEC / VIS_PACK:
- BASIC: P0, P1, P6
- RELEASE_READY: P0, P1, P4, P5, P6
- MASTERPIECE: P0, P1, P2, P3, P4, P5, P6

LOR.CANON_UPDATE / LORE_NODE:
- BASIC: P0, P1, P6
- RELEASE_READY: P0, P1, P3, P4, P6
- MASTERPIECE: P0, P1, P2, P3, P4, P6, P7

CORE.LAW/STD/TPL:
- BASIC: P0, P1, P6
- RELEASE_READY: P0, P1, P4, P6, P7
- MASTERPIECE: P0, P1, P3, P4, P5, P6, P7

---

## [M] RULES
1) ORC обязан объявить COVERAGE_LEVEL в PLAN_TOKEN.
2) ORC обязан показать, какие сущности закрывают какие Pillars (через XREF map).
3) CTL обязан проверить, что покрытие выполнено (иначе REWORK).
4) VAL/QA обязаны подтвердить ключевые Pillars (для MUSIC: P4 и P3 обязательны на релиз-уровне).

---

## [M] GATES
PASS если:
- покрытие по уровню выполнено и зафиксировано в TRACE_TOKEN/PLAN_TOKEN
REWORK если:
- не закрыт хотя бы один обязательный Pillar
STOP если:
- PLAN_TOKEN отсутствует и уровень покрытия не определён
