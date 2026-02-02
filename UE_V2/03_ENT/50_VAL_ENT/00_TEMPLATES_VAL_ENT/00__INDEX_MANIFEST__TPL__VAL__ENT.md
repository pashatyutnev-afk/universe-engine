FILE: UE_V2/03_ENT/50_VAL_ENT/00_TEMPLATES_VAL_ENT/00__INDEX_MANIFEST__TPL__VAL__ENT.md
SCOPE: UE_V2 / 03_ENT / 50_VAL_ENT / 00_TEMPLATES_VAL_ENT
DOC_TYPE: INDEX_MANIFEST
DOMAIN: TPL_VAL_ENT
UID: UE.V2.ENT.IDX.TPL_VAL_ENT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: VAL_ENT
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — адресная таблица реалма 00_TEMPLATES_VAL_ENT.
Хранит RAW и короткие смыслы шаблонов VAL. Без длинных объяснений.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Каждый элемент имеет KEY. PIPELINE_CONTRACT ссылается только на KEY.
- Коротко: 1–2 строки смысла. Без лирики.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/03_ENT/50_VAL_ENT/00_TEMPLATES_VAL_ENT
- FOLDER_NAME: 00_TEMPLATES_VAL_ENT
- INDEX_SCOPE_TAGS: [ENT, VAL, TPL]

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
  UID: UE.V2.ENT.IDX.TPL_VAL_ENT.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for 00_TEMPLATES_VAL_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/50_VAL_ENT/00_TEMPLATES_VAL_ENT/00__INDEX_MANIFEST__TPL__VAL__ENT.md
  PATH: UE_V2/03_ENT/50_VAL_ENT/00_TEMPLATES_VAL_ENT/00__INDEX_MANIFEST__TPL__VAL__ENT.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: VAL_ENT
  UPDATED: 2026-02-02

### [M] REQUIRED
- KEY: INDEX_MANIFEST
  UID: UE.V2.ENT.IDX.TPL_VAL_ENT.001
  KIND: FILE
  ROLE: Address table for VAL templates realm
  DESC: RAW addresses + short meaning for templates
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/50_VAL_ENT/00_TEMPLATES_VAL_ENT/00__INDEX_MANIFEST__TPL__VAL__ENT.md
  PATH: UE_V2/03_ENT/50_VAL_ENT/00_TEMPLATES_VAL_ENT/00__INDEX_MANIFEST__TPL__VAL__ENT.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: VAL_ENT
  UPDATED: 2026-02-02

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.ENT.PIPE.TPL_VAL_ENT.001
  KIND: PIPE
  ROLE: Navigator for template retrieval actions
  DESC: Uses KEYS, resolves RAW via INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/50_VAL_ENT/00_TEMPLATES_VAL_ENT/00__PIPELINE_CONTRACT__TPL__VAL__ENT.md
  PATH: UE_V2/03_ENT/50_VAL_ENT/00_TEMPLATES_VAL_ENT/00__PIPELINE_CONTRACT__TPL__VAL__ENT.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: VAL_ENT
  UPDATED: 2026-02-02

### [O] CONTENT (TEMPLATES)
- KEY: TPL.VAL_ENTITY
  UID: UE.V2.ENT.TPL.VAL_ENTITY.001
  KIND: TPL
  ROLE: Template for VAL validator docs
  DESC: Canon structure for a validator (checks, evidence, gates)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/50_VAL_ENT/00_TEMPLATES_VAL_ENT/01__TPL__VAL_ENTITY__VAL__ENT.md
  PATH: UE_V2/03_ENT/50_VAL_ENT/00_TEMPLATES_VAL_ENT/01__TPL__VAL_ENTITY__VAL__ENT.md
  MARKERS: [TPL, VAL]
  STATUS: ACTIVE
  OWNER: VAL_ENT
  UPDATED: 2026-02-02

- KEY: TPL.VAL_VIOLATION
  UID: UE.V2.ENT.TPL.VAL_VIOLATION.001
  KIND: TPL
  ROLE: Template for violation records
  DESC: Canon format for violations, severity, fail codes, required fixes
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/50_VAL_ENT/00_TEMPLATES_VAL_ENT/02__TPL__VAL_VIOLATION__VAL__ENT.md
  PATH: UE_V2/03_ENT/50_VAL_ENT/00_TEMPLATES_VAL_ENT/02__TPL__VAL_VIOLATION__VAL__ENT.md
  MARKERS: [TPL, VAL, LOG]
  STATUS: ACTIVE
  OWNER: VAL_ENT
  UPDATED: 2026-02-02

- KEY: TPL.INDEX_MANIFEST_VAL
  UID: UE.V2.ENT.TPL.INDEX_MANIFEST_VAL.001
  KIND: TPL
  ROLE: Template for INDEX_MANIFEST docs (VAL realms)
  DESC: Canon INDEX_MANIFEST structure for VAL realms (MUS/VID/WEB/DOC/VAL_ENG/LIB)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/50_VAL_ENT/00_TEMPLATES_VAL_ENT/03__TPL__INDEX_MANIFEST__VAL__ENT.md
  PATH: UE_V2/03_ENT/50_VAL_ENT/00_TEMPLATES_VAL_ENT/03__TPL__INDEX_MANIFEST__VAL__ENT.md
  MARKERS: [TPL, INDEX]
  STATUS: ACTIVE
  OWNER: VAL_ENT
  UPDATED: 2026-02-02

- KEY: TPL.PIPELINE_CONTRACT_VAL
  UID: UE.V2.ENT.TPL.PIPELINE_CONTRACT_VAL.001
  KIND: TPL
  ROLE: Template for PIPELINE_CONTRACT docs (VAL realms)
  DESC: Canon pipeline contract structure for validators routing
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/50_VAL_ENT/00_TEMPLATES_VAL_ENT/04__TPL__PIPELINE_CONTRACT__VAL__ENT.md
  PATH: UE_V2/03_ENT/50_VAL_ENT/00_TEMPLATES_VAL_ENT/04__TPL__PIPELINE_CONTRACT__VAL__ENT.md
  MARKERS: [TPL, PIPE]
  STATUS: ACTIVE
  OWNER: VAL_ENT
  UPDATED: 2026-02-02
