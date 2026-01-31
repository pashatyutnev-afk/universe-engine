SCOPE: Universe Engine (UE_V2)
DOC_TYPE: LAW / STANDARD
UID: UE.V2.LAW.ROUTER.PIPE.CONFLICT.019
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)

---

## [M] PURPOSE
Жёстко развести роли ROUTER и PIPELINE, чтобы они не дублировали друг друга.

---

## [M] ROUTER ROLE (DECISION ONLY)
ROUTER отвечает только за:
- классификацию задачи
- формирование ROUTE_TOKEN:
  DOMAIN, ARTIFACT_TYPE, MODE, PIPE_SELECTED, DEFAULT_ORC,
  REQUIRED_IDX, REQUIRED_CHECKS, EXEC_MODE

ROUTER НЕ выполняет работу и НЕ запускает шаги пайпа.

---

## [M] PIPELINE ROLE (EXECUTION ONLY)
PIPELINE_CONTRACT отвечает только за:
- шаги исполнения (STEP-RUN)
- подбор REQUIRED KEYS (SPC/KB/PANELS) по домену
- сбор результата (artifact)
- выдачу NEXT: "го"

PIPELINE НЕ решает “какой домен выбрать” — он исполняет уже выбранное.

---

## [M] HOW THEY “FRIEND” EACH OTHER
Канон цепочки:
START → ROUTER → NAV_ROOT → (INDEX_MANIFEST) → START_NODE (если есть) → PIPE_DEFAULT → DOMAIN PIPELINE_CONTRACT

---

## [M] GATES
PASS если:
- ROUTER формирует ROUTE_TOKEN и передаёт дальше
- PIPELINE исполняет только по KEY через INDEX_MANIFEST
FAIL если:
- ROUTER начинает описывать шаги пайпа
- PIPELINE начинает “переклассифицировать задачу” и менять домен
