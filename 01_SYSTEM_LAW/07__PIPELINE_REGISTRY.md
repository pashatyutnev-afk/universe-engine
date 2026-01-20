# PIPELINE REGISTRY (LAW) — CANON

FILE: 01_SYSTEM_LAW/07__PIPELINE_REGISTRY.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 01_SYSTEM_LAW
DOC_TYPE: REGISTRY (LAW)
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.LAW.PIPELINE_REGISTRY.001
OWNER: SYSTEM
ROLE: Canon registry of allowed pipelines (ORC routes). Defines what pipelines exist, how they are invoked, what gates they must pass (CTL/VAL/QA), and what minimum inputs/outputs are required. Prevents “invisible routes” and enforces deterministic routing.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Introduced canonical pipeline registry: allowed ORC routes, required gates, KB consumption flags, stop conditions, and deprecation rules."
- REASON: "Without a registry, routing becomes implicit and error-prone; hidden pipelines create inconsistent behavior."
- IMPACT: "All runtime work must map to an explicit pipeline record; signoff and validation become enforceable."
- CHANGE_ID: UE.CHG.2026-01-20.LAW.PIPELINE.001

---

## 0) PURPOSE (LAW)
Этот реестр фиксирует единственную “карту разрешённых маршрутов” (pipelines).
- Пайплайн = детерминированная цепочка ORC шагов + обязательные CTL/VAL/QA гейты.
- Если пайплайна нет в реестре — его нельзя выполнять в рантайме.

---

## 1) ABSOLUTE LAWS
### 1.1 Registry-only execution
Система имеет право выполнять только те пайплайны, которые зарегистрированы в этом файле.

### 1.2 Single entrypoint still applies
Любая задача начинается через `START_UNIVERSE_ENGINE`.
Этот реестр не заменяет START, а задаёт разрешённые маршруты после ROUTING.

### 1.3 Mandatory gates per pipeline
Каждый пайплайн обязан пройти указанные в записи:
- CTL (контроль)
- VAL (валидация)
- QA (приёмка/регресс)
Пайплайн не может “обойти” обязательный гейт.

### 1.4 KB consumption flag is binding
Если пайплайн помечен `KB_CONSUMPTION: TRUE`, то:
- требуется `KB_SCOPE_RAW` на входе
- provenance markers должны быть переносимы в выходные артефакты
Если это не подтверждено → STOP.

### 1.5 Stop conditions (only these)
Остановка допустима только:
- RAW missing
- marker not confirmed
- input absent

---

## 2) PIPELINE RECORD FORMAT (CANON)
Каждая запись пайплайна должна содержать минимум:

- PIPELINE_ID
- NAME
- DOMAIN (e.g., MUSIC)
- ENTRY_ORC_RAW (главный оркестратор)
- KB_CONSUMPTION: TRUE|FALSE
- MIN_INPUTS (what must be present)
- OUTPUTS (what artifacts must be produced)
- REQUIRED_GATES:
  - CTL: list (RAW)
  - VAL: list (RAW)
  - QA:  list (RAW)
- DEFAULT_RETURN (RAW) (куда возвращаться при FAIL)
- NOTES (optional)
- STATUS/LOCK/VERSION/CHANGE_NOTE (doc control is handled at file level; pipeline-level notes may include last update line)

---

## 3) PIPELINE CATALOG (ALLOWED)
Ниже перечислены разрешённые пайплайны.  
Если задача не подходит ни под один — фиксируется GAP и предлагается создать новый пайплайн (через ORC + registry update).

---

### P-000 — READINESS / BOOT GATE (SYSTEM)
PIPELINE_ID: UE.PIPE.SYSTEM.READINESS.000
NAME: Readiness Gate (Boot + Linkbase + KB readiness)
DOMAIN: SYSTEM
ENTRY_ORC_RAW: (none — CTL gate)
KB_CONSUMPTION: CONDITIONAL
MIN_INPUTS:
- START_UNIVERSE_ENGINE command
- ROOT_LINK_BASE_RAW
- TASK
OUTPUTS:
- READINESS trace (PASS/FAIL)
REQUIRED_GATES:
- CTL:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/01__READINESS_CHECK_CTL.md
- VAL: (none)
- QA:  (none)
DEFAULT_RETURN:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/00_INDEX/01__START_UNIVERSE_ENGINE.md
NOTES:
- Must pass before any execution pipeline.

---

### P-101 — MUSIC: GROUP → ALBUM (Blueprint)
PIPELINE_ID: UE.PIPE.MUSIC.GROUP_TO_ALBUM.101
NAME: Group to Album (Album blueprint planning)
DOMAIN: MUSIC
ENTRY_ORC_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/01__GROUP_TO_ALBUM_ORC.md
KB_CONSUMPTION: FALSE
MIN_INPUTS:
- group identity / style inputs
- album intent (mood, targets, count)
OUTPUTS:
- ALBUM_BLUEPRINT (document artifact)
REQUIRED_GATES:
- CTL:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/01__PROMPT_CONTRACT_CTL.md
- VAL: (optional by matrix)
- QA:  (optional by matrix)
DEFAULT_RETURN:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/01__GROUP_TO_ALBUM_ORC.md
NOTES:
- If variants strategy is needed, add it inside blueprint.

