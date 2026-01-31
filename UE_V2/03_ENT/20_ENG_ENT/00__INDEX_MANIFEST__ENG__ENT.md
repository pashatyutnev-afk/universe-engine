FILE: UE_V2/03_ENT/20_ENG_ENT/00__INDEX_MANIFEST__ENG__ENT.md
SCOPE: UE_V2 / 03_ENT / 20_ENG_ENT
DOC_TYPE: INDEX_MANIFEST
DOMAIN: ENG_ENT
UID: UE.V2.ENT.ENG.INDEX_MANIFEST.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — мастер “таблица адресов” для слоя 20_ENG_ENT.
Хранит RAW и машинные паспорта входов в ENG-семейства. Без длинных объяснений.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Любая навигация по 20_ENG_ENT: KEY -> resolve RAW here -> open.
- PIPELINE_CONTRACT ссылается только на KEY.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).
- NO GUESSING: если RAW не зафиксирован -> RAW пустой, MARKERS включают GAP.

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/03_ENT/20_ENG_ENT
- FOLDER_NAME: 20_ENG_ENT
- INDEX_SCOPE_TAGS: [ENT, ENG]

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
  UID: UE.V2.ENT.ENG.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: Master index-manifest for 20_ENG_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/00__INDEX_MANIFEST__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/00__INDEX_MANIFEST__ENG__ENT.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [M] REQUIRED (layer routers)
- KEY: INDEX_MANIFEST
  UID: UE.V2.ENT.ENG.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Address table for layer
  DESC: Master address table for all ENG families
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/00__INDEX_MANIFEST__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/00__INDEX_MANIFEST__ENG__ENT.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.ENT.ENG.PIPELINE_CONTRACT.001
  KIND: PIPE
  ROLE: Layer step-run navigator
  DESC: Routes to ENG families by KEYS (resolves via this INDEX_MANIFEST)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/00__PIPELINE_CONTRACT__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/00__PIPELINE_CONTRACT__ENG__ENT.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [O] CONTENT (ENG family entrypoints)
# NOTE:
# - Здесь регистрируем входы семейств (их INDEX_MANIFEST), но пока RAW неизвестен -> ставим GAP.
# - Когда ты создашь/зальёшь семейный INDEX_MANIFEST, заменим RAW пустой на рабочий.

## FAMILY 00 — GOVERNANCE_ENG_ENT (GVN)
- KEY: ENG.FAM.GVN.ROOT
  UID:
  KIND: FOLDER
  ROLE: Family folder entrypoint
  DESC: Governance ENG family root (index not registered yet)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/00_GOVERNANCE_ENG_ENT/00__INDEX_MANIFEST__GVN__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/00_GOVERNANCE_ENG_ENT
  MARKERS: [ENG, FAMILY, GVN, GAP]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

## FAMILY 01 — CORE_ENG_ENT (CORE)
- KEY: ENG.FAM.CORE.ROOT
  UID:
  KIND: FOLDER
  ROLE: Family folder entrypoint
  DESC: Core ENG family root (index not registered yet)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/01_CORE_ENG_ENT/00__INDEX_MANIFEST__COR__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/01_CORE_ENG_ENT
  MARKERS: [ENG, FAMILY, CORE, GAP]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

## FAMILY 02 — NARRATIVE_ENG_ENT (NRR)
- KEY: ENG.FAM.NRR.ROOT
  UID:
  KIND: FOLDER
  ROLE: Family folder entrypoint
  DESC: Narrative ENG family root (index not registered yet)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/02_NARRATIVE_ENG_ENT/00__INDEX_MANIFEST__NRR__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/02_NARRATIVE_ENG_ENT
  MARKERS: [ENG, FAMILY, NRR, GAP]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

## FAMILY 03 — CHARACTER_ENG_ENT (CHR)
- KEY: ENG.FAM.CHR.ROOT
  UID:
  KIND: FOLDER
  ROLE: Family folder entrypoint
  DESC: Character ENG family root (index not registered yet)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/03_CHARACTER_ENG_ENT/00__INDEX_MANIFEST__CHR__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/03_CHARACTER_ENG_ENT
  MARKERS: [ENG, FAMILY, CHR, GAP]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

## FAMILY 04 — WORLD_ENG_ENT (WRL)
- KEY: ENG.FAM.WRL.ROOT
  UID:
  KIND: FOLDER
  ROLE: Family folder entrypoint
  DESC: World ENG family root (index not registered yet)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/04_WORLD_ENG_ENT/00__INDEX_MANIFEST__WRL__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/04_WORLD_ENG_ENT
  MARKERS: [ENG, FAMILY, WRL, GAP]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

