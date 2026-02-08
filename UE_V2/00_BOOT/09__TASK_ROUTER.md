# 09__TASK_ROUTER

SCOPE: UE_V2  
DOC_TYPE: BOOT / TASK_ROUTER  
VERSION: 1.2.0  
STATUS: ACTIVE  
MODE: REPO (USAGE-ONLY, NO-EDIT)  
NAV_RULE: Use RAW links only  
PURPOSE: Детерминированно преобразует TASK_TEXT в ROUTE_TOKEN и задаёт минимальный набор IDX/PIPE/проверок.

---

## [M] INPUTS
REQUIRED:
- TASK_TEXT

OPTIONAL:
- MODE_HINT: FAST | RELEASE_READY | MASTERPIECE
- constraints: platform, duration, style, references (и т.п.)

---

## [M] ROUTE_TOKEN (OUTPUT SHAPE)
ROUTE_TOKEN:
- DOMAIN
- ARTIFACT_TYPE
- MODE
- PIPE_SELECTED
- DEFAULT_ORC
- REQUIRED_IDX
- REQUIRED_CHECKS
- EXEC_MODE

---

## [M] DET RULES (NO GUESSING)
- Никаких обходов деревьев. Всё через NAV IDX.
- Если для выбранного DOMAIN нет IDX или PIPE → GAP (не STOP).
- STOP только если нет TASK_TEXT или если MUST_LOAD недоступен.

---

## [M] CLASSIFIERS (LIGHT)
ARTIFACT_TYPE:
- MUSIC_TRACK  -> если явно “трек/песня/лирика/суно”
- DOC          -> если “док/README/правила/шаблон/исправить документацию”
- VISUAL       -> если “обложка/баннер/картинка/кадры/видео/veo”

DOMAIN (минимум):
- DOM_AUD  -> музыка/аудио/лирика/сведение/мастер
- DOM_VIS  -> визуал/видео/обложки
- KB       -> KB/примеры/гейты/рубрики/калибровка
- PIPE     -> пайплайны/шаги/контракты
- CORE     -> boot/nav/log/общесистемное

MODE:
- если MODE_HINT задан → берём его
- иначе:
  - MUSIC_TRACK -> MASTERPIECE
  - DOC/PIPE/CORE/KB -> RELEASE_READY
  - VISUAL -> RELEASE_READY

EXEC_MODE:
- STEP_RUN (по умолчанию, чтобы работать “го”)
- FOCUS_LOOP включается только если пользователь явно просит “дожать до идеала”

---

## [M] PIPE SELECTION (CANON)
Если DOMAIN=DOM_AUD:
- PIPE_SELECTED = UE_V2/06_PIPE/20__PIPE_MUSIC_TRACK.md

Если DOMAIN=DOM_VIS:
- PIPE_SELECTED = UE_V2/06_PIPE/04__PIPE_VIS.md

Если DOMAIN=KB:
- PIPE_SELECTED = UE_V2/06_PIPE/02__PIPE_GAP.md

Если DOMAIN=PIPE или CORE:
- PIPE_SELECTED = UE_V2/06_PIPE/01__PIPE_DEFAULT.md

---

## [M] DEFAULT_ORC (CANON)
- По умолчанию: ORC = PIPE_DEFAULT routing (то есть оркестратор выбирается внутри пайпа по контракту)
- Явный DEFAULT_ORC тут НЕ фиксируем, чтобы не ломать доменные пайпы.

---

## [M] REQUIRED_IDX (MIN)
Всегда:
- UE_V2/04_NAV/00__NAV_ROOT.md

Плюс 1 доменный индекс:
- DOM_AUD -> UE_V2/07_DOM_AUD/00__INDEX_MANIFEST__DOM__AUD.md
- DOM_VIS -> UE_V2/08_DOM_VIS/00__INDEX_MANIFEST__DOM__VIS.md
- KB      -> UE_V2/05_KB/00__INDEX_MANIFEST__KB.md (если отсутствует → GAP)
- PIPE    -> UE_V2/06_PIPE/00__INDEX_MANIFEST__PIPE.md
- CORE    -> UE_V2/06_PIPE/00__INDEX_MANIFEST__PIPE.md

---

## [M] REQUIRED_CHECKS (MIN)
- NAV_ACCESS: доступ к NAV_ROOT + доменному IDX
- PIPE_ACCESS: доступ к PIPE_SELECTED
- LOG_ACCESS: доступ к UE_V2/14_LOG/00__INDEX_MANIFEST__LOG.md

---

## [M] ROUTER ALGO (DETERMINISTIC)
1) Если TASK_TEXT пустой → STOP (INPUT_ABSENT)
2) Определить ARTIFACT_TYPE по ключевым словам
3) Определить DOMAIN:
   - MUSIC_TRACK -> DOM_AUD
   - VISUAL      -> DOM_VIS
   - DOC + слова (boot/nav/log/idx/router/manifest) -> CORE
   - DOC + слова (pipe/pipeline/step-run/focus-loop) -> PIPE
   - DOC + слова (kb/gate/rubric/example) -> KB
   - иначе -> CORE
4) Выбрать MODE
5) Выбрать PIPE_SELECTED
6) Сформировать REQUIRED_IDX + REQUIRED_CHECKS
7) EXEC_MODE = STEP_RUN (по умолчанию)

---

## [M] START OUTPUT
Когда ROUTE_TOKEN сформирован, вернуть:
- ROUTE_TOKEN
- FIRST_STEP_PROMPT: "го"
