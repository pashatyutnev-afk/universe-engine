# 09__TASK_ROUTER

SCOPE: UE_V2
DOC_TYPE: BOOT / ROUTER
UID: UE.V2.BOOT.ROUTER.009
VERSION: 2.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only

PURPOSE:
Детерминированно маршрутизирует TASK_TEXT в ROUTE_TOKEN:
- DOMAIN
- ARTIFACT_TYPE
- MODE (FAST|RELEASE_READY|MASTERPIECE)
- PIPE_SELECTED
- DEFAULT_ORC
- REQUIRED_IDX (минимальный набор IDX/manifest для доступа к REG/XREF/KB/PIPE/LOG)
- REQUIRED_CHECKS
- EXEC_MODE (STEP_RUN default)

---

## [M] INPUTS
- TASK_TEXT (required)
- OPTIONAL: MODE_HINT (FAST|RELEASE_READY|MASTERPIECE)
- OPTIONAL: constraints (platform, duration, style, references)

---

## [M] OUTPUT
ROUTE_TOKEN (required fields):
- DOMAIN
- ARTIFACT_TYPE
- MODE
- PIPE_SELECTED
- DEFAULT_ORC
- REQUIRED_IDX
- REQUIRED_CHECKS
- EXEC_MODE

---

## [M] ROUTER LAW (NO-GUESS / NO-NOISE)
- Routing must be deterministic: same TASK_TEXT -> same ROUTE_TOKEN.
- Do not load trees. Only:
  - START + RUNTIME_MANIFEST + ROUTER + NAV_ROOT
  - then one domain IDX/manifest
  - then 1–3 target files.
- No обходы IDX: доступ к REG/XREF/KB/PIPE/LOG подтверждается через REQUIRED_IDX.
- Default EXEC_MODE = STEP_RUN.

---

## [M] NORMALIZATION
N0) Trim TASK_TEXT.
N1) Lowercase copy for detection (original preserved).
N2) Extract keywords set: split by spaces + punctuation.
N3) If MODE_HINT not provided -> MODE = RELEASE_READY (default).
N4) If constraints include platform keywords -> bind to token (does not change routing unless explicitly stated in rules below).

---

## [M] DOMAIN DETECTION (priority order)
Return first match in this order:

D1) MUSIC:
If TASK_TEXT contains any of:
- "трек", "track", "песня", "lyrics", "куплет", "припев", "бит", "сведение", "мастеринг", "suno", "вокал"

D2) VIS:
If contains:
- "видео", "ролик", "veo", "prompt", "кадр", "шот", "shot", "camera", "8 секунд", "стиль", "cinematic", "рендер"

D3) LOR:
If contains:
- "лор", "lore", "канон", "сюжет", "персонаж", "арка", "сцена", "эпоха"

D4) REL:
If contains:
- "релиз", "release", "дроп", "пост", "публикация", "дистрибуция", "обложка", "метаданные"

D5) DOC:
If contains:
- "README", "док", "шаблон", "template", "протокол", "правило", "индекс", "manifest"

Else:
DOMAIN = DOC

---

## [M] ARTIFACT_TYPE DETECTION (by DOMAIN)
A1) If DOMAIN=MUSIC:
- If contains "текст", "lyrics", "куплет", "припев" -> ARTIFACT_TYPE = LYRICS
- Else -> ARTIFACT_TYPE = TRACK

A2) If DOMAIN=VIS:
- ARTIFACT_TYPE = VIS_PROMPT

A3) If DOMAIN=LOR:
- ARTIFACT_TYPE = LORE_DOC

A4) If DOMAIN=REL:
- ARTIFACT_TYPE = RELEASE_PACK

A5) If DOMAIN=DOC:
- ARTIFACT_TYPE = DOC_PATCH

---

## [M] PIPE SELECTION
P0) EXEC_MODE = STEP_RUN

P1) If DOMAIN=MUSIC:
- If ARTIFACT_TYPE=TRACK -> PIPE_SELECTED = UE_V2/06_PIPE/20__PIPE_MUSIC_TRACK.md
- If ARTIFACT_TYPE=LYRICS -> PIPE_SELECTED = UE_V2/06_PIPE/21__PIPE_MUSIC_LYRICS.md
- Else -> PIPE_SELECTED = UE_V2/06_PIPE/01__PIPE_DEFAULT.md

P2) If DOMAIN=VIS:
- PIPE_SELECTED = UE_V2/06_PIPE/04__PIPE_VIS.md

P3) If DOMAIN=LOR:
- PIPE_SELECTED = UE_V2/06_PIPE/05__PIPE_LOR.md

