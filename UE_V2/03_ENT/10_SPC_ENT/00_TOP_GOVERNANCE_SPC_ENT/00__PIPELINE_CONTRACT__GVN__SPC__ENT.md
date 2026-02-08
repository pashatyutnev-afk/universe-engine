# 00__PIPELINE_CONTRACT__GVN__SPC_ENT

SCOPE: UE_V2  
DOC_TYPE: PIPELINE_CONTRACT (SPC_ENT / TOP_GOVERNANCE)  
UID: UE.V2.SPC.GVN.PIPE.001  
VERSION: 1.0.0  
STATUS: ACTIVE  
MODE: REPO (USAGE-ONLY, NO-EDIT)  
NAV_RULE: Use RAW links only  

PURPOSE:  
Этот контракт фиксирует “первого спеца” (TOP_GOVERNANCE SPC) как обязательную входную точку до любых ORC/ENG.  
Нужен, чтобы система не стартовала “в воздухе”, не пропускала REG/XREF/KB/PIPE/NAV/LOG и работала пошагово через "го".

---

## [M] ENTRY ROLE (SPC-FIRST)
ENTRY_SPC_ROLE:
- PRIMARY: GVN_MACHINE_ARCHITECT_SPC_ENT
- FALLBACK_1: GVN_GOVERNANCE_OWNER_SPC_ENT
- FALLBACK_2: GVN_DOC_CONTROLLER_SPC_ENT

RULE:
- Если PRIMARY недоступен/не найден, использовать следующий FALLBACK по порядку.
- Запрещено запускать ORC до выбора ENTRY_SPC_ROLE.

---

## [M] MIN_INPUTS
REQUIRED:
- TASK_TEXT

OPTIONAL:
- MODE_HINT (FAST|RELEASE_READY|MASTERPIECE)
- constraints (platform, duration, style, references)

---

## [M] OUTPUTS
GVN_SPC_OUTPUT:
- ROUTE_TOKEN (обязателен)
- ROUTE_DECISION (почему выбран такой маршрут)
- REQUIRED_IDX (какие IDX надо открыть на шаге NAV)
- REQUIRED_CHECKS (какие проверки обязательны)
- HANDOFF (куда передать управление после GVN_SPC)

---

## [M] DETERMINISTIC ROUTING RULES
Цель: один и тот же TASK_TEXT при одинаковых constraints даёт одинаковый ROUTE_TOKEN.

ROUTER_DECISION_ORDER:
1) DOMAIN
2) ARTIFACT_TYPE
3) MODE (если нет MODE_HINT → DEFAULT)
4) PIPE_SELECTED
5) DEFAULT_ORC
6) REQUIRED_IDX
7) REQUIRED_CHECKS
8) EXEC_MODE

DEFAULT_MODE:
- если MODE_HINT отсутствует → RELEASE_READY

---

## [M] DOMAIN DETECTION (MINIMAL)
DOMAIN rules (deterministic keywords):
- DOM_AUD: музыка, трек, вокал, бит, микс, мастер, loudness, bpm, стиль
- DOM_VIS: обложка, баннер, картинка, видео, кадр, shot, стиль, визуал
- DOM_LOR: лор, канон, персонаж, мир, арка, сцена, таймлайн
- SYS/STD/ENT: индекс, шаблон, контракт, правило, стандарт, сущности, паспорт
- KB: база знаний, пример, гейт, рубрика, калибровка, эталон

Если совпало несколько:
- приоритет: SYS/STD/ENT > KB > DOM_LOR > DOM_VIS > DOM_AUD

---

## [M] ARTIFACT_TYPE DETECTION (MINIMAL)
- MUSIC_TRACK: трек, музыка, instrumental, beat
- MUSIC_LYRICS: текст песни, куплет, припев, рифма
- VIS_ASSET: обложка, арт, баннер
- DOC_PATCH: исправить документ, переделать readme, обновить контракт
- INDEX_BUILD: индекс, манифест, manifest

---

## [M] PIPE SELECTION
PIPE_SELECTED rules:
- если DOMAIN = DOM_AUD → UE_V2/06_PIPE/20__PIPE_MUSIC_TRACK.md или UE_V2/06_PIPE/21__PIPE_MUSIC_LYRICS.md (по ARTIFACT_TYPE)
- если DOMAIN = DOM_VIS → UE_V2/06_PIPE/04__PIPE_VIS.md
- если DOMAIN = DOM_LOR → UE_V2/06_PIPE/05__PIPE_LOR.md
- если DOMAIN = KB → UE_V2/06_PIPE/02__PIPE_GAP.md (если не хватает KB) иначе UE_V2/06_PIPE/01__PIPE_DEFAULT.md
- если DOMAIN = SYS/STD/ENT → UE_V2/06_PIPE/01__PIPE_DEFAULT.md

