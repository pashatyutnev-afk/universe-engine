FILE: UE_V2/00__INDEX_MANIFEST__UE_V2.md
SCOPE: Universe Engine (UE_V2)
DOC_TYPE: INDEX_MANIFEST (ROOT)
DOMAIN: UE_V2
UID: UE.V2.ROOT.INDEX_MANIFEST.001
VERSION: 1.2.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
OWNER: SYS
NAV_RULE: RAW lives here (internal). Public entrypoint = START only.

---

## [M] PURPOSE
INDEX_MANIFEST — корневой “адресный стол” UE_V2.
Единственный разрешённый способ резолва KEY → RAW для рантайма.
Содержит только то, что нужно для:
- детерминированной навигации
- проверки доступа к слоям (REG/XREF/KB/PIPE/NAV/LOG + DOM/REL/TKN/LEX/STR_PNT)
- запуска STEP-RUN пайплайна через PIPELINE_CONTRACT/PIPE_DEFAULT

---

## [M] PUBLIC_ENTRY_LAW (NO BYPASS)
LAW:
- Единственная публичная ссылка для запуска UE_V2: START (BOOT/ENTRYPOINT).
- Любые прочие RAW ссылки считаются INTERNAL и не используются как “вход” задачи.
- Рантайм принимает задачу только через START_SEQUENCE; INDEX_MANIFEST используется только после START.

EFFECT:
- Никаких “срезов” контекста через прямой RAW любого файла.
- Любой доступ к слоям: START → ROUTER → REQUIRED_IDX → (KEY→RAW via this file).

---

## [M] HARD_RULES (STRICT)
1) Любая навигация UE_V2: KEY → resolve RAW here → open.
2) Запрещён обход через PATH, если RAW известен.
3) PIPELINE_CONTRACT и ROUTER оперируют только KEY (не RAW, не PATH).
4) Любой слой обязан иметь свой LAYER INDEX MANIFEST (KEY), и он обязан быть зарегистрирован тут.
5) Любая “дыра” = GAP, а не “пойдём напрямую”.
6) Разрешённые места хранения RAW:
   - START (как публичный вход)
   - ROOT LINK BASE (как хранилище ключей)
   - этот INDEX_MANIFEST (как корневой реестр)
   В остальных файлах: только KEY.

---

## [M] ANTI_NOISE_POLICY (ROOT)
- Этот файл не объясняет систему. Он только “адреса + маркеры”.
- Не грузить деревья папок. Только REQUIRED_SET + доменный IDX по ROUTE_TOKEN.
- Любые дополнительные файлы — только через REQUIRED_IDX и только точечно.

---

## [M] ENTRY_SCHEMA (v1.1)
Each entry is ONE line block.

FIELDS:
- KEY:                 (string, unique, stable)
- UID:                 (string, optional until assigned)
- KIND:                FILE|FOLDER|LAYER_IDX|PIPE|REG|XREF|KB|LOG|STD|LAW|TPL|ENTITY|PANEL
- ROLE:                (short role)
- DESC:                (1 line)
- RAW:                 (raw url or empty if GAP)
- PATH:                (path for humans only)
- MARKERS:             [..] (MUST_LOAD, ROUTER, NAV, PIPE, REG, XREF, KB, LOG, DOMAIN_*, GAP, DEPRECATED)
- ACCESS:              PUBLIC|INTERNAL (default INTERNAL)
- STATUS:              ACTIVE|DRAFT|DEPRECATED
- OWNER:               SYS|RUNTIME|USER
- UPDATED:             YYYY-MM-DD

---

## [M] REQUIRED_SET (ROOT MUST_LOAD)
NOTE:
- MUST_LOAD_SET минимальный. Всё остальное грузится после ROUTE_TOKEN.

