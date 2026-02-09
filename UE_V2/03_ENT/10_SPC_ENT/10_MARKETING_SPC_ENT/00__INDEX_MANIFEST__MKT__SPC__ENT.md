FILE: UE_V2/03_ENT/10_SPC_ENT/10_MARKETING_SPC_ENT/00__INDEX_MANIFEST__MKT__SPC__ENT.md
SCOPE: UE_V2 / 03_ENT / 10_SPC_ENT / 10_MARKETING_SPC_ENT
DOC_TYPE: INDEX_MANIFEST
DOMAIN: MKT_SPC
UID: UE.V2.ENT.SPC.MKT.INDEX_MANIFEST.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — “таблица адресов” и кратких смыслов для реалма MARKETING_SPC_ENT.
Хранит RAW и машинные паспорта marketing-специалистов (MKT). Без длинных объяснений.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Каждый элемент имеет KEY. PIPELINE_CONTRACT ссылается только на KEY.
- Коротко: 1–2 строки смысла. Без лирики.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/03_ENT/10_SPC_ENT/10_MARKETING_SPC_ENT
- FOLDER_NAME: 10_MARKETING_SPC_ENT
- INDEX_SCOPE_TAGS: [ENT, SPC, MKT]

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
  UID: UE.V2.ENT.SPC.MKT.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for MARKETING_SPC_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/10_MARKETING_SPC_ENT/00__INDEX_MANIFEST__MKT__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/10_MARKETING_SPC_ENT/00__INDEX_MANIFEST__MKT__SPC__ENT.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [M] REQUIRED (минимум для реалма)
- KEY: INDEX_MANIFEST
  UID: UE.V2.ENT.SPC.MKT.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: Raw addresses + short meaning for MARKETING_SPC_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/10_MARKETING_SPC_ENT/00__INDEX_MANIFEST__MKT__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/10_MARKETING_SPC_ENT/00__INDEX_MANIFEST__MKT__SPC__ENT.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.ENT.SPC.MKT.PIPELINE_CONTRACT.001
  KIND: PIPE
  ROLE: Realm step-run navigator
  DESC: KEY-only contract; resolves targets via this INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/10_MARKETING_SPC_ENT/00__PIPELINE_CONTRACT__MKT__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/10_MARKETING_SPC_ENT/00__PIPELINE_CONTRACT__MKT__SPC__ENT.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [O] CONTENT (marketing specialists)

