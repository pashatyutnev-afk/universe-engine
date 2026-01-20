# PIPELINE MAP (CANON)

FILE: 03_SYSTEM_ENTITIES/90_XREF__CROSSREF/04__MAP__PIPELINES.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
REALM: 90_XREF__CROSSREF
LEVEL: L2
DOC_TYPE: XREF (PIPELINE MAP)
INDEX_TYPE: MAP
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.XREF.PIPELINES.MAP.001
OWNER: SYSTEM
ROLE: Deterministic registry: TASK intent → pipeline selection → primary entities → required gates → output targets.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Initialized pipeline registry with minimal canonical set (4 pipelines) + required gate order."
- REASON: "Prevent ambiguous routing and eliminate guessing. Provide deterministic default route when task is unclear."
- IMPACT: "Routing becomes auditable and repeatable. Every run can reference a pipeline ID with stable gate order."
- CHANGE_ID: UE.CHG.2026-01-20.PIPEMAP.001

---

## 0) PURPOSE (LAW)
Этот файл — канонический XREF-реестр пайплайнов.
- Он не описывает методы выполнения в деталях.
- Он фиксирует: **какой тип задачи** → **какой пайплайн** → **какие сущности обязательны** → **какие гейты обязательны** → **куда складывать результат**.
- Любая работа, где возможна неоднозначность маршрута, должна ссылаться на PIPELINE_ID из этого файла.

---

## 1) ABSOLUTE RULES
### 1.1 RAW-only navigation
Никаких угадываний. Использовать только RAW ссылки из ROOT LINK BASE или присланные пользователем.

### 1.2 Mandatory gate order (finish chain)
По умолчанию для любого пайплайна:
READINESS_CHECK_CTL → relevant VAL → relevant QA → DOC_CONTROLLER_SPC → MACHINE_ARCHITECT_SPC signoff

### 1.3 Minimal set first
Если задача неясная, берём:
- PIPELINE_ID = PL__DOC_AUDIT_AND_FIX (сначала стабилизируем документы/структуру)

---

## 2) RECORD SCHEMA (CANON)
Каждая запись пайплайна обязана содержать:

- PIPELINE_ID (human id)
- PIPELINE_UID (system uid)
- INTENT (коротко: что делает)
- PRIMARY_SPC (RAW)
- PRIMARY_ORC (RAW)
- REQUIRED_ENTITIES (минимум: SPC/ORC/CTL; VAL/QA — "relevant")
- REQUIRED_GATES (явный порядок)
- OUTPUT_TARGETS (куда складываем артефакты/логи)
- NOTES (границы пайплайна)

---

## 3) PIPELINE REGISTRY (MINIMUM CANON SET)