---

### P-102 — MUSIC: ALBUM → TRACK (Generation / Patch)
PIPELINE_ID: UE.PIPE.MUSIC.ALBUM_TO_TRACK.102
NAME: Album to Track (Generate candidate or patch one-axis)
DOMAIN: MUSIC
ENTRY_ORC_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/02__ALBUM_TO_TRACK_ORC.md
KB_CONSUMPTION: CONDITIONAL
MIN_INPUTS:
- album blueprint
- track slot intent
- if KB_CONSUMPTION TRUE: KB_SCOPE_RAW (or POET_PACK_RAW)
OUTPUTS:
- TRACK_CARD
- TRACK_PROMPT (or prompt-ready block)
REQUIRED_GATES:
- CTL:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/01__PROMPT_CONTRACT_CTL.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/06__FINGERPRINT_COLLISION_THRESHOLDS_CTL.md
- VAL:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/03__REPEAT_GUARD_VAL.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/05__COLLISION_BLOCKER_VAL.md
- QA: (optional by matrix)
DEFAULT_RETURN:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/02__ALBUM_TO_TRACK_ORC.md
NOTES:
- One-axis patch discipline applies when reworking.

---

### P-103 — MUSIC: TRACK TEST DOC GATE (Pre-release)
PIPELINE_ID: UE.PIPE.MUSIC.TRACK_TEST_GATE.103
NAME: Track Test Doc Gate (pre-pack validation gateway)
DOMAIN: MUSIC
ENTRY_ORC_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/03__TRACK_TEST_DOC_GATE_ORC.md
KB_CONSUMPTION: CONDITIONAL
MIN_INPUTS:
- TRACK_CARD + TRACK_PROMPT (or equivalent)
OUTPUTS:
- gate verdict + required fixes list
REQUIRED_GATES:
- CTL: (as chosen by matrix)
- VAL: (as chosen by matrix)
- QA:  (as chosen by matrix)
DEFAULT_RETURN:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/02__ALBUM_TO_TRACK_ORC.md
NOTES:
- Gateway used when matrix requires stronger assurance before packaging.

---

### P-104 — MUSIC: RELEASE PACK (Packaging)
PIPELINE_ID: UE.PIPE.MUSIC.RELEASE_PACK.104
NAME: Release Pack (variants + metadata + publish readiness)
DOMAIN: MUSIC
ENTRY_ORC_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/04__RELEASE_PACK_ORC.md
KB_CONSUMPTION: CONDITIONAL
MIN_INPUTS:
- TRACK_CARD (final candidate)
- variants intent (if any)
- if KB-consuming: KB_SCOPE_RAW / provenance markers
OUTPUTS:
- MUSIC_RELEASE_PACK artifact (publish-ready document set)
REQUIRED_GATES:
- CTL:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/13__CREDITS_METADATA_POLICY_CTL.md
- VAL:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/06__RELEASE_PACK_READY_VAL.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/09__CREDITS_RIGHTS_VAL.md
- QA:  (optional by matrix)
DEFAULT_RETURN:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/04__RELEASE_PACK_ORC.md

---

### P-105 — MUSIC: POET PACK (KB Corpus Intake)
PIPELINE_ID: UE.PIPE.MUSIC.POET_PACK.105
NAME: Poet Pack (KB-sourced corpus package)
DOMAIN: MUSIC
ENTRY_ORC_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/06__POET_PACK_ORC.md
KB_CONSUMPTION: TRUE
MIN_INPUTS:
- KB_SCOPE_RAW (source item/module)
- task intent (poet/work/selection constraints)
OUTPUTS:
- POET_PACK artifact with provenance + excerpt policy + handoff block
REQUIRED_GATES:
- CTL:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/05__POET_PD_POLICY_CTL.md
- VAL:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/04__PD_ONLY_VAL.md
- QA: (optional by matrix)
DEFAULT_RETURN:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/06__POET_PACK_ORC.md

---

## 4) REGISTRATION RULES (LAW)
### 4.1 When to add a pipeline record
Добавлять запись обязательно, если:
- создаётся новый ORC маршрут
- меняется набор обязательных гейтов
- пайплайн начинает/перестаёт потреблять KB
- пайплайн становится “дефолтным” при ambiguous routing

### 4.2 Pipeline record must be updated with CHANGE_ID
Любое изменение записи пайплайна в этом реестре требует:
- VERSION bump файла (как controlled document)
- CHANGE_NOTE + CHANGE_ID

### 4.3 No hidden routes
Запрещено ссылаться на ORC как на “разрешённый маршрут”, если он не зарегистрирован здесь.

---

## 5) DEPRECATION POLICY (LAW)
Если пайплайн заменяется:
- старая запись остаётся в реестре, но помечается как deprecated внутри NOTES
- добавляется replacement PIPELINE_ID и ENTRY_ORC_RAW
- обновление выполняется через CHANGE MANAGEMENT PROTOCOL

---

END.
