# 10__IDX_OPERATIONS

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: NAV / INDEX
UID: UE.V2.NAV.IDX_OPERATIONS.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Операционный индекс — минимальный путь рантайма. Сюда система заглядывает, чтобы не блуждать.

---

## [M] INTENT
Дать системе короткую карту "как работать" без мусора:
- что грузить всегда
- куда проваливаться по индексу
- как запускать пайп и фиксировать логи

---

## [M] MIN_RUNTIME_PATH (CANON)
1) ENTRY / BOOT:
- UE_V2/00_BOOT/00__START.md
- UE_V2/00_BOOT/08__RUNTIME_MANIFEST.md
- UE_V2/00_BOOT/09__TASK_ROUTER.md

2) NAV ROOT:
- UE_V2/04_NAV/00__NAV_ROOT.md

3) CORE IDX (ALWAYS):
- UE_V2/04_NAV/03__IDX_PIPE.md
- UE_V2/04_NAV/08__IDX_REG.md
- UE_V2/04_NAV/09__IDX_XREF.md
- UE_V2/04_NAV/04__IDX_KB.md
- UE_V2/04_NAV/11__IDX_LOG.md
- UE_V2/04_NAV/07__IDX_LEX.md

4) EXEC:
- UE_V2/06_PIPE/01__PIPE_DEFAULT.md (handoff to domain pipes)
- UE_V2/00_BOOT/10__STEP_RUN_PROTOCOL.md
- UE_V2/00_BOOT/12__FOCUS_LOOP_PROTOCOL.md
- UE_V2/00_BOOT/13__COMMANDS.md

---

## [M] DOMAIN IDX (ON-DEMAND)
MUSIC:
- UE_V2/04_NAV/12__IDX_MUSIC.md

VIS:
- UE_V2/04_NAV/06__IDX_VIS.md

AUD:
- UE_V2/04_NAV/05__IDX_AUD.md

LOR:
- (если будет IDX_LOR — добавить сюда)

REL:
- (если будет IDX_REL — добавить сюда)

---

## [M] LOAD_POLICY (ANTI-NOISE)
- ALWAYS: START + MANIFEST + ROUTER + NAV_ROOT
- THEN: открыть 1 доменный IDX из ROUTE_TOKEN (например IDX_MUSIC)
- THEN: открыть 1–3 целевых файла (PIPE + ORC + 1 QA/VAL)
- NEVER: обход IDX и сканирование деревьев папок

---

## [M] GATES
PASS если:
- путь достижим по RAW и позволяет выбрать PIPE/ORC/QA
GAP если:
- отсутствует доменный IDX, требуемый ROUTE_TOKEN
STOP если:
- нет START или NAV_ROOT
