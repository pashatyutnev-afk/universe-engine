FILE: UE_V2/03_ENT/50_VAL_ENT/00_TEMPLATES_VAL_ENT/03__TPL__INDEX_MANIFEST__VAL__ENT.md
SCOPE: UE_V2 / 03_ENT / 50_VAL_ENT / 00_TEMPLATES_VAL_ENT
DOC_TYPE: TPL
DOMAIN: TPL_VAL_ENT
UID: UE.V2.ENT.TPL.INDEX_MANIFEST_VAL.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: VAL_ENT
NAV_RULE: Template doc contains no RAW

---

## [M] TEMPLATE_NAME
INDEX_MANIFEST_VAL_TEMPLATE

## [M] PURPOSE
Шаблон INDEX_MANIFEST для VAL реалмов.
RAW ссылки допускаются только в самом INDEX_MANIFEST файле.

---

# [T] FILE HEADER (copy and fill)
FILE: <PATH_TO_TARGET_INDEX_MANIFEST>
SCOPE: <SCOPE>
DOC_TYPE: INDEX_MANIFEST
DOMAIN: <MUS_VAL_ENT|VID_VAL_ENT|WEB_VAL_ENT|DOC_VAL_ENT|VAL_ENG_VAL_ENT|LIB_VAL_ENT|...>
UID: <UID>
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 0000-00-00
UPDATED: 0000-00-00
OWNER: VAL_ENT
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — адресная таблица реалма.
Хранит RAW и короткие смыслы. Без длинных объяснений.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Каждый элемент имеет KEY. PIPELINE_CONTRACT ссылается только на KEY.
- SELF запись обязательна.

## [M] ENTRY_SCHEMA (v1)
(используй ENTRY_SCHEMA из индекс-манифеста шаблонов)

## [M] REQUIRED DEFAULT KEYS
- SELF
- INDEX_MANIFEST
- PIPELINE_CONTRACT
- README (recommended)
- DOD (recommended)

## [M] CONTENT KEYS (pattern)
- VAL.<DOMAIN>.<NAME>
- VAL_ENG.<NAME> (если это валидирующие engines внутри VAL)
