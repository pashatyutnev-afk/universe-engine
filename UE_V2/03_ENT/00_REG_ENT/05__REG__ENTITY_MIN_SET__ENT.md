FILE: UE_V2/03_ENT/00_REG/05__REG_ENTITY_MIN_SET.md
SCOPE: Universe Engine (UE_V2)
DOC_TYPE: REG_RULES
DOMAIN: REG
UID: UE.V2.REG.ENTITY_MIN_SET.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-30
OWNER: SYS

---

# REG — ENTITY MIN SET

PURPOSE:
Минимальные наборы документов/объектов, которые должны быть доступны для разных режимов и доменов, чтобы рантайм не фантазировал и не проходил мимо обязательных слоёв.

---

## GLOBAL MIN SET (any run)
- BOOT: START, BOOT_SEQ, TRACE, FAIL_CODES, RUNTIME_MANIFEST, TASK_ROUTER
- NAV: NAV_ROOT
- PIPE: PIPE_DEFAULT
- LOG: RUN_LOG, DECISION_LOG, TOKEN_ARCHIVE

---

## REG MIN SET (when REG is required)
- REG: INDEX_MANIFEST, PIPELINE_CONTRACT, ENTITY_IDS, PATH_MAP, UID_REGISTRY

---

## MODE HINT IMPACT
FAST:
- грузим только GLOBAL MIN SET + доменный MIN SET
RELEASE_READY:
- + ENTITY_TYPES, ENTITY_REGISTRY, ARTIFACT_REGISTRY (если есть выпуск артефакта)
MASTERPIECE:
- + QA/VAL набор домена (если предусмотрено доменом)

---

## GAP / STOP
STOP_IF:
- отсутствует RAW для REG MIN SET

GAP_IF:
- отсутствуют дополнительные ключи, запрошенные роутером/пайпом, но не критичные для старта
