# 09__TASK_ROUTER

SCOPE: UE_V2  
DOC_TYPE: ROUTER (BOOT)  
UID: UE.V2.BOOT.ROUTER.009  
VERSION: 1.0.0  
STATUS: ACTIVE  
MODE: REPO (USAGE-ONLY, NO-EDIT)  
NAV_RULE: Use RAW links only  

PURPOSE:  
Детерминированно преобразует вход (TASK_TEXT + optional MODE_HINT + constraints) в ROUTE_TOKEN.  
Запрещает “вольную маршрутизацию”, пропуски REG/XREF/KB/PIPE/NAV/LOG и не допускает шумовую загрузку.

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
ROUTE_TOKEN (обязателен, всегда один):

ROUTE_TOKEN_SCHEMA:
- DOMAIN
- ARTIFACT_TYPE
- MODE
- PIPE_SELECTED
- DEFAULT_ORC
- REQUIRED_IDX
- REQUIRED_CHECKS
- EXEC_MODE

PLUS:
- ROUTE_DECISION (коротко, 3–7 строк: почему так)
- FIRST_STEP_PROMPT: го

---

## [M] ROUTER DECISION ORDER (DETERMINISTIC)
Решения делаются строго в порядке, без перескоков:

D0) INPUT_PRESENT
D1) DOMAIN
D2) ARTIFACT_TYPE
D3) MODE
D4) PIPE_SELECTED
D5) DEFAULT_ORC
D6) REQUIRED_IDX
D7) REQUIRED_CHECKS
D8) EXEC_MODE

RULE:
- если на шаге решение не может быть принято из-за отсутствия обязательного компонента навигации → GAP
- STOP только при отсутствии TASK_TEXT или при MUST_LOAD missing по RAW

---

## [M] D0 — ENTRYPOINT CHECK
ENTRYPOINT_CHECK:
- PASS если TASK_TEXT непустой
- STOP если TASK_TEXT отсутствует

---

## [M] D1 — DOMAIN DETECTION (MINIMAL, KEYWORDS)
DOMAIN_KEYWORDS:

SYS_ENT_STD:
- индекс, index, manifest, манифест
- шаблон, template
- контракт, contract
- стандарт, standard
- правило, law, policy
- сущность, entity, паспорт

KB:
- база знаний, knowledge base, kb
- пример, example
- гейт, gate
- рубрика, rubric
- калибровка, calibration
- эталон, exemplar

DOM_LOR:
- лор, lore
- канон, canon
- персонаж, character
- мир, world
- арка, arc
- сцена, scene
- таймлайн, timeline

DOM_VIS:
- обложка, cover
- баннер, banner
- картинка, image
- визуал, visual
- видео, video
- кадр, shot
- стиль картинки, style image

DOM_AUD:
- трек, track
- музыка, music
- вокал, vocal
- бит, beat
- припев, chorus
- куплет, verse
- микс, mix
- мастер, master
- loudness, bpm

TIEBREAK (если совпало несколько):
PRIORITY:
1) SYS_ENT_STD
2) KB
3) DOM_LOR
4) DOM_VIS
5) DOM_AUD

Если не совпало ничего:
- DOMAIN = SYS_ENT_STD (дефолт), но в ROUTE_DECISION отметить “no keyword match”.

---

## [M] D2 — ARTIFACT_TYPE DETECTION (MINIMAL)
ARTIFACT_TYPE rules:

Если DOMAIN = DOM_AUD:
- MUSIC_LYRICS: текст песни, lyrics, куплет, припев, рифма
- MUSIC_TRACK: трек, instrumental, бит, beat, музыка (если не MUSIC_LYRICS)

Если DOMAIN = DOM_VIS:
- VIS_ASSET: обложка, баннер, арт, image, cover, banner

Если DOMAIN = DOM_LOR:
- LORE_DOC: лор, канон, арка, сцена, персонаж, мир

Если DOMAIN = KB:
- KB_ITEM: пример, гейт, рубрика, калибровка, exemplar