### [M] SELF
- KEY: UEV2.ROOT.INDEX_MANIFEST
  UID: UE.V2.ROOT.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Root address table for UE_V2
  DESC: Root INDEX_MANIFEST registry (KEY→RAW)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00__INDEX_MANIFEST__UE_V2.md
  PATH: UE_V2/00__INDEX_MANIFEST__UE_V2.md
  MARKERS: [INDEX, MUST_LOAD]
  ACCESS: INTERNAL
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-02-07

### [M] START (PUBLIC ENTRYPOINT)
- KEY: UEV2.BOOT.START
  UID: UE.V2.BOOT.START.001
  KIND: FILE
  ROLE: Public runtime entrypoint
  DESC: Единственный публичный вход. Принимает TASK_TEXT. Запускает START_SEQUENCE.
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/00__START.md
  PATH: UE_V2/00__START.md
  MARKERS: [BOOT, START, MUST_LOAD, ROUTER]
  ACCESS: PUBLIC
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-02-07

### [M] PIPELINE_CONTRACT (ROOT ROUTING)
- KEY: UEV2.ROOT.PIPELINE_CONTRACT
  UID: UE.V2.ROOT.PIPELINE_CONTRACT.001
  KIND: PIPE
  ROLE: Root step-run navigator
  DESC: Договор пайплайна. ROUTER/PIPE_DEFAULT работают через KEY.
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00__PIPELINE_CONTRACT__UE_V2.md
  PATH: UE_V2/00__PIPELINE_CONTRACT__UE_V2.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  ACCESS: INTERNAL
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-02-07

### [M] NAV_ROOT (ACCESS CHECKS)
- KEY: UEV2.NAV.NAV_ROOT
  UID: UE.V2.NAV.NAV_ROOT.001
  KIND: FILE
  ROLE: Navigation root rules
  DESC: Правила NAV + подтверждение доступа к REG/XREF/KB/PIPE/LOG через IDX.
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/04_NAV/00__NAV_ROOT.md
  PATH: UE_V2/04_NAV/00__NAV_ROOT.md
  MARKERS: [NAV, MUST_LOAD]
  ACCESS: INTERNAL
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-02-07

### [M] STRUCTURE (HUMAN MAP)
- KEY: UEV2.ROOT.STRUCTURE
  UID:
  KIND: FILE
  ROLE: Human-readable folder/file map
  DESC: Структура UE_V2 для людей. Не использовать как навигационный резолвер.
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/structure.md
  PATH: UE_V2/structure.md
  MARKERS: [MAP]
  ACCESS: INTERNAL
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-02-07

---

## [M] LAYERS (INDEX_MANIFEST REGISTRY)
RULE:
- Каждый слой регистрируется как LAYER_IDX (не FOLDER-плейсхолдер).

### BOOT
- KEY: UEV2.BOOT.INDEX_MANIFEST
  UID: UE.V2.BOOT.INDEX_MANIFEST.001
  KIND: LAYER_IDX
  ROLE: Layer index for 00_BOOT
  DESC: BOOT layer registry
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/00__INDEX_MANIFEST__BOOT.md
  PATH: UE_V2/00_BOOT/00__INDEX_MANIFEST__BOOT.md
  MARKERS: [INDEX, LAYER, BOOT]
  ACCESS: INTERNAL
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-02-07

### SYS
- KEY: UEV2.SYS.INDEX_MANIFEST
  UID: UE.V2.SYS.INDEX_MANIFEST.001
  KIND: LAYER_IDX
  ROLE: Layer index for 01_SYS
  DESC: SYS layer registry
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/00__INDEX_MANIFEST__SYS.md
  PATH: UE_V2/01_SYS/00__INDEX_MANIFEST__SYS.md
  MARKERS: [INDEX, LAYER, SYS]
  ACCESS: INTERNAL
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-02-07

### STD
- KEY: UEV2.STD.INDEX_MANIFEST
  UID: UE.V2.STD.INDEX_MANIFEST.001
  KIND: LAYER_IDX
  ROLE: Layer index for 02_STD
  DESC: STD layer registry
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/02_STD/00__INDEX_MANIFEST__STD.md
  PATH: UE_V2/02_STD/00__INDEX_MANIFEST__STD.md
  MARKERS: [INDEX, LAYER, STD]
  ACCESS: INTERNAL
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-02-07

