FILE: UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/00__INDEX_MANIFEST__MUS__VAL__ENT.md
SCOPE: UE_V2 / 03_ENT / 50_VAL_ENT / 10_MUSIC_VAL
DOC_TYPE: INDEX_MANIFEST
DOMAIN: MUS_VAL_ENT
UID: UE.V2.ENT.IDX.MUS_VAL_ENT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: VAL_ENT
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — адресная таблица реалма музыкальных валидаторов (VAL).
Хранит RAW и короткие смыслы файлов. Без длинных объяснений.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Каждый элемент имеет KEY. PIPELINE_CONTRACT ссылается только на KEY.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL
- FOLDER_NAME: 10_MUSIC_VAL
- INDEX_SCOPE_TAGS: [ENT, VAL, MUS]

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
  UID: UE.V2.ENT.IDX.MUS_VAL_ENT.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for MUS VAL realm
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/00__INDEX_MANIFEST__MUS__VAL__ENT.md
  PATH: UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/00__INDEX_MANIFEST__MUS__VAL__ENT.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: VAL_ENT
  UPDATED: 2026-02-02

### [M] REQUIRED
- KEY: INDEX_MANIFEST
  UID: UE.V2.ENT.IDX.MUS_VAL_ENT.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: RAW addresses + short meaning for MUS validators
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/00__INDEX_MANIFEST__MUS__VAL__ENT.md
  PATH: UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/00__INDEX_MANIFEST__MUS__VAL__ENT.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: VAL_ENT
  UPDATED: 2026-02-02

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.ENT.PIPE.MUS_VAL_ENT.001
  KIND: PIPE
  ROLE: Router for applying validators
  DESC: Uses KEYS, resolves RAW via INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/00__PIPELINE_CONTRACT__MUS__VAL__ENT.md
  PATH: UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/00__PIPELINE_CONTRACT__MUS__VAL__ENT.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: VAL_ENT
  UPDATED: 2026-02-02

### [O] VALIDATORS
- KEY: VAL.MUS.HOOK_TIMING
  UID: UE.V2.ENT.VAL.MUS.HOOK_TIMING.001
  KIND: ENTITY
  ROLE: Hook timing validator
  DESC: Validates that hook appears within target window when required
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/01__MUS__HOOK_TIMING__VAL__ENT.md
  PATH: UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/01__MUS__HOOK_TIMING__VAL__ENT.md
  MARKERS: [VAL, MUS]
  STATUS: ACTIVE
  OWNER: VAL_ENT
  UPDATED: 2026-02-02

- KEY: VAL.MUS.UGC_READY
  UID: UE.V2.ENT.VAL.MUS.UGC_READY.001
  KIND: ENTITY
  ROLE: UGC readiness validator
  DESC: Validates UGC/shortform readiness rules and structure
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/02__MUS__UGC_READY__VAL__ENT.md
  PATH: UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/02__MUS__UGC_READY__VAL__ENT.md
  MARKERS: [VAL, MUS]
  STATUS: ACTIVE
  OWNER: VAL_ENT
  UPDATED: 2026-02-02

- KEY: VAL.MUS.REPEAT_GUARD
  UID: UE.V2.ENT.VAL.MUS.REPEAT_GUARD.001
  KIND: ENTITY
  ROLE: Repeat guard validator
  DESC: Detects excessive repetition and low-variance loops
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/03__MUS__REPEAT_GUARD__VAL__ENT.md
  PATH: UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/03__MUS__REPEAT_GUARD__VAL__ENT.md
  MARKERS: [VAL, MUS]
  STATUS: ACTIVE
  OWNER: VAL_ENT
  UPDATED: 2026-02-02

