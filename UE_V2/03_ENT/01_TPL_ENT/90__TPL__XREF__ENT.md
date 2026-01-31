FILE: UE_V2/03_ENT/01_TPL_ENT/90__TPL__XREF__ENT.md
SCOPE: UE_V2 / 03_ENT / 01_TPL_ENT
DOC_TYPE: TEMPLATE
TEMPLATE_FOR: ENTITY_PASSPORT (XREF)
DOMAIN: ENT
UID: UE.V2.ENT.TPL.XREF.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: Template has no RAW

---

## [M] PURPOSE
Шаблон паспорта XREF.
XREF — таблица связей KEY→KEY (без RAW), которая помогает маршрутизации и выбору сущностей.

## [M] HARD_RULES
- Никаких RAW внутри XREF. Только KEY→KEY.
- Любая ссылка должна быть резолвима через INDEX_MANIFEST.
- Тип связи обязателен (LINK_TYPE).
- Минимальность: связи короткие, без лирики.

## [M] LINK_TYPES (canonical)
- USES
- PRODUCES
- DEPENDS_ON
- VALIDATES
- CONTROLS
- ROUTES_TO
- REFERENCES
- RELATED

## [M] XREF_ENTRY_SCHEMA
- FROM_KEY: <KEY>
  LINK_TYPE: <TYPE>
  TO_KEY: <KEY>
  NOTE: <one line>
  STATUS: ACTIVE|DEPRECATED
  UPDATED: 0000-00-00

## [M] BODY_TEMPLATE

### ENTITY_HEADER
ENTITY_TYPE: XREF
ENTITY_NAME: <REPLACE_ME>
ENTITY_KEY: <KEY_FOR_INDEX_MANIFEST>
DOMAIN_TAGS: [XREF, <LIST>]
OWNER_TEAM: <SYS|TEAM>
LIFECYCLE: ACTIVE|DRAFT|DEPRECATED

### PURPOSE
<1-2 lines>

### SCOPE
- DESCRIBES: <what area this xref covers>
- KEYSPACE: <one line>                         # e.g. ENT.*, REG.*, LAW_*

### ENTRIES (KEY->KEY)
- FROM_KEY: <REPLACE_ME>
  LINK_TYPE: USES
  TO_KEY: <REPLACE_ME>
  NOTE: <one line>
  STATUS: ACTIVE
  UPDATED: 2026-01-31

### OUTPUTS
- ARTIFACTS: [XREF_TABLE]
- TOKENS: [ROUTING_HINTS?]

### ROUTING_HINTS (optional)
- <one line>

### DEPENDENCIES (KEYS ONLY)
- LAW_KEYS: [LAW_01, LAW_04, LAW_05, LAW_06, LAW_19, LAW_20]
- REG_KEYS: [<KEYS_ONLY>]

### GATES
PASS_IF:
- all entries are KEY->KEY and link types are valid
REWORK_IF:
- missing link type / ambiguous keys
FAIL_IF:
- RAW embedded / bypass manifest

### CHANGELOG (append-only)
- DATE: 0000-00-00
  CHANGE_ID: <REPLACE_ME>
  TYPE: CREATE|UPDATE|DEPRECATE
  NOTES: <one line>