Если DOMAIN = SYS_ENT_STD:
- DOC_PATCH: исправить, переделать, обновить, поправить, refactor doc
- INDEX_BUILD: индекс, манифест, manifest, registry view
- CONTRACT_BUILD: контракт, contract
- TEMPLATE_BUILD: шаблон, template
- DEFAULT: DOC_PATCH

---

## [M] D3 — MODE (EXEC QUALITY)
MODE:
- если MODE_HINT задан → MODE = MODE_HINT
- иначе MODE = RELEASE_READY

MODE_BEHAVIOR:
- FAST: минимум проверок, но NAV/LOG/TRACE/FAIL_CODES обязательны
- RELEASE_READY: стандартный прогон по PIPE_DEFAULT + доменный handoff
- MASTERPIECE: расширенный QA + PACK (если существует в домене)

---

## [M] D4 — PIPE_SELECTED
PIPE_SELECTED rules (строго по DOMAIN + ARTIFACT_TYPE):

- SYS_ENT_STD:
  - UE_V2/06_PIPE/01__PIPE_DEFAULT.md

- KB:
  - UE_V2/06_PIPE/01__PIPE_DEFAULT.md
  - если в REQUIRED_IDX/REQUIRED_CHECKS выясняется, что нужных KB панелей/сущностей нет → PIPE_SELECTED = UE_V2/06_PIPE/02__PIPE_GAP.md

- DOM_AUD:
  - если ARTIFACT_TYPE = MUSIC_LYRICS → UE_V2/06_PIPE/21__PIPE_MUSIC_LYRICS.md
  - если ARTIFACT_TYPE = MUSIC_TRACK → UE_V2/06_PIPE/20__PIPE_MUSIC_TRACK.md
  - иначе → UE_V2/06_PIPE/01__PIPE_DEFAULT.md

- DOM_VIS:
  - UE_V2/06_PIPE/04__PIPE_VIS.md

- DOM_LOR:
  - UE_V2/06_PIPE/05__PIPE_LOR.md

---

## [M] D5 — DEFAULT_ORC (HANDOFF TARGET)
DEFAULT_ORC rules:

- SYS_ENT_STD → DEFAULT_ORC = ORC_DEFAULT
- KB → DEFAULT_ORC = ORC_DEFAULT
- DOM_AUD → DEFAULT_ORC = ORC_AUD_DEFAULT
- DOM_VIS → DEFAULT_ORC = ORC_VIS_DEFAULT
- DOM_LOR → DEFAULT_ORC = ORC_LOR_DEFAULT

NOTE:
- Реальные ORC-энтити выбираются через доменный IDX на шаге NAV.
- Если доменный ORC не найден → GAP (не STOP), с указанием “DEFAULT_ORC missing”.

---

## [M] D6 — REQUIRED_IDX (NAV MUST CONFIRM)
REQUIRED_IDX_MINSET (ALWAYS):
- UE_V2/04_NAV/00__NAV_ROOT.md
- UE_V2/06_PIPE/00__INDEX_MANIFEST__PIPE.md
- UE_V2/14_LOG/00__INDEX_MANIFEST__LOG.md

DOMAIN IDX:
- если DOMAIN = SYS_ENT_STD → UE_V2/03_ENT/00__INDEX_MANIFEST__ENT.md
- если DOMAIN = KB → UE_V2/05_KB/00__INDEX_MANIFEST__KB.md
- если DOMAIN = DOM_AUD → UE_V2/07_DOM_AUD/00__INDEX_MANIFEST__DOM__AUD.md
- если DOMAIN = DOM_VIS → UE_V2/08_DOM_VIS/00__INDEX_MANIFEST__DOM__VIS.md
- если DOMAIN = DOM_LOR → UE_V2/09_DOM_LOR/00__INDEX_MANIFEST__DOM__LOR.md

RULE:
- ALWAYS элементы — обязательны (missing → STOP только если это MUST_LOAD по BOOT, иначе GAP по NAV)
- DOMAIN IDX — missing → GAP

---

