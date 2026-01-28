## AI NAV HANDSHAKE (MANDATORY — READ FIRST)
This file is the ONLY operational navigation source for entity files in `03_SYSTEM_ENTITIES/00_REG__REGISTRIES`.

### RULE 1 — NO GUESSING LINKS (ABSOLUTE)
- The assistant MUST NOT invent/guess RAW URLs.
- The assistant MUST use ONLY RAW links explicitly present in:
  A) this file (if opened), OR
  B) the user’s message (if the user pasted a subset).

### RULE 2 — USER MESSAGE SUBSET MODE (ABSOLUTE)
If the user pasted part of this index into the chat:
- treat that pasted subset as the ONLY allowed link library for this session;
- do NOT assume other files exist beyond pasted RAW lines.

### RULE 3 — VERIFY BEFORE CLAIM (MANDATORY)
Before saying “file is empty / filled / needs rewrite” the assistant MUST:
- quote the exact RAW URL being checked (one line),
- and confirm a recognizable marker (e.g., first header line).

### RULE 4 — IF LINK MISSING (STOP CONDITION)
If a required file link is not present in the pasted library:
- the assistant must ask for the RAW link (one line),
- and must NOT proceed by constructing a URL.

---

# REG REGISTRIES INDEX — GLOBAL REGISTRY (CANON ROADMAP)
CANON FILE: 03_SYSTEM_ENTITIES/00_REG__REGISTRIES/00__INDEX_ALL_REGISTRIES.md

SCOPE: Universe Engine  
LAYER: 03_SYSTEM_ENTITIES  
ENTITY_GROUP: REGISTRIES (REG)  
DOC_TYPE: INDEX  
INDEX_TYPE: GLOBAL_REGISTRY_INDEX  
LEVEL: L1  
STATUS: ACTIVE  
LOCK: FIXED  
VERSION: 1.0.1  
UID: UE.REG.IDX.ALL.001  
OWNER: SYSTEM  
ROLE: Canonical navigation law + existence registry for all REG registries (RAW-ONLY NAV)

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: PATCH
- SUMMARY: "Fixed broken RAW filenames (added __ + .md), added AI NAV HANDSHAKE, aligned ROOT FILES + authority order with global one-file index."
- REASON: "Operational navigation must be deterministic; broken links break the system."
- IMPACT: "REG layer navigation becomes stable in one-file mode."
- CHANGE_ID: UE.CHG.2026-01-12.REG.IDX.ALL.002

---

## NAV MODE (IMPORTANT)
- Открываешь ТОЛЬКО этот файл (или берёшь RAW из сообщения пользователя, если он вставил subset).
- Дальше копируешь нужный `RAW:` и вставляешь в адресную строку.
- PATH — это метка/ориентир. NAV = только RAW.

---

## 0) PURPOSE (LAW)
Этот INDEX — единая точка истины для NAV/EXISTENCE папки:
`03_SYSTEM_ENTITIES/00_REG__REGISTRIES/`

Он фиксирует:
- какие REG-реестры существуют
- строгий порядок реестров (authority order)
- RAW-only навигацию
- анти-дубли entrypoint/индексов (alias rule)

---

## 1) EXISTENCE RULE (ABSOLUTE)
- Если файла нет в CANON MAP ниже — он **не существует** для слоя REG.
- Если файл есть в репо, но не зарегистрирован здесь — **NON-CANON / ignored**.
- NAV работает **только по RAW ссылкам**.

---

## 2) BASE PATH
PATH: `03_SYSTEM_ENTITIES/00_REG__REGISTRIES/`

---

