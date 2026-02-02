FILE: UE_V2/03_ENT/30_ORC_ENT/06_WEB_ORC_ENT/00__INDEX_MANIFEST__WEB__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 06_WEB_ORC_ENT
DOC_TYPE: INDEX_MANIFEST
DOMAIN: WEB_ORC_ENT
UID: UE.V2.ENT.IDX.WEB_ORC_ENT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — адресная таблица реалма 06_WEB_ORC_ENT.
Хранит KEYS, короткий смысл, RAW и PATH (как справка). Без длинных историй.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Каждый элемент имеет KEY. PIPELINE_CONTRACT ссылается только на KEY.
- Коротко: 1–2 строки смысла. Без лирики.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/03_ENT/30_ORC_ENT/06_WEB_ORC_ENT
- FOLDER_NAME: 06_WEB_ORC_ENT
- INDEX_SCOPE_TAGS: [ENT, ORC, WEB]

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
  UID: UE.V2.ENT.IDX.WEB_ORC_ENT.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for 06_WEB_ORC_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/06_WEB_ORC_ENT/00__INDEX_MANIFEST__WEB__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/06_WEB_ORC_ENT/00__INDEX_MANIFEST__WEB__ORC__ENT.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

### [M] REQUIRED (минимум для реалма)
- KEY: INDEX_MANIFEST
  UID: UE.V2.ENT.IDX.WEB_ORC_ENT.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: Raw addresses + short meaning for 06_WEB_ORC_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/06_WEB_ORC_ENT/00__INDEX_MANIFEST__WEB__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/06_WEB_ORC_ENT/00__INDEX_MANIFEST__WEB__ORC__ENT.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.ENT.PIPE.WEB_ORC_ENT.001
  KIND: PIPE
  ROLE: Navigator for realm actions
  DESC: Uses KEYS, resolves RAW via INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/06_WEB_ORC_ENT/00__PIPELINE_CONTRACT__WEB__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/06_WEB_ORC_ENT/00__PIPELINE_CONTRACT__WEB__ORC__ENT.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

### [O] WEB ORC ENT (modules)
- KEY: WEB.BRIEF_FACTORY
  UID:
  KIND: FILE
  ROLE: Web brief factory
  DESC: Builds web brief: page goal, sections, constraints, target audience, CTA
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/06_WEB_ORC_ENT/01__WEB__BRIEF_FACTORY__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/06_WEB_ORC_ENT/01__WEB__BRIEF_FACTORY__ORC__ENT.md
  MARKERS: [WEB, BRIEF, NAV]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: WEB.BLOCK_FACTORY
  UID:
  KIND: FILE
  ROLE: Web block factory
  DESC: Produces self-contained HTML/CSS/JS blocks with UX + motion defaults
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/06_WEB_ORC_ENT/02__WEB__BLOCK_FACTORY__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/06_WEB_ORC_ENT/02__WEB__BLOCK_FACTORY__ORC__ENT.md
  MARKERS: [WEB, BLOCK, OUTPUT]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: WEB.A11Y_QA
  UID:
  KIND: FILE
  ROLE: Accessibility QA
  DESC: Checks a11y: semantics, focus, contrast principles, keyboard nav, aria
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/06_WEB_ORC_ENT/03__WEB__A11Y_QA__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/06_WEB_ORC_ENT/03__WEB__A11Y_QA__ORC__ENT.md
  MARKERS: [WEB, A11Y, QA, GATE]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: WEB.SEO_PACKAGER
  UID:
  KIND: FILE
  ROLE: SEO packager
  DESC: Packages meta-tags, JSON-LD, copy blocks and internal linking notes
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/06_WEB_ORC_ENT/04__WEB__SEO_PACKAGER__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/06_WEB_ORC_ENT/04__WEB__SEO_PACKAGER__ORC__ENT.md
  MARKERS: [WEB, SEO, OUTPUT]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: WEB.DEPLOY_HANDOFF
  UID:
  KIND: FILE
  ROLE: Deploy handoff
  DESC: Defines deploy steps, platform constraints, asset naming, and handoff checklist
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/06_WEB_ORC_ENT/05__WEB__DEPLOY_HANDOFF__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/06_WEB_ORC_ENT/05__WEB__DEPLOY_HANDOFF__ORC__ENT.md
  MARKERS: [WEB, DEPLOY, OUTPUT]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02