### ENT
- KEY: UEV2.ENT.INDEX_MANIFEST
  UID: UE.V2.ENT.INDEX_MANIFEST.001
  KIND: LAYER_IDX
  ROLE: Layer index for 03_ENT
  DESC: ENT layer registry
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/00__INDEX_MANIFEST__ENT.md
  PATH: UE_V2/03_ENT/00__INDEX_MANIFEST__ENT.md
  MARKERS: [INDEX, LAYER, ENT]
  ACCESS: INTERNAL
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-02-07

### NAV
- KEY: UEV2.NAV.INDEX_MANIFEST
  UID: UE.V2.NAV.INDEX_MANIFEST.001
  KIND: LAYER_IDX
  ROLE: Layer index for 04_NAV
  DESC: NAV layer registry
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/04_NAV/00__INDEX_MANIFEST__NAV.md
  PATH: UE_V2/04_NAV/00__INDEX_MANIFEST__NAV.md
  MARKERS: [INDEX, LAYER, NAV]
  ACCESS: INTERNAL
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-02-07

### KB
- KEY: UEV2.KB.INDEX_MANIFEST
  UID: UE.V2.KB.INDEX_MANIFEST.001
  KIND: LAYER_IDX
  ROLE: Layer index for 05_KB
  DESC: KB layer registry
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/05_KB/00__INDEX_MANIFEST__KB.md
  PATH: UE_V2/05_KB/00__INDEX_MANIFEST__KB.md
  MARKERS: [INDEX, LAYER, KB]
  ACCESS: INTERNAL
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-02-07

### PIPE
- KEY: UEV2.PIPE.INDEX_MANIFEST
  UID: UE.V2.PIPE.INDEX_MANIFEST.001
  KIND: LAYER_IDX
  ROLE: Layer index for 06_PIPE
  DESC: PIPE layer registry
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/06_PIPE/00__INDEX_MANIFEST__PIPE.md
  PATH: UE_V2/06_PIPE/00__INDEX_MANIFEST__PIPE.md
  MARKERS: [INDEX, LAYER, PIPE]
  ACCESS: INTERNAL
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-02-07

### DOM_AUD
- KEY: UEV2.DOM.AUD.INDEX_MANIFEST
  UID: UE.V2.DOM.AUD.INDEX_MANIFEST.001
  KIND: LAYER_IDX
  ROLE: Layer index for 07_DOM_AUD
  DESC: Domain AUDIO layer registry
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/07_DOM_AUD/00__INDEX_MANIFEST__DOM__AUD.md
  PATH: UE_V2/07_DOM_AUD/00__INDEX_MANIFEST__DOM__AUD.md
  MARKERS: [INDEX, LAYER, DOMAIN_AUD]
  ACCESS: INTERNAL
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-02-07

### DOM_VIS
- KEY: UEV2.DOM.VIS.INDEX_MANIFEST
  UID: UE.V2.DOM.VIS.INDEX_MANIFEST.001
  KIND: LAYER_IDX
  ROLE: Layer index for 08_DOM_VIS
  DESC: Domain VISUAL layer registry
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/08_DOM_VIS/00__INDEX_MANIFEST__DOM__VIS.md
  PATH: UE_V2/08_DOM_VIS/00__INDEX_MANIFEST__DOM__VIS.md
  MARKERS: [INDEX, LAYER, DOMAIN_VIS]
  ACCESS: INTERNAL
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-02-07

### DOM_LOR
- KEY: UEV2.DOM.LOR.INDEX_MANIFEST
  UID: UE.V2.DOM.LOR.INDEX_MANIFEST.001
  KIND: LAYER_IDX
  ROLE: Layer index for 09_DOM_LOR
  DESC: Domain LORE layer registry
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/09_DOM_LOR/00__INDEX_MANIFEST__DOM__LOR.md
  PATH: UE_V2/09_DOM_LOR/00__INDEX_MANIFEST__DOM__LOR.md
  MARKERS: [INDEX, LAYER, DOMAIN_LOR]
  ACCESS: INTERNAL
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-02-07

