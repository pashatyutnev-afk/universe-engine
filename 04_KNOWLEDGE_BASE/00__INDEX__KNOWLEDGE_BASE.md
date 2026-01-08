# KNOWLEDGE BASE INDEX — MASTER REGISTRY (CANON)
FILE: 04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: INDEX
INDEX_TYPE: MASTER
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 4.0.1
UID: UE.KB.IDX.MASTER.001
OWNER: SYSTEM
ROLE: Single canonical entrypoint + existence registry + navigation map for Knowledge Base layer

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: PATCH
- SUMMARY: "Clarified index ban: sub-indexes as NAV/EXISTENCE are forbidden; governance INDEX documents allowed as dictionaries/catalogs. Renamed governance section label (no 'SoT')."
- REASON: "Убрать логическую коллизию: запрет INDEX* vs существующие governance dictionaries."
- IMPACT: "KB law is self-consistent; validators won't flag governance dictionaries."

---

## PURPOSE (LAW)
Этот INDEX — единственная точка истины для Knowledge Base.

---

## ONE-ROOT / ONE-NAV (ABSOLUTE)
1) Единственный канонический ROOT KB: `04_KNOWLEDGE_BASE/` (подпапки допустимы).
2) Единственный канонический NAV+EXISTENCE индекс KB: `04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md`.
3) Запрещены любые sub-indexes как NAV/EXISTENCE реестры (любого уровня, в любых подпапках).
   - Запрещено: любые локальные оглавления/реестры существования (topics-index, realm-index, entities-index и т.п.).
   - Примеры запрещённого: `*/00__INDEX__*.md`, `*/_index.md`, `*/00_INDEX*.md`.
   - Разрешено: governance-словари/каталоги в `00_KB_GOVERNANCE/` (включая файлы с `INDEX` в имени),
     но они НЕ имеют authority по existence/nav.
4) Делегирование subtree запрещено (никаких “existence определяется другим индексом”).
5) Ссылки внутри любых документов НЕ создают существование и НЕ расширяют канон.

ENFORCEMENT:
- Любой sub-index (NAV/EXISTENCE) должен быть удалён.
- Любой файл, не перечисленный в CANON MAP ниже — NON-CANON / ignored.

---

## EXISTENCE RULE (ABSOLUTE)
- Канон существует только по спискам в этом файле (CANON MAP).
- Любой файл в репо, не перечисленный здесь, считается NON-CANON / ignored.

---

## ORDER OF AUTHORITY (KB)
1) `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/*`  (контент-правила)
2) `04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md` (существование + навигация)
3) `04_KNOWLEDGE_BASE/*` (контент KB)

NOTE:
Authority в (1) и (3) относится к содержанию/нормам.
EXISTENCE и NAV определяются только этим INDEX.

---

## CANON MAP — KB TREE

### 00_KB_GOVERNANCE (rules / dictionaries / control)
Folder: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/`

00 — README: KB Realm
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/00__README__KB_REALM.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/00__README__KB_REALM.md

01 — RULES: KB
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB.md

02 — INDEX: KB Global Registry (dictionary)
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/02__INDEX__KB_GLOBAL_REGISTRY.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/02__INDEX__KB_GLOBAL_REGISTRY.md

03 — INDEX: KB Entity Types (dictionary)
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

### TOPICS (registered directly in GLOBAL INDEX)
Folder: `04_KNOWLEDGE_BASE/10_TOPICS/`

00 — README: Topics Realm
PATH: `04_KNOWLEDGE_BASE/10_TOPICS/00__README__TOPICS_REALM.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/10_TOPICS/00__README__TOPICS_REALM.md

01 — Topic: Narrative — Scene Craft
PATH: `04_KNOWLEDGE_BASE/10_TOPICS/01__NARRATIVE__SCENE_CRAFT.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/10_TOPICS/01__NARRATIVE__SCENE_CRAFT.md

02 — Topic: Character — Motivation
PATH: `04_KNOWLEDGE_BASE/10_TOPICS/02__CHARACTER__MOTIVATION.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/10_TOPICS/02__CHARACTER__MOTIVATION.md

03 — Topic: Visual — Lighting
PATH: `04_KNOWLEDGE_BASE/10_TOPICS/03__VISUAL__LIGHTING.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/10_TOPICS/03__VISUAL__LIGHTING.md

NOTE:
Любой topic-файл, не перечисленный здесь, считается NON-CANON / ignored.

---

## NON-CANON (ALIASES / LEGACY POINTERS)
Эти файлы не являются каноном. Их содержимое — только pointer на этот INDEX:

- `04_KNOWLEDGE_BASE/98__ALIAS__README__KB.md`
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/98__ALIAS__README__KB.md
- `04_KNOWLEDGE_BASE/99__ALIAS__KB_INDEX.md`
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/99__ALIAS__KB_INDEX.md

--- END.