## 3) ORDER OF AUTHORITY (REG)
1) `00__README__REGISTRIES.md` (Realm / смысл / рамки)
2) `00__INDEX_ALL_REGISTRIES.md` (NAV/EXISTENCE SoT — THIS FILE)
3) `02__REG_NAMING_RULES.md` (правила именования)
4) `01__REG_ENTITY_IDS.md` (ID/UID namespaces)
5) `03__REG_PATH_MAP.md` (карта путей)
6) `00__TEMPLATE__REGISTRY.md` (шаблон реестра)
7) `90__REG_CHANGELOG.md` (история изменений)
8) `91__REG_DEPRECATION.md` (вывод из канона / deprecations)

---

## 4) ROOT FILES (REG LAYER) — RAW ONLY
00 — README: REGISTRIES Realm  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/00_REG__REGISTRIES/00__README__REGISTRIES.md

01 — INDEX: ALL REGISTRIES (THIS FILE)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/00_REG__REGISTRIES/00__INDEX_ALL_REGISTRIES.md

02 — TEMPLATE: REGISTRY  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/00_REG__REGISTRIES/00__TEMPLATE__REGISTRY.md

03 — REGISTRY: ENTITY IDS (UID namespaces)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/00_REG__REGISTRIES/01__REG_ENTITY_IDS.md

04 — REGISTRY: NAMING RULES  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/00_REG__REGISTRIES/02__REG_NAMING_RULES.md

05 — REGISTRY: PATH MAP  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/00_REG__REGISTRIES/03__REG_PATH_MAP.md

90 — REG CHANGELOG  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/00_REG__REGISTRIES/90__REG_CHANGELOG.md

91 — REG DEPRECATION  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/00_REG__REGISTRIES/91__REG_DEPRECATION.md

---

## 5) HOW TO USE (ROADMAP)
1) Открываешь `00__README__REGISTRIES.md` — рамки слоя REG.
2) По этому INDEX выбираешь нужный реестр (IDs / Naming / Path Map).
3) Любые изменения:
   - обязаны сохранять RAW-only навигацию,
   - обязаны фиксироваться в `90__REG_CHANGELOG.md`,
   - не должны создавать дублей entrypoint/индексов.
4) Добавление нового REG-файла:
   - сначала регистрируется тут (CANON MAP),
   - затем создаётся файл,
   - затем фиксируется изменение в `90__REG_CHANGELOG.md`.

---

# CANON MAP — 00_REG__REGISTRIES (RAW-ONLY NAV)

00 — README: REGISTRIES Realm  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/00_REG__REGISTRIES/00__README__REGISTRIES.md

01 — INDEX: ALL REGISTRIES  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/00_REG__REGISTRIES/00__INDEX_ALL_REGISTRIES.md

02 — TEMPLATE: REGISTRY  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/00_REG__REGISTRIES/00__TEMPLATE__REGISTRY.md

03 — REGISTRY: ENTITY IDS / UID NAMESPACES  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/00_REG__REGISTRIES/01__REG_ENTITY_IDS.md

04 — REGISTRY: NAMING RULES  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/00_REG__REGISTRIES/02__REG_NAMING_RULES.md

05 — REGISTRY: PATH MAP  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/00_REG__REGISTRIES/03__REG_PATH_MAP.md

90 — REG CHANGELOG  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/00_REG__REGISTRIES/90__REG_CHANGELOG.md

91 — REG DEPRECATION  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/00_REG__REGISTRIES/91__REG_DEPRECATION.md

---

## 6) ALIAS RULE (STRICT)
Любые дубли entrypoint/индексов в этой папке (например `INDEX*`, `*REGISTRIES_INDEX*`) кроме CANON FILE выше
должны быть либо удалены, либо превращены в чистый POINTER на:
`03_SYSTEM_ENTITIES/00_REG__REGISTRIES/00__INDEX_ALL_REGISTRIES.md`

---

## FINAL RULE (LOCK)
Этот INDEX — единственная точка истины о составе и порядке REG-реестров.  
Любая правка структуры/ссылок обязана фиксироваться в `90__REG_CHANGELOG.md`.

OWNER: SYSTEM  
LOCK: FIXED

--- END.
