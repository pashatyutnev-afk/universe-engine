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
  DESC: Routes to layers via layer INDEX_MANIFEST (KEY-only)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00__PIPELINE_CONTRACT__UE_V2.md
  PATH: UE_V2/00__PIPELINE_CONTRACT__UE_V2.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [O] CONTENT (layer entrypoints)
# RULE:
# - If layer INDEX_MANIFEST RAW is known -> register as KIND: FILE with RAW.
# - If not known yet -> register layer folder as KIND: FOLDER with RAW empty and MARKERS include GAP.
# - No pipeline duplicates here.

## READY LAYERS (index known)

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

## REGISTERED LAYERS (folder placeholders, index not registered yet)

- KEY: UEV2.NAV.LAYER
  UID:
  KIND: FOLDER
  ROLE: Layer folder placeholder for 04_NAV
  DESC: Layer exists; INDEX_MANIFEST RAW not registered yet
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/04_NAV/00__INDEX_MANIFEST__NAV.md
  PATH: UE_V2/04_NAV
  MARKERS: [LAYER, NAV, GAP]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: UEV2.KB.LAYER
  UID:
  KIND: FOLDER
  ROLE: Layer folder placeholder for 05_KB
  DESC: Layer exists; INDEX_MANIFEST RAW not registered yet
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/05_KB/00__INDEX_MANIFEST__KB.md
  PATH: UE_V2/05_KB
  MARKERS: [LAYER, KB, GAP]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: UEV2.PIPE.LAYER
  UID:
  KIND: FOLDER
  ROLE: Layer folder placeholder for 06_PIPE
  DESC: Layer exists; INDEX_MANIFEST RAW not registered yet
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/06_PIPE/00__INDEX_MANIFEST__PIPE.md
  PATH: UE_V2/06_PIPE
  MARKERS: [LAYER, PIPE, GAP]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: UEV2.DOM_AUD.LAYER
  UID:
  KIND: FOLDER
  ROLE: Layer folder placeholder for 07_DOM_AUD
  DESC: Layer exists; INDEX_MANIFEST RAW not registered yet
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/07_DOM_AUD/00__INDEX_MANIFEST__DOM__AUD.md
  PATH: UE_V2/07_DOM_AUD
  MARKERS: [LAYER, DOM, AUD, GAP]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: UEV2.DOM_VIS.LAYER
  UID:
  KIND: FOLDER
  ROLE: Layer folder placeholder for 08_DOM_VIS
  DESC: Layer exists; INDEX_MANIFEST RAW not registered yet
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/08_DOM_VIS/00__INDEX_MANIFEST__DOM__VIS.md
  PATH: UE_V2/08_DOM_VIS
  MARKERS: [LAYER, DOM, VIS, GAP]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: UEV2.DOM_LOR.LAYER
  UID:
  KIND: FOLDER
  ROLE: Layer folder placeholder for 09_DOM_LOR
  DESC: Layer exists; INDEX_MANIFEST RAW not registered yet
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/09_DOM_LOR/00__INDEX_MANIFEST__DOM__LOR.md
  PATH: UE_V2/09_DOM_LOR
  MARKERS: [LAYER, DOM, LOR, GAP]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: UEV2.REL.LAYER
  UID:
  KIND: FOLDER
  ROLE: Layer folder placeholder for 10_REL
  DESC: Layer exists; INDEX_MANIFEST RAW not registered yet
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/10_REL/00__INDEX_MANIFEST__REL.md
  PATH: UE_V2/10_REL
  MARKERS: [LAYER, REL, GAP]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: UEV2.TKN.LAYER
  UID:
  KIND: FOLDER
  ROLE: Layer folder placeholder for 11_TKN
  DESC: Layer exists; INDEX_MANIFEST RAW not registered yet
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/11_TKN/00__INDEX_MANIFEST__TKN.md
  PATH: UE_V2/11_TKN
  MARKERS: [LAYER, TKN, GAP]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: UEV2.LEX.LAYER
  UID:
  KIND: FOLDER
  ROLE: Layer folder placeholder for 12_LEX
  DESC: Layer exists; INDEX_MANIFEST RAW not registered yet
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/12_LEX/00__INDEX_MANIFEST__LEX.md
  PATH: UE_V2/12_LEX
  MARKERS: [LAYER, LEX, GAP]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: UEV2.STR_PNT.LAYER
  UID:
  KIND: FOLDER
  ROLE: Layer folder placeholder for 13_STR_PNT
  DESC: Layer exists; INDEX_MANIFEST RAW not registered yet
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/13_STR_PNT/00__INDEX_MANIFEST__STR__PNT.md
  PATH: UE_V2/13_STR_PNT
  MARKERS: [LAYER, STR_PNT, GAP]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: UEV2.LOG.LAYER
  UID:
  KIND: FOLDER
  ROLE: Layer folder placeholder for 14_LOG
  DESC: Layer exists; INDEX_MANIFEST RAW not registered yet
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/14_LOG/00__INDEX_MANIFEST__LOG.md
  PATH: UE_V2/14_LOG
  MARKERS: [LAYER, LOG, GAP]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31