- KEY: SPC.MKT.BRAND_ARCHITECT
  UID:
  KIND: ENTITY
  ROLE: Brand architect
  DESC: Defines brand identity system, voice, promise; outputs identity constraints and coherence checks
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/10_MARKETING_SPC_ENT/01__MKT__BRAND_ARCHITECT_SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/10_MARKETING_SPC_ENT/01__MKT__BRAND_ARCHITECT_SPC__ENT.md
  MARKERS: [SPC, MKT, SPECIALIST, BRAND]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.MKT.AUDIENCE_ANALYST
  UID:
  KIND: ENTITY
  ROLE: Audience analyst
  DESC: Models target audiences and segments; outputs audience map and positioning constraints
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/10_MARKETING_SPC_ENT/02__MKT__AUDIENCE_ANALYST_SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/10_MARKETING_SPC_ENT/02__MKT__AUDIENCE_ANALYST_SPC__ENT.md
  MARKERS: [SPC, MKT, SPECIALIST, AUD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.MKT.AUDIENCE_RESEARCH_SPECIALIST
  UID:
  KIND: ENTITY
  ROLE: Audience research specialist
  DESC: Runs research loops and insights extraction; outputs research briefs and evidence-backed conclusions
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/10_MARKETING_SPC_ENT/03__MKT__AUDIENCE_RESEARCH_SPECIALIST_SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/10_MARKETING_SPC_ENT/03__MKT__AUDIENCE_RESEARCH_SPECIALIST_SPC__ENT.md
  MARKERS: [SPC, MKT, SPECIALIST, RCH]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.MKT.CONTENT_PACKAGING_SPECIALIST
  UID:
  KIND: ENTITY
  ROLE: Content packaging specialist
  DESC: Packages content into platform-ready units; outputs packaging templates and deliverable specs
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/10_MARKETING_SPC_ENT/04__MKT__CONTENT_PACKAGING_SPECIALIST_SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/10_MARKETING_SPC_ENT/04__MKT__CONTENT_PACKAGING_SPECIALIST_SPC__ENT.md
  MARKERS: [SPC, MKT, SPECIALIST, PACK]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.MKT.PLATFORM_DISTRIBUTION_SPECIALIST
  UID:
  KIND: ENTITY
  ROLE: Platform distribution specialist
  DESC: Plans platform distribution and scheduling; outputs distribution plan and channel constraints
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/10_MARKETING_SPC_ENT/05__MKT__PLATFORM_DISTRIBUTION_SPECIALIST_SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/10_MARKETING_SPC_ENT/05__MKT__PLATFORM_DISTRIBUTION_SPECIALIST_SPC__ENT.md
  MARKERS: [SPC, MKT, SPECIALIST, DIST]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.MKT.SEO_DISCOVERY_SPECIALIST
  UID:
  KIND: ENTITY
  ROLE: SEO and discovery specialist
  DESC: Optimizes discovery (SEO/metadata); outputs SEO pack and indexing constraints
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/10_MARKETING_SPC_ENT/06__MKT__SEO_DISCOVERY_SPECIALIST_SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/10_MARKETING_SPC_ENT/06__MKT__SEO_DISCOVERY_SPECIALIST_SPC__ENT.md
  MARKERS: [SPC, MKT, SPECIALIST, SEO]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.MKT.TRAILER_TEASER_SPECIALIST
  UID:
  KIND: ENTITY
  ROLE: Trailer/teaser specialist
  DESC: Designs trailers/teasers structure; outputs teaser script/beat map and variant plan
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/10_MARKETING_SPC_ENT/07__MKT__TRAILER_TEASER_SPECIALIST_SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/10_MARKETING_SPC_ENT/07__MKT__TRAILER_TEASER_SPECIALIST_SPC__ENT.md
  MARKERS: [SPC, MKT, SPECIALIST, TRAILER]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.MKT.COMMUNITY_MANAGER
  UID:
  KIND: ENTITY
  ROLE: Community manager
  DESC: Builds community loops and moderation rules; outputs community plan and engagement guidelines
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/10_MARKETING_SPC_ENT/08__MKT__COMMUNITY_MANAGER_SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/10_MARKETING_SPC_ENT/08__MKT__COMMUNITY_MANAGER_SPC__ENT.md
  MARKERS: [SPC, MKT, SPECIALIST, COM]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.MKT.ENGAGEMENT_STRATEGIST
  UID:
  KIND: ENTITY
  ROLE: Engagement strategist
  DESC: Designs engagement loops and retention; outputs engagement strategy and experiments plan
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/10_MARKETING_SPC_ENT/09__MKT__ENGAGEMENT_STRATEGIST_SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/10_MARKETING_SPC_ENT/09__MKT__ENGAGEMENT_STRATEGIST_SPC__ENT.md
  MARKERS: [SPC, MKT, SPECIALIST, ENG]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.MKT.GROWTH_HACKER
  UID:
  KIND: ENTITY
  ROLE: Growth hacker
  DESC: Drives growth experiments and acquisition; outputs growth hypotheses and KPI plan
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/10_MARKETING_SPC_ENT/10__MKT__GROWTH_HACKER_SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/10_MARKETING_SPC_ENT/10__MKT__GROWTH_HACKER_SPC__ENT.md
  MARKERS: [SPC, MKT, SPECIALIST, GROW]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.MKT.MONETIZATION_STRATEGIST
  UID:
  KIND: ENTITY
  ROLE: Monetization strategist
  DESC: Designs monetization routes and offers; outputs monetization model and constraints
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/10_MARKETING_SPC_ENT/11__MKT__MONETIZATION_STRATEGIST_SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/10_MARKETING_SPC_ENT/11__MKT__MONETIZATION_STRATEGIST_SPC__ENT.md
  MARKERS: [SPC, MKT, SPECIALIST, MONEY]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31
