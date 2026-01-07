# ENTITY PASSPORT TEMPLATE (BASE) (CANON)
FILE: 02_STANDARDS/03_TECHNICAL/ENTITY_PASSPORT_TEMPLATE.md

SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: TEMPLATE
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.STD.TPL.ENTITY_PASSPORT.300
OWNER: SYSTEM
ROLE: Canonical base template for describing any system entity as a passport (identity, classification, attributes, relations). This is a base contract; KB passport templates may extend it.

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MINOR
- SUMMARY: "Шаблон базового паспорта сущности: UID-first, атрибуты, отношения, статус, источник истины"
- REASON: "Нужен единый каркас сущностей для всех слоёв без дублей"
- IMPACT: "KB passports, standards modules, research/production artifacts"

---

## XREF (UID-first)
XREF: UE.LAW.UID.002 | depends_on | UID is primary entity identity | 01_SYSTEM_LAW/02__UID_RULES.md
XREF: UE.STD.SPEC.DOC_CONTROL.103 | depends_on | doc header + change note format | 02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md
XREF: UE.STD.SPEC.REL_XREF.104 | depends_on | UID-first linking policy | 02_STANDARDS/01_SPECIFICATIONS/04__REL_POLICY_XREF_STANDARD.md
XREF: UE.STD.SPEC.STORAGE_MAP.102 | references | where passports may live by layer rules | 02_STANDARDS/01_SPECIFICATIONS/02__STORAGE_MAP_STANDARD.md

---

# ENTITY PASSPORT — COPY TEMPLATE (INSTANCE)
> Инструкция: скопируй этот блок для новой сущности и заполни.
> Это базовый паспорт. Реалмы/KB могут добавлять расширенные секции, но не ломать базовый контракт.

---

## DOC CONTROL (INSTANCE HEADER)
FILE: <path-to-your-entity-passport.md>
SCOPE: Universe Engine
LAYER: <layer-or-kb-realm>
DOC_TYPE: ARTIFACT
ARTIFACT_TYPE: ENTITY_PASSPORT
LEVEL: L2
STATUS: <DRAFT|ACTIVE>
LOCK: <OPEN|FIXED>
VERSION: 0.1.0
UID: <PASSPORT_DOC_UID>         # UID документа (если канон)
OWNER: <owner/team>
ROLE: Entity Passport instance

CHANGE_NOTE:
- DATE: YYYY-MM-DD
- TYPE: PATCH|MINOR|MAJOR
- SUMMARY: "..."
- REASON: "..."
- IMPACT: "..."

---

## 1) ENTITY IDENTITY (REQUIRED)
ENTITY_UID: <ENTITY_UID>               # главный UID сущности (обязателен)
ENTITY_NAME: "<canonical name>"
ENTITY_TYPE: "<type>"                 # controlled by KB Entity Types (если применимо)
ENTITY_CLASS: "<class or category>"   # optional higher grouping
ENTITY_STATUS: "<draft|active|retired|...>"   # статус сущности (не путать с STATUS документа)

PRIMARY_LAYER: "<where this entity is governed>"
PRIMARY_SOT_UID: <UID or null>         # если есть SoT документ/паспорт — указать

---

## 2) ONE-LINE SUMMARY (REQUIRED)
SUMMARY: "<one-line definition of the entity>"

---

## 3) DESCRIPTION (OPTIONAL)
DESCRIPTION: |
  <paragraphs, background, intent, role in the system/world>

---

## 4) ATTRIBUTES (STRUCTURED)
> Структурированный список свойств. Можно расширять.

ATTRIBUTES:
- KEY: "<key>"
  VALUE: "<value>"
  TYPE: "<string|int|float|bool|enum|ref|list|map>"
  NOTES: "<optional>"

- KEY: "<key>"
  VALUE: "<value>"
  TYPE: "<...>"
  NOTES: "<optional>"

---

## 5) CONSTRAINTS / LIMITS (OPTIONAL)
CONSTRAINTS:
- "<hard limitation>"
- "<soft limitation>"

---

## 6) RELATIONS / XREF (UID-first) (REQUIRED SECTION)
> Связи с другими сущностями/доками. Формат XREF стандартизирован.

XREF:
- XREF: <UID_TARGET> | references | "<why>" | <path(optional)>
- XREF: <UID_TARGET> | depends_on | "<why>" | <path(optional)>
- XREF: <UID_TARGET> | extends | "<why>" | <path(optional)>
- XREF: <UID_TARGET> | maps_to | "<why>" | <path(optional)>

---

## 7) SOURCES / EVIDENCE (OPTIONAL BUT RECOMMENDED)
> Если сущность опирается на исследования/факты/референсы — фиксируй источники.
> (Если источники внешние — можно URL, но внутри системы всё равно UID-first для внутренних объектов.)

SOURCES:
- TYPE: "<internal|external>"
  REF: "<UID or URL>"
  NOTE: "<why relevant>"

---

## 8) CHANGELOG (OPTIONAL)
> Если нужно вести историю внутри паспорта (не обязательно), но header Change Note всегда обязателен для канона.

CHANGELOG:
- DATE: YYYY-MM-DD | NOTE: "<what changed>"

---

## 9) EXTENSIONS (OPTIONAL)
> Здесь перечисляются расширения профиля (например KB профиль), чтобы не плодить разные паспорта.

EXTENSIONS:
- EXT: "<name>"
  XREF:
    - XREF: <UID_TARGET> | references | "<why>" | <path(optional)>

--- END OF TEMPLATE