## FAMILY 05 — EXPRESSION_ENG_ENT (EXP)
- KEY: ENG.FAM.EXP.ROOT
  UID:
  KIND: FOLDER
  ROLE: Family folder entrypoint
  DESC: Expression ENG family root (index not registered yet)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/05_EXPRESSION_ENG_ENT/00__INDEX_MANIFEST__EXP__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/05_EXPRESSION_ENG_ENT
  MARKERS: [ENG, FAMILY, EXP, GAP]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

## FAMILY 06 — GENRESTYLE_ENG_ENT (GEN)
- KEY: ENG.FAM.GEN.ROOT
  UID:
  KIND: FOLDER
  ROLE: Family folder entrypoint
  DESC: Genre/style ENG family root (index not registered yet)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/06_GENRESTYLE_ENG_ENT/00__INDEX_MANIFEST__GST__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/06_GENRESTYLE_ENG_ENT
  MARKERS: [ENG, FAMILY, GEN, GAP]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

## FAMILY 07 — PRODUCTIONFORMAT_ENG_ENT (PRF)
- KEY: ENG.FAM.PRF.ROOT
  UID:
  KIND: FOLDER
  ROLE: Family folder entrypoint
  DESC: Production format ENG family root (index not registered yet)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/07_PRODUCTIONFORMAT_ENG_ENT/00__INDEX_MANIFEST__PFT__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/07_PRODUCTIONFORMAT_ENG_ENT
  MARKERS: [ENG, FAMILY, PRF, GAP]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

## FAMILY 08 — KNOWLEDGEPRODUCTION_ENG_ENT (KNP)
- KEY: ENG.FAM.KNP.ROOT
  UID:
  KIND: FOLDER
  ROLE: Family folder entrypoint
  DESC: Knowledge production ENG family root (index not registered yet)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/08_KNOWLEDGEPRODUCTION_ENG_ENT/00__INDEX_MANIFEST__KPR__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/08_KNOWLEDGEPRODUCTION_ENG_ENT
  MARKERS: [ENG, FAMILY, KNP, GAP]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

## FAMILY 09 — AUDIO_ENG_ENT (AUD)
- KEY: ENG.FAM.AUD.ROOT
  UID:
  KIND: FOLDER
  ROLE: Family folder entrypoint
  DESC: Audio ENG family root (index not registered yet)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/09_AUDIO_ENG_ENT/00__INDEX_MANIFEST__AUD__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/09_AUDIO_ENG_ENT
  MARKERS: [ENG, FAMILY, AUD, GAP]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

## FAMILY 10 — METAEVOLUTION_ENG_ENT (MET)
- KEY: ENG.FAM.MET.ROOT
  UID:
  KIND: FOLDER
  ROLE: Family folder entrypoint
  DESC: Meta-evolution ENG family root (index not registered yet)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/10_METAEVOLUTION_ENG_ENT/00__INDEX_MANIFEST__MEV_ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/10_METAEVOLUTION_ENG_ENT
  MARKERS: [ENG, FAMILY, MET, GAP]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

## FAMILY 11 — MUSICFACTORY_ENG_ENT (MFC)
- KEY: ENG.FAM.MFC.ROOT
  UID:
  KIND: FOLDER
  ROLE: Family folder entrypoint
  DESC: Music factory ENG family root (index not registered yet)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/11_MUSICFACTORY_ENG_ENT/00__INDEX_MANIFEST__MFX__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/11_MUSICFACTORY_ENG_ENT
  MARKERS: [ENG, FAMILY, MFC, GAP]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

## FAMILY 12 — TRENDGENRE_ENG_ENT (TRN)
- KEY: ENG.FAM.TRN.ROOT
  UID:
  KIND: FOLDER
  ROLE: Family folder entrypoint
  DESC: Trend/genre ENG family root (index not registered yet)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/12_TRENDGENRE_ENG_ENT/00__INDEX_MANIFEST__TGR__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/12_TRENDGENRE_ENG_ENT
  MARKERS: [ENG, FAMILY, TRN, GAP]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

## FAMILY 13 — POETCORPUS_ENG_ENT (POET)
- KEY: ENG.FAM.POET.ROOT
  UID:
  KIND: FOLDER
  ROLE: Family folder entrypoint
  DESC: Poet corpus ENG family root (index not registered yet)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/13_POETCORPUS_ENG_ENT/00__INDEX_MANIFEST__PCR__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/13_POETCORPUS_ENG_ENT
  MARKERS: [ENG, FAMILY, POET, GAP]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

## FAMILY 14 — NAMINGIDENTITY_ENG_ENT (NAM)
- KEY: ENG.FAM.NAM.ROOT
  UID:
  KIND: FOLDER
  ROLE: Family folder entrypoint
  DESC: Naming/identity ENG family root (index not registered yet)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/14_NAMINGIDENTITY_ENG_ENT/00__INDEX_MANIFEST__NID__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/14_NAMINGIDENTITY_ENG_ENT
  MARKERS: [ENG, FAMILY, NAM, GAP]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31
