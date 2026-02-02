FILE: UE_V2/03_ENT/60_QA_ENT/10_MUSIC_QA/00__INDEX_MANIFEST__MUS__QA__ENT.md
SCOPE: UE_V2 / 03_ENT / 60_QA_ENT / 10_MUSIC_QA
DOC_TYPE: INDEX_MANIFEST
DOMAIN: MUS_QA_ENT
UID: UE.V2.ENT.IDX.MUS_QA_ENT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: QA_ENT
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — адресная таблица реалма музыкального QA.
Хранит RAW и короткие смыслы файлов (панели/аудиты/гейты) для проверки музыки.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Каждый элемент имеет KEY. PIPELINE_CONTRACT ссылается только на KEY.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).
- Коротко: 1–2 строки смысла. Без лирики.

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/03_ENT/60_QA_ENT/10_MUSIC_QA
- FOLDER_NAME: 10_MUSIC_QA
- INDEX_SCOPE_TAGS: [ENT, QA, MUS]

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
  UID: UE.V2.ENT.IDX.MUS_QA_ENT.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for MUS QA realm
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/60_QA_ENT/10_MUSIC_QA/00__INDEX_MANIFEST__MUS__QA__ENT.md
  PATH: UE_V2/03_ENT/60_QA_ENT/10_MUSIC_QA/00__INDEX_MANIFEST__MUS__QA__ENT.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: QA_ENT
  UPDATED: 2026-02-02

### [M] REQUIRED
- KEY: INDEX_MANIFEST
  UID: UE.V2.ENT.IDX.MUS_QA_ENT.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: RAW addresses + short meaning for music QA
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/60_QA_ENT/10_MUSIC_QA/00__INDEX_MANIFEST__MUS__QA__ENT.md
  PATH: UE_V2/03_ENT/60_QA_ENT/10_MUSIC_QA/00__INDEX_MANIFEST__MUS__QA__ENT.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: QA_ENT
  UPDATED: 2026-02-02

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.ENT.PIPE.MUS_QA_ENT.001
  KIND: PIPE
  ROLE: Router for music QA actions
  DESC: Uses KEYS, resolves RAW via INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/60_QA_ENT/10_MUSIC_QA/00__PIPELINE_CONTRACT__MUS__QA__ENT.md
  PATH: UE_V2/03_ENT/60_QA_ENT/10_MUSIC_QA/00__PIPELINE_CONTRACT__MUS__QA__ENT.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: QA_ENT
  UPDATED: 2026-02-02

### [O] QA PANELS / CHECKS
- KEY: QA.MUS.SCROLL_STOP_5S
  UID: UE.V2.ENT.QA.MUS.SCROLL_STOP_5S.001
  KIND: ENTITY
  ROLE: 5s scroll-stop test
  DESC: Checks first 5 seconds catch attention (thumb-stopping)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/60_QA_ENT/10_MUSIC_QA/01__MUS__SCROLL_STOP_5S__QA__ENT.md
  PATH: UE_V2/03_ENT/60_QA_ENT/10_MUSIC_QA/01__MUS__SCROLL_STOP_5S__QA__ENT.md
  MARKERS: [QA, MUS, GATE]
  STATUS: ACTIVE
  OWNER: QA_ENT
  UPDATED: 2026-02-02

- KEY: QA.MUS.LOOP_15S
  UID: UE.V2.ENT.QA.MUS.LOOP_15S.001
  KIND: ENTITY
  ROLE: 15s loop test
  DESC: Checks if 15s loop stays engaging and seamless
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/60_QA_ENT/10_MUSIC_QA/02__MUS__LOOP_15S__QA__ENT.md
  PATH: UE_V2/03_ENT/60_QA_ENT/10_MUSIC_QA/02__MUS__LOOP_15S__QA__ENT.md
  MARKERS: [QA, MUS, GATE]
  STATUS: ACTIVE
  OWNER: QA_ENT
  UPDATED: 2026-02-02

- KEY: QA.MUS.RECOGNITION_10S
  UID: UE.V2.ENT.QA.MUS.RECOGNITION_10S.001
  KIND: ENTITY
  ROLE: 10s recognition test
  DESC: Checks recognizability of hook/motif within 10 seconds
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/60_QA_ENT/10_MUSIC_QA/03__MUS__RECOGNITION_10S__QA__ENT.md
  PATH: UE_V2/03_ENT/60_QA_ENT/10_MUSIC_QA/03__MUS__RECOGNITION_10S__QA__ENT.md
  MARKERS: [QA, MUS, GATE]
  STATUS: ACTIVE
  OWNER: QA_ENT
  UPDATED: 2026-02-02