### REL
- KEY: UEV2.REL.INDEX_MANIFEST
  UID: UE.V2.REL.INDEX_MANIFEST.001
  KIND: LAYER_IDX
  ROLE: Layer index for 10_REL
  DESC: RELEASE / REL layer registry
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/10_REL/00__INDEX_MANIFEST__REL.md
  PATH: UE_V2/10_REL/00__INDEX_MANIFEST__REL.md
  MARKERS: [INDEX, LAYER, REL]
  ACCESS: INTERNAL
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-02-07

### TKN
- KEY: UEV2.TKN.INDEX_MANIFEST
  UID: UE.V2.TKN.INDEX_MANIFEST.001
  KIND: LAYER_IDX
  ROLE: Layer index for 11_TKN
  DESC: TOKENS layer registry
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/11_TKN/00__INDEX_MANIFEST__TKN.md
  PATH: UE_V2/11_TKN/00__INDEX_MANIFEST__TKN.md
  MARKERS: [INDEX, LAYER, TKN]
  ACCESS: INTERNAL
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-02-07

### LEX
- KEY: UEV2.LEX.INDEX_MANIFEST
  UID: UE.V2.LEX.INDEX_MANIFEST.001
  KIND: LAYER_IDX
  ROLE: Layer index for 12_LEX
  DESC: LEXICON layer registry
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/12_LEX/00__INDEX_MANIFEST__LEX.md
  PATH: UE_V2/12_LEX/00__INDEX_MANIFEST__LEX.md
  MARKERS: [INDEX, LAYER, LEX]
  ACCESS: INTERNAL
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-02-07

### STR_PNT
- KEY: UEV2.STR.PNT.INDEX_MANIFEST
  UID: UE.V2.STR.PNT.INDEX_MANIFEST.001
  KIND: LAYER_IDX
  ROLE: Layer index for 13_STR_PNT
  DESC: STRUCTURE / POINTS layer registry
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/13_STR_PNT/00__INDEX_MANIFEST__STR__PNT.md
  PATH: UE_V2/13_STR_PNT/00__INDEX_MANIFEST__STR__PNT.md
  MARKERS: [INDEX, LAYER, STR_PNT]
  ACCESS: INTERNAL
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-02-07

### LOG
- KEY: UEV2.LOG.INDEX_MANIFEST
  UID: UE.V2.LOG.INDEX_MANIFEST.001
  KIND: LAYER_IDX
  ROLE: Layer index for 14_LOG
  DESC: LOG layer registry
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/14_LOG/00__INDEX_MANIFEST__LOG.md
  PATH: UE_V2/14_LOG/00__INDEX_MANIFEST__LOG.md
  MARKERS: [INDEX, LAYER, LOG]
  ACCESS: INTERNAL
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-02-07

---

## [M] ROUTER_DEPENDENCIES (KEY-ONLY)
The ROUTER / STEP-RUN must be able to resolve these KEYS:
- UEV2.BOOT.START
- UEV2.ROOT.PIPELINE_CONTRACT
- UEV2.NAV.NAV_ROOT
- UEV2.PIPE.INDEX_MANIFEST
- UEV2.KB.INDEX_MANIFEST
- UEV2.LOG.INDEX_MANIFEST

If any missing → GAP.

---

## [M] VALIDATION (ROOT)
PASS if:
- START exists and marked ACCESS: PUBLIC
- REQUIRED_SET keys exist
- All LAYERS are registered as KIND: LAYER_IDX (not folder placeholders)

FAIL if:
- Any file outside START/ROOT LINK BASE/this file contains RAW used for nav
- ROUTER or PIPELINE_CONTRACT relies on RAW directly instead of KEY
