# 08__RUNTIME_MANIFEST

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: BOOT / MANIFEST
UID: UE.V2.BOOT.RUNTIME_MANIFEST.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Define MUST_LOAD ядро рантайма (минимальные файлы), без которых запуск запрещён. Доменные IDX грузятся on-demand.

---

## [M] INTENT
Определить минимальный набор файлов для запуска, чтобы:
- система не прошла мимо REG/XREF/KB/PIPE/NAV/LOG
- контекст не засорялся
- доменные части подключались строго по ROUTE_TOKEN

---

## [M] RULES
1) MUST_LOAD подхватывается в начале каждой задачи.
2) Загружается только MUST_LOAD + (domain IDX по ROUTE_TOKEN) + 1–3 целевых файла.
3) ROOT_INDEX используется только как “доступ к RAW”, не как логика.
4) Если любой MUST_LOAD недоступен по RAW — STOP.
5) Любой файл вне MUST_LOAD допускается только через NAV_ROOT → IDX_* → TARGET.
6) Доменные IDX НЕ входят в MUST_LOAD, они грузятся on-demand по ROUTE_TOKEN.REQUIRED_IDX.

---

## [M] MUST_LOAD_SET (PATH_REF)
BOOT:
- UE_V2/00_BOOT/00__START.md
- UE_V2/00_BOOT/01__BOOT_SEQ.md
- UE_V2/00_BOOT/02__STOP_GAP.md
- UE_V2/00_BOOT/06__TRACE.md
- UE_V2/00_BOOT/07__FAIL_CODES.md
- UE_V2/00_BOOT/08__RUNTIME_MANIFEST.md
- UE_V2/00_BOOT/09__TASK_ROUTER.md
- UE_V2/00_BOOT/10__STEP_RUN_PROTOCOL.md
- UE_V2/00_BOOT/12__FOCUS_LOOP_PROTOCOL.md
- UE_V2/00_BOOT/13__COMMANDS.md

STD ядро:
- UE_V2/02_STD/04__MARKERS.md
- UE_V2/02_STD/05__NAV_RULES.md
- UE_V2/02_STD/09__GATES.md
- UE_V2/02_STD/12__NOISE_BUDGET.md
- UE_V2/02_STD/14__CONTRIBUTION_TOKEN_FMT.md
- UE_V2/02_STD/15__STEP_TOKEN_SET.md
- UE_V2/02_STD/17__QUESTIONS_GATE.md
- UE_V2/02_STD/18__PIPELINE_STAGE_MODEL.md
- UE_V2/02_STD/19__IO_TYPES.md
- UE_V2/02_STD/16__COVERAGE_RULES.md

NAV ядро:
- UE_V2/04_NAV/00__NAV_ROOT.md
- UE_V2/04_NAV/10__IDX_OPERATIONS.md
- UE_V2/04_NAV/08__IDX_REG.md
- UE_V2/04_NAV/09__IDX_XREF.md
- UE_V2/04_NAV/03__IDX_PIPE.md
- UE_V2/04_NAV/04__IDX_KB.md
- UE_V2/04_NAV/11__IDX_LOG.md
- UE_V2/04_NAV/07__IDX_LEX.md

PIPE ядро:
- UE_V2/06_PIPE/00__PIPE_INDEX.md
- UE_V2/06_PIPE/01__PIPE_DEFAULT.md
- UE_V2/06_PIPE/02__PIPE_GAP.md
- UE_V2/06_PIPE/06__CTL_READINESS.md
- UE_V2/06_PIPE/07__CTL_NOISE.md
- UE_V2/06_PIPE/15__PIPE_STEP_RUN.md
- UE_V2/06_PIPE/16__PIPE_FOCUS_LOOP.md
- UE_V2/06_PIPE/17__VAL_CHAIN_COMPLETENESS.md
- UE_V2/06_PIPE/18__CTL_COVERAGE_GATE.md
- UE_V2/06_PIPE/13__SIGNOFF.md

KB ядро:
- UE_V2/05_KB/00__KB_START.md
- UE_V2/05_KB/01__KB_RULES.md
- UE_V2/05_KB/02__KB_INPUTS.md
- UE_V2/05_KB/03__KB_OUTPUTS.md
- UE_V2/05_KB/04__KB_BOUNDARIES.md
- UE_V2/05_KB/08__KB_SOURCES.md
- UE_V2/05_KB/09__KB_SCOPE_PROFILES.md

LOG ядро:
- UE_V2/12_LOG/00__LOG_RULES.md
- UE_V2/12_LOG/01__RUN_LOG.md
- UE_V2/12_LOG/02__CHANGE_LOG.md
- UE_V2/12_LOG/03__TOKEN_ARCHIVE.md
- UE_V2/12_LOG/04__DECISION_LOG.md

---

## [M] DOMAIN_IDX_POLICY (ON-DEMAND)
- ROUTE_TOKEN.REQUIRED_IDX может содержать доменные индексы:
  - UE_V2/04_NAV/12__IDX_MUSIC.md
  - UE_V2/04_NAV/05__IDX_AUD.md
  - UE_V2/04_NAV/06__IDX_VIS.md
  - UE_V2/04_NAV/(IDX_LOR / IDX_REL если появятся)
- Эти файлы не MUST_LOAD. Они читаются только когда DOMAIN требует.

---

## [M] LOAD_POLICY
- DEFAULT: грузим MUST_LOAD_SET один раз на старт задачи.
- PER_STEP: перечитываем только нужные MUST_LOAD, не “всё подряд”.
- CONTEXT_BUDGET: если MUST_LOAD не помещается — REWORK (уплотнить тексты MUST_LOAD).

---

## [M] GATES
PASS если:
- все MUST_LOAD доступны по RAW
- NAV_ROOT достижим
- PIPE_DEFAULT достижим
- LOG ядро доступно
STOP если:
- любой MUST_LOAD missing
- marker not confirmed в MUST_LOAD
- input absent (нет задачи)
GAP если:
- ROUTE_TOKEN требует доменный IDX/PIPE, а их нет
