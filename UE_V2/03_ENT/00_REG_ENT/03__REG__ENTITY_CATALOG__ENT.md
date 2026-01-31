FILE: UE_V2/03_ENT/00_REG_ENT/03__REG__ENTITY_CATALOG__ENT.md
SCOPE: UE_V2 / 03_ENT / 00_REG_ENT
DOC_TYPE: REG_CATALOG
DOMAIN: REG
UID: UE.V2.REG.ENTITY_CATALOG.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-30
OWNER: SYS

---

# REG — ENTITY CATALOG (UE_V2 Core)

PURPOSE:
Каталог "что обязательно существует" для работоспособности UE_V2.
Это не реестр адресов и не реестр UID. Это список объектов и их смысл.

---

## CORE OBJECTS (minimum viability)

| OBJECT | FAMILY | PURPOSE_BRIEF |
|---|---|---|
| START | BOOT | точка входа, запрещает обходы |
| BOOT_SEQ | BOOT | минимальная последовательность загрузки |
| RUNTIME_MANIFEST | BOOT | MUST_LOAD_SET и минимальные компоненты |
| TASK_ROUTER | BOOT | детерминированный выбор маршрута |
| NAV_ROOT | NAV | корень навигации и доступов |
| PIPE_DEFAULT | PIPE | дефолтный пайп для handoff |
| TRACE | BOOT | трассировка и минимальный трейс |
| FAIL_CODES | BOOT | коды ошибок и STOP/GAP |
| RUN_LOG | LOG | журнал прогона |
| DECISION_LOG | LOG | журнал решений |
| TOKEN_ARCHIVE | LOG | архив токенов |

---

## REG REQUIRED OBJECTS
| OBJECT | FAMILY | PURPOSE_BRIEF |
|---|---|---|
| ENTITY_IDS | REG | кодировка и семейства |
| PATH_MAP | REG | смысл корней и стабильность |
| UID_REGISTRY | REG | проверка коллизий UID |
| ENTITY_REGISTRY | REG | канон сущностей |
| ARTIFACT_REGISTRY | REG | канон артефактов |

---

## NOTE
Если какой-то объект отсутствует — это GAP/STOP в зависимости от того, входит ли он в MIN_SET текущего прогона.
