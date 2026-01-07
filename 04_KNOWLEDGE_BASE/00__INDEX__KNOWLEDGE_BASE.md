# KNOWLEDGE BASE INDEX — MASTER REGISTRY (CANON)
FILE: 04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: INDEX
INDEX_TYPE: MASTER
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.2.0
UID: UE.KB.IDX.MASTER.001
OWNER: SYSTEM
ROLE: Single canonical entrypoint + existence registry for KB layer

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MINOR
- SUMMARY: "Синхронизировано с фактическим деревом: добавлен TOPICS index, учтены governance-файлы 07/91/92, нормализованы имена realms (NN__NAME)"
- REASON: "Index обязан совпадать с репо и правилами нейминга"
- IMPACT: "KB navigation + existence rule"

---

## PURPOSE (LAW)
Этот INDEX — единственная точка истины для слоя `04_KNOWLEDGE_BASE`.

### EXISTENCE RULE (ABSOLUTE)
Если файла нет в этом INDEX — он не существует для KB слоя.  
Если файл лежит в репо, но не зарегистрирован здесь — NON-CANON / ignored.

---

## ORDER OF AUTHORITY (KB)
1) `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/*`
2) `04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE`
3) `04_KNOWLEDGE_BASE/*` (realms/content + topics)

---

## CANON MAP — KB TREE

### 00_KB_GOVERNANCE
Folder: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/`

00 — README: KB Realm  
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/00__README__KB_REALM`  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/00__README__KB_REALM

01 — RULES: KB  
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB`  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB

02 — INDEX: KB Global Registry  
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/02__INDEX__KB_GLOBAL_REGISTRY`  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/02__INDEX__KB_GLOBAL_REGISTRY

03 — INDEX: KB Entity Types  
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/03__INDEX__KB_ENTITY_TYPES`  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/03__INDEX__KB_ENTITY_TYPES

04 — KB Storage Map  
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/04__KB_STORAGE_MAP`  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/04__KB_STORAGE_MAP

05 — TEMPLATE: KB Entity Passport  
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/05__TEMPLATE__KB_ENTITY_PASSPORT`  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/05__TEMPLATE__KB_ENTITY_PASSPORT

06 — KB Create Flow  
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/06__KB_CREATE_FLOW`  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/06__KB_CREATE_FLOW

07 — KB Doc Control (KB-layer rules)  
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/07__KB_DOC_CONTROL`  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/07__KB_DOC_CONTROL

90 — KB Tags (System)  
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/90__KB_TAGS`  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/90__KB_TAGS

91 — KB REL Types (System)  
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/91__KB_REL_TYPES`  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/91__KB_REL_TYPES

92 — KB XREF Rules (System)  
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/92__KB_XREF_RULES`  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/92__KB_XREF_RULES

---

### KB REALMS (01..08)
Folder: `04_KNOWLEDGE_BASE/`

01 — Narrative Craft  
PATH: `04_KNOWLEDGE_BASE/01__NARRATIVE_CRAFT`  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/01__NARRATIVE_CRAFT

02 — Character Craft  
PATH: `04_KNOWLEDGE_BASE/02__CHARACTER_CRAFT`  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/02__CHARACTER_CRAFT

03 — Visual Cinema  
PATH: `04_KNOWLEDGE_BASE/03__VISUAL_CINEMA`  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/03__VISUAL_CINEMA

04 — Sound & Music  
PATH: `04_KNOWLEDGE_BASE/04__SOUND_MUSIC`  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/04__SOUND_MUSIC

05 — Production Pipeline  
PATH: `04_KNOWLEDGE_BASE/05__PRODUCTION_PIPELINE`  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/05__PRODUCTION_PIPELINE

06 — Marketing & Distribution  
PATH: `04_KNOWLEDGE_BASE/06__MARKETING_DISTRIBUTION`  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/06__MARKETING_DISTRIBUTION

07 — Reference Glossary  
PATH: `04_KNOWLEDGE_BASE/07__REFERENCE_GLOSSARY`  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/07__REFERENCE_GLOSSARY

08 — Research & Fact Checking  
PATH: `04_KNOWLEDGE_BASE/08__RESEARCH_FACT_CHECKING`  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/08__RESEARCH_FACT_CHECKING

---

### 10_TOPICS (KB Articles / Topic Packs)
Folder: `04_KNOWLEDGE_BASE/10_TOPICS/`

00 — INDEX: Topics  
PATH: `04_KNOWLEDGE_BASE/10_TOPICS/00__INDEX__TOPICS`  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/10_TOPICS/00__INDEX__TOPICS

---

## NON-CANON (ALIASES / LEGACY POINTERS)
Эти файлы не являются каноном и должны содержать только pointer на этот INDEX:

- `04_KNOWLEDGE_BASE/98__ALIAS__README__KB`
- `04_KNOWLEDGE_BASE/99__ALIAS__KB_INDEX`

---

## RULES (MINIMAL)
- Дубли смысла между realms запрещены без явного XREF/REL.
- System файлы KB живут в `00_KB_GOVERNANCE/90__*` и не коллизят с realms/topics.

---

## FINAL RULE (LOCK)
Этот INDEX — единственная точка истины о составе и порядке `04_KNOWLEDGE_BASE`.
--- END.
