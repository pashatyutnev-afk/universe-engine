# KNOWLEDGE BASE INDEX — MASTER REGISTRY (CANON)
FILE: 04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: INDEX
INDEX_TYPE: MASTER
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 3.0.1
UID: UE.KB.IDX.MASTER.001
OWNER: SYSTEM
ROLE: Single canonical entrypoint + existence registry for Knowledge Base layer

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: PATCH
- SUMMARY: "10_TOPICS README закреплён как 99__README__TOPICS_REALM.md; master-index синхронизирован с topics sub-index."
- REASON: "Убрать несоответствия/поиск несуществующих файлов."
- IMPACT: "KB navigation + existence rule enforcement."

---

## PURPOSE (LAW)
Этот INDEX — единственная точка истины для слоя `04_KNOWLEDGE_BASE`.

### EXISTENCE RULE (ABSOLUTE)
- Канон существует только по спискам в этом файле (CANON MAP).
- Subtree `10_TOPICS` делегирован: existence topics определяется файлом
  `04_KNOWLEDGE_BASE/10_TOPICS/00__INDEX__TOPICS.md`.
- Файл в репо без регистрации в соответствующем index = NON-CANON / ignored.

---

## ORDER OF AUTHORITY (KB)
1) `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/*`
2) `04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md`
3) `04_KNOWLEDGE_BASE/*` (realms) + `04_KNOWLEDGE_BASE/10_TOPICS/*` (topics)

---

## CANON MAP — KB TREE

### 00_KB_GOVERNANCE (KB governance SoT)
Folder: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/`

00 — README: KB Realm
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/00__README__KB_REALM.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/00__README__KB_REALM.md

01 — RULES: KB
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB.md

02 — INDEX: KB Global Registry
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/02__INDEX__KB_GLOBAL_REGISTRY.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/02__INDEX__KB_GLOBAL_REGISTRY.md

03 — INDEX: KB Entity Types
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/03__INDEX__KB_ENTITY_TYPES.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/03__INDEX__KB_ENTITY_TYPES.md

04 — KB Storage Map
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/04__KB_STORAGE_MAP.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/04__KB_STORAGE_MAP.md

05 — TEMPLATE: KB Entity Passport
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/05__TEMPLATE__KB_ENTITY_PASSPORT.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/05__TEMPLATE__KB_ENTITY_PASSPORT.md

06 — KB Create Flow
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/06__KB_CREATE_FLOW.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/06__KB_CREATE_FLOW.md

07 — KB Doc Control
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/07__KB_DOC_CONTROL.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/07__KB_DOC_CONTROL.md

90 — KB Tags (System)
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/90__KB_TAGS.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/90__KB_TAGS.md

91 — KB REL Types (System)
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/91__KB_REL_TYPES.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/91__KB_REL_TYPES.md

92 — KB XREF Rules (System)
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/92__KB_XREF_RULES.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/92__KB_XREF_RULES.md

---

### 10_TOPICS (delegated subtree)
Folder: `04_KNOWLEDGE_BASE/10_TOPICS/`

00 — INDEX: Topics (SoT for topics existence)
PATH: `04_KNOWLEDGE_BASE/10_TOPICS/00__INDEX__TOPICS.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/10_TOPICS/00__INDEX__TOPICS.md

99 — README: Topics Realm
PATH: `04_KNOWLEDGE_BASE/10_TOPICS/99__README__TOPICS_REALM.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/10_TOPICS/99__README__TOPICS_REALM.md

NOTE:
Все topic-файлы (01..98) регистрируются внутри `00__INDEX__TOPICS.md` и не перечисляются здесь.

---

### KB REALMS (01..08)
Folder: `04_KNOWLEDGE_BASE/`

01 — Narrative Craft
PATH: `04_KNOWLEDGE_BASE/01__NARRATIVE_CRAFT.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/01__NARRATIVE_CRAFT.md

02 — Character Craft
PATH: `04_KNOWLEDGE_BASE/02__CHARACTER_CRAFT.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/02__CHARACTER_CRAFT.md

03 — Visual Cinema
PATH: `04_KNOWLEDGE_BASE/03__VISUAL_CINEMA.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/03__VISUAL_CINEMA.md

04 — Sound & Music
PATH: `04_KNOWLEDGE_BASE/04__SOUND_MUSIC.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/04__SOUND_MUSIC.md

05 — Production Pipeline
PATH: `04_KNOWLEDGE_BASE/05__PRODUCTION_PIPELINE.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/05__PRODUCTION_PIPELINE.md

06 — Marketing & Distribution
PATH: `04_KNOWLEDGE_BASE/06__MARKETING_DISTRIBUTION.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/06__MARKETING_DISTRIBUTION.md

07 — Reference Glossary
PATH: `04_KNOWLEDGE_BASE/07__REFERENCE_GLOSSARY.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/07__REFERENCE_GLOSSARY.md

08 — Research & Fact Checking
PATH: `04_KNOWLEDGE_BASE/08__RESEARCH_FACT_CHECKING.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/08__RESEARCH_FACT_CHECKING.md

---

## NON-CANON (ALIASES / LEGACY POINTERS)
Эти файлы не являются каноном. Их содержимое — только pointer на этот INDEX:

- `04_KNOWLEDGE_BASE/98__ALIAS__README__KB.md`
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/98__ALIAS__README__KB.md
- `04_KNOWLEDGE_BASE/99__ALIAS__KB_INDEX.md`
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/99__ALIAS__KB_INDEX.md

--- END.
