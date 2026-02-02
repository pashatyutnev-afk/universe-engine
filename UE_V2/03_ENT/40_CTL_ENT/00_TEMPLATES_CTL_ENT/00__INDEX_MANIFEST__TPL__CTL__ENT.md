FILE: UE_V2/03_ENT/40_CTL_ENT/00_TEMPLATES_CTL_ENT/00__INDEX_MANIFEST__TPL__CTL__ENT.md
SCOPE: UE_V2 / 03_ENT / 40_CTL_ENT / 00_TEMPLATES_CTL_ENT
DOC_TYPE: INDEX_MANIFEST
DOMAIN: TPL_CTL_ENT
UID: UE.V2.ENT.IDX.TPL_CTL_ENT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: CTL_ENT
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — адресная таблица реалма 00_TEMPLATES_CTL_ENT.
Хранит RAW и короткие смыслы шаблонов CTL. Никаких длинных объяснений.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Каждый элемент имеет KEY. Любой контракт/раннер ссылается только на KEY.
- Коротко: 1–2 строки смысла. Без лирики.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/03_ENT/40_CTL_ENT/00_TEMPLATES_CTL_ENT
- FOLDER_NAME: 00_TEMPLATES_CTL_ENT
- INDEX_SCOPE_TAGS: [ENT, CTL, TPL]

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
  UID: UE.V2.ENT.IDX.TPL_CTL_ENT.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for 00_TEMPLATES_CTL_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/40_CTL_ENT/00_TEMPLATES_CTL_ENT/00__INDEX_MANIFEST__TPL__CTL__ENT.md
  PATH: UE_V2/03_ENT/40_CTL_ENT/00_TEMPLATES_CTL_ENT/00__INDEX_MANIFEST__TPL__CTL__ENT.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: CTL_ENT
  UPDATED: 2026-02-02

### [M] REQUIRED
- KEY: INDEX_MANIFEST
  UID: UE.V2.ENT.IDX.TPL_CTL_ENT.001
  KIND: FILE
  ROLE: Address table for CTL templates realm
  DESC: RAW addresses + short meaning for templates
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/40_CTL_ENT/00_TEMPLATES_CTL_ENT/00__INDEX_MANIFEST__TPL__CTL__ENT.md
  PATH: UE_V2/03_ENT/40_CTL_ENT/00_TEMPLATES_CTL_ENT/00__INDEX_MANIFEST__TPL__CTL__ENT.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: CTL_ENT
  UPDATED: 2026-02-02

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.ENT.PIPE.TPL_CTL_ENT.001
  KIND: PIPE
  ROLE: Navigator for template retrieval actions
  DESC: Uses KEYS, resolves RAW via INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/40_CTL_ENT/00_TEMPLATES_CTL_ENT/00__PIPELINE_CONTRACT__TPL__CTL__ENT.md
  PATH: UE_V2/03_ENT/40_CTL_ENT/00_TEMPLATES_CTL_ENT/00__PIPELINE_CONTRACT__TPL__CTL__ENT.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: CTL_ENT
  UPDATED: 2026-02-02

### [O] CONTENT (TEMPLATES)
- KEY: TPL.CTL_ENTITY
  UID: UE.V2.ENT.TPL.CTL_ENTITY.001
  KIND: TPL
  ROLE: Template for CTL entity docs
  DESC: Canon structure for a CTL controller (ruleset + gates + KB scope)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/40_CTL_ENT/00_TEMPLATES_CTL_ENT/01__TPL__CTL_ENTITY__CTL__ENT.md
  PATH: UE_V2/03_ENT/40_CTL_ENT/00_TEMPLATES_CTL_ENT/01__TPL__CTL_ENTITY__CTL__ENT.md
  MARKERS: [TPL, CTL]
  STATUS: ACTIVE
  OWNER: CTL_ENT
  UPDATED: 2026-02-02

- KEY: TPL.CTL_BLOCKER
  UID: UE.V2.ENT.TPL.CTL_BLOCKER.001
  KIND: TPL
  ROLE: Template for CTL blocker docs
  DESC: Canon format for hard-stop/violation block and override policy
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/40_CTL_ENT/00_TEMPLATES_CTL_ENT/02__TPL__CTL_BLOCKER__CTL__ENT.md
  PATH: UE_V2/03_ENT/40_CTL_ENT/00_TEMPLATES_CTL_ENT/02__TPL__CTL_BLOCKER__CTL__ENT.md
  MARKERS: [TPL, CTL, BLOCK]
  STATUS: ACTIVE
  OWNER: CTL_ENT
  UPDATED: 2026-02-02

- KEY: TPL.INDEX_MANIFEST_CTL
  UID: UE.V2.ENT.TPL.INDEX_MANIFEST_CTL.001
  KIND: TPL
  ROLE: Template for CTL realm index-manifest docs
  DESC: Canon INDEX_MANIFEST structure for CTL realms (MUS/VID/WEB/DOC)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/40_CTL_ENT/00_TEMPLATES_CTL_ENT/03__TPL__INDEX_MANIFEST__CTL__ENT.md
  PATH: UE_V2/03_ENT/40_CTL_ENT/00_TEMPLATES_CTL_ENT/03__TPL__INDEX_MANIFEST__CTL__ENT.md
  MARKERS: [TPL, INDEX]
  STATUS: ACTIVE
  OWNER: CTL_ENT
  UPDATED: 2026-02-02
