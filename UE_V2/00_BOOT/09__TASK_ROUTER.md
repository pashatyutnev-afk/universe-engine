# 09__TASK_ROUTER

SCOPE: UE_V2
DOC_TYPE: BOOT / ROUTER
UID: UE.V2.BOOT.ROUTER.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only

PURPOSE:
Детерминированно формирует ROUTE_TOKEN.
Гарантирует, что работа всегда начинается с PRIMARY_SPC (главный SPC),
а затем передаётся в нужный домен / пайплайн.

---

## [M] INPUTS
REQUIRED:
- TASK_TEXT

OPTIONAL:
- MODE_HINT: FAST | RELEASE_READY | MASTERPIECE
- constraints:
  - platform
  - duration
  - style
  - references

---

## [M] OUTPUT
ROUTE_TOKEN:
- DOMAIN
- ARTIFACT_TYPE
- MODE
- PIPE_SELECTED
- EXEC_MODE
- PRIMARY_SPC
- DEFAULT_ORC
- REQUIRED_IDX
- REQUIRED_CHECKS
- NOTES (short)

---

## [M] HARD RULES (NON-NEGOTIABLE)
R1) PRIMARY_SPC always present:
- Любая задача обязана начинаться с главного SPC (governance entrypoint).
- Запрещено начинать сразу с ORC/PIPE.

R2) Determinism:
- Один и тот же TASK_TEXT + MODE_HINT => один и тот же ROUTE_TOKEN.
- Если есть сомнение между 2 доменами — выбираем более общий PIPE_DEFAULT + DOMAIN_PLUGIN (если есть),
  иначе ставим GAP.

R3) Anti-noise:
- ROUTER не грузит деревья.
- ROUTER возвращает только ROUTE_TOKEN и короткую инструкцию "го".

---

## [M] PRIMARY_SPC (GLOBAL ENTRY)
PRIMARY_SPC_PATH:
- UE_V2/03_ENT/10_SPC_ENT/00_TOP_GOVERNANCE_SPC_ENT/01_GVN_MACHINE_ARCHITECT_SPC_ENT

PRIMARY_SPC_ROLE:
- принимает TASK_TEXT
- проверяет MIN_INPUTS
- нормализует запрос (без потери смысла)
- инициирует доменный SPC/ORC по ROUTE_TOKEN
- контролирует что NAV/IDX/LOG не пропущены

---

## [M] CLASSIFICATION (DOMAIN / ARTIFACT_TYPE)

### ARTIFACT_TYPE
T1) MUSIC_TRACK:
если в TASK_TEXT есть (одно из):
- трек, track, песня, куплет, припев, бит, музыка, вокал

T2) DOC:
если в TASK_TEXT есть:
- документация, README, шаблон, контракт, индекс, manifest, policy, standard

T3) VISUAL:
если в TASK_TEXT есть:
- видео, кадр, промпт, shot, сцена, клип, обложка

Иначе:
- ARTIFACT_TYPE = DOC (по умолчанию, самый безопасный)

### DOMAIN
D1) DOM_AUD:
если ARTIFACT_TYPE = MUSIC_TRACK
или если в TASK_TEXT есть: микс, мастеринг, лирика, bpm, жанр

D2) DOM_VIS:
если ARTIFACT_TYPE = VISUAL

D3) DOM_LOR:
если в TASK_TEXT есть: лор, канон, персонаж, раса, планета, хроника

D4) SYS/STD/ENT/NAV/KB/PIPE/LOG:
если в TASK_TEXT есть явные маркеры папок/слоёв (boot, nav, kb, pipe, log, ent, reg, xref)

Иначе:
- DOMAIN = SYS (общесистемная обработка через PIPE_DEFAULT)

---

## [M] PIPE SELECTION
P1) If ARTIFACT_TYPE = MUSIC_TRACK:
- PIPE_SELECTED = UE_V2/06_PIPE/20__PIPE_MUSIC_TRACK.md

P2) If ARTIFACT_TYPE = DOC and TASK_TEXT про boot/nav/idx/router/log:
- PIPE_SELECTED = UE_V2/06_PIPE/01__PIPE_DEFAULT.md

