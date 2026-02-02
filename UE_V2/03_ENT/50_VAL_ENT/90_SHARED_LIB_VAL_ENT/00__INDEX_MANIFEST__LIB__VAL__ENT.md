FILE: UE_V2/03_ENT/50_VAL_ENT/90_SHARED_LIB_VAL_ENT/00__INDEX_MANIFEST__LIB__VAL__ENT.md
SCOPE: UE_V2 / 03_ENT / 50_VAL_ENT / 90_SHARED_LIB_VAL_ENT
DOC_TYPE: INDEX_MANIFEST
DOMAIN: LIB_VAL_ENT
UID: UE.V2.ENT.IDX.LIB_VAL_ENT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: VAL_ENT
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — адресная таблица реалма общей библиотеки валидаторов (VAL).
Хранит RAW и короткие смыслы общих валидаторных библиотек/правил.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Каждый элемент имеет KEY. PIPELINE_CONTRACT ссылается только на KEY.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).
- Никаких длинных историй: 1–2 строки смысла.

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/03_ENT/50_VAL_ENT/90_SHARED_LIB_VAL_ENT
- FOLDER_NAME: 90_SHARED_LIB_VAL_ENT
- INDEX_SCOPE_TAGS: [ENT, VAL, LIB]

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
  UID: UE.V2.ENT.IDX.LIB_VAL_ENT.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for 90_SHARED_LIB_VAL_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/50_VAL_ENT/90_SHARED_LIB_VAL_ENT/00__INDEX_MANIFEST__LIB__VAL__ENT.md
  PATH: UE_V2/03_ENT/50_VAL_ENT/90_SHARED_LIB_VAL_ENT/00__INDEX_MANIFEST__LIB__VAL__ENT.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: VAL_ENT
  UPDATED: 2026-02-02

### [M] REQUIRED
- KEY: INDEX_MANIFEST
  UID: UE.V2.ENT.IDX.LIB_VAL_ENT.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: RAW addresses + short meaning for shared VAL libs
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/50_VAL_ENT/90_SHARED_LIB_VAL_ENT/00__INDEX_MANIFEST__LIB__VAL__ENT.md
  PATH: UE_V2/03_ENT/50_VAL_ENT/90_SHARED_LIB_VAL_ENT/00__INDEX_MANIFEST__LIB__VAL__ENT.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: VAL_ENT
  UPDATED: 2026-02-02

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.ENT.PIPE.LIB_VAL_ENT.001
  KIND: PIPE
  ROLE: Router for shared VAL library usage
  DESC: Uses KEYS, resolves RAW via INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/50_VAL_ENT/90_SHARED_LIB_VAL_ENT/00__PIPELINE_CONTRACT__LIB__VAL__ENT.md
  PATH: UE_V2/03_ENT/50_VAL_ENT/90_SHARED_LIB_VAL_ENT/00__PIPELINE_CONTRACT__LIB__VAL__ENT.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: VAL_ENT
  UPDATED: 2026-02-02

### [O] CONTENT
- KEY: VAL.LIB.VIOLATION_TAXONOMY
  UID: UE.V2.ENT.VAL.LIB.VIOLATION_TAXONOMY.001
  KIND: ENTITY
  ROLE: Shared violation taxonomy
  DESC: Canon violation ids and severity classes for VAL layer
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/50_VAL_ENT/90_SHARED_LIB_VAL_ENT/01__LIB__VIOLATION_TAXONOMY__VAL__ENT.md
  PATH: UE_V2/03_ENT/50_VAL_ENT/90_SHARED_LIB_VAL_ENT/01__LIB__VIOLATION_TAXONOMY__VAL__ENT.md
  MARKERS: [VAL, LIB, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: VAL_ENT
  UPDATED: 2026-02-02

- KEY: VAL.LIB.FAIL_CODE_MAP
  UID: UE.V2.ENT.VAL.LIB.FAIL_CODE_MAP.001
  KIND: ENTITY
  ROLE: Shared fail-code map
  DESC: Canon fail codes and when to use them (VAL scope)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/50_VAL_ENT/90_SHARED_LIB_VAL_ENT/02__LIB__FAIL_CODE_MAP__VAL__ENT.md
  PATH: UE_V2/03_ENT/50_VAL_ENT/90_SHARED_LIB_VAL_ENT/02__LIB__FAIL_CODE_MAP__VAL__ENT.md
  MARKERS: [VAL, LIB, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: VAL_ENT
  UPDATED: 2026-02-02

- KEY: VAL.LIB.EVIDENCE_RULES
  UID: UE.V2.ENT.VAL.LIB.EVIDENCE_RULES.001
  KIND: ENTITY
  ROLE: Shared evidence rules
  DESC: What counts as evidence; no-guessing boundaries for PASS/FAIL
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/50_VAL_ENT/90_SHARED_LIB_VAL_ENT/03__LIB__EVIDENCE_RULES__VAL__ENT.md
  PATH: UE_V2/03_ENT/50_VAL_ENT/90_SHARED_LIB_VAL_ENT/03__LIB__EVIDENCE_RULES__VAL__ENT.md
  MARKERS: [VAL, LIB, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: VAL_ENT
  UPDATED: 2026-02-02
