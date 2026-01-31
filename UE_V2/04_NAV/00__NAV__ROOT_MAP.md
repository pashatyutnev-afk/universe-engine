# 00__NAV_ROOT

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: NAV / ROOT
UID: UE.V2.NAV.ROOT.001
VERSION: 1.2.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Корневая карта навигации рантайма. Определяет минимальные входы (IDX) и запрещает обход индексов.

---

## [M] INTENT
Дать системе короткий и стабильный маршрут:
- куда идти за сущностями/картами/KB/пайпами/логами
- как не засорять контекст
- как быстро находить нужные файлы через индексы

---

## [M] MIN_RUNTIME_PATH (CANON)
1) START:
- UE_V2/00_BOOT/00__START.md
- UE_V2/00_BOOT/08__RUNTIME_MANIFEST.md
- UE_V2/00_BOOT/09__TASK_ROUTER.md

2) NAV ROOT:
- UE_V2/04_NAV/00__NAV_ROOT.md

3) OPERATIONS ядро:
- UE_V2/04_NAV/10__IDX_OPERATIONS.md

4) EXEC:
- UE_V2/04_NAV/03__IDX_PIPE.md -> выбрать PIPE
- доменный IDX -> выбрать доменные файлы (AUD/VIS/LOR/REL/MUSIC)
- UE_V2/04_NAV/11__IDX_LOG.md -> фиксация токенов/решений/изменений

---

## [M] IDX LIST (ENTRYPOINTS)
BOOT:
- UE_V2/04_NAV/01__IDX_BOOT.md

ENTITIES (контракты/модель):
- UE_V2/04_NAV/02__IDX_ENT.md

PIPE:
- UE_V2/04_NAV/03__IDX_PIPE.md

KB:
- UE_V2/04_NAV/04__IDX_KB.md

AUD domain:
- UE_V2/04_NAV/05__IDX_AUD.md

VIS domain:
- UE_V2/04_NAV/06__IDX_VIS.md

LEX:
- UE_V2/04_NAV/07__IDX_LEX.md

OPERATIONS (минимальный путь):
- UE_V2/04_NAV/10__IDX_OPERATIONS.md

REG (реестр совместимости):
- UE_V2/04_NAV/08__IDX_REG.md

XREF (карты связности):
- UE_V2/04_NAV/09__IDX_XREF.md

LOG (токены/решения/изменения):
- UE_V2/04_NAV/11__IDX_LOG.md

MUSIC domain:
- UE_V2/04_NAV/12__IDX_MUSIC.md

---

## [M] NAV POLICY (ANTI-NOISE)
1) Любой переход вглубь делается только через IDX_*.
2) Запрещено:
   - сканировать дерево папок
   - тащить много файлов в контекст "на всякий случай"
3) DEFAULT: открыть NAV_ROOT -> затем один нужный IDX -> затем 1–3 целевых файла.
4) ROOT_INDEX не используется как навигация (LAW_16). Он только даёт RAW-доступ.

---

## [M] HOW TO FIND THINGS (FAST)
- Нужны правила/законы: IDX_BOOT / IDX_ENT / KB
- Нужны сущности и совместимость: IDX_REG + IDX_XREF
- Нужны пайпы: IDX_PIPE
- Нужны логи/токены: IDX_LOG
- Нужен минимальный "как работать": IDX_OPERATIONS
- Нужна музыка: IDX_MUSIC

---

## [M] GATES
PASS если:
- все IDX из IDX LIST доступны по RAW
GAP если:
- отсутствует доменный IDX (например MUSIC) и он нужен по ROUTE_TOKEN
STOP если:
- NAV_ROOT недоступен при запуске
