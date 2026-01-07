# TEMPLATE — ENTITY PASSPORT (TECHNICAL)
FILE: 02_STANDARDS/03_TECHNICAL/01__ENTITY_PASSPORT_TEMPLATE.md

SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: TEMPLATE
TEMPLATE_TYPE: ENTITY_PASSPORT
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.TPL.STD.ENTITY_PASSPORT.001
OWNER: SYSTEM
ROLE: Canonical technical template for creating an Entity Passport (unified schema across projects/KB/system entities)

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Шаблон паспорта сущности нормализован: Doc Control + единый скелет + поля для xref/rel/статусов"
- REASON: "Нужен единый паспорт как атомарная единица знаний/сущности"
- IMPACT: "Стандартизирует создание сущностей во всех слоях"

---

## 0) HOW TO USE (MANDATORY)
1) Копируешь шаблон.
2) Заполняешь только фактические данные.
3) Регистрируешь сущность и файл по правилам naming/UID.
4) Добавляешь REL/XREF, если есть связи.

---

## 1) ENTITY PASSPORT — TEMPLATE (COPY BELOW)

# ENTITY PASSPORT — <ENTITY_NAME>
FILE: <CANON_PATH_TO_THIS_PASSPORT.md>

SCOPE: Universe Engine
LAYER: <LAYER_NAME>
ENTITY_TYPE: <TYPE_CODE>
ENTITY_GROUP: <GROUP_CODE>
LEVEL: <L0|L1|L2|L3>
STATUS: <DRAFT|ACTIVE|DEPRECATED|ARCHIVED>
LOCK: <OPEN|FIXED>
VERSION: <X.Y.Z>
UID: <UE....>

OWNER: <SYSTEM|PROJECT|...>
ROLE: <one-line purpose of this entity passport>

CHANGE_NOTE:
- DATE: <YYYY-MM-DD>
- TYPE: <PATCH|MINOR|MAJOR>
- SUMMARY: "<short summary>"
- REASON: "<why>"
- IMPACT: "<what it affects>"

---

## 0) IDENTITY
- NAME: <canonical name>
- ALIASES: [<optional>, ...]
- SHORT_DESC: <1–2 lines>
- TAGS: [<tag>, <tag>, ...]

## 1) CANON STATUS
- CANON_SCOPE: <SYSTEM|PROJECT|KB|ASSET>
- EXISTENCE: <REGISTERED_IN_MASTER_INDEX: YES/NO>
- SOURCE_OF_TRUTH: <YES/NO>  (if YES — this is SoT for its topic)
- DEPRECATES: [<UID>, ...]
- DEPRECATED_BY: [<UID>, ...]

## 2) DEFINITION (SoT)
- DEFINITION: <strict definition>
- BOUNDARIES: <what is included/excluded>
- NON_GOALS: <what this entity is NOT>

## 3) STRUCTURE / INTERNALS
- COMPONENTS: [<optional>, ...]
- PROPERTIES:
  - <key>: <value>
- STATES (if applicable):
  - <STATE_A>: <meaning>
  - <STATE_B>: <meaning>

## 4) RELATIONSHIPS (REL / XREF)
- REL:
  - <REL_TYPE>: <TARGET_UID> | WHY:<short>
- XREF:
  - <DOC_UID>: <section pointer> | WHY:<short>

## 5) USAGE / INTERFACE
- CONSUMES: [<artifact/doc types>, ...]
- PRODUCES: [<artifact/doc types>, ...]
- OUTPUT_TARGET: <path or layer target>
- RULES_APPLIED:
  - <LAW/STANDARD UID or PATH>

## 6) VALIDATION
- CHECKLIST:
  - [ ] UID valid + unique
  - [ ] Naming complies
  - [ ] Status/Lock correct
  - [ ] No duplication with existing SoT
  - [ ] REL/XREF present if needed

## 7) CHANGELOG (LOCAL)
- <YYYY-MM-DD> <TYPE> — <summary>
--- END.

---

## FILE 11B/∞  
`02_STANDARDS/03_TECHNICAL/02__INDEX_TEMPLATE.md` (NEW CANON)

```md
# TEMPLATE — INDEX (TECHNICAL)
FILE: 02_STANDARDS/03_TECHNICAL/02__INDEX_TEMPLATE.md

SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: TEMPLATE
TEMPLATE_TYPE: INDEX
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.TPL.STD.INDEX.001
OWNER: SYSTEM
ROLE: Canonical template for any INDEX file (master-index, registry index, realm index) with strict Doc Control and existence rules

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Добавлен единый шаблон индекса: Doc Control + existence rule + authority order + canon map"
- REASON: "Чтобы все индексы выглядели одинаково и читались как законы"
- IMPACT: "Ускоряет построение слоёв и снижает косяки навигации"

---

## 0) INDEX — TEMPLATE (COPY BELOW)

```md
# <INDEX TITLE>
FILE: <CANON_PATH_TO_THIS_INDEX.md>

SCOPE: Universe Engine
LAYER: <LAYER_NAME>
DOC_TYPE: INDEX
INDEX_TYPE: <MASTER|REGISTRY|REALM|GLOBAL|...>
LEVEL: <L0|L1|L2>
STATUS: <DRAFT|ACTIVE|DEPRECATED|ARCHIVED>
LOCK: <OPEN|FIXED>
VERSION: <X.Y.Z>
UID: <UE....>
OWNER: <SYSTEM|...>
ROLE: <one-line purpose>

CHANGE_NOTE:
- DATE: <YYYY-MM-DD>
- TYPE: <PATCH|MINOR|MAJOR>
- SUMMARY: "<short summary>"
- REASON: "<why>"
- IMPACT: "<what it affects>"

---

## 0) PURPOSE (LAW)
<What this index is the single source of truth for>

### EXISTENCE RULE (ABSOLUTE)
Если сущности/файла нет в этом INDEX — он не существует в рамках scope.

---

## 1) HOW TO USE (MANDATORY FLOW)
1) <step>
2) <step>
3) <step>

---

## 2) ORDER OF AUTHORITY (PRIORITY)
<list of priorities>

---

## 3) CANON MAP (REGISTERED)
<Numbered list with PATH + RAW links>

---

## 4) DOC CONTROL RULES
- Each registered doc must have Doc Control header
- No duplicate OWNER/LOCK/VERSION in footer
- Naming must follow naming rules

---

## FINAL RULE (LOCK)
LOCK: <FIXED|OPEN>
--- END.

---

Дальше **FILE 12/∞** — делаю alias-pointer’ы из старых:
- `02_STANDARDS/03_TECHNICAL/ENTITY_PASSPORT_TEMPLATE.md` → alias на `01__ENTITY_PASSPORT_TEMPLATE.md`
- `02_STANDARDS/03_TECHNICAL/INDEX_TEMPLATE.md` → alias на `02__INDEX_TEMPLATE.md`

Го?
::contentReference[oaicite:0]{index=0}
