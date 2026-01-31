FILE: UE_V2/01_SYS/02_SYS_LAW/00__INDEX_MANIFEST__SYS__LAW.md
SCOPE: UE_V2 / 01_SYS / 02_SYS_LAW
DOC_TYPE: INDEX_MANIFEST
DOMAIN: SYS_LAW
UID: UE.V2.SYS.IDX.SYS_LAW.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — “таблица адресов” и кратких смыслов для папки/реалма 02_SYS_LAW.
Хранит RAW и машинные паспорта LAW-доков. Никаких “историй” и длинных объяснений.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Каждый элемент имеет KEY. PIPELINE_CONTRACT ссылается только на KEY.
- Коротко: 1–2 строки смысла. Без лирики.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/01_SYS/02_SYS_LAW
- FOLDER_NAME: 02_SYS_LAW
- INDEX_SCOPE_TAGS: [SYS, LAW]

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
  UID: UE.V2.SYS.IDX.SYS_LAW.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for 02_SYS_LAW
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/02_SYS_LAW/00__INDEX_MANIFEST__SYS__LAW.md
  PATH: UE_V2/01_SYS/02_SYS_LAW/00__INDEX_MANIFEST__SYS__LAW.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [M] REQUIRED (минимум для реалма)
- KEY: INDEX_MANIFEST
  UID: UE.V2.SYS.IDX.SYS_LAW.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: Raw addresses + short meaning for 02_SYS_LAW
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/02_SYS_LAW/00__INDEX_MANIFEST__SYS__LAW.md
  PATH: UE_V2/01_SYS/02_SYS_LAW/00__INDEX_MANIFEST__SYS__LAW.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.SYS.PIPE.SYS_LAW.001
  KIND: PIPE
  ROLE: Navigator for realm actions
  DESC: Uses KEYS, resolves RAW via INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/02_SYS_LAW/00__PIPELINE_CONTRACT__SYS__LAW.md
  PATH: UE_V2/01_SYS/02_SYS_LAW/00__PIPELINE_CONTRACT__SYS__LAW.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [O] CONTENT (laws)
# RULE: RAW must be copied from each LAW file "Raw" button (no guessing).
# UID optional here — do not guess.

- KEY: LAW_01
  UID:
  KIND: LAW
  ROLE: System law 01
  DESC: Canon law slot 01
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_01.md
  PATH: UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_01.md
  MARKERS: [LAW]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LAW_02
  UID:
  KIND: LAW
  ROLE: System law 02
  DESC: Canon law slot 02
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_02.md
  PATH: UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_02.md
  MARKERS: [LAW]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LAW_03
  UID:
  KIND: LAW
  ROLE: System law 03
  DESC: Canon law slot 03
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_03.md
  PATH: UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_03.md
  MARKERS: [LAW]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LAW_04
  UID:
  KIND: LAW
  ROLE: System law 04
  DESC: Canon law slot 04
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_04.md
  PATH: UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_04.md
  MARKERS: [LAW, NAV]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LAW_05
  UID:
  KIND: LAW
  ROLE: System law 05
  DESC: Canon law slot 05
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_05.md
  PATH: UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_05.md
  MARKERS: [LAW]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LAW_06
  UID:
  KIND: LAW
  ROLE: System law 06
  DESC: Canon law slot 06
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_06.md
  PATH: UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_06.md
  MARKERS: [LAW, TRACE]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LAW_07
  UID:
  KIND: LAW
  ROLE: System law 07
  DESC: Canon law slot 07
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_07.md
  PATH: UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_07.md
  MARKERS: [LAW]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LAW_08
  UID:
  KIND: LAW
  ROLE: System law 08
  DESC: Canon law slot 08
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_08.md
  PATH: UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_08.md
  MARKERS: [LAW]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LAW_09
  UID:
  KIND: LAW
  ROLE: System law 09
  DESC: Canon law slot 09
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_09.md
  PATH: UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_09.md
  MARKERS: [LAW]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LAW_10
  UID:
  KIND: LAW
  ROLE: System law 10
  DESC: Canon law slot 10
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_10.md
  PATH: UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_10.md
  MARKERS: [LAW]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LAW_11
  UID:
  KIND: LAW
  ROLE: System law 11
  DESC: Canon law slot 11
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_11.md
  PATH: UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_11.md
  MARKERS: [LAW]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LAW_12
  UID:
  KIND: LAW
  ROLE: System law 12
  DESC: Canon law slot 12
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_12.md
  PATH: UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_12.md
  MARKERS: [LAW]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LAW_13
  UID:
  KIND: LAW
  ROLE: System law 13
  DESC: Canon law slot 13
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_13.md
  PATH: UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_13.md
  MARKERS: [LAW]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LAW_14
  UID:
  KIND: LAW
  ROLE: System law 14
  DESC: Canon law slot 14
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_14.md
  PATH: UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_14.md
  MARKERS: [LAW]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LAW_15
  UID:
  KIND: LAW
  ROLE: System law 15
  DESC: Canon law slot 15
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_15.md
  PATH: UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_15.md
  MARKERS: [LAW]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LAW_16
  UID:
  KIND: LAW
  ROLE: System law 16
  DESC: Canon law slot 16
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_16.md
  PATH: UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_16.md
  MARKERS: [LAW]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LAW_17
  UID:
  KIND: LAW
  ROLE: System law 17
  DESC: Canon law slot 17
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_17.md
  PATH: UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_17.md
  MARKERS: [LAW]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LAW_18
  UID:
  KIND: LAW
  ROLE: System law 18
  DESC: Canon law slot 18
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_18.md
  PATH: UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_18.md
  MARKERS: [LAW]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LAW_19
  UID:
  KIND: LAW
  ROLE: System law 19
  DESC: Canon law slot 19
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_19.md
  PATH: UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_19.md
  MARKERS: [LAW]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LAW_20
  UID:
  KIND: LAW
  ROLE: System law 20
  DESC: Canon law slot 20
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_20.md
  PATH: UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_20.md
  MARKERS: [LAW]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LAW_21
  UID:
  KIND: LAW
  ROLE: System law 21
  DESC: Canon law slot 21
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_21.md
  PATH: UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_21.md
  MARKERS: [LAW]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31
