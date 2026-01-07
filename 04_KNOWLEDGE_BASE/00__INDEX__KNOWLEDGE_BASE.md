# KNOWLEDGE BASE INDEX — MASTER REGISTRY (CANON)
FILE: 04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: INDEX
INDEX_TYPE: MASTER
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.1.0
UID: UE.KB.IDX.MASTER.001
OWNER: SYSTEM
ROLE: Single canonical entrypoint + existence registry for KB layer

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MINOR
- SUMMARY: "Приведено к фактической структуре папок/файлов (без 404): убраны коллизии, KB_TAGS перенесён в governance"
- REASON: "Индекс обязан совпадать с текущим деревом репо"
- IMPACT: "KB navigation + existence rule"

---

## PURPOSE (LAW)
Этот INDEX — **единственная точка истины** для слоя `04_KNOWLEDGE_BASE`.

### EXISTENCE RULE (ABSOLUTE)
Если файла нет в этом INDEX — он **не существует** для KB слоя.  
Если файл лежит в репо, но не зарегистрирован здесь — **NON-CANON / ignored**.

---

## ORDER OF AUTHORITY (KB)
1) `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/*`
2) `04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md`
3) `04_KNOWLEDGE_BASE/*` (realms/content)

---

## CANON MAP — KB TREE

### 00_KB_GOVERNANCE
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

90 — KB Tags (System)  
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/90__KB_TAGS.md`  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/90__KB_TAGS.md

---

### KB REALMS (01..08)
Folder: `04_KNOWLEDGE_BASE/`

01 — Narrative Craft  
PATH: `04_KNOWLEDGE_BASE/01_NARRATIVE_CRAFT.md`  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/01_NARRATIVE_CRAFT.md

02 — Character Craft  
PATH: `04_KNOWLEDGE_BASE/02_CHARACTER_CRAFT.md`  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/02_CHARACTER_CRAFT.md

03 — Visual Cinema  
PATH: `04_KNOWLEDGE_BASE/03_VISUAL_CINEMA.md`  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/03_VISUAL_CINEMA.md

04 — Sound & Music  
PATH: `04_KNOWLEDGE_BASE/04_SOUND_MUSIC.md`  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/04_SOUND_MUSIC.md

05 — Production Pipeline  
PATH: `04_KNOWLEDGE_BASE/05_PRODUCTION_PIPELINE.md`  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/05_PRODUCTION_PIPELINE.md

06 — Marketing & Distribution  
PATH: `04_KNOWLEDGE_BASE/06_MARKETING_DISTRIBUTION.md`  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/06_MARKETING_DISTRIBUTION.md

07 — Reference Glossary  
PATH: `04_KNOWLEDGE_BASE/07_REFERENCE_GLOSSARY.md`  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/07_REFERENCE_GLOSSARY.md

08 — Research & Fact Checking  
PATH: `04_KNOWLEDGE_BASE/08_RESEARCH_FACT_CHECKING.md`  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/08_RESEARCH_FACT_CHECKING.md

---

## NON-CANON (ALIASES / LEGACY POINTERS)
Эти файлы не являются каноном и должны быть либо удалены, либо содержать только pointer на этот INDEX:

- `04_KNOWLEDGE_BASE/00__README__KB.md`
- `04_KNOWLEDGE_BASE/01__KB_INDEX.md`

---

## RULES (MINIMAL)
- Дубли смысла между realms запрещены без явного XREF/REL.
- System файлы KB (типа TAGS) не должны коллизить по номерам с realms → поэтому `90__*`.

---

## FINAL RULE (LOCK)
Этот INDEX — единственная точка истины о составе и порядке `04_KNOWLEDGE_BASE`.
--- END.
