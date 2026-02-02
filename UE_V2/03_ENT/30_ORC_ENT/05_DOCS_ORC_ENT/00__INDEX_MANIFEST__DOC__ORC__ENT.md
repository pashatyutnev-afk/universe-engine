FILE: UE_V2/03_ENT/30_ORC_ENT/05_DOCS_ORC_ENT/00__INDEX_MANIFEST__DOC__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 05_DOCS_ORC_ENT
DOC_TYPE: INDEX_MANIFEST
DOMAIN: DOC_ORC_ENT
UID: UE.V2.ENT.IDX.DOC_ORC_ENT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — адресная таблица реалма 05_DOCS_ORC_ENT.
Хранит KEYS, короткий смысл, RAW и PATH (как справка). Без длинных историй.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Каждый элемент имеет KEY. PIPELINE_CONTRACT ссылается только на KEY.
- Коротко: 1–2 строки смысла. Без лирики.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/03_ENT/30_ORC_ENT/05_DOCS_ORC_ENT
- FOLDER_NAME: 05_DOCS_ORC_ENT
- INDEX_SCOPE_TAGS: [ENT, ORC, DOCS]

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
  UID: UE.V2.ENT.IDX.DOC_ORC_ENT.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for 05_DOCS_ORC_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/05_DOCS_ORC_ENT/00__INDEX_MANIFEST__DOC__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/05_DOCS_ORC_ENT/00__INDEX_MANIFEST__DOC__ORC__ENT.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

### [M] REQUIRED (минимум для реалма)
- KEY: INDEX_MANIFEST
  UID: UE.V2.ENT.IDX.DOC_ORC_ENT.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: Raw addresses + short meaning for 05_DOCS_ORC_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/05_DOCS_ORC_ENT/00__INDEX_MANIFEST__DOC__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/05_DOCS_ORC_ENT/00__INDEX_MANIFEST__DOC__ORC__ENT.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.ENT.PIPE.DOC_ORC_ENT.001
  KIND: PIPE
  ROLE: Navigator for realm actions
  DESC: Uses KEYS, resolves RAW via INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/05_DOCS_ORC_ENT/00__PIPELINE_CONTRACT__DOC__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/05_DOCS_ORC_ENT/00__PIPELINE_CONTRACT__DOC__ORC__ENT.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

### [O] DOCS ORC ENT (modules)
- KEY: DOC.BRIEF_FACTORY
  UID:
  KIND: FILE
  ROLE: Document brief factory
  DESC: Builds doc brief: purpose, audience, scope, constraints, output format
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/05_DOCS_ORC_ENT/01__DOC__BRIEF_FACTORY__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/05_DOCS_ORC_ENT/01__DOC__BRIEF_FACTORY__ORC__ENT.md
  MARKERS: [DOC, BRIEF, NAV]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: DOC.BUILDER
  UID:
  KIND: FILE
  ROLE: Document builder
  DESC: Builds the document using templates and required header sections
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/05_DOCS_ORC_ENT/02__DOC__BUILDER__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/05_DOCS_ORC_ENT/02__DOC__BUILDER__ORC__ENT.md
  MARKERS: [DOC, BUILD]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: DOC.KB_SCOPE_BUILDER
  UID:
  KIND: FILE
  ROLE: KB scope builder
  DESC: Builds KB scope: inputs/outputs/boundaries + RAW references
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/05_DOCS_ORC_ENT/03__DOC__KB_SCOPE_BUILDER__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/05_DOCS_ORC_ENT/03__DOC__KB_SCOPE_BUILDER__ORC__ENT.md
  MARKERS: [DOC, KB]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: DOC.LINT_QA
  UID:
  KIND: FILE
  ROLE: Lint + QA for docs
  DESC: Runs doc lint checks: headers, sections, RAW-only rules, and gates
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/05_DOCS_ORC_ENT/04__DOC__LINT_QA__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/05_DOCS_ORC_ENT/04__DOC__LINT_QA__ORC__ENT.md
  MARKERS: [DOC, QA, GATE]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: DOC.RELEASE_PACKAGER
  UID:
  KIND: FILE
  ROLE: Release packager for docs
  DESC: Packages docs into OUTPUT_PACK with deterministic naming and changelog notes
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/05_DOCS_ORC_ENT/05__DOC__RELEASE_PACKAGER__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/05_DOCS_ORC_ENT/05__DOC__RELEASE_PACKAGER__ORC__ENT.md
  MARKERS: [DOC, OUTPUT, PACK]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02
