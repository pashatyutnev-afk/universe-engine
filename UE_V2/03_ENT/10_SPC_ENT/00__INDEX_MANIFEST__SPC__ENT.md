FILE: UE_V2/03_ENT/10_SPC_ENT/00__INDEX_MANIFEST__SPC__ENT.md
SCOPE: UE_V2 / 03_ENT / 10_SPC_ENT
DOC_TYPE: INDEX_MANIFEST
DOMAIN: SPC_ENT
UID: UE.V2.ENT.SPC.INDEX_MANIFEST.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — мастер “таблица адресов” для слоя 10_SPC_ENT.
Хранит RAW и машинные паспорта под-реалмов (семей SPC). Никаких длинных объяснений.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Любая навигация по 10_SPC_ENT: KEY -> resolve RAW here -> open.
- Каждый под-реалм должен иметь свой INDEX_MANIFEST и PIPELINE_CONTRACT.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/03_ENT/10_SPC_ENT
- FOLDER_NAME: 10_SPC_ENT
- INDEX_SCOPE_TAGS: [ENT, SPC]

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
  UID: UE.V2.ENT.SPC.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: Master index-manifest for 10_SPC_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/00__INDEX_MANIFEST__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/00__INDEX_MANIFEST__SPC__ENT.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [M] REQUIRED (layer routers)
- KEY: INDEX_MANIFEST
  UID: UE.V2.ENT.SPC.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Address table for layer
  DESC: Master address table for all SPC families
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/00__INDEX_MANIFEST__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/00__INDEX_MANIFEST__SPC__ENT.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.ENT.SPC.PIPELINE_CONTRACT.001
  KIND: PIPE
  ROLE: Layer step-run navigator
  DESC: Routes to SPC family pipelines by KEYS (resolves via this INDEX_MANIFEST)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/00__PIPELINE_CONTRACT__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/00__PIPELINE_CONTRACT__SPC__ENT.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [O] CONTENT (SPC family indexes)
# RULE: RAW must be copied from each file "Raw" button (no guessing).
# UID optional here — do not guess if not fixed.

## FAMILY 00 — TOP_GOVERNANCE_SPC_ENT (GVN)
- KEY: SPC.FAM.GVN.INDEX_MANIFEST
  UID: UE.V2.ENT.SPC.GVN.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Family index for TOP_GOVERNANCE_SPC_ENT
  DESC: Address table for governance SPC set (01–06)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/00_TOP_GOVERNANCE_SPC_ENT/00__INDEX_MANIFEST__GVN__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/00_TOP_GOVERNANCE_SPC_ENT/00__INDEX_MANIFEST__GVN__SPC__ENT.md
  MARKERS: [INDEX, SPC, GVN]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

## FAMILY 01 — CREATIVE_SPC_ENT (CRV)
- KEY: SPC.FAM.CRV.INDEX_MANIFEST
  UID: UE.V2.ENT.SPC.CRV.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Family index for CREATIVE_SPC_ENT
  DESC: Address table for creative SPC set (01–08)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/01_CREATIVE_SPC_ENT/00__INDEX_MANIFEST__CRV__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/01_CREATIVE_SPC_ENT/00__INDEX_MANIFEST__CRV__SPC__ENT.md
  MARKERS: [INDEX, SPC, CRV]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

## FAMILY 02 — NARRATIVE_SPC_ENT (NAR)
- KEY: SPC.FAM.NAR.INDEX_MANIFEST
  UID:
  KIND: FILE
  ROLE: Family index for NARRATIVE_SPC_ENT
  DESC: Address table for narrative SPC set
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/02_NARRATIVE_SPC_ENT/00__INDEX_MANIFEST__NRR__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/02_NARRATIVE_SPC_ENT/00__INDEX_MANIFEST__NRR__SPC__ENT.md
  MARKERS: [INDEX, SPC, NAR]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

## FAMILY 03 — CHARACTER_SPC_ENT (CHR)
- KEY: SPC.FAM.CHR.INDEX_MANIFEST
  UID:
  KIND: FILE
  ROLE: Family index for CHARACTER_SPC_ENT
  DESC: Address table for character SPC set
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/03_CHARACTER_SPC_ENT/00__INDEX_MANIFEST__CHR__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/03_CHARACTER_SPC_ENT/00__INDEX_MANIFEST__CHR__SPC__ENT.md
  MARKERS: [INDEX, SPC, CHR]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

