FILE: UE_V2/03_ENT/60_QA_ENT/90_SHARED_LIB_QA_ENT/00__INDEX_MANIFEST__LIB__QA__ENT.md
SCOPE: UE_V2 / 03_ENT / 60_QA_ENT / 90_SHARED_LIB_QA_ENT
DOC_TYPE: INDEX_MANIFEST
DOMAIN: LIB_QA_ENT
UID: UE.V2.ENT.IDX.LIB_QA_ENT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: QA_ENT
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — адресная таблица реалма общей библиотеки QA.
Хранит RAW и краткие смыслы общих QA-правил: severity scale, fail codes, evidence requirements.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Каждый элемент имеет KEY. PIPELINE_CONTRACT ссылается только на KEY.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).
- 1–2 строки смысла. Без лирики.

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/03_ENT/60_QA_ENT/90_SHARED_LIB_QA_ENT
- FOLDER_NAME: 90_SHARED_LIB_QA_ENT
- INDEX_SCOPE_TAGS: [ENT, QA, LIB]

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
  UID: UE.V2.ENT.IDX.LIB_QA_ENT.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for shared QA library realm
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/60_QA_ENT/90_SHARED_LIB_QA_ENT/00__INDEX_MANIFEST__LIB__QA__ENT.md
  PATH: UE_V2/03_ENT/60_QA_ENT/90_SHARED_LIB_QA_ENT/00__INDEX_MANIFEST__LIB__QA__ENT.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: QA_ENT
  UPDATED: 2026-02-02

### [M] REQUIRED
- KEY: INDEX_MANIFEST
  UID: UE.V2.ENT.IDX.LIB_QA_ENT.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: RAW addresses + short meaning for shared QA library
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/60_QA_ENT/90_SHARED_LIB_QA_ENT/00__INDEX_MANIFEST__LIB__QA__ENT.md
  PATH: UE_V2/03_ENT/60_QA_ENT/90_SHARED_LIB_QA_ENT/00__INDEX_MANIFEST__LIB__QA__ENT.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: QA_ENT
  UPDATED: 2026-02-02

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.ENT.PIPE.LIB_QA_ENT.001
  KIND: PIPE
  ROLE: Router for shared QA library usage
  DESC: Uses KEYS, resolves RAW via INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/60_QA_ENT/90_SHARED_LIB_QA_ENT/00__PIPELINE_CONTRACT__LIB__QA__ENT.md
  PATH: UE_V2/03_ENT/60_QA_ENT/90_SHARED_LIB_QA_ENT/00__PIPELINE_CONTRACT__LIB__QA__ENT.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: QA_ENT
  UPDATED: 2026-02-02

### [O] CONTENT
- KEY: QA.LIB.SEVERITY_SCALE
  UID: UE.V2.ENT.QA.LIB.SEVERITY_SCALE.001
  KIND: ENTITY
  ROLE: Shared severity scale
  DESC: Canon severity levels and meanings for QA reports/issues
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/60_QA_ENT/90_SHARED_LIB_QA_ENT/01__LIB__QA_SEVERITY_SCALE__QA__ENT.md
  PATH: UE_V2/03_ENT/60_QA_ENT/90_SHARED_LIB_QA_ENT/01__LIB__QA_SEVERITY_SCALE__QA__ENT.md
  MARKERS: [QA, LIB, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: QA_ENT
  UPDATED: 2026-02-02

- KEY: QA.LIB.FAIL_CODE_MAP
  UID: UE.V2.ENT.QA.LIB.FAIL_CODE_MAP.001
  KIND: ENTITY
  ROLE: Shared fail-code map
  DESC: Canon fail codes and usage for QA scope
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/60_QA_ENT/90_SHARED_LIB_QA_ENT/02__LIB__QA_FAIL_CODE_MAP__QA__ENT.md
  PATH: UE_V2/03_ENT/60_QA_ENT/90_SHARED_LIB_QA_ENT/02__LIB__QA_FAIL_CODE_MAP__QA__ENT.md
  MARKERS: [QA, LIB, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: QA_ENT
  UPDATED: 2026-02-02

- KEY: QA.LIB.EVIDENCE_REQUIREMENTS
  UID: UE.V2.ENT.QA.LIB.EVIDENCE_REQUIREMENTS.001
  KIND: ENTITY
  ROLE: Shared evidence requirements
  DESC: Evidence rules for QA decisions (ASK vs WARN vs FAIL)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/60_QA_ENT/90_SHARED_LIB_QA_ENT/03__LIB__QA_EVIDENCE_REQUIREMENTS__QA__ENT.md
  PATH: UE_V2/03_ENT/60_QA_ENT/90_SHARED_LIB_QA_ENT/03__LIB__QA_EVIDENCE_REQUIREMENTS__QA__ENT.md
  MARKERS: [QA, LIB, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: QA_ENT
  UPDATED: 2026-02-02
