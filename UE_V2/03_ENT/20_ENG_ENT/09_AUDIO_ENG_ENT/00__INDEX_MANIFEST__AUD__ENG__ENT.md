FILE: UE_V2/03_ENT/20_ENG_ENT/09_AUDIO_ENG_ENT/00__INDEX_MANIFEST__AUD__ENG__ENT.md
SCOPE: UE_V2 / 03_ENT / 20_ENG_ENT / 09_AUDIO_ENG_ENT
DOC_TYPE: INDEX_MANIFEST
DOMAIN: AUD_ENG
UID: UE.V2.ENT.ENG.AUD.INDEX_MANIFEST.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — “таблица адресов” и кратких смыслов для реалма AUDIO_ENG_ENT (AUD).
Хранит RAW и машинные паспорта AUD-движков. Без длинных объяснений.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Любая навигация по реалму: KEY -> resolve RAW here -> open.
- PIPELINE_CONTRACT ссылается только на KEY.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).
- NO GUESSING: для движков RAW заполняем только после фиксации кнопкой Raw (иначе GAP).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/03_ENT/20_ENG_ENT/09_AUDIO_ENG_ENT
- FOLDER_NAME: 09_AUDIO_ENG_ENT
- INDEX_SCOPE_TAGS: [ENT, ENG, AUD]

## [M] KEYSPACE
KEY_FORMAT: AUD.
RESOLUTION_RULE: KEY -> RAW берётся только из ENTRIES ниже

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
  UID: UE.V2.ENT.ENG.AUD.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for AUDIO_ENG_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/09_AUDIO_ENG_ENT/00__INDEX_MANIFEST__AUD__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/09_AUDIO_ENG_ENT/00__INDEX_MANIFEST__AUD__ENG__ENT.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [M] REQUIRED (minimum for realm)
- KEY: INDEX_MANIFEST
  UID: UE.V2.ENT.ENG.AUD.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: Raw addresses + short meaning for AUD engines
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/09_AUDIO_ENG_ENT/00__INDEX_MANIFEST__AUD__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/09_AUDIO_ENG_ENT/00__INDEX_MANIFEST__AUD__ENG__ENT.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.ENT.ENG.AUD.PIPELINE_CONTRACT.001
  KIND: PIPE
  ROLE: Realm step-run navigator
  DESC: KEY-only contract; resolves targets via this INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/09_AUDIO_ENG_ENT/00__PIPELINE_CONTRACT__AUD__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/09_AUDIO_ENG_ENT/00__PIPELINE_CONTRACT__AUD__ENG__ENT.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [O] CONTENT (AUD engines)