## FAMILY 04 — WORLD_SPC_ENT (WRL)
- KEY: SPC.FAM.WRL.INDEX_MANIFEST
  UID:
  KIND: FILE
  ROLE: Family index for WORLD_SPC_ENT
  DESC: Address table for world SPC set
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/04_WORLD_SPC_ENT/00__INDEX_MANIFEST__WRL__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/04_WORLD_SPC_ENT/00__INDEX_MANIFEST__WRL__SPC__ENT.md
  MARKERS: [INDEX, SPC, WRL]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

## FAMILY 05 — VISUAL_SPC_ENT (VIS)
- KEY: SPC.FAM.VIS.INDEX_MANIFEST
  UID:
  KIND: FILE
  ROLE: Family index for VISUAL_SPC_ENT
  DESC: Address table for visual SPC set
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/05_VISUAL_SPC_ENT/00__INDEX_MANIFEST__VIS__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/05_VISUAL_SPC_ENT/00__INDEX_MANIFEST__VIS__SPC__ENT.md
  MARKERS: [INDEX, SPC, VIS]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

## FAMILY 06 — SOUND_MUSIC_SPC_ENT (SND)
- KEY: SPC.FAM.SND.INDEX_MANIFEST
  UID:
  KIND: FILE
  ROLE: Family index for SOUND_MUSIC_SPC_ENT
  DESC: Address table for sound/music SPC set
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/06_SOUND_MUSIC_SPC_ENT/00__INDEX_MANIFEST__SND_MUS__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/06_SOUND_MUSIC_SPC_ENT/00__INDEX_MANIFEST__SND_MUS__SPC__ENT.md
  MARKERS: [INDEX, SPC, SND]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

## FAMILY 07 — PRODUCTION_SPC_ENT (PRD)
- KEY: SPC.FAM.PRD.INDEX_MANIFEST
  UID:
  KIND: FILE
  ROLE: Family index for PRODUCTION_SPC_ENT
  DESC: Address table for production SPC set
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/07_PRODUCTION_SPC_ENT/00__INDEX_MANIFEST__PRD__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/07_PRODUCTION_SPC_ENT/00__INDEX_MANIFEST__PRD__SPC__ENT.md
  MARKERS: [INDEX, SPC, PRD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

## FAMILY 08 — PSYCHOLOGY_SPC_ENT (PSY)
- KEY: SPC.FAM.PSY.INDEX_MANIFEST
  UID:
  KIND: FILE
  ROLE: Family index for PSYCHOLOGY_SPC_ENT
  DESC: Address table for psychology SPC set
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/08_PSYCHOLOGY_SPC_ENT/00__INDEX_MANIFEST__PSY__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/08_PSYCHOLOGY_SPC_ENT/00__INDEX_MANIFEST__PSY__SPC__ENT.md
  MARKERS: [INDEX, SPC, PSY]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

## FAMILY 09 — RESEARCH_SPC_ENT (RSC)
- KEY: SPC.FAM.RSC.INDEX_MANIFEST
  UID:
  KIND: FILE
  ROLE: Family index for RESEARCH_SPC_ENT
  DESC: Address table for research SPC set
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/09_RESEARCH_SPC_ENT/00__INDEX_MANIFEST__RCH__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/09_RESEARCH_SPC_ENT/00__INDEX_MANIFEST__RCH__SPC__ENT.md
  MARKERS: [INDEX, SPC, RSC]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

## FAMILY 10 — MARKETING_SPC_ENT (MKT)
- KEY: SPC.FAM.MKT.INDEX_MANIFEST
  UID:
  KIND: FILE
  ROLE: Family index for MARKETING_SPC_ENT
  DESC: Address table for marketing SPC set
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/10_MARKETING_SPC_ENT/00__INDEX_MANIFEST__MKT__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/10_MARKETING_SPC_ENT/00__INDEX_MANIFEST__MKT__SPC__ENT.md
  MARKERS: [INDEX, SPC, MKT]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

## FAMILY 11 — META_SPC_ENT (META)
- KEY: SPC.FAM.META.INDEX_MANIFEST
  UID:
  KIND: FILE
  ROLE: Family index for META_SPC_ENT
  DESC: Address table for meta SPC set
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/11_META_SPC_ENT/00__INDEX_MANIFEST__MET__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/11_META_SPC_ENT/00__INDEX_MANIFEST__MET__SPC__ENT.md
  MARKERS: [INDEX, SPC, META]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31
