# FILE: UE_V2/04_NAV/00__NAV_ROOT.md
SCOPE: UE_V2
LAYER: 04_NAV
DOC_TYPE: NAV_ROOT
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.1.0
UID: UE.V2.NAV.ROOT.001
OWNER: SYSTEM
TITLE: NAV ROOT (SMALL)

## MARKERS
- [M] INTENT
- [M] NAV_RULES
- [M] ENTRYPOINTS
- [M] ACCESS_CHECKS
- [M] ROUTE_MAP
- [M] STOP_CONDITIONS

---

## [M] INTENT
Единственный корневой NAV-узел UE_V2.
Содержит только “малые” входы (IDX) и панель проверки доступа к слоям (REG/XREF/KB/PIPE/LOG и домены).
Никакого контента, правил или “толстых” индексов.

---

## [M] NAV_RULES
1) Навигация рантайма по UE_V2: только через:
   START → ROUTER → REQUIRED_IDX → (KEY→RAW via ROOT INDEX_MANIFEST) → TARGET
2) 04_NAV хранит только:
   - точки входа (IDX_*)
   - панель обязательных доступов (ACCESS_CHECKS)
3) Индексы (IDX_*) не содержат правил/контента. Только ссылки + 1 строка назначения.
4) Запрещены “гигантские” общие индексы (BLOAT).
5) Если нужной ссылки/слоя нет → GAP (фиксировать дыру, не обходить напрямую).

---

## [M] ENTRYPOINTS
SMALL IDX entrypoints for ROUTER and STEP-RUN:

- IDX_BOOT: UE_V2/04_NAV/01__IDX_BOOT.md
- IDX_ENT:  UE_V2/04_NAV/02__IDX_ENT.md
- IDX_PIPE: UE_V2/04_NAV/03__IDX_PIPE.md
- IDX_KB:   UE_V2/04_NAV/04__IDX_KB.md
- IDX_AUD:  UE_V2/04_NAV/05__IDX_AUD.md
- IDX_VIS:  UE_V2/04_NAV/06__IDX_VIS.md
- IDX_LEX:  UE_V2/04_NAV/07__IDX_LEX.md

NOTE:
- Если добавляется новый домен/семейство — добавляется новый IDX_* (малый).
- NAV_ROOT не расширяется “всё-в-одном”.

---

## [M] ACCESS_CHECKS
Цель: подтвердить, что рантайм реально может добраться до слоёв REG/XREF/KB/PIPE/LOG и доменных панелей через зарегистрированные LAYER INDEX MANIFEST.

### [M] REQUIRED_LAYERS (MUST_HAVE)
Если любой RAW missing → GAP (не обходить).

- KEY: UEV2.BOOT.INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/00__INDEX_MANIFEST__BOOT.md
  PURPOSE: BOOT layer registry

- KEY: UEV2.SYS.INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/00__INDEX_MANIFEST__SYS.md
  PURPOSE: SYS layer registry

- KEY: UEV2.STD.INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/02_STD/00__INDEX_MANIFEST__STD.md
  PURPOSE: STD layer registry

- KEY: UEV2.ENT.INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/00__INDEX_MANIFEST__ENT.md
  PURPOSE: ENT layer registry

- KEY: UEV2.NAV.INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/04_NAV/00__INDEX_MANIFEST__NAV.md
  PURPOSE: NAV layer registry

- KEY: UEV2.KB.INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/05_KB/00__INDEX_MANIFEST__KB.md
  PURPOSE: KB layer registry

- KEY: UEV2.PIPE.INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/06_PIPE/00__INDEX_MANIFEST__PIPE.md
  PURPOSE: PIPE layer registry

- KEY: UEV2.DOM.AUD.INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/07_DOM_AUD/00__INDEX_MANIFEST__DOM__AUD.md
  PURPOSE: Domain AUD registry

- KEY: UEV2.DOM.VIS.INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/08_DOM_VIS/00__INDEX_MANIFEST__DOM__VIS.md
  PURPOSE: Domain VIS registry

- KEY: UEV2.DOM.LOR.INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/09_DOM_LOR/00__INDEX_MANIFEST__DOM__LOR.md
  PURPOSE: Domain LOR registry

- KEY: UEV2.REL.INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/10_REL/00__INDEX_MANIFEST__REL.md
  PURPOSE: REL layer registry

- KEY: UEV2.TKN.INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/11_TKN/00__INDEX_MANIFEST__TKN.md
  PURPOSE: TKN layer registry

- KEY: UEV2.LEX.INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/12_LEX/00__INDEX_MANIFEST__LEX.md
  PURPOSE: LEX layer registry

- KEY: UEV2.STR.PNT.INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/13_STR_PNT/00__INDEX_MANIFEST__STR__PNT.md
  PURPOSE: STR_PNT layer registry

- KEY: UEV2.LOG.INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/14_LOG/00__INDEX_MANIFEST__LOG.md
  PURPOSE: LOG layer registry

### [M] ACCESS_CHECK_PROTOCOL (RUNTIME)
PASS if:
- Все REQUIRED_LAYERS доступны по RAW (HTTP 200) и содержат маркер INDEX_MANIFEST / LAYER_IDX (по своим правилам слоя)
- ROUTER может сослаться на нужный REQUIRED_IDX (из ROUTE_TOKEN) без прямых обходов

GAP if:
- любой REQUIRED_LAYERS RAW missing или возвращает невалидный файл
- нужный доменный IDX_* отсутствует в ENTRYPOINTS

---

## [M] ROUTE_MAP
Детерминированный выбор REQUIRED_IDX.

- если задача про старт, стопы, step-run, trace, fail-codes, manifest, commands → IDX_BOOT
- если задача про сущности, паспорта, контракты сущностей, шаблоны сущностей → IDX_ENT
- если задача про пайпы, контроль, валидации, QA, gates, orchestration → IDX_PIPE
- если задача про KB scope, inputs/outputs, границы знаний, источники → IDX_KB
- если задача про аудио, музыку, метрики, структуру трека, Suno пайп → IDX_AUD
- если задача про визуал, кадры, промпты, Law15, Veo пайп → IDX_VIS
- если задача про словарь, коды, термины, нормализацию имен → IDX_LEX

Если DOMAIN не матчится → IDX_BOOT (как safe-default) и поднять GAP на доменный IDX.

---

## [M] STOP_CONDITIONS
STOP только если:
- RAW missing для MUST_LOAD / REQUIRED_LAYERS
- marker not confirmed для MUST_LOAD
- input absent (нет задачи)