P3) If ARTIFACT_TYPE = VISUAL:
- PIPE_SELECTED = UE_V2/06_PIPE/01__PIPE_DEFAULT.md
  (дальше доменный handoff через DOMAIN_PLUGIN при наличии)

P4) Fallback:
- PIPE_SELECTED = UE_V2/06_PIPE/01__PIPE_DEFAULT.md

---

## [M] REQUIRED_IDX (NAV GUARANTEE)
ROUTER должен назначить минимум один IDX, чтобы NAV мог подтвердить доступ к REG/XREF/KB/PIPE/LOG.

IDX_RULE:
- если PIPE_SELECTED в 06_PIPE -> REQUIRED_IDX включает:
  - UE_V2/06_PIPE/00__INDEX_MANIFEST__PIPE.md
  - UE_V2/04_NAV/03__IDX_PIPE.md

- если DOMAIN = DOM_AUD -> REQUIRED_IDX добавляет:
  - UE_V2/07_DOM_AUD/00__INDEX_MANIFEST__DOM__AUD.md

- если DOMAIN = DOM_VIS -> REQUIRED_IDX добавляет:
  - UE_V2/08_DOM_VIS/00__INDEX_MANIFEST__DOM__VIS.md

- если DOMAIN = DOM_LOR -> REQUIRED_IDX добавляет:
  - UE_V2/09_DOM_LOR/00__INDEX_MANIFEST__DOM__LOR.md

Примечание:
Если нужного доменного INDEX_MANIFEST нет — ставим GAP.

---

## [M] REQUIRED_CHECKS (MIN SET)
DEFAULT REQUIRED_CHECKS:
- ENTRYPOINT_CHECK (TASK_TEXT present)
- MUST_LOAD_AVAILABLE (BOOT manifest reachable)
- NAV_ROOT_AVAILABLE
- PIPE_DEFAULT_AVAILABLE
- LOG_AVAILABLE

If ARTIFACT_TYPE = MUSIC_TRACK add:
- SUNO_NO_EXCLAMATION (если применимо в твоих правилах контента)

---

## [M] MODE + EXEC_MODE
MODE (from MODE_HINT):
- FAST -> MODE=FAST
- RELEASE_READY -> MODE=RELEASE_READY
- MASTERPIECE -> MODE=MASTERPIECE
- else -> MODE=RELEASE_READY (default)

EXEC_MODE:
- STEP_RUN (always default)
(дальше управляется командами из COMMANDS.md)

---

## [M] DEFAULT_ORC
DEFAULT_ORC_RULE:
- если DOMAIN = DOM_AUD -> DEFAULT_ORC = "ORC_AUD"
- если DOMAIN = DOM_VIS -> DEFAULT_ORC = "ORC_VIS"
- если DOMAIN = DOM_LOR -> DEFAULT_ORC = "ORC_LOR"
- иначе -> DEFAULT_ORC = "ORC_DEFAULT"

Если соответствующая ORC сущность не найдена через IDX — GAP.

---

## [M] ROUTE_TOKEN TEMPLATE (FINAL)
ROUTE_TOKEN = {
  DOMAIN,
  ARTIFACT_TYPE,
  MODE,
  PIPE_SELECTED,
  EXEC_MODE: "STEP_RUN",
  PRIMARY_SPC: PRIMARY_SPC_PATH,
  DEFAULT_ORC,
  REQUIRED_IDX: [list],
  REQUIRED_CHECKS: [list],
  NOTES
}

---

## [M] FAIL / GAP
STOP:
- TASK_TEXT отсутствует

GAP:
- отсутствует доменный INDEX_MANIFEST для выбранного DOMAIN
- отсутствует PIPE_SELECTED
- невозможно подтвердить PRIMARY_SPC_PATH (путь/сущность не существует)

---

## [M] ROUTER RETURN (START OUTPUT)
Возвращай только:
- ROUTE_TOKEN
- FIRST_STEP_PROMPT: "го"
- (без справок и длинных объяснений)
