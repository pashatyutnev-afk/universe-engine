FILE: UE_V2/03_ENT/60_QA_ENT/00__INDEX_MANIFEST__QA__ENT.md
SCOPE: UE_V2 / 03_ENT / 60_QA_ENT
DOC_TYPE: INDEX_MANIFEST
DOMAIN: QA_ENT
UID: UE.V2.ENT.IDX.QA_ENT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: QA_ENT
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — адресная таблица реалма 60_QA_ENT.
Хранит RAW и короткие смыслы для QA-реалмов и root QA файлов. Без длинных объяснений.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Каждый элемент имеет KEY. PIPELINE_CONTRACT ссылается только на KEY.
- SELF запись обязательна.
- Коротко: 1–2 строки смысла. Без лирики.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/03_ENT/60_QA_ENT
- FOLDER_NAME: 60_QA_ENT
- INDEX_SCOPE_TAGS: [ENT, QA]

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
  UID: UE.V2.ENT.IDX.QA_ENT.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for 60_QA_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/60_QA_ENT/00__INDEX_MANIFEST__QA__ENT.md
  PATH: UE_V2/03_ENT/60_QA_ENT/00__INDEX_MANIFEST__QA__ENT.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: QA_ENT
  UPDATED: 2026-02-02

### [M] REQUIRED (root files)
- KEY: INDEX_MANIFEST
  UID: UE.V2.ENT.IDX.QA_ENT.001
  KIND: FILE
  ROLE: Address table for QA realm
  DESC: RAW addresses + short meaning for 60_QA_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/60_QA_ENT/00__INDEX_MANIFEST__QA__ENT.md
  PATH: UE_V2/03_ENT/60_QA_ENT/00__INDEX_MANIFEST__QA__ENT.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: QA_ENT
  UPDATED: 2026-02-02

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.ENT.PIPE.QA_ENT.001
  KIND: PIPE
  ROLE: Router for QA realm actions
  DESC: Routes to QA sub-realms via KEYS only
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/60_QA_ENT/00__PIPELINE_CONTRACT__QA__ENT.md
  PATH: UE_V2/03_ENT/60_QA_ENT/00__PIPELINE_CONTRACT__QA__ENT.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: QA_ENT
  UPDATED: 2026-02-02

- KEY: QA.NATURALNESS_GATE
  UID: UE.V2.ENT.QA.NATURALNESS_GATE.001
  KIND: ENTITY
  ROLE: Root naturalness gate
  DESC: Minimal naturalness QA gate (root entry)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/60_QA_ENT/01__NATURALNESS_GATE__QA__ENT.md
  PATH: UE_V2/03_ENT/60_QA_ENT/01__NATURALNESS_GATE__QA__ENT.md
  MARKERS: [QA, GATE, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: QA_ENT
  UPDATED: 2026-02-02

- KEY: QA.CREATE_FLOW
  UID: UE.V2.ENT.QA.CREATE_FLOW.001
  KIND: ENTITY
  ROLE: Root QA create-flow
  DESC: Canon QA flow builder (root entry)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/60_QA_ENT/02__CREATE_FLOW__QA__ENT.md
  PATH: UE_V2/03_ENT/60_QA_ENT/02__CREATE_FLOW__QA__ENT.md
  MARKERS: [QA, ROUTER, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: QA_ENT
  UPDATED: 2026-02-02

- KEY: DOD
  UID: UE.V2.ENT.QA.DOD.001
  KIND: STD
  ROLE: Definition of done for QA realm
  DESC: Completion checklist + invariants for 60_QA_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/60_QA_ENT/99__DEFINITION_OF_DONE__QA__ENT.md
  PATH: UE_V2/03_ENT/60_QA_ENT/99__DEFINITION_OF_DONE__QA__ENT.md
  MARKERS: [STD, GATE, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: QA_ENT
  UPDATED: 2026-02-02

---

## [M] REALMS (folders + their indexes/contracts)

### [M] 00_GOVERNANCE_QA_ENT
- KEY: REALM.GVN_QA
  UID: UE.V2.ENT.REALM.GVN_QA.001
  KIND: FOLDER
  ROLE: Governance QA realm
  DESC: QA governance: naturalness gate, create flow, issue lifecycle (realm)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/60_QA_ENT/00_GOVERNANCE_QA_ENT/00__INDEX_MANIFEST__GVN__QA__ENT.md
  PATH: UE_V2/03_ENT/60_QA_ENT/00_GOVERNANCE_QA_ENT
  MARKERS: [NAV, QA, GVN, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: QA_ENT
  UPDATED: 2026-02-02

### [M] 10_MUSIC_QA
- KEY: REALM.MUS_QA
  UID: UE.V2.ENT.REALM.MUS_QA.001
  KIND: FOLDER
  ROLE: Music QA realm
  DESC: Panels and gates for music QA (hook/scroll/loop/mix/regression)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/60_QA_ENT/10_MUSIC_QA/00__INDEX_MANIFEST__MUS__QA__ENT.md
  PATH: UE_V2/03_ENT/60_QA_ENT/10_MUSIC_QA
  MARKERS: [NAV, QA, MUS, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: QA_ENT
  UPDATED: 2026-02-02

### [M] 20_VIDEO_QA_ENT
- KEY: REALM.VID_QA
  UID: UE.V2.ENT.REALM.VID_QA.001
  KIND: FOLDER
  ROLE: Video QA realm
  DESC: Video QA basics: README + regression guard
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/60_QA_ENT/20_VIDEO_QA_ENT/00__INDEX_MANIFEST__VID__QA__ENT.md
  PATH: UE_V2/03_ENT/60_QA_ENT/20_VIDEO_QA_ENT
  MARKERS: [NAV, QA, VID, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: QA_ENT
  UPDATED: 2026-02-02

### [M] 30_WEB_QA_ENT
- KEY: REALM.WEB_QA
  UID: UE.V2.ENT.REALM.WEB_QA.001
  KIND: FOLDER
  ROLE: Web QA realm
  DESC: Web QA: a11y audit and related checks
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/60_QA_ENT/30_WEB_QA_ENT/00__INDEX_MANIFEST__WEB__QA__ENT.md
  PATH: UE_V2/03_ENT/60_QA_ENT/30_WEB_QA_ENT
  MARKERS: [NAV, QA, WEB, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: QA_ENT
  UPDATED: 2026-02-02

### [M] 40_DOCS_QA_ENT
- KEY: REALM.DOC_QA
  UID: UE.V2.ENT.REALM.DOC_QA.001
  KIND: FOLDER
  ROLE: Docs QA realm
  DESC: Docs QA: lint audit and minimum structure checks
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/60_QA_ENT/40_DOCS_QA_ENT/00__INDEX_MANIFEST__DOC__QA__ENT.md
  PATH: UE_V2/03_ENT/60_QA_ENT/40_DOCS_QA_ENT
  MARKERS: [NAV, QA, DOC, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: QA_ENT
  UPDATED: 2026-02-02

### [M] 90_SHARED_LIB_QA_ENT
- KEY: REALM.LIB_QA
  UID: UE.V2.ENT.REALM.LIB_QA.001
  KIND: FOLDER
  ROLE: Shared QA library realm
  DESC: Shared rules: severity scale, fail code map, evidence requirements
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/60_QA_ENT/90_SHARED_LIB_QA_ENT/00__INDEX_MANIFEST__LIB__QA__ENT.md
  PATH: UE_V2/03_ENT/60_QA_ENT/90_SHARED_LIB_QA_ENT
  MARKERS: [NAV, QA, LIB, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: QA_ENT
  UPDATED: 2026-02-02