- KEY: AUD.MUSIC_COMPOSITION
  UID:
  KIND: ENTITY
  ROLE: Music composition engine
  DESC: Produces composition plan, motif map, harmonic intent; emits COMPOSITION_TOKEN
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/09_AUDIO_ENG_ENT/01__AUD__MUSIC_COMPOSITION__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/09_AUDIO_ENG_ENT/01__AUD__MUSIC_COMPOSITION__ENG__ENT.md
  MARKERS: [ENG, AUD, COMP]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: AUD.SONG_STRUCTURE
  UID:
  KIND: ENTITY
  ROLE: Song structure engine
  DESC: Builds section map and timing grid; emits SONG_STRUCTURE_TOKEN
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/09_AUDIO_ENG_ENT/02__AUD__SONG_STRUCTURE__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/09_AUDIO_ENG_ENT/02__AUD__SONG_STRUCTURE__ENG__ENT.md
  MARKERS: [ENG, AUD, STRUCT]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: AUD.HARMONY_CHORD
  UID:
  KIND: ENTITY
  ROLE: Harmony and chord engine
  DESC: Defines chord progressions/voicings; emits HARMONY_CHORD_TOKEN
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/09_AUDIO_ENG_ENT/03__AUD__HARMONY_CHORD__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/09_AUDIO_ENG_ENT/03__AUD__HARMONY_CHORD__ENG__ENT.md
  MARKERS: [ENG, AUD, HARMONY]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: AUD.MELODY_HOOK
  UID:
  KIND: ENTITY
  ROLE: Melody and hook engine
  DESC: Generates lead melody + hook candidates; emits MELODY_HOOK_PACK
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/09_AUDIO_ENG_ENT/04__AUD__MELODY_HOOK__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/09_AUDIO_ENG_ENT/04__AUD__MELODY_HOOK__ENG__ENT.md
  MARKERS: [ENG, AUD, HOOK]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: AUD.RHYTHM_GROOVE
  UID:
  KIND: ENTITY
  ROLE: Rhythm and groove engine
  DESC: Defines groove grid and rhythmic motifs; emits RHYTHM_GROOVE_TOKEN
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/09_AUDIO_ENG_ENT/05__AUD__RHYTHM_GROOVE__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/09_AUDIO_ENG_ENT/05__AUD__RHYTHM_GROOVE__ENG__ENT.md
  MARKERS: [ENG, AUD, GROOVE]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: AUD.RHYME_METER
  UID:
  KIND: ENTITY
  ROLE: Rhyme and meter engine
  DESC: Sets meter/flow constraints for lyrics; emits RHYME_METER_TOKEN
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/09_AUDIO_ENG_ENT/06__AUD__RHYME_METER__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/09_AUDIO_ENG_ENT/06__AUD__RHYME_METER__ENG__ENT.md
  MARKERS: [ENG, AUD, METER]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: AUD.LYRICS
  UID:
  KIND: ENTITY
  ROLE: Lyrics engine
  DESC: Produces lyric drafts aligned to structure/meter; emits LYRICS_PACK
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/09_AUDIO_ENG_ENT/07__AUD__LYRICS__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/09_AUDIO_ENG_ENT/07__AUD__LYRICS__ENG__ENT.md
  MARKERS: [ENG, AUD, LYRICS]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: AUD.ARRANGEMENT_INSTRUMENTATION
  UID:
  KIND: ENTITY
  ROLE: Arrangement and instrumentation engine
  DESC: Builds instrumentation map + arrangement plan; emits ARRANGEMENT_TOKEN
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/09_AUDIO_ENG_ENT/08__AUD__ARRANGEMENT_INSTRUMENTATION__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/09_AUDIO_ENG_ENT/08__AUD__ARRANGEMENT_INSTRUMENTATION__ENG__ENT.md
  MARKERS: [ENG, AUD, ARR]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: AUD.VOCAL_PERFORMANCE
  UID:
  KIND: ENTITY
  ROLE: Vocal performance engine
  DESC: Defines vocal delivery/phrasing/texture; emits VOCAL_PERFORMANCE_TOKEN
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/09_AUDIO_ENG_ENT/09__AUD__VOCAL_PERFORMANCE__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/09_AUDIO_ENG_ENT/09__AUD__VOCAL_PERFORMANCE__ENG__ENT.md
  MARKERS: [ENG, AUD, VOCAL]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: AUD.SOUND_DESIGN
  UID:
  KIND: ENTITY
  ROLE: Sound design engine
  DESC: Sound palette/FX/transitions; emits SOUND_DESIGN_PACK
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/09_AUDIO_ENG_ENT/10__AUD__SOUND_DESIGN__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/09_AUDIO_ENG_ENT/10__AUD__SOUND_DESIGN__ENG__ENT.md
  MARKERS: [ENG, AUD, SFX]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: AUD.MUSIC_STYLE_CONSISTENCY
  UID:
  KIND: ENTITY
  ROLE: Music style consistency engine
  DESC: Enforces style fingerprint consistency; emits STYLE_CONSISTENCY_REPORT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/09_AUDIO_ENG_ENT/11__AUD__MUSIC_STYLE_CONSISTENCY__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/09_AUDIO_ENG_ENT/11__AUD__MUSIC_STYLE_CONSISTENCY__ENG__ENT.md
  MARKERS: [ENG, AUD, STYLE, QA]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: AUD.MUSIC_TO_SCENE
  UID:
  KIND: ENTITY
  ROLE: Music-to-scene mapping engine
  DESC: Maps music cues to scene beats; emits MUSIC_TO_SCENE_MAP
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/09_AUDIO_ENG_ENT/12__AUD__MUSIC_TO_SCENE__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/09_AUDIO_ENG_ENT/12__AUD__MUSIC_TO_SCENE__ENG__ENT.md
  MARKERS: [ENG, AUD, VIS_LINK]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: AUD.MIX_MASTER
  UID:
  KIND: ENTITY
  ROLE: Mix and master engine
  DESC: Defines mix/master targets and checks; emits MIX_MASTER_TARGETS_PACK
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/09_AUDIO_ENG_ENT/13__AUD__MIX_MASTER__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/09_AUDIO_ENG_ENT/13__AUD__MIX_MASTER__ENG__ENT.md
  MARKERS: [ENG, AUD, MIX, MASTER]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

---

## [M] LOAD_HINTS
MIN_SET_KEYS:
- INDEX_MANIFEST
- PIPELINE_CONTRACT

OPTIONAL_KEYS:
- AUD.MUSIC_COMPOSITION
- AUD.SONG_STRUCTURE
- AUD.HARMONY_CHORD
- AUD.MELODY_HOOK
- AUD.RHYTHM_GROOVE
- AUD.RHYME_METER
- AUD.LYRICS
- AUD.ARRANGEMENT_INSTRUMENTATION
- AUD.VOCAL_PERFORMANCE
- AUD.SOUND_DESIGN
- AUD.MUSIC_STYLE_CONSISTENCY
- AUD.MUSIC_TO_SCENE
- AUD.MIX_MASTER

## [M] GUARDS
STOP_IF:
- RAW missing for any MIN_SET_KEYS
GAP_IF:
- requested KEY not present in ENTRIES
- any engine RAW is empty
