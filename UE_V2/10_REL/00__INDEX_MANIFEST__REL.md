FILE: UE_V2/10_REL/00__INDEX_MANIFEST__REL.md
SCOPE: UE_V2 / 10_REL
DOC_TYPE: INDEX_MANIFEST
DOMAIN: REL
UID: UE.V2.REL.INDEX_MANIFEST.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — “таблица адресов” и кратких смыслов для реалма 10_REL.
Хранит RAW и машинные паспорта релизного слоя: readiness, impact, rework, packaging, post-release.
Без длинных объяснений.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Любая навигация по 10_REL выполняется через KEY → RAW.
- PIPELINE_CONTRACT ссылается только на KEY.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/10_REL
- FOLDER_NAME: 10_REL
- INDEX_SCOPE_TAGS: [REL, SYS]

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
  UID: UE.V2.REL.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for 10_REL
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/10_REL/00__INDEX_MANIFEST__REL.md
  PATH: UE_V2/10_REL/00__INDEX_MANIFEST__REL.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [M] REQUIRED (минимум для реалма)
- KEY: INDEX_MANIFEST
  UID: UE.V2.REL.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: Raw addresses + short meaning for 10_REL
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/10_REL/00__INDEX_MANIFEST__REL.md
  PATH: UE_V2/10_REL/00__INDEX_MANIFEST__REL.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.REL.PIPELINE_CONTRACT.001
  KIND: PIPE
  ROLE: Realm step-run navigator
  DESC: KEY-only contract; resolves targets via this INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/10_REL/00__PIPELINE_CONTRACT__REL.md
  PATH: UE_V2/10_REL/00__PIPELINE_CONTRACT__REL.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [O] CONTENT (release set)

- KEY: REL.CAL_A
  UID:
  KIND: STD
  ROLE: Release calendar / cadence A
  DESC: Release cadence rules, cycles, timing constraints
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/10_REL/01__CAL_A.md
  PATH: UE_V2/10_REL/01__CAL_A.md
  MARKERS: [REL, CAL]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: REL.READINESS_MATRIX
  UID:
  KIND: STD
  ROLE: Release readiness matrix
  DESC: Readiness criteria matrix and status interpretation
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/10_REL/02__READINESS_MATRIX.md
  PATH: UE_V2/10_REL/02__READINESS_MATRIX.md
  MARKERS: [REL, GATE, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: REL.ARC_IMPACT
  UID:
  KIND: STD
  ROLE: Arc impact model
  DESC: Impact model for arc/season/series changes and compatibility
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/10_REL/03__ARC_IMPACT.md
  PATH: UE_V2/10_REL/03__ARC_IMPACT.md
  MARKERS: [REL]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: REL.SHEET_FMT
  UID:
  KIND: STD
  ROLE: Release sheet format
  DESC: Canon sheet format for release tracking and reporting
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/10_REL/04__SHEET_FMT.md
  PATH: UE_V2/10_REL/04__SHEET_FMT.md
  MARKERS: [REL, STD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: REL.UID_TRACK
  UID:
  KIND: STD
  ROLE: UID tracking for release
  DESC: UID tracking rules for release packaging and audit trail
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/10_REL/05__UID_TRACK.md
  PATH: UE_V2/10_REL/05__UID_TRACK.md
  MARKERS: [REL, UID, TRACE]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: REL.REWORK
  UID:
  KIND: STD
  ROLE: Rework policy
  DESC: Rework triggers, rules, and loop discipline before release
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/10_REL/06__REWORK.md
  PATH: UE_V2/10_REL/06__REWORK.md
  MARKERS: [REL, REWORK]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: REL.DROP_RULES
  UID:
  KIND: LAW
  ROLE: Drop rules
  DESC: Drop conditions, constraints, and safety rules for release
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/10_REL/07__DROP_RULES.md
  PATH: UE_V2/10_REL/07__DROP_RULES.md
  MARKERS: [REL, LAW]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: REL.PACK_REL
  UID:
  KIND: STD
  ROLE: Release packaging pack
  DESC: Packaging checklist + required pointers for release output pack
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/10_REL/08__PACK_REL.md
  PATH: UE_V2/10_REL/08__PACK_REL.md
  MARKERS: [REL, OUTPUT, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: REL.POST_REL
  UID:
  KIND: STD
  ROLE: Post-release protocol
  DESC: Post-release checks, logging, and follow-up actions
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/10_REL/09__POST_REL.md
  PATH: UE_V2/10_REL/09__POST_REL.md
  MARKERS: [REL, POST]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31