- KEY: VAL.MUS.PD_ONLY
  UID: UE.V2.ENT.VAL.MUS.PD_ONLY.001
  KIND: ENTITY
  ROLE: PD-only validator (blocker)
  DESC: Blocks direct copying and unsafe reference demands
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/04__MUS__PD_ONLY__VAL__ENT.md
  PATH: UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/04__MUS__PD_ONLY__VAL__ENT.md
  MARKERS: [VAL, MUS, BLOCK, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: VAL_ENT
  UPDATED: 2026-02-02

- KEY: VAL.MUS.COLLISION_BLOCKER
  UID: UE.V2.ENT.VAL.MUS.COLLISION_BLOCKER.001
  KIND: ENTITY
  ROLE: Collision blocker validator
  DESC: Blocks catalog/name/hook collisions when evidence indicates
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/05__MUS__COLLISION_BLOCKER__VAL__ENT.md
  PATH: UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/05__MUS__COLLISION_BLOCKER__VAL__ENT.md
  MARKERS: [VAL, MUS, BLOCK, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: VAL_ENT
  UPDATED: 2026-02-02

- KEY: VAL.MUS.RELEASE_PACK_READY
  UID: UE.V2.ENT.VAL.MUS.RELEASE_PACK_READY.001
  KIND: ENTITY
  ROLE: Release pack readiness validator
  DESC: Validates required artifacts for release packaging
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/06__MUS__RELEASE_PACK_READY__VAL__ENT.md
  PATH: UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/06__MUS__RELEASE_PACK_READY__VAL__ENT.md
  MARKERS: [VAL, MUS, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: VAL_ENT
  UPDATED: 2026-02-02

- KEY: VAL.MUS.NAMING_COLLISION
  UID: UE.V2.ENT.VAL.MUS.NAMING_COLLISION.001
  KIND: ENTITY
  ROLE: Naming collision validator
  DESC: Validates title/artist/version naming has no collisions
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/07__MUS__NAMING_COLLISION__VAL__ENT.md
  PATH: UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/07__MUS__NAMING_COLLISION__VAL__ENT.md
  MARKERS: [VAL, MUS]
  STATUS: ACTIVE
  OWNER: VAL_ENT
  UPDATED: 2026-02-02

- KEY: VAL.MUS.PROMPT_FIDELITY
  UID: UE.V2.ENT.VAL.MUS.PROMPT_FIDELITY.001
  KIND: ENTITY
  ROLE: Prompt fidelity validator
  DESC: Validates output stays aligned with brief/style tokens
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/08__MUS__PROMPT_FIDELITY__VAL__ENT.md
  PATH: UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/08__MUS__PROMPT_FIDELITY__VAL__ENT.md
  MARKERS: [VAL, MUS]
  STATUS: ACTIVE
  OWNER: VAL_ENT
  UPDATED: 2026-02-02

- KEY: VAL.MUS.CREDITS_RIGHTS
  UID: UE.V2.ENT.VAL.MUS.CREDITS_RIGHTS.001
  KIND: ENTITY
  ROLE: Credits and rights validator
  DESC: Validates metadata/credits consistency and risk flags
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/09__MUS__CREDITS_RIGHTS__VAL__ENT.md
  PATH: UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/09__MUS__CREDITS_RIGHTS__VAL__ENT.md
  MARKERS: [VAL, MUS, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: VAL_ENT
  UPDATED: 2026-02-02

- KEY: VAL.MUS.VOICE_DIVERSITY
  UID: UE.V2.ENT.VAL.MUS.VOICE_DIVERSITY.001
  KIND: ENTITY
  ROLE: Voice diversity validator
  DESC: Validates variety and avoids repeated voice identity patterns
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/10__MUS__VOICE_DIVERSITY__VAL__ENT.md
  PATH: UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/10__MUS__VOICE_DIVERSITY__VAL__ENT.md
  MARKERS: [VAL, MUS]
  STATUS: ACTIVE
  OWNER: VAL_ENT
  UPDATED: 2026-02-02

- KEY: VAL.MUS.CHAIN_COMPLETENESS
  UID: UE.V2.ENT.VAL.MUS.CHAIN_COMPLETENESS.001
  KIND: ENTITY
  ROLE: Chain completeness validator
  DESC: Validates required chain steps/tokens are present
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/11__MUS__CHAIN_COMPLETENESS__VAL__ENT.md
  PATH: UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/11__MUS__CHAIN_COMPLETENESS__VAL__ENT.md
  MARKERS: [VAL, MUS, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: VAL_ENT
  UPDATED: 2026-02-02

- KEY: VAL.MUS.COVERAGE_PASS
  UID: UE.V2.ENT.VAL.MUS.COVERAGE_PASS.001
  KIND: ENTITY
  ROLE: Coverage pass validator
  DESC: Validates requested scope is covered by artifacts
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/12__MUS__COVERAGE_PASS__VAL__ENT.md
  PATH: UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/12__MUS__COVERAGE_PASS__VAL__ENT.md
  MARKERS: [VAL, MUS]
  STATUS: ACTIVE
  OWNER: VAL_ENT
  UPDATED: 2026-02-02

- KEY: VAL.MUS.PROMPT_SPEC
  UID: UE.V2.ENT.VAL.MUS.PROMPT_SPEC.001
  KIND: ENTITY
  ROLE: Prompt spec validator
  DESC: Validates prompt spec is complete and deterministic
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/13__MUS__PROMPT_SPEC__VAL__ENT.md
  PATH: UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/13__MUS__PROMPT_SPEC__VAL__ENT.md
  MARKERS: [VAL, MUS]
  STATUS: ACTIVE
  OWNER: VAL_ENT
  UPDATED: 2026-02-02

- KEY: VAL.MUS.SYNTHESIS_COHERENCE
  UID: UE.V2.ENT.VAL.MUS.SYNTHESIS_COHERENCE.001
  KIND: ENTITY
  ROLE: Synthesis coherence validator
  DESC: Validates merged/iterated result remains coherent
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/14__MUS__SYNTHESIS_COHERENCE__VAL__ENT.md
  PATH: UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/14__MUS__SYNTHESIS_COHERENCE__VAL__ENT.md
  MARKERS: [VAL, MUS]
  STATUS: ACTIVE
  OWNER: VAL_ENT
  UPDATED: 2026-02-02
