# 09__TASK_ROUTER

SCOPE: Universe Engine (UE_V2)  
DOC_TYPE: BOOT / ROUTER  
UID: UE.V2.BOOT.TASK_ROUTER.001  
VERSION: 1.2.0  
STATUS: ACTIVE  
MODE: REPO (USAGE-ONLY, NO-EDIT)  
NAV_RULE: Use RAW links only  
PURPOSE: Детерминированно превращает TASK_TEXT в ROUTE_TOKEN и гарантирует запуск “первого спеца” (SPC_FIRST) до любых ORC.

---

## [M] INTENT
TASK_ROUTER обязан:
- принять TASK_TEXT и минимальные optional hints,
- определить DOMAIN + ARTIFACT_TYPE + MODE,
- выбрать PIPE (дефолтный или доменный),
- назначить “первого спеца” (SPC_FIRST) и правила handoff,
- вернуть ROUTE_TOKEN, который дальше использует NAV + PIPE_DEFAULT,
- не засорять контекст (anti-noise).

---

## [M] INPUTS
REQUIRED:
- TASK_TEXT

OPTIONAL:
- MODE_HINT: FAST | RELEASE_READY | MASTERPIECE
- constraints:
  - platform (e.g. suno, veo, youtube, site, docs)
  - duration (sec/min)
  - style
  - references (links, assets)
  - language
  - “allow_mate” (если допустим мат в тексте)

---

## [M] OUTPUT
ROUTE_TOKEN (обязателен) — компактный объект маршрута.

---

## [M] ROUTE_TOKEN SCHEMA (CANON)
ROUTE_TOKEN:
- DOMAIN: one_of [DOC | AUD | VIS | LOR | REL | KB | NAV | PIPE | TKN | LEX | LOG]
- ARTIFACT_TYPE: short_code (e.g. DOC_FIX, README, SPEC, PROMPT, LYRICS, TRACK_BRIEF, PACK, INDEX)
- MODE: one_of [FAST | RELEASE_READY | MASTERPIECE] (default = RELEASE_READY)
- EXEC_MODE: one_of [STEP_RUN] (default = STEP_RUN)

- PIPE_SELECTED: RAW_PATH (default: UE_V2/06_PIPE/01__PIPE_DEFAULT.md)
- DEFAULT_ORC: RAW_PATH | NONE
- DEFAULT_SPC_FIRST: RAW_PATH (обязателен)
- SPC_FIRST_REQUIRED: true (обязателен, default = true)
- HANDOFF_ORDER: ordered list [SPC_FIRST, ORC, CTL, VAL, QA] (default)

- REQUIRED_IDX: list of RAW_PATH (минимум 1 доменный IDX)
- REQUIRED_CHECKS: list of short_codes (e.g. NAV_OK, REG_OK, XREF_OK, KB_OK, PIPE_OK, LOG_OK)
- REQUIRED_PANELS: list of RAW_PATH (если нужны панели/шаблоны)

- TARGET_FILES: list of RAW_PATH (1–3 файла максимум по anti-noise)
- NOTES: 0–3 bullets (коротко)

---

## [M] SPC_FIRST LAW (NON-NEGOTIABLE)
L1) **Перед любым ORC всегда должен быть SPC_FIRST**.  
L2) ROUTER обязан вернуть `DEFAULT_SPC_FIRST` и `SPC_FIRST_REQUIRED=true`.  
L3) Если SPC_FIRST не определён (RAW missing) → GAP.  
L4) SPC_FIRST не “должен угадываться”. Он выбирается по таблице ниже.

---

## [M] SPC_FIRST SELECTION TABLE
Выбор “первого спеца” делается по DOMAIN:

- DOMAIN = DOC  → SPC_FIRST = `UE_V2/03_SPC/??__SPC_DOC_FIRST.md`  
- DOMAIN = AUD  → SPC_FIRST = `UE_V2/03_SPC/??__SPC_AUD_FIRST.md`  
- DOMAIN = VIS  → SPC_FIRST = `UE_V2/03_SPC/??__SPC_VIS_FIRST.md`  
- DOMAIN = LOR  → SPC_FIRST = `UE_V2/03_SPC/??__SPC_LOR_FIRST.md`  
- DOMAIN = REL  → SPC_FIRST = `UE_V2/03_SPC/??__SPC_REL_FIRST.md`  
- DOMAIN = KB   → SPC_FIRST = `UE_V2/03_SPC/??__SPC_KB_FIRST.md`  
- DOMAIN = NAV  → SPC_FIRST = `UE_V2/03_SPC/??__SPC_NAV_FIRST.md`  
- DOMAIN = PIPE → SPC_FIRST = `UE_V2/03_SPC/??__SPC_PIPE_FIRST.md`  
- DOMAIN = TKN  → SPC_FIRST = `UE_V2/03_SPC/??__SPC_TKN_FIRST.md`  
- DOMAIN = LEX  → SPC_FIRST = `UE_V2/03_SPC/??__SPC_LEX_FIRST.md`  
- DOMAIN = LOG  → SPC_FIRST = `UE_V2/03_SPC/??__SPC_LOG_FIRST.md`

NOTE:
- Здесь указаны “слоты” (??), чтобы правило было каноническим.
- Реальные SPC_FIRST файлы должны существовать в репо и быть достижимы через IDX.
- Пока слоты не заполнены — ROUTER обязан вернуть GAP с кодом `GAP.SPC_FIRST_MISSING`.

---

## [M] DOMAIN DETECTION (DETERMINISTIC)
Определение DOMAIN идёт по приоритету:

