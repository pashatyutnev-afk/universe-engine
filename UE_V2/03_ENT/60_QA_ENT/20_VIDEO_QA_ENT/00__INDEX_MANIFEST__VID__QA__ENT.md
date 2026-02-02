FILE: UE_V2/03_ENT/60_QA_ENT/20_VIDEO_QA_ENT/00__INDEX_MANIFEST__VID__QA__ENT.md
SCOPE: UE_V2 / 03_ENT / 60_QA_ENT / 20_VIDEO_QA_ENT
DOC_TYPE: INDEX_MANIFEST
DOMAIN: VID_QA_ENT
UID: UE.V2.ENT.IDX.VID_QA_ENT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: QA_ENT
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — адресная таблица реалма видео QA.
Хранит RAW и короткие смыслы файлов для проверки видео: README, regression guard.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Каждый элемент имеет KEY. PIPELINE_CONTRACT ссылается только на KEY.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/03_ENT/60_QA_ENT/20_VIDEO_QA_ENT
- FOLDER_NAME: 20_VIDEO_QA_ENT
- INDEX_SCOPE_TAGS: [ENT, QA, VID]

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

---

## [M] ENTRIES

### [M] SELF
- KEY: SELF
  UID: UE.V2.ENT.IDX.VID_QA_ENT.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for VID QA realm
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/60_QA_ENT/20_VIDEO_QA_ENT/00__INDEX_MANIFEST__VID__QA__ENT.md
  PATH: UE_V2/03_ENT/60_QA_ENT/20_VIDEO_QA_ENT/00__INDEX_MANIFEST__VID__QA__ENT.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: QA_ENT
  UPDATED: 2026-02-02

### [M] REQUIRED
- KEY: INDEX_MANIFEST
  UID: UE.V2.ENT.IDX.VID_QA_ENT.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: RAW addresses + short meaning for video QA
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/60_QA_ENT/20_VIDEO_QA_ENT/00__INDEX_MANIFEST__VID__QA__ENT.md
  PATH: UE_V2/03_ENT/60_QA_ENT/20_VIDEO_QA_ENT/00__INDEX_MANIFEST__VID__QA__ENT.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: QA_ENT
  UPDATED: 2026-02-02

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.ENT.PIPE.VID_QA_ENT.001
  KIND: PIPE
  ROLE: Router for video QA actions
  DESC: Uses KEYS, resolves RAW via INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/60_QA_ENT/20_VIDEO_QA_ENT/00__PIPELINE_CONTRACT__VID__QA__ENT.md
  PATH: UE_V2/03_ENT/60_QA_ENT/20_VIDEO_QA_ENT/00__PIPELINE_CONTRACT__VID__QA__ENT.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: QA_ENT
  UPDATED: 2026-02-02

- KEY: README
  UID: UE.V2.ENT.QA.VID.README.001
  KIND: FILE
  ROLE: Usage notes for video QA realm
  DESC: How to run VID QA checks (keys-only)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/60_QA_ENT/20_VIDEO_QA_ENT/01__README__VID__QA__ENT.md
  PATH: UE_V2/03_ENT/60_QA_ENT/20_VIDEO_QA_ENT/01__README__VID__QA__ENT.md
  MARKERS: [DOC, NAV]
  STATUS: ACTIVE
  OWNER: QA_ENT
  UPDATED: 2026-02-02

### [O] QA CONTENT
- KEY: QA.VID.REGRESSION_GUARD
  UID: UE.V2.ENT.QA.VID.REGRESSION_GUARD.001
  KIND: ENTITY
  ROLE: Regression guard for video iterations
  DESC: Prevents quality regressions across variants/edits
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/60_QA_ENT/20_VIDEO_QA_ENT/90__VID__REGRESSION_GUARD__QA__ENT.md
  PATH: UE_V2/03_ENT/60_QA_ENT/20_VIDEO_QA_ENT/90__VID__REGRESSION_GUARD__QA__ENT.md
  MARKERS: [QA, VID, GATE, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: QA_ENT
  UPDATED: 2026-02-02