## [M] D7 — REQUIRED_CHECKS
REQUIRED_CHECKS_ALWAYS:
- ENTRYPOINT_CHECK
- TRACE_ON
- FAIL_CODES_ON
- NAV_ACCESS_CONFIRM (REG/XREF/KB/PIPE/LOG reachability via IDX)
- NO_MASS_LOAD (ANTI_NOISE)

DOMAIN CHECKS (минимум):
- DOM_AUD: AUD_READINESS (если существует CTL gate, иначе “not found” → GAP)
- DOM_VIS: VIS_READINESS (аналогично)
- DOM_LOR: CANON_LOCK (если существует, иначе GAP)
- KB: KB_GATE_BINDING + QA_RUBRIC_STANDARD (если существуют, иначе GAP)
- SYS_ENT_STD: DOC_CONTRACT_COMPLIANCE (если существует, иначе допускается PASS без)

---

## [M] D8 — EXEC_MODE (STEP-RUN ALWAYS)
EXEC_MODE:
- ALWAYS: STEP_RUN
- COMMAND: “го” двигает систему на следующий шаг пайпа

FIRST_STEP_PROMPT:
го

---

## [M] ANTI-NOISE POLICY (HARD)
HARD RULES:
- Нельзя грузить деревья папок “про запас”.
- После ROUTE_TOKEN грузится только:
  - NAV_ROOT
  - REQUIRED_IDX (один доменный + ALWAYS)
  - 1–3 target файла по задаче (не больше)
- Запрещены обходы IDX.
- Любые “угадывания путей” запрещены: только RAW ссылки.

---

## [M] FAILURE MODES
STOP:
- TASK_TEXT отсутствует
- MUST_LOAD missing по RAW (BOOT/NAV/PIPE/LOG базовые)

GAP:
- отсутствует доменный IDX
- отсутствует доменный PIPE по PIPE_SELECTED
- отсутствует DEFAULT_ORC или обязательная сущность/панель для handoff
- marker not confirmed для MUST_LOAD

---

## [M] ROUTE_TOKEN EXAMPLE (FORMAT ONLY)
ROUTE_TOKEN:
- DOMAIN: DOM_AUD
- ARTIFACT_TYPE: MUSIC_LYRICS
- MODE: RELEASE_READY
- PIPE_SELECTED: UE_V2/06_PIPE/21__PIPE_MUSIC_LYRICS.md
- DEFAULT_ORC: ORC_AUD_DEFAULT
- REQUIRED_IDX:
  - UE_V2/04_NAV/00__NAV_ROOT.md
  - UE_V2/06_PIPE/00__INDEX_MANIFEST__PIPE.md
  - UE_V2/14_LOG/00__INDEX_MANIFEST__LOG.md
  - UE_V2/07_DOM_AUD/00__INDEX_MANIFEST__DOM__AUD.md
- REQUIRED_CHECKS:
  - ENTRYPOINT_CHECK
  - TRACE_ON
  - FAIL_CODES_ON
  - NAV_ACCESS_CONFIRM
  - NO_MASS_LOAD
  - AUD_READINESS
- EXEC_MODE: STEP_RUN

ROUTE_DECISION (example):
- TASK_TEXT содержит “трек/музыка/куплет” → DOMAIN=DOM_AUD
- найдены “текст/рифма/куплет” → ARTIFACT_TYPE=MUSIC_LYRICS
- MODE_HINT отсутствует → MODE=RELEASE_READY
- доменный пайп выбран по ARTIFACT_TYPE → PIPE_MUSIC_LYRICS
- дальше NAV подтвердит IDX/ORC и доступы

---

## [M] INTERFACES (RAW ONLY)
- START:
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/00__START.md

- NAV ROOT:
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/04_NAV/00__NAV_ROOT.md

- PIPE DEFAULT:
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/06_PIPE/01__PIPE_DEFAULT.md

- PIPE INDEX MANIFEST:
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/06_PIPE/00__INDEX_MANIFEST__PIPE.md

- LOG INDEX MANIFEST:
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/14_LOG/00__INDEX_MANIFEST__LOG.md

END.
