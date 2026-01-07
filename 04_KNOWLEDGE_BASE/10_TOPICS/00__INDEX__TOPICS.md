# TOPICS INDEX — MASTER REGISTRY (CANON)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/00__INDEX__TOPICS.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
SUBTREE: 10_TOPICS
DOC_TYPE: INDEX
INDEX_TYPE: SUBTREE_MASTER
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.TOPICS.IDX.MASTER.001
OWNER: SYSTEM
ROLE: Single canonical entrypoint + existence registry for Topics subtree

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Topics index rebuilt to match current folder content (00 README + 01..03 topics)."
- REASON: "Master KB index delegates existence for 10_TOPICS to this file."
- IMPACT: "Topics navigation + existence correctness"

---

## PURPOSE (LAW)
Этот INDEX — единственная точка истины для subtree `04_KNOWLEDGE_BASE/10_TOPICS/`.

### EXISTENCE RULE (ABSOLUTE)
- Topic существует только если он перечислен в разделе **CANON MAP** этого файла.
- Любой файл в `10_TOPICS/`, которого нет в этом INDEX = **NON-CANON / ignored**.

---

## ORDER OF AUTHORITY (TOPICS)
1) `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/*`
2) `04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md`
3) `04_KNOWLEDGE_BASE/10_TOPICS/00__INDEX__TOPICS.md`
4) `04_KNOWLEDGE_BASE/10_TOPICS/*` (topic docs)

---

## NAMING RULES (HARD)
- Только формат: `NN__DOMAIN__TOPIC_NAME.md`
- `00__*` зарезервирован под index/README внутри `10_TOPICS/`
- `01..89` — обычные топики
- `90..99` — системные/служебные топики (если появятся)

---

## CANON MAP — 10_TOPICS TREE
Folder: `04_KNOWLEDGE_BASE/10_TOPICS/`

00 — INDEX: Topics (SoT for topics existence)  
PATH: `04_KNOWLEDGE_BASE/10_TOPICS/00__INDEX__TOPICS.md`  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/10_TOPICS/00__INDEX__TOPICS.md

00 — README: Topics Realm  
PATH: `04_KNOWLEDGE_BASE/10_TOPICS/00__README__TOPICS_REALM.md`  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/10_TOPICS/00__README__TOPICS_REALM.md

01 — Narrative: Scene Craft  
PATH: `04_KNOWLEDGE_BASE/10_TOPICS/01__NARRATIVE__SCENE_CRAFT.md`  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/10_TOPICS/01__NARRATIVE__SCENE_CRAFT.md

02 — Character: Motivation  
PATH: `04_KNOWLEDGE_BASE/10_TOPICS/02__CHARACTER__MOTIVATION.md`  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/10_TOPICS/02__CHARACTER__MOTIVATION.md

03 — Visual: Lighting  
PATH: `04_KNOWLEDGE_BASE/10_TOPICS/03__VISUAL__LIGHTING.md`  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/10_TOPICS/03__VISUAL__LIGHTING.md

---

## CREATE FLOW (MINIMAL)
1) Создаёшь новый topic-файл `NN__DOMAIN__NAME.md`
2) Добавляешь его сюда в **CANON MAP**
3) Только после этого topic считается существующим (canonical)

--- END.
