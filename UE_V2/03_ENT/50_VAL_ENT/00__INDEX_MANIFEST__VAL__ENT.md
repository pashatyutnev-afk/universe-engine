FILE: UE_V2/03_ENT/50_VAL_ENT/00__INDEX_MANIFEST__VAL__ENT.md
SCOPE: UE_V2 / 03_ENT / 50_VAL_ENT
DOC_TYPE: INDEX_MANIFEST
DOMAIN: VAL_ENT
UID: UE.V2.ENT.IDX.VAL_ENT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: VAL_ENT
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — адресная таблица реалма 50_VAL_ENT.
Хранит RAW и короткие смыслы для VAL-реалмов и их контрактов. Без длинных объяснений.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Каждый элемент имеет KEY. PIPELINE_CONTRACT ссылается только на KEY.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/03_ENT/50_VAL_ENT
- FOLDER_NAME: 50_VAL_ENT
- INDEX_SCOPE_TAGS: [ENT, VAL]

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
  UID: UE.V2.ENT.IDX.VAL_ENT.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for 50_VAL_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/50_VAL_ENT/00__INDEX_MANIFEST__VAL__ENT.md
  PATH: UE_V2/03_ENT/50_VAL_ENT/00__INDEX_MANIFEST__VAL__ENT.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: VAL_ENT
  UPDATED: 2026-02-02

### [M] REQUIRED (root files)
- KEY: INDEX_MANIFEST
  UID: UE.V2.ENT.IDX.VAL_ENT.001
  KIND: FILE
  ROLE: Address table for VAL realm
  DESC: RAW addresses + short meaning for 50_VAL_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/50_VAL_ENT/00__INDEX_MANIFEST__VAL__ENT.md
  PATH: UE_V2/03_ENT/50_VAL_ENT/00__INDEX_MANIFEST__VAL__ENT.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: VAL_ENT
  UPDATED: 2026-02-02

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.ENT.PIPE.VAL_ENT.001
  KIND: PIPE
  ROLE: Router for VAL realm actions
  DESC: Routes to domain validators via KEYS only
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/50_VAL_ENT/00__PIPELINE_CONTRACT__VAL__ENT.md
  PATH: UE_V2/03_ENT/50_VAL_ENT/00__PIPELINE_CONTRACT__VAL__ENT.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: VAL_ENT
  UPDATED: 2026-02-02

- KEY: DOD
  UID: UE.V2.ENT.VAL.DOD.001
  KIND: STD
  ROLE: Definition of done for VAL realm
  DESC: Completion checklist + invariants for 50_VAL_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/50_VAL_ENT/99__DEFINITION_OF_DONE__VAL__ENT.md
  PATH: UE_V2/03_ENT/50_VAL_ENT/99__DEFINITION_OF_DONE__VAL__ENT.md
  MARKERS: [STD, GATE, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: VAL_ENT
  UPDATED: 2026-02-02

---

## [M] REALMS (folders + their indexes/contracts)

### [M] 00_TEMPLATES_VAL_ENT
- KEY: REALM.TPL_VAL
  UID: UE.V2.ENT.REALM.TPL_VAL.001
  KIND: FOLDER
  ROLE: Templates realm
  DESC: Templates for VAL entities, violations, index-manifests, contracts
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/50_VAL_ENT/00_TEMPLATES_VAL_ENT/00__INDEX_MANIFEST__TPL__VAL__ENT.md
  PATH: UE_V2/03_ENT/50_VAL_ENT/00_TEMPLATES_VAL_ENT
  MARKERS: [NAV, TPL, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: VAL_ENT
  UPDATED: 2026-02-02

### [M] 10_MUSIC_VAL
- KEY: REALM.MUS_VAL
  UID: UE.V2.ENT.REALM.MUS_VAL.001
  KIND: FOLDER
  ROLE: Music validators realm
  DESC: Validators for music artifacts (pd, collisions, readiness, fidelity)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/00__INDEX_MANIFEST__MUS__VAL__ENT.md
  PATH: UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL
  MARKERS: [NAV, VAL, MUS, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: VAL_ENT
  UPDATED: 2026-02-02

### [M] 11_VALIDATION_ENGINES
- KEY: REALM.VAL_ENG
  UID: UE.V2.ENT.REALM.VAL_ENG.001
  KIND: FOLDER
  ROLE: Cross-domain validation engines realm
  DESC: Engines for format/facts/language/cultural/historical/scientific checks
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/50_VAL_ENT/11_VALIDATION_ENGINES/00__INDEX_MANIFEST__VAL_ENG__VAL__ENT.md
  PATH: UE_V2/03_ENT/50_VAL_ENT/11_VALIDATION_ENGINES
  MARKERS: [NAV, VAL, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: VAL_ENT
  UPDATED: 2026-02-02

### [M] 20_VIDEO_VAL_ENT
- KEY: REALM.VID_VAL
  UID: UE.V2.ENT.REALM.VID_VAL.001
  KIND: FOLDER
  ROLE: Video validators realm
  DESC: Validators for video prompt constraints and export safety
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/50_VAL_ENT/20_VIDEO_VAL_ENT/00__INDEX_MANIFEST__VID__VAL__ENT.md
  PATH: UE_V2/03_ENT/50_VAL_ENT/20_VIDEO_VAL_ENT
  MARKERS: [NAV, VAL, VID, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: VAL_ENT
  UPDATED: 2026-02-02

### [M] 30_WEB_VAL_ENT
- KEY: REALM.WEB_VAL
  UID: UE.V2.ENT.REALM.WEB_VAL.001
  KIND: FOLDER
  ROLE: Web validators realm
  DESC: Validators for web artifacts (a11y minimum and related checks)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/50_VAL_ENT/30_WEB_VAL_ENT/00__INDEX_MANIFEST__WEB__VAL__ENT.md
  PATH: UE_V2/03_ENT/50_VAL_ENT/30_WEB_VAL_ENT
  MARKERS: [NAV, VAL, WEB, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: VAL_ENT
  UPDATED: 2026-02-02

### [M] 40_DOCS_VAL_ENT
- KEY: REALM.DOC_VAL
  UID: UE.V2.ENT.REALM.DOC_VAL.001
  KIND: FOLDER
  ROLE: Docs validators realm
  DESC: Validators for document structure and minimal lint
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/50_VAL_ENT/40_DOCS_VAL_ENT/00__INDEX_MANIFEST__DOC__VAL__ENT.md
  PATH: UE_V2/03_ENT/50_VAL_ENT/40_DOCS_VAL_ENT
  MARKERS: [NAV, VAL, DOC, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: VAL_ENT
  UPDATED: 2026-02-02

### [M] 90_SHARED_LIB_VAL_ENT
- KEY: REALM.LIB_VAL
  UID: UE.V2.ENT.REALM.LIB_VAL.001
  KIND: FOLDER
  ROLE: Shared VAL library realm
  DESC: Shared taxonomy, fail-code map, and evidence rules
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/50_VAL_ENT/90_SHARED_LIB_VAL_ENT/00__INDEX_MANIFEST__LIB__VAL__ENT.md
  PATH: UE_V2/03_ENT/50_VAL_ENT/90_SHARED_LIB_VAL_ENT
  MARKERS: [NAV, VAL, LIB, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: VAL_ENT
  UPDATED: 2026-02-02
