# 08__REG_ENTITY_MIN_SET

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: REGISTRY / MIN_SET
UID: UE.V2.REG.MIN_SET.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Минимальный набор сущностей, без которых система не должна выполнять задачи.

---

## [M] INTENT
Сделать запуск устойчивым: даже если доменные сущности не готовы, ядро обязано работать и правильно уходить в GAP, а не в хаос.

---

## [M] MIN_SET_DEFAULT (ROLES REQUIRED)
- Lead SPC (CORE): MACHINE_ARCHITECT_SPC
- ORC (CORE): PIPELINE_ARCHITECT_ORC
- CTL (CORE): READINESS_CHECK_CTL, NOISE_BUDGET_CTL
- VAL (CORE): DOC_FMT_VAL
- QA (CORE): QA_ACCEPT
- XREF (CORE): MAP__PIPELINES, MAP__VALIDATION_MATRIX

---

## [M] MIN_SET_PER_DOMAIN (ADDITIVE)
MUSIC:
- ORC: TRACK_BUILD_STEP_ORC (если нет → GAP создать)
- CTL: QUALITY_GATES_CTL (если нет → GAP)
- VAL: PROMPT_SPEC_VAL, RELEASE_PACK_READY_VAL (если нет → GAP)
- QA: QA_PANEL_TRACK (если нет → GAP)

VIS:
- PIPE: PIPE_VIS (если нет → GAP)
- VAL: VIS_PACK_READY_VAL (если нет → GAP)
- QA: QA_VIS_ACCEPT (если нет → GAP)

LOR:
- PIPE: PIPE_LOR (если нет → GAP)
- VAL: CANON_LOCK_VAL (если нет → GAP)
- QA: QA_LOR_ACCEPT (если нет → GAP)

REL:
- PIPE: PIPE_REL (если нет → GAP)
- VAL: RELEASE_PACK_READY_VAL (если нет → GAP)
- QA: QA_REL_ACCEPT (если нет → GAP)

---

## [M] RULES
1) Если MIN_SET_DEFAULT неполон — STOP (это фундамент).
2) Если доменный MIN_SET неполон — GAP (создать/добавить доменные сущности или пайп).
3) MIN_SET не должен раздуваться. Дополнение — только если без него невозможно пройти обязательные стадии.

---

## [M] GATES
PASS если:
- MIN_SET_DEFAULT доступен и может быть использован
STOP если:
- отсутствует любой элемент MIN_SET_DEFAULT
GAP если:
- отсутствует доменный элемент
