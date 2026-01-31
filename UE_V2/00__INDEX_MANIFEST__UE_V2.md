FILE: UE_V2/00__INDEX_MANIFEST__UE_V2.md
SCOPE: UE_V2
DOC_TYPE: INDEX_MANIFEST
DOMAIN: UE_V2
UID: UE.V2.ROOT.INDEX_MANIFEST.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — мастер “таблица адресов” для корня UE_V2.
Хранит RAW и машинные паспорта входов в слои UE_V2 (layer entrypoints). Без длинных объяснений.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Любая навигация по UE_V2: KEY -> resolve RAW here -> open.
- PIPELINE_CONTRACT ссылается только на KEY.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2
- FOLDER_NAME: UE_V2
- INDEX_SCOPE_TAGS: [ROOT, NAV, SYS]

## [M] ENTRY_SCHEMA (v1)
- KEY: <UNIQUE_KEY>
  UID: <OPTIONAL_UID>
  KIND: FILE|FOLDER|ENTITY|PIPE|KB|REG|XREF|LOG|STD|LAW|TPL
  ROLE: <ONE_LINE_ROLE>
  DESC: <ONE_LINE_DESC>
  RAW: <RAW_URL_OR_EMPTY>
  PATH: <REPO_PATH_OR_EMPTY>
  MARKERS: [MUST_LOAD, ROUTER, NAV, ...]
  STATUS: ACTIVE|DRAFT|DEPRECATED
  OWNER: SYS|RUNTIME|USER|<TEAM>
  UPDATED: 0000-00-00

## [M] ENTRIES

### [M] SELF
- KEY: SELF
  UID: UE.V2.ROOT.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This root index-manifest file for UE_V2
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00__INDEX_MANIFEST__UE_V2.md
  PATH: UE_V2/00__INDEX_MANIFEST__UE_V2.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [M] REQUIRED (root routers)
- KEY: INDEX_MANIFEST
  UID: UE.V2.ROOT.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Address table for UE_V2 root
  DESC: Root address table for UE_V2 layer entrypoints
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00__INDEX_MANIFEST__UE_V2.md
  PATH: UE_V2/00__INDEX_MANIFEST__UE_V2.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.ROOT.PIPELINE_CONTRACT.001
  KIND: PIPE
  ROLE: Root step-run navigator
  DESC: Routes to layer pipelines via layer INDEX_MANIFEST (KEY-only)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00__PIPELINE_CONTRACT__UE_V2.md
  PATH: UE_V2/00__PIPELINE_CONTRACT__UE_V2.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [O] CONTENT (layer entrypoints)
# RULE: Root index stores only layer INDEX_MANIFEST entrypoints (no pipeline duplicates here).
# Layer PIPELINE_CONTRACT must be resolved inside each layer index.

- KEY: UEV2.BOOT.INDEX_MANIFEST
  UID: UE.V2.BOOT.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Layer index for 00_BOOT
  DESC: Entry index-manifest for BOOT layer
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/00__INDEX_MANIFEST__BOOT.md
  PATH: UE_V2/00_BOOT/00__INDEX_MANIFEST__BOOT.md
  MARKERS: [INDEX, LAYER, BOOT]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: UEV2.SYS.INDEX_MANIFEST
  UID: UE.V2.SYS.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Layer index for 01_SYS
  DESC: Entry index-manifest for SYS layer
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/00__INDEX_MANIFEST__SYS.md
  PATH: UE_V2/01_SYS/00__INDEX_MANIFEST__SYS.md
  MARKERS: [INDEX, LAYER, SYS]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: UEV2.STD.INDEX_MANIFEST
  UID: UE.V2.STD.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Layer index for 02_STD
  DESC: Entry index-manifest for STD layer
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/02_STD/00__INDEX_MANIFEST__STD.md
  PATH: UE_V2/02_STD/00__INDEX_MANIFEST__STD.md
  MARKERS: [INDEX, LAYER, STD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: UEV2.ENT.INDEX_MANIFEST
  UID: UE.V2.ENT.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Layer index for 03_ENT
  DESC: Entry index-manifest for ENT layer
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/00__INDEX_MANIFEST__ENT.md
  PATH: UE_V2/03_ENT/00__INDEX_MANIFEST__ENT.md
  MARKERS: [INDEX, LAYER, ENT]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31
