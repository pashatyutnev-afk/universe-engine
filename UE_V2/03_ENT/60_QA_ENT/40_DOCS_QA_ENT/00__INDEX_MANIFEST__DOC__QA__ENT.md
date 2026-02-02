FILE: UE_V2/03_ENT/60_QA_ENT/40_DOCS_QA_ENT/00__INDEX_MANIFEST__DOC__QA__ENT.md
SCOPE: UE_V2 / 03_ENT / 60_QA_ENT / 40_DOCS_QA_ENT
DOC_TYPE: INDEX_MANIFEST
DOMAIN: DOC_QA_ENT
UID: UE.V2.ENT.IDX.DOC_QA_ENT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: QA_ENT
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — адресная таблица реалма DOC QA.
Хранит RAW и короткие смыслы файлов для QA документов: контракт и lint audit.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Каждый элемент имеет KEY. PIPELINE_CONTRACT ссылается только на KEY.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/03_ENT/60_QA_ENT/40_DOCS_QA_ENT
- FOLDER_NAME: 40_DOCS_QA_ENT
- INDEX_SCOPE_TAGS: [ENT, QA, DOC]

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
  UID: UE.V2.ENT.IDX.DOC_QA_ENT.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for DOC QA realm
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/60_QA_ENT/40_DOCS_QA_ENT/00__INDEX_MANIFEST__DOC__QA__ENT.md
  PATH: UE_V2/03_ENT/60_QA_ENT/40_DOCS_QA_ENT/00__INDEX_MANIFEST__DOC__QA__ENT.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: QA_ENT
  UPDATED: 2026-02-02

### [M] REQUIRED
- KEY: INDEX_MANIFEST
  UID: UE.V2.ENT.IDX.DOC_QA_ENT.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: RAW addresses + short meaning for DOC QA
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/60_QA_ENT/40_DOCS_QA_ENT/00__INDEX_MANIFEST__DOC__QA__ENT.md
  PATH: UE_V2/03_ENT/60_QA_ENT/40_DOCS_QA_ENT/00__INDEX_MANIFEST__DOC__QA__ENT.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: QA_ENT
  UPDATED: 2026-02-02

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.ENT.PIPE.DOC_QA_ENT.001
  KIND: PIPE
  ROLE: Router for docs QA actions
  DESC: Uses KEYS, resolves RAW via INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/60_QA_ENT/40_DOCS_QA_ENT/00__PIPELINE_CONTRACT__DOC__QA__ENT.md
  PATH: UE_V2/03_ENT/60_QA_ENT/40_DOCS_QA_ENT/00__PIPELINE_CONTRACT__DOC__QA__ENT.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: QA_ENT
  UPDATED: 2026-02-02

### [O] QA CONTENT
- KEY: QA.DOC.LINT_AUDIT
  UID: UE.V2.ENT.QA.DOC.LINT_AUDIT.001
  KIND: ENTITY
  ROLE: Docs lint audit
  DESC: Audits doc structure, headers, RAW rule compliance, sections order
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/60_QA_ENT/40_DOCS_QA_ENT/90__DOC__LINT_AUDIT__QA__ENT.md
  PATH: UE_V2/03_ENT/60_QA_ENT/40_DOCS_QA_ENT/90__DOC__LINT_AUDIT__QA__ENT.md
  MARKERS: [QA, DOC, AUDIT, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: QA_ENT
  UPDATED: 2026-02-02