P4) If DOMAIN=REL:
- PIPE_SELECTED = UE_V2/06_PIPE/14__PIPE_REL.md

P5) If DOMAIN=DOC:
- PIPE_SELECTED = UE_V2/06_PIPE/01__PIPE_DEFAULT.md

---

## [M] DEFAULT ORC (deterministic)
O1) DOMAIN=MUSIC  -> DEFAULT_ORC = ORC_MUSIC
O2) DOMAIN=VIS    -> DEFAULT_ORC = ORC_VIS
O3) DOMAIN=LOR    -> DEFAULT_ORC = ORC_LOR
O4) DOMAIN=REL    -> DEFAULT_ORC = ORC_REL
O5) DOMAIN=DOC    -> DEFAULT_ORC = ORC_DEFAULT

NOTE:
DEFAULT_ORC is a role-token. Реальная сущность/файл ORC берётся через MUST_LOAD_SET из RUNTIME_MANIFEST + NAV lookup.
Роутер НЕ хардкодит путь к сущности, чтобы не ломаться при реорганизации дерева.

---

## [M] REQUIRED_IDX (minimum access coverage)
Всегда включать:
- UE_V2/04_NAV/00__NAV_ROOT.md
- UE_V2/06_PIPE/00__PIPELINE_CONTRACT__PIPE.md
- UE_V2/06_PIPE/00__INDEX_MANIFEST__PIPE.md
- UE_V2/14_LOG/00__INDEX_MANIFEST__LOG.md

Доменные добавки:
- If DOMAIN=MUSIC:
  - UE_V2/07_DOM_AUD/00__INDEX_MANIFEST__DOM__AUD.md
  - UE_V2/07_DOM_AUD/00__PIPELINE_CONTRACT__DOM__AUD.md
- If DOMAIN=VIS:
  - UE_V2/08_DOM_VIS/00__INDEX_MANIFEST__DOM__VIS.md
  - UE_V2/08_DOM_VIS/00__PIPELINE_CONTRACT__DOM__VIS.md
- If DOMAIN=LOR:
  - UE_V2/09_DOM_LOR/00__INDEX_MANIFEST__DOM__LOR.md
  - UE_V2/09_DOM_LOR/00__PIPELINE_CONTRACT__DOM__LOR.md
- If DOMAIN=REL:
  - UE_V2/10_REL/00__INDEX_MANIFEST__REL.md
  - UE_V2/10_REL/00__PIPELINE_CONTRACT__REL.md
- If DOMAIN=DOC:
  - UE_V2/00__INDEX_MANIFEST__UE_V2.md

KB/XREF coverage (required for all domains if KB is referenced in TASK_TEXT):
If TASK_TEXT contains "kb", "пример", "example", "gate", "gates", "xref":
- add: UE_V2/05_KB/00__INDEX_MANIFEST__KB.md (if exists via NAV_ROOT; else GAP handled by START rules)

---

## [M] REQUIRED_CHECKS
Всегда:
- CHECK_NAV_ROOT_ACCESS
- CHECK_PIPE_DEFAULT_ACCESS
- CHECK_LOG_ACCESS

Доменные:
- MUSIC: CHECK_DOM_AUD_ACCESS
- VIS:   CHECK_DOM_VIS_ACCESS
- LOR:   CHECK_DOM_LOR_ACCESS
- REL:   CHECK_REL_ACCESS
- DOC:   CHECK_UE_V2_MANIFEST_ACCESS

---

## [M] MODE RESOLUTION
If MODE_HINT provided and valid -> MODE = MODE_HINT
Else:
- If TASK_TEXT contains "быстро", "fast", "черновик" -> MODE=FAST
- If contains "шедевр", "masterpiece", "идеал", "максимум" -> MODE=MASTERPIECE
- Else MODE=RELEASE_READY

---

## [M] ROUTE_TOKEN TEMPLATE (final)
ROUTE_TOKEN = {
  DOMAIN: <DOMAIN>,
  ARTIFACT_TYPE: <ARTIFACT_TYPE>,
  MODE: <MODE>,
  PIPE_SELECTED: <PIPE_SELECTED>,
  DEFAULT_ORC: <DEFAULT_ORC>,
  REQUIRED_IDX: [ ... ],
  REQUIRED_CHECKS: [ ... ],
  EXEC_MODE: "STEP_RUN"
}

---

## [M] FAIL / GAP CONDITIONS (router-side)
STOP only if:
- TASK_TEXT absent

GAP if:
- PIPE_SELECTED missing/unreachable by RAW
- NAV_ROOT missing/unreachable by RAW
- required domain manifest missing/unreachable by RAW
(Resolution handled by START: report GAP with missing RAW path)

---