D0) если constraints.platform указывает явно:
- suno/track/lyrics/mix/master → AUD
- veo/video/shot/prompt/8k → VIS
- lore/arc/canon → LOR
- release/pack/post → REL
- docs/readme/spec/template/index → DOC
- nav/index/manifest/root → NAV
- kb/example/gate/rubric → KB
- token/style_token/brief_token → TKN
- codes/abbr/lex → LEX
- logs/run_log/decision_log → LOG
- pipeline/pipe/step-run → PIPE

D1) иначе по ключевым словам в TASK_TEXT (первое совпадение выигрывает)
D2) иначе default DOMAIN = DOC

---

## [M] ARTIFACT_TYPE RULES
ARTIFACT_TYPE выбирается по шаблону задачи:

- “исправить/переписать документ” → DOC_FIX
- “README/манифест/индекс” → README или INDEX
- “сделай промпт/сценарий/шоты” → PROMPT (VIS)
- “сделай текст/лирику/трек” → LYRICS или TRACK_BRIEF (AUD)
- “пак/релиз/подготовка к публикации” → PACK (REL)

---

## [M] MODE RESOLUTION
MODE:
- если MODE_HINT задан → использовать его
- иначе:
  - FAST если “быстро/черновик/срочно”
  - MASTERPIECE если “шедевр/идеал/хит/максимум”
  - иначе RELEASE_READY

---

## [M] PIPE SELECTION (DETERMINISTIC)
PIPE_SELECTED:
- default: `UE_V2/06_PIPE/01__PIPE_DEFAULT.md`
- если DOMAIN имеет доменный PIPE и он существует в NAV/IDX → выбрать доменный
- если доменный отсутствует → default и пометить в NOTES “domain_pipe_missing”

EXEC_MODE всегда STEP_RUN.

---

## [M] REQUIRED_IDX (ANTI-NOISE)
REQUIRED_IDX должен включать:
- 1) NAV root (загружается на шаге NAV, не здесь)
- 2) **ровно один** доменный IDX (по DOMAIN)
- 3) optional: IDX для SPC/ORC если доменный IDX их не покрывает

ROUTER сам не “грузит” файлы — он только перечисляет, что нужно открыть дальше.

---

## [M] REQUIRED_CHECKS (MIN SET)
REQUIRED_CHECKS default:
- NAV_OK
- PIPE_OK
- LOG_OK

Если DOMAIN = KB → + KB_OK  
Если DOMAIN = REL → + REL_OK  
Если DOMAIN = VIS → + VIS_OK  
Если DOMAIN = AUD → + AUD_OK  
Если DOMAIN = LOR → + LOR_OK

---

## [M] HANDOFF RULE
H0) SPC_FIRST всегда первый.
H1) SPC_FIRST делает:
- нормализацию задачи,
- минимальные входы,
- выбор обязательных сущностей (ORC/CTL/VAL/QA) если нужно,
- формирует `SPC_DIRECTIVE_PACK` (коротко),
- возвращает управление PIPE_DEFAULT.

H2) ORC не запускается напрямую из ROUTER.

---

## [M] FAIL / GAP CODES (ROUTER LEVEL)
GAP conditions:
- GAP.SPC_FIRST_MISSING (нет конкретного SPC_FIRST файла)
- GAP.DOMAIN_IDX_MISSING (нет доменного индекса)
- GAP.DOMAIN_PIPE_MISSING (нет доменного пайпа, если он обязателен)
- GAP.NAV_ACCESS_UNCONFIRMED (не подтверждён доступ через IDX)

STOP conditions:
- STOP.INPUT_ABSENT (нет TASK_TEXT)

---

## [M] ROUTER OUTPUT TEMPLATE (STRICT)
ROUTE_TOKEN:
- DOMAIN: ...
- ARTIFACT_TYPE: ...
- MODE: ...
- EXEC_MODE: STEP_RUN
- PIPE_SELECTED: ...
- DEFAULT_ORC: ...
- DEFAULT_SPC_FIRST: ...
- SPC_FIRST_REQUIRED: true
- HANDOFF_ORDER: [SPC_FIRST, ORC, CTL, VAL, QA]
- REQUIRED_IDX: [...]
- REQUIRED_CHECKS: [...]
- REQUIRED_PANELS: [...]
- TARGET_FILES: [...]
- NOTES: [...]

---

## [M] EXAMPLE (MINIMAL)
TASK_TEXT: “исправим документацию, чтобы первым работал главный спец до оркестратора”

ROUTE_TOKEN:
- DOMAIN: DOC
- ARTIFACT_TYPE: DOC_FIX
- MODE: RELEASE_READY
- EXEC_MODE: STEP_RUN
- PIPE_SELECTED: UE_V2/06_PIPE/01__PIPE_DEFAULT.md
- DEFAULT_ORC: NONE
- DEFAULT_SPC_FIRST: UE_V2/03_SPC/??__SPC_DOC_FIRST.md
- SPC_FIRST_REQUIRED: true
- HANDOFF_ORDER: [SPC_FIRST, ORC, CTL, VAL, QA]
- REQUIRED_IDX: [UE_V2/00__INDEX_MANIFEST__DOC.md]
- REQUIRED_CHECKS: [NAV_OK, PIPE_OK, LOG_OK]
- REQUIRED_PANELS: []
- TARGET_FILES: [UE_V2/00_BOOT/09__TASK_ROUTER.md]
- NOTES: ["ensure SPC_FIRST stage exists", "no direct ORC call"]

---

## [M] GATES
PASS если:
- ROUTE_TOKEN сформирован
- DEFAULT_SPC_FIRST заполнен
- REQUIRED_IDX содержит 1 доменный IDX минимум
- PIPE_SELECTED задан

GAP если:
- SPC_FIRST слот не разрешён в реальный RAW_PATH
- доменный IDX отсутствует

STOP если:
- нет TASK_TEXT
