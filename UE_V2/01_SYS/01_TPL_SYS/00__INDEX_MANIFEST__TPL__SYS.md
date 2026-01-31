FILE: 0000-00-00__TPL__INDEX_MANIFEST__SYS.md
SCOPE: UE_V2 / SYS
DOC_TYPE: TEMPLATE
TEMPLATE_FOR: INDEX_MANIFEST
UID: UE.V2.SYS.TPL.INDEX_MANIFEST.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-30
UPDATED: 2026-01-30
OWNER: SYS
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — это “таблица адресов” и кратких смыслов для папки/реалма.
Хранит RAW и машинные паспорта элементов. Никаких “историй” и длинных объяснений.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Каждый элемент имеет KEY. PIPELINE_CONTRACT ссылается только на KEY.
- Коротко: 1–2 строки смысла. Без лирики.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: <REPLACE_ME>            # например: UE_V2/04_NAV/05__IDX_AUD
- FOLDER_NAME: <REPLACE_ME>         # имя папки как в дереве
- INDEX_SCOPE_TAGS: [NAV, SYS]      # можно расширять

## [M] ENTRY_SCHEMA (v1)
Каждая запись — YAML-блок фиксированного вида:

- KEY: <UNIQUE_KEY>                 # короткий ключ, уникален в рамках реалма
  UID: <OPTIONAL_UID>               # если есть канонический UID
  KIND: FILE|FOLDER|ENTITY|PIPE|KB|REG|XREF|LOG|STD|LAW|TPL
  ROLE: <ONE_LINE_ROLE>             # зачем оно нужно системе
  DESC: <ONE_LINE_DESC>             # что внутри (коротко)
  RAW: <RAW_URL_OR_EMPTY>           # основной адрес
  PATH: <REPO_PATH_OR_EMPTY>        # справочно
  MARKERS: [MUST_LOAD, ROUTER, NAV, ...]   # маркерные флаги
  STATUS: ACTIVE|DRAFT|DEPRECATED
  OWNER: SYS|RUNTIME|USER|<TEAM>
  UPDATED: 0000-00-00

## [M] ENTRIES

### [M] SELF
- KEY: SELF
  UID: <UID_OF_THIS_INDEX>
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for current realm
  RAW: <RAW_OF_THIS_FILE>
  PATH: <PATH_OF_THIS_FILE>
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 0000-00-00

### [M] REQUIRED (минимум для реалма)
- KEY: INDEX_MANIFEST
  UID: <UID_OR_EMPTY>
  KIND: FILE
  ROLE: Address table for realm
  DESC: Raw addresses + short meaning
  RAW: <RAW>
  PATH: <PATH>
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 0000-00-00

- KEY: PIPELINE_CONTRACT
  UID: <UID_OR_EMPTY>
  KIND: FILE
  ROLE: Navigator for realm actions
  DESC: Uses KEYS, resolves RAW via INDEX_MANIFEST
  RAW: <RAW>
  PATH: <PATH>
  MARKERS: [PIPE, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 0000-00-00

### [O] CONTENT (пример структуры)
# добавляй по мере наполнения папки
# - KEY: SPC.MIX_ENGINEER
#   UID: UE.V2.ENT.SPC.MIX_ENGINEER.001
#   KIND: ENTITY
#   ROLE: Mix strategy, hook clarity, vocal space control
#   DESC: Produces MIX_TOKEN and revision notes
#   RAW: <RAW>
#   PATH: <PATH>
#   MARKERS: [SPC, MUSIC, TEXT]
#   STATUS: ACTIVE
#   OWNER: SYS
#   UPDATED: 0000-00-00
