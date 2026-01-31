FILE: UE_V2/07_DOM_AUD/00__INDEX_MANIFEST__DOM__AUD.md
SCOPE: UE_V2 / 07_DOM_AUD
DOC_TYPE: INDEX_MANIFEST
DOMAIN: DOM_AUD
UID: UE.V2.DOM.AUD.INDEX_MANIFEST.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — “таблица адресов” и кратких смыслов для реалма 07_DOM_AUD.
Хранит RAW и машинные паспорта AUD домена: метрики, формы (ORUM), спеки-дельта, fail, аномалии, микс и мастер-таргеты.
Без длинных объяснений.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Любая навигация по 07_DOM_AUD выполняется через KEY → RAW.
- PIPELINE_CONTRACT ссылается только на KEY.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/07_DOM_AUD
- FOLDER_NAME: 07_DOM_AUD
- INDEX_SCOPE_TAGS: [DOM, AUD]

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
  UID: UE.V2.DOM.AUD.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for 07_DOM_AUD
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/07_DOM_AUD/00__INDEX_MANIFEST__DOM__AUD.md
  PATH: UE_V2/07_DOM_AUD/00__INDEX_MANIFEST__DOM__AUD.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [M] REQUIRED (минимум для реалма)
- KEY: INDEX_MANIFEST
  UID: UE.V2.DOM.AUD.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: Raw addresses + short meaning for 07_DOM_AUD
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/07_DOM_AUD/00__INDEX_MANIFEST__DOM__AUD.md
  PATH: UE_V2/07_DOM_AUD/00__INDEX_MANIFEST__DOM__AUD.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.DOM.AUD.PIPELINE_CONTRACT.001
  KIND: PIPE
  ROLE: Domain step-run navigator
  DESC: KEY-only contract; resolves targets via this INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/07_DOM_AUD/00__PIPELINE_CONTRACT__DOM__AUD.md
  PATH: UE_V2/07_DOM_AUD/00__PIPELINE_CONTRACT__DOM__AUD.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [O] CONTENT (AUD domain set)

- KEY: AUD.ORUM.A
  UID:
  KIND: FILE
  ROLE: ORUM A form / rubric
  DESC: ORUM-A evaluation form and interpretation rules
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/07_DOM_AUD/01__ORUM_A.md
  PATH: UE_V2/07_DOM_AUD/01__ORUM_A.md
  MARKERS: [DOM, AUD, SCORE]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: AUD.ORUM.B
  UID:
  KIND: FILE
  ROLE: ORUM B form / rubric
  DESC: ORUM-B evaluation form and interpretation rules
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/07_DOM_AUD/02__ORUM_B.md
  PATH: UE_V2/07_DOM_AUD/02__ORUM_B.md
  MARKERS: [DOM, AUD, SCORE]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: AUD.MET.RI
  UID:
  KIND: STD
  ROLE: Readability/impact metric (RI)
  DESC: RI metric definition, measurement notes, and usage in gates
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/07_DOM_AUD/03__MET_RI.md
  PATH: UE_V2/07_DOM_AUD/03__MET_RI.md
  MARKERS: [DOM, AUD, METRIC, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: AUD.MET.WTI
  UID:
  KIND: STD
  ROLE: Wear texture index metric (WTI)
  DESC: WTI metric definition and acceptable wear texture constraints
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/07_DOM_AUD/04__MET_WTI.md
  PATH: UE_V2/07_DOM_AUD/04__MET_WTI.md
  MARKERS: [DOM, AUD, METRIC]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: AUD.MET.CF
  UID:
  KIND: STD
  ROLE: CF sync metric / mapping
  DESC: CF metric mapping and sync rules for audio decisions
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/07_DOM_AUD/05__MET_CF.md
  PATH: UE_V2/07_DOM_AUD/05__MET_CF.md
  MARKERS: [DOM, AUD, METRIC, SYNC]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: AUD.MET.LRA
  UID:
  KIND: STD
  ROLE: LRA metric / mapping
  DESC: LRA metric definition and integration usage
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/07_DOM_AUD/06__MET_LRA.md
  PATH: UE_V2/07_DOM_AUD/06__MET_LRA.md
  MARKERS: [DOM, AUD, METRIC, SYNC]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: AUD.SPEC.DELTA
  UID:
  KIND: STD
  ROLE: Spec delta rules
  DESC: What changes are allowed vs forbidden (delta) across mix/master revisions
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/07_DOM_AUD/07__SPEC_DELTA.md
  PATH: UE_V2/07_DOM_AUD/07__SPEC_DELTA.md
  MARKERS: [DOM, AUD, STD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: AUD.FAIL
  UID:
  KIND: FILE
  ROLE: AUD failure handling
  DESC: AUD-specific fail patterns and recovery actions
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/07_DOM_AUD/08__FAIL_AUD.md
  PATH: UE_V2/07_DOM_AUD/08__FAIL_AUD.md
  MARKERS: [DOM, AUD, FAIL]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: AUD.CAL.ANOM
  UID:
  KIND: STD
  ROLE: Anomaly calendar
  DESC: Anomaly calendar rules (exceptions, spikes, special handling)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/07_DOM_AUD/09__CAL_ANOM.md
  PATH: UE_V2/07_DOM_AUD/09__CAL_ANOM.md
  MARKERS: [DOM, AUD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: AUD.MIX.LOW
  UID:
  KIND: STD
  ROLE: Low-end mix rules
  DESC: Low-end anchor rules for mix decisions and checks
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/07_DOM_AUD/10__MIX_LOW.md
  PATH: UE_V2/07_DOM_AUD/10__MIX_LOW.md
  MARKERS: [DOM, AUD, MIX]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: AUD.MASTER.TARGETS
  UID:
  KIND: STD
  ROLE: Mastering targets
  DESC: Master targets (levels, loudness, dynamics) and acceptance constraints
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/07_DOM_AUD/11__MASTER_TARGETS.md
  PATH: UE_V2/07_DOM_AUD/11__MASTER_TARGETS.md
  MARKERS: [DOM, AUD, MASTER, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31
