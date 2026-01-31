FILE: UE_V2/11_TKN/00__INDEX_MANIFEST__TKN.md
SCOPE: UE_V2 / 11_TKN
DOC_TYPE: INDEX_MANIFEST
DOMAIN: TKN
UID: UE.V2.TKN.INDEX_MANIFEST.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — “таблица адресов” и кратких смыслов для реалма 11_TKN.
Хранит RAW и машинные паспорта токенов (brief/style/structure/lyrics/qa) для детерминированного рантайма.
Без длинных объяснений.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Любая навигация по 11_TKN выполняется через KEY → RAW.
- PIPELINE_CONTRACT ссылается только на KEY.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/11_TKN
- FOLDER_NAME: 11_TKN
- INDEX_SCOPE_TAGS: [TKN, SYS, TOKEN]

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
  UID: UE.V2.TKN.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for 11_TKN
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/11_TKN/00__INDEX_MANIFEST__TKN.md
  PATH: UE_V2/11_TKN/00__INDEX_MANIFEST__TKN.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [M] REQUIRED (минимум для реалма)
- KEY: INDEX_MANIFEST
  UID: UE.V2.TKN.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: Raw addresses + short meaning for 11_TKN
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/11_TKN/00__INDEX_MANIFEST__TKN.md
  PATH: UE_V2/11_TKN/00__INDEX_MANIFEST__TKN.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.TKN.PIPELINE_CONTRACT.001
  KIND: PIPE
  ROLE: Realm step-run navigator
  DESC: KEY-only contract; resolves targets via this INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/11_TKN/00__PIPELINE_CONTRACT__TKN.md
  PATH: UE_V2/11_TKN/00__PIPELINE_CONTRACT__TKN.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [O] CONTENT (token schemas)

- KEY: TKN.BRIEF
  UID:
  KIND: TKN
  ROLE: Brief token schema
  DESC: Minimal task brief token; input for routing and pipelines
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/11_TKN/01__TKN__BRIEF_TOKEN.md
  PATH: UE_V2/11_TKN/01__TKN__BRIEF_TOKEN.md
  MARKERS: [TKN, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: TKN.STYLE
  UID:
  KIND: TKN
  ROLE: Style token schema
  DESC: Style/constraints token for VIS/AUD/LOR/MUSIC outputs
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/11_TKN/02__TKN__STYLE_TOKEN.md
  PATH: UE_V2/11_TKN/02__TKN__STYLE_TOKEN.md
  MARKERS: [TKN]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: TKN.STRUCTURE
  UID:
  KIND: TKN
  ROLE: Structure token schema
  DESC: Structure token for step-run, sections, and output layout
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/11_TKN/03__TKN__STRUCTURE_TOKEN.md
  PATH: UE_V2/11_TKN/03__TKN__STRUCTURE_TOKEN.md
  MARKERS: [TKN, PIPE]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: TKN.LYRICS
  UID:
  KIND: TKN
  ROLE: Lyrics token schema
  DESC: Lyrics token format for music text generation and checks
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/11_TKN/04__TKN__LYRICS_TOKEN.md
  PATH: UE_V2/11_TKN/04__TKN__LYRICS_TOKEN.md
  MARKERS: [TKN, MUSIC, TEXT]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: TKN.QA
  UID:
  KIND: TKN
  ROLE: QA token schema
  DESC: QA acceptance/check token format (pass/fail/gap/stop)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/11_TKN/05__TKN__QA_TOKEN.md
  PATH: UE_V2/11_TKN/05__TKN__QA_TOKEN.md
  MARKERS: [TKN, QA]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31