- KEY: QA.MUS.CREATOR_PANEL
  UID: UE.V2.ENT.QA.MUS.CREATOR_PANEL.001
  KIND: ENTITY
  ROLE: Creator panel QA
  DESC: Checklist for creator panel notes: structure, vocal, energy, clarity
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/60_QA_ENT/10_MUSIC_QA/04__MUS__CREATOR_PANEL__QA__ENT.md
  PATH: UE_V2/03_ENT/60_QA_ENT/10_MUSIC_QA/04__MUS__CREATOR_PANEL__QA__ENT.md
  MARKERS: [QA, MUS, PANEL]
  STATUS: ACTIVE
  OWNER: QA_ENT
  UPDATED: 2026-02-02

- KEY: QA.MUS.MIX_TRANSLATION
  UID: UE.V2.ENT.QA.MUS.MIX_TRANSLATION.001
  KIND: ENTITY
  ROLE: Mix translation QA
  DESC: Checks translation across phone/car/earbuds and loudness balance
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/60_QA_ENT/10_MUSIC_QA/05__MUS__MIX_TRANSLATION__QA__ENT.md
  PATH: UE_V2/03_ENT/60_QA_ENT/10_MUSIC_QA/05__MUS__MIX_TRANSLATION__QA__ENT.md
  MARKERS: [QA, MUS]
  STATUS: ACTIVE
  OWNER: QA_ENT
  UPDATED: 2026-02-02

- KEY: QA.MUS.HOOK_PANEL
  UID: UE.V2.ENT.QA.MUS.HOOK_PANEL.001
  KIND: ENTITY
  ROLE: Hook panel QA
  DESC: Hook clarity, singability, phrase length, re-listen pull
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/60_QA_ENT/10_MUSIC_QA/06__MUS__HOOK_PANEL__QA__ENT.md
  PATH: UE_V2/03_ENT/60_QA_ENT/10_MUSIC_QA/06__MUS__HOOK_PANEL__QA__ENT.md
  MARKERS: [QA, MUS, PANEL]
  STATUS: ACTIVE
  OWNER: QA_ENT
  UPDATED: 2026-02-02

- KEY: QA.MUS.CATALOG_DIFFERENTIATION
  UID: UE.V2.ENT.QA.MUS.CATALOG_DIFFERENTIATION.001
  KIND: ENTITY
  ROLE: Catalog differentiation QA
  DESC: Ensures track differs enough from internal catalog references
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/60_QA_ENT/10_MUSIC_QA/07__MUS__CATALOG_DIFFERENTIATION__QA__ENT.md
  PATH: UE_V2/03_ENT/60_QA_ENT/10_MUSIC_QA/07__MUS__CATALOG_DIFFERENTIATION__QA__ENT.md
  MARKERS: [QA, MUS]
  STATUS: ACTIVE
  OWNER: QA_ENT
  UPDATED: 2026-02-02

- KEY: QA.MUS.VOICE_DIVERSITY_AUDIT
  UID: UE.V2.ENT.QA.MUS.VOICE_DIVERSITY_AUDIT.001
  KIND: ENTITY
  ROLE: Voice diversity audit
  DESC: Audits voice variety across a batch/portfolio
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/60_QA_ENT/10_MUSIC_QA/08__MUS__VOICE_DIVERSITY_AUDIT__QA__ENT.md
  PATH: UE_V2/03_ENT/60_QA_ENT/10_MUSIC_QA/08__MUS__VOICE_DIVERSITY_AUDIT__QA__ENT.md
  MARKERS: [QA, MUS, AUDIT]
  STATUS: ACTIVE
  OWNER: QA_ENT
  UPDATED: 2026-02-02

- KEY: QA.MUS.REGRESSION_GUARD
  UID: UE.V2.ENT.QA.MUS.REGRESSION_GUARD.001
  KIND: ENTITY
  ROLE: Regression guard
  DESC: Prevents quality regression across iterations/variants
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/60_QA_ENT/10_MUSIC_QA/09__MUS__REGRESSION_GUARD__QA__ENT.md
  PATH: UE_V2/03_ENT/60_QA_ENT/10_MUSIC_QA/09__MUS__REGRESSION_GUARD__QA__ENT.md
  MARKERS: [QA, MUS, GATE]
  STATUS: ACTIVE
  OWNER: QA_ENT
  UPDATED: 2026-02-02

- KEY: QA.MUS.TRACK_QA_PANEL
  UID: UE.V2.ENT.QA.MUS.TRACK_QA_PANEL.001
  KIND: ENTITY
  ROLE: Final track QA panel
  DESC: Final decision panel combining key checks into one report
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/60_QA_ENT/10_MUSIC_QA/10__MUS__TRACK_QA_PANEL__QA__ENT.md
  PATH: UE_V2/03_ENT/60_QA_ENT/10_MUSIC_QA/10__MUS__TRACK_QA_PANEL__QA__ENT.md
  MARKERS: [QA, MUS, PANEL, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: QA_ENT
  UPDATED: 2026-02-02
