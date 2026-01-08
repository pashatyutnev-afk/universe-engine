# TEMPLATE — KB ENTITY PASSPORT (CANON)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/05__TEMPLATE__KB_ENTITY_PASSPORT.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TEMPLATE
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.TPL.ENTITY_PASSPORT.001
OWNER: SYSTEM
ROLE: Шаблон паспорта сущности KB (без ссылок, только UID/XREF)

---

## TEMPLATE (COPY FROM HERE)

# KB ENTITY PASSPORT
FILE: <fill>
SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: PASSPORT
LEVEL: L3
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: <fill unique UID>
OWNER: <fill>
ROLE: Entity passport for KB object

---

## IDENTITY
- NAME: <human-readable name>
- ENTITY_TYPE: <TOPIC | REALM | RULE | DICTIONARY | TEMPLATE | PROCESS | CONTROL>
- STATUS: <DRAFT | ACTIVE | DEPRECATED | ARCHIVED>

## SUMMARY
<what it is, why it exists, what problem it solves>

## SCOPE & BOUNDARIES
- IN-SCOPE: <what is included>
- OUT-OF-SCOPE: <what is excluded>

## KEY RULES (IF ANY)
- <rule 1>
- <rule 2>

## ATTRIBUTES (OPTIONAL)
- <key>: <value>
- <key>: <value>

## RELATIONS (UID-ONLY)
Use REL types dictionary (by meaning, no links). Format:
- REL: <REL_TYPE> | TARGET: <UID> | WHY: <reason>

Example:
- REL: DEFINES | TARGET: UE.KB.DICT.TAGS.001 | WHY: establishes tag vocabulary

## XREF (UID-ONLY)
Format:
- XREF: <UID> | WHY: <reason>

## CHANGELOG
- DATE: <YYYY-MM-DD>
  TYPE: <MAJOR|MINOR|PATCH>
  SUMMARY: <what changed>
  IMPACT: <what it affects>

--- END TEMPLATE.