### 3.1 Registry table
| PIPELINE_ID | PIPELINE_UID | INTENT | PRIMARY_SPC | PRIMARY_ORC | REQUIRED_GATES (ORDER) | OUTPUT_TARGETS |
|---|---|---|---|---|---|---|
| PL__DOC_AUDIT_AND_FIX | UE.PPL.DOC.AUDIT.001 | Audit + fix controlled docs, indexes, standards, entity docs | MACHINE_ARCHITECT_SPC | PIPELINE_ORCHESTRATOR | READINESS → VAL(relevant) → QA(relevant) → DOC_CONTROLLER → SIGNOFF | 99_LOGS/LOG__AUDIT.md + updated docs |
| PL__ENTITY_CREATE_OR_REPAIR | UE.PPL.ENTITY.REPAIR.001 | Create/repair missing SPC/ORC/CTL/VAL/QA/XREF + required templates | MACHINE_ARCHITECT_SPC | PIPELINE_ORCHESTRATOR | READINESS → VAL(relevant) → QA(relevant) → DOC_CONTROLLER → SIGNOFF | 03_SYSTEM_ENTITIES/* + 99_LOGS |
| PL__KB_SCOPE_LOAD_AND_APPLY | UE.PPL.KB.SCOPE.001 | Select KB_SCOPE + load minimal KB modules + enforce trace discipline | STANDARDS_OWNER_SPC | PIPELINE_ORCHESTRATOR | READINESS → VAL(relevant) → QA(relevant) → DOC_CONTROLLER → SIGNOFF | 04_KNOWLEDGE_BASE/* + 99_LOGS |
| PL__MUSIC_FACTORY_RUN | UE.PPL.MUSIC.FACTORY.001 | Music workflow run: group → album → track → gates → release pack | INTEGRATION_PACKER_SPC | ALBUM_TO_TRACK_ORC | READINESS → VAL(relevant) → QA(relevant) → DOC_CONTROLLER → SIGNOFF | 08_DATABASES/10_MUSIC_CATALOG/* + 05_PROJECTS/07_MUSIC_LABEL/* |

---

## 4) PIPELINE DEFINITIONS (DETAIL BLOCKS)

### PL__DOC_AUDIT_AND_FIX
PIPELINE_UID: UE.PPL.DOC.AUDIT.001  
INTENT: Audit + fix controlled docs, indexes, navigation laws, registries, entity docs.

PRIMARY_SPC (RAW):
- MACHINE_ARCHITECT_SPC:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/01__MACHINE_ARCHITECT_SPC.md
- DOC_CONTROLLER_SPC:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/04__DOC_CONTROLLER_SPC.md

PRIMARY_ORC (RAW):
- PIPELINE_ORCHESTRATOR:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/01_CORE_ORCHESTRATORS/05__PIPELINE_ORCHESTRATOR_ENG.md

REQUIRED_ENTITIES (MINIMUM):
- CTL: READINESS_CHECK_CTL
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/01__READINESS_CHECK_CTL.md
- VAL: relevant (doc control / index integrity / naming-uid consistency)
- QA: relevant (readability / regression / acceptance)
- REG/LOG: audit trail

REQUIRED_GATES (ORDER):
1) READINESS_CHECK_CTL
2) relevant VAL
3) relevant QA
4) DOC_CONTROLLER_SPC
5) MACHINE_ARCHITECT_SPC signoff

OUTPUT_TARGETS:
- 99_LOGS/LOG__AUDIT.md (фиксировать найденные нарушения и итоги)
- исправленные документы (PATCH change_note внутри каждого файла)

NOTES:
- Не трогать LOCK: FIXED документы без явной задачи на изменение.

---

### PL__ENTITY_CREATE_OR_REPAIR
PIPELINE_UID: UE.PPL.ENTITY.REPAIR.001  
INTENT: Create/repair missing entities + required templates so the runtime can proceed without guessing.

PRIMARY_SPC (RAW):
- MACHINE_ARCHITECT_SPC:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/01__MACHINE_ARCHITECT_SPC.md
- PIPELINE_ARCHITECT_SPC:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/05__PIPELINE_ARCHITECT_SPC.md
- DOC_CONTROLLER_SPC:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/04__DOC_CONTROLLER_SPC.md

PRIMARY_ORC (RAW):
- PIPELINE_ORCHESTRATOR:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/01_CORE_ORCHESTRATORS/05__PIPELINE_ORCHESTRATOR_ENG.md

REQUIRED_ENTITIES (MINIMUM):
- CTL: READINESS_CHECK_CTL
- TPL index: all templates index (to select correct template)
- REG index: registries index (to register new entity)

REQUIRED_GATES (ORDER):
1) READINESS_CHECK_CTL
2) relevant VAL (naming/uid/doc control)
3) relevant QA (completeness + regression)
4) DOC_CONTROLLER_SPC
5) MACHINE_ARCHITECT_SPC signoff

OUTPUT_TARGETS:
- 03_SYSTEM_ENTITIES/* (новые/исправленные сущности)
- 99_LOGS/* (audit/change trace)

NOTES:
- Если сущности/шаблона нет: сначала GAP фиксируется, потом создаётся полный файл сущности, только затем продолжаем.

---

### PL__KB_SCOPE_LOAD_AND_APPLY
PIPELINE_UID: UE.PPL.KB.SCOPE.001  
INTENT: Select KB_SCOPE + load minimal KB governance + load required modules + enforce trace discipline.

PRIMARY_SPC (RAW):
- STANDARDS_OWNER_SPC:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/03__STANDARDS_OWNER_SPC.md
- DOC_CONTROLLER_SPC:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/04__DOC_CONTROLLER_SPC.md

PRIMARY_ORC (RAW):
- PIPELINE_ORCHESTRATOR:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/01_CORE_ORCHESTRATORS/05__PIPELINE_ORCHESTRATOR_ENG.md

REQUIRED_ENTITIES (MINIMUM):
- KB entrypoint (master index)
- KB governance rules
- CTL: READINESS_CHECK_CTL (must require KB_SCOPE + trace)
- VAL/QA: relevant (scope compliance + no-fantasy execution discipline)

REQUIRED_GATES (ORDER):
1) READINESS_CHECK_CTL
2) relevant VAL
3) relevant QA
4) DOC_CONTROLLER_SPC
5) MACHINE_ARCHITECT_SPC signoff

OUTPUT_TARGETS:
- 04_KNOWLEDGE_BASE/* (если задача требует создания/обновления модулей)
- 99_LOGS/* (trace применённых KB модулей)

NOTES:
- Каждый ран обязан фиксировать KB_SCOPE и минимальный trace применённых модулей.

---

### PL__MUSIC_FACTORY_RUN
PIPELINE_UID: UE.PPL.MUSIC.FACTORY.001  
INTENT: Music workflow run: group → album → track → gates → release pack.

PRIMARY_SPC (RAW):
- INTEGRATION_PACKER_SPC:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/06__INTEGRATION_PACKER_SPC.md
- DOC_CONTROLLER_SPC:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/04__DOC_CONTROLLER_SPC.md
- MACHINE_ARCHITECT_SPC:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/01__MACHINE_ARCHITECT_SPC.md

PRIMARY_ORC (RAW):
- ALBUM_TO_TRACK_ORC:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/02__ALBUM_TO_TRACK_ORC.md

SUPPORTING_ORC (RAW):
- GROUP_TO_ALBUM_ORC:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/01__GROUP_TO_ALBUM_ORC.md
- TRACK_TEST_DOC_GATE_ORC:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/03__TRACK_TEST_DOC_GATE_ORC.md
- RELEASE_PACK_ORC:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/04__RELEASE_PACK_ORC.md

REQUIRED_ENTITIES (MINIMUM):
- CTL: READINESS_CHECK_CTL
- VAL: relevant (collision/rights/naming compliance)
- QA: relevant (hook/ugc/mix/regression gates)
- KB: music topics + music system docs (by KB_SCOPE)

REQUIRED_GATES (ORDER):
1) READINESS_CHECK_CTL
2) relevant VAL
3) relevant QA
4) DOC_CONTROLLER_SPC
5) MACHINE_ARCHITECT_SPC signoff

OUTPUT_TARGETS:
- 08_DATABASES/10_MUSIC_CATALOG/* (catalog cards/prompts/releases)
- 05_PROJECTS/07_MUSIC_LABEL/* (brand/releases packs)
- 99_LOGS/*

NOTES:
- Если нет нужной сущности/шаблона для музыкального выпуска: сначала GAP и создание, затем продолжение пайплайна.

---

## 5) CHANGE POLICY
- Любые изменения в записях пайплайнов: только PATCH + CHANGE_NOTE в этом файле.
- Удаление пайплайна: только через deprecation pointer (если внедрён в вашем процессе).

