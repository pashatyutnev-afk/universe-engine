FILE: UE_V2/01_SYS/02_SYS_LAW/00__INDEX_MANIFEST__SYS__LAW.md
SCOPE: UE_V2 / 01_SYS / 02_SYS_LAW
DOC_TYPE: INDEX_MANIFEST
DOMAIN: SYS_LAW
UID: UE.V2.SYS.IDX.SYS_LAW.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — “таблица адресов” и кратких смыслов для папки/реалма 02_SYS_LAW.
Хранит RAW и машинные паспорта LAW-доков. Никаких “историй” и длинных объяснений.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Каждый элемент имеет KEY. PIPELINE_CONTRACT ссылается только на KEY.
- Коротко: 1–2 строки смысла. Без лирики.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/01_SYS/02_SYS_LAW
- FOLDER_NAME: 02_SYS_LAW
- INDEX_SCOPE_TAGS: [SYS, LAW]

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
  UID: UE.V2.SYS.IDX.SYS_LAW.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for 02_SYS_LAW
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/02_SYS_LAW/00__INDEX_MANIFEST__SYS__LAW.md
  PATH: UE_V2/01_SYS/02_SYS_LAW/00__INDEX_MANIFEST__SYS__LAW.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [M] REQUIRED (минимум для реалма)
- KEY: INDEX_MANIFEST
  UID: UE.V2.SYS.IDX.SYS_LAW.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: Raw addresses + short meaning for 02_SYS_LAW
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/02_SYS_LAW/00__INDEX_MANIFEST__SYS__LAW.md
  PATH: UE_V2/01_SYS/02_SYS_LAW/00__INDEX_MANIFEST__SYS__LAW.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.SYS.PIPE.SYS_LAW.001
  KIND: PIPE
  ROLE: Navigator for realm actions
  DESC: Uses KEYS, resolves RAW via INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/02_SYS_LAW/00__PIPELINE_CONTRACT__SYS__LAW.md
  PATH: UE_V2/01_SYS/02_SYS_LAW/00__PIPELINE_CONTRACT__SYS__LAW.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [O] CONTENT (laws)
- KEY: LAW_01
  UID:
  KIND: LAW
  ROLE: Canon integrity
  DESC: Canon Integrity: единый смысл, нет внутренних конфликтов
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_01.md
  PATH: UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_01.md
  MARKERS: [LAW]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LAW_02
  UID:
  KIND: LAW
  ROLE: Identity stability
  DESC: Identity Stability: UID/версии фиксируют сущность и историю
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_02.md
  PATH: UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_02.md
  MARKERS: [LAW]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LAW_03
  UID:
  KIND: LAW
  ROLE: Artifact only
  DESC: Artifact Only: нет “голого контента”, только артефакт
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_03.md
  PATH: UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_03.md
  MARKERS: [LAW]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LAW_04
  UID:
  KIND: LAW
  ROLE: Navigation integrity
  DESC: Navigation Integrity: RAW-only, no guessing
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_04.md
  PATH: UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_04.md
  MARKERS: [LAW, NAV]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LAW_05
  UID:
  KIND: LAW
  ROLE: Minimality
  DESC: Minimality: минимально-достаточные сущности и тексты
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_05.md
  PATH: UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_05.md
  MARKERS: [LAW]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LAW_06
  UID:
  KIND: LAW
  ROLE: Traceability
  DESC: Traceability: всё проверяемо по маркерам и трассе
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_06.md
  PATH: UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_06.md
  MARKERS: [LAW, TRACE]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LAW_07
  UID:
  KIND: LAW
  ROLE: Wear texture
  DESC: Wear Texture: допустимая “текстура износа” (WTI)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_07.md
  PATH: UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_07.md
  MARKERS: [LAW]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LAW_08
  UID:
  KIND: LAW
  ROLE: Inverse contrast
  DESC: Inverse Contrast: громко→тихо как осознанная форма
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_08.md
  PATH: UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_08.md
  MARKERS: [LAW]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LAW_09
  UID:
  KIND: LAW
  ROLE: Readability boundary
  DESC: Readability Boundary: граница читаемости (RI)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_09.md
  PATH: UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_09.md
  MARKERS: [LAW]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LAW_10
  UID:
  KIND: LAW
  ROLE: Non-clone variance
  DESC: Non-Clone Variance: “единая ДНК”, но не клоны
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_10.md
  PATH: UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_10.md
  MARKERS: [LAW]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LAW_11
  UID:
  KIND: LAW
  ROLE: Low-end anchor
  DESC: Low-End Anchor: tight low end и якоря саба
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_11.md
  PATH: UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_11.md
  MARKERS: [LAW]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LAW_12
  UID:
  KIND: LAW
  ROLE: Impact predict
  DESC: Impact Predict: прогноз нейро-реакции (Alienation/Rage/Hope)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_12.md
  PATH: UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_12.md
  MARKERS: [LAW]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LAW_13
  UID:
  KIND: LAW
  ROLE: Silence point
  DESC: Silence Point: провал в тишину как целевое состояние
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_13.md
  PATH: UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_13.md
  MARKERS: [LAW]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LAW_14
  UID:
  KIND: LAW
  ROLE: Acceptance and release
  DESC: Acceptance & Release: приёмка, rework, выпуск
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_14.md
  PATH: UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_14.md
  MARKERS: [LAW, RELEASE]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LAW_15
  UID:
  KIND: LAW
  ROLE: Visual-audio link
  DESC: Visual-Audio Link: аудио-метрики управляют визуалом
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_15.md
  PATH: UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_15.md
  MARKERS: [LAW, VIS, AUD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LAW_16
  UID:
  KIND: LAW
  ROLE: ROOT index access only
  DESC: ROOT_INDEX используется только для выдачи RAW-доступа
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_16.md
  PATH: UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_16.md
  MARKERS: [LAW, NAV]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LAW_17
  UID:
  KIND: LAW
  ROLE: Single entrypoint start
  DESC: Единая точка запуска рантайма — START
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_17.md
  PATH: UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_17.md
  MARKERS: [LAW, NAV]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LAW_18
  UID:
  KIND: LAW
  ROLE: Must-load manifest
  DESC: RUNTIME_MANIFEST обязателен, MUST_LOAD ядра
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_18.md
  PATH: UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_18.md
  MARKERS: [LAW, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LAW_19
  UID:
  KIND: LAW
  ROLE: Route via xref reg kb
  DESC: Выбор маршрута через REG+XREF+KB_SCOPE, по памяти запрещено
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_19.md
  PATH: UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_19.md
  MARKERS: [LAW, ROUTE]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LAW_20
  UID:
  KIND: LAW
  ROLE: Noise budget
  DESC: Жёсткие лимиты на контекст/участников/варианты
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_20.md
  PATH: UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_20.md
  MARKERS: [LAW, LIMITS]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LAW_21
  UID:
  KIND: LAW
  ROLE: Focus-loop allowed
  DESC: Многопроходная доработка одного фокуса разрешена (FOCUS-LOOP)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_21.md
  PATH: UE_V2/01_SYS/02_SYS_LAW/SYS__LAW_21.md
  MARKERS: [LAW, LOOP]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31
