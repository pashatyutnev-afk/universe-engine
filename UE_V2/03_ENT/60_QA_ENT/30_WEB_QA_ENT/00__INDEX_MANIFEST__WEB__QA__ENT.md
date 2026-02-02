FILE: UE_V2/03_ENT/60_QA_ENT/30_WEB_QA_ENT/00__INDEX_MANIFEST__WEB__QA__ENT.md
SCOPE: UE_V2 / 03_ENT / 60_QA_ENT / 30_WEB_QA_ENT
DOC_TYPE: INDEX_MANIFEST
DOMAIN: WEB_QA_ENT
UID: UE.V2.ENT.IDX.WEB_QA_ENT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: QA_ENT
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — адресная таблица реалма WEB QA.
Хранит RAW и короткие смыслы файлов для QA веб-артефактов: контракт и a11y audit.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Каждый элемент имеет KEY. PIPELINE_CONTRACT ссылается только на KEY.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/03_ENT/60_QA_ENT/30_WEB_QA_ENT
- FOLDER_NAME: 30_WEB_QA_ENT
- INDEX_SCOPE_TAGS: [ENT, QA, WEB]

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
  UID: UE.V2.ENT.IDX.WEB_QA_ENT.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for WEB QA realm
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/60_QA_ENT/30_WEB_QA_ENT/00__INDEX_MANIFEST__WEB__QA__ENT.md
  PATH: UE_V2/03_ENT/60_QA_ENT/30_WEB_QA_ENT/00__INDEX_MANIFEST__WEB__QA__ENT.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: QA_ENT
  UPDATED: 2026-02-02

### [M] REQUIRED
- KEY: INDEX_MANIFEST
  UID: UE.V2.ENT.IDX.WEB_QA_ENT.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: RAW addresses + short meaning for WEB QA
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/60_QA_ENT/30_WEB_QA_ENT/00__INDEX_MANIFEST__WEB__QA__ENT.md
  PATH: UE_V2/03_ENT/60_QA_ENT/30_WEB_QA_ENT/00__INDEX_MANIFEST__WEB__QA__ENT.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: QA_ENT
  UPDATED: 2026-02-02

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.ENT.PIPE.WEB_QA_ENT.001
  KIND: PIPE
  ROLE: Router for web QA actions
  DESC: Uses KEYS, resolves RAW via INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/60_QA_ENT/30_WEB_QA_ENT/00__PIPELINE_CONTRACT__WEB__QA__ENT.md
  PATH: UE_V2/03_ENT/60_QA_ENT/30_WEB_QA_ENT/00__PIPELINE_CONTRACT__WEB__QA__ENT.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: QA_ENT
  UPDATED: 2026-02-02

### [O] QA CONTENT
- KEY: QA.WEB.A11Y_AUDIT
  UID: UE.V2.ENT.QA.WEB.A11Y_AUDIT.001
  KIND: ENTITY
  ROLE: A11y audit for web artifacts
  DESC: Audits keyboard, focus, labels, motion and semantics per bundle
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/60_QA_ENT/30_WEB_QA_ENT/90__WEB__A11Y_AUDIT__QA__ENT.md
  PATH: UE_V2/03_ENT/60_QA_ENT/30_WEB_QA_ENT/90__WEB__A11Y_AUDIT__QA__ENT.md
  MARKERS: [QA, WEB, AUDIT, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: QA_ENT
  UPDATED: 2026-02-02