EXEC_MODE:
- FAST → сокращённые проверки (но NAV/LOG не отключать)
- RELEASE_READY → полный стандартный прогон
- MASTERPIECE → плюс расширенный QA и PACK

---

## [M] REQUIRED IDX (NAV MUST CONFIRM)
REQUIRED_IDX is minimal set, chosen by DOMAIN:
- ALWAYS:
  - UE_V2/04_NAV/00__NAV_ROOT.md
  - UE_V2/06_PIPE/00__INDEX_MANIFEST__PIPE.md
  - UE_V2/14_LOG/00__INDEX_MANIFEST__LOG.md

- IF DOMAIN = DOM_AUD:
  - UE_V2/07_DOM_AUD/00__INDEX_MANIFEST__DOM__AUD.md

- IF DOMAIN = DOM_VIS:
  - UE_V2/08_DOM_VIS/00__INDEX_MANIFEST__DOM__VIS.md

- IF DOMAIN = DOM_LOR:
  - UE_V2/09_DOM_LOR/00__INDEX_MANIFEST__DOM__LOR.md

- IF DOMAIN = KB:
  - UE_V2/05_KB/00__INDEX_MANIFEST__KB.md  (если файл отсутствует → GAP)

- IF DOMAIN = SYS/STD/ENT:
  - UE_V2/03_ENT/00__INDEX_MANIFEST__ENT.md (если файл отсутствует → GAP)

NOTE:
- Если любого REQUIRED IDX нет по RAW → GAP (не STOP), кроме ALWAYS.

---

## [M] REQUIRED CHECKS
ALWAYS checks:
- ENTRYPOINT_CHECK: TASK_TEXT присутствует
- RAW_ACCESS_CHECK: доступ к MUST_LOAD и NAV_ROOT
- TRACE_ON: трасса включена
- FAIL_CODES_ON: коды ошибок включены

DOMAIN checks:
- DOM_AUD: AUD readiness (если есть соответствующий CTL gate)
- DOM_VIS: VIS readiness
- DOM_LOR: CANON lock rules
- KB: gate binding rules и rubric standard

---

## [M] HANDOFF RULE (SPC → ORC)
После формирования ROUTE_TOKEN:
- управление передаётся DEFAULT_ORC по PIPE_SELECTED через PIPE_DEFAULT.

DEFAULT_ORC rules:
- для DOM_AUD → ORC_A (если существует в домене) иначе ORC (default)
- для SYS/STD/ENT → ORC (default)
- для KB → ORC (default)

Если DEFAULT_ORC отсутствует в навигации/индексах → GAP.

---

## [M] STEP-RUN INTEGRATION
Система обязана работать пошагово через "го".

COMMAND:
- GVN_SPC завершает свою работу, выдаёт ROUTE_TOKEN и строку:
FIRST_STEP_PROMPT: го

Дальше пайплайн берёт ROUTE_TOKEN и запускает PIPE_DEFAULT (STEP-RUN).

---

## [M] STOP / GAP
STOP только если:
- input absent (нет TASK_TEXT)
- MUST_LOAD missing по RAW для BOOT/NAV/PIPE_DEFAULT/LOG_RULES

GAP если:
- отсутствует REQUIRED IDX по DOMAIN
- отсутствует доменный PIPE по PIPE_SELECTED
- отсутствует DEFAULT_ORC или обязательные сущности/панели для handoff

---

## [M] INTERFACES (RAW ONLY)
BOOT / ROUTER / NAV / PIPE / LOG:
- START (BOOT/ENTRYPOINT):
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00__START.md

- PIPE DEFAULT:
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/06_PIPE/01__PIPE_DEFAULT.md

- NAV ROOT:
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/04_NAV/00__NAV_ROOT.md

- LOG RULES (если актуальный путь в UE_V2 это 14_LOG, использовать его):
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/14_LOG/00__PIPELINE_CONTRACT__LOG.md

---

## [M] KB SCOPE (KB)
KB SCOPE (for this contract):
- Inputs: TASK_TEXT, MODE_HINT, constraints
- Outputs: ROUTE_TOKEN, REQUIRED_IDX, REQUIRED_CHECKS
- Boundaries: не исполняет пайплайн, только выбирает маршрут и handoff
- RAW References:
  - START, NAV_ROOT, PIPE_DEFAULT (см. INTERFACES)

---

## [M] GATES
PASS если:
- ENTRY_SPC_ROLE выбран
- ROUTE_TOKEN сформирован
- REQUIRED_IDX определён
- FIRST_STEP_PROMPT = "го" выдан

STOP если:
- нет TASK_TEXT
- MUST_LOAD missing (BOOT/NAV/PIPE_DEFAULT/LOG)

GAP если:
- REQUIRED IDX / PIPE / ORC не доступны по RAW

END.
