# REG REGISTRIES INDEX — GLOBAL (CANON)

FILE: 03_SYSTEM_ENTITIES/00_REG__REGISTRIES/00__INDEX_ALL_REGISTRIES.md  
SCOPE: Universe Engine  
LAYER: 03_SYSTEM_ENTITIES  
ENTITY_GROUP: REGISTRIES (REG)  
DOC_TYPE: INDEX  
INDEX_TYPE: REGISTRY_FOLDER_INDEX  
LEVEL: L2  
STATUS: ACTIVE  
LOCK: FIXED  
VERSION: 1.0.0  
UID: UE.REG.IDX.ALL.001  
OWNER: SYSTEM  
ROLE: Canonical navigation + existence registry for `00_REG__REGISTRIES` (RAW-ONLY NAV)

CHANGE_NOTE:
- DATE: 2026-01-11
- TYPE: MAJOR
- SUMMARY: Built REG registries folder index: RAW-only canon map + strict existence/alias rules.
- REASON: Need deterministic navigation and existence enforcement for registries.
- IMPACT: Registries folder becomes canon-locked and audit-friendly.
- CHANGE_ID: UE.CHG.2026-01-11.REG.IDX.ALL.001

---

## 0) PURPOSE (LAW)
This INDEX is the single source of truth for NAV/EXISTENCE of folder:
`03_SYSTEM_ENTITIES/00_REG__REGISTRIES/`

It defines:
- which registry files exist in this folder
- RAW-only canonical navigation
- alias + no-extra-files enforcement

---

## 1) EXISTENCE RULE (ABSOLUTE)
- If a file is not registered in CANON MAP below — it does not exist for REG registries.
- If a file exists in repo but is not registered here — NON-CANON / ignored.
- NAV works only via RAW links (PATH is a label only).

---

## 2) NO-EXTRA-FILES RULE (ABSOLUTE)
No additional files are allowed in this folder beyond this canon map.

Any extra file found must be:
- removed, OR
- converted into a pure POINTER to an existing canonical file (no extra rules inside).

---

## 3) ALIAS RULE (STRICT)
Any duplicate entrypoint/index/readme/template variants must be:
- removed, OR
- converted into a pure POINTER to this canonical target file:
  `03_SYSTEM_ENTITIES/00_REG__REGISTRIES/00__INDEX_ALL_REGISTRIES.md`

---

## 4) BASE PATH
PATH: `03_SYSTEM_ENTITIES/00_REG__REGISTRIES/`

---

# CANON MAP — 00_REG__REGISTRIES (RAW-ONLY NAV)

- 00 — README: REGISTRIES REALM  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/00_REG__REGISTRIES/00__README__REGISTRIES.md

- 00 — INDEX: ALL REGISTRIES (THIS FILE)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/00_REG__REGISTRIES/00__INDEX_ALL_REGISTRIES.md

- 00 — TEMPLATE: REGISTRY  
  # ВЫБЕРИ ОДИН ВАРИАНТ (ПО ИМЕНИ ФАЙЛА У ТЕБЯ) И УДАЛИ ДРУГОЙ:
  # A) если файл называется: 00__TEMPLATE__REGISTRY.md  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/00_REG__REGISTRIES/00__TEMPLATE__REGISTRY.md  
  # B) если файл называется: 00__TEMPLATE_REGISTRY.md  
  # RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/00_REG__REGISTRIES/00__TEMPLATE_REGISTRY.md

- 01 — REGISTRY: ENTITY IDS  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/00_REG__REGISTRIES/01__REG_ENTITY_IDS.md

- 02 — REGISTRY: NAMING RULES  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/00_REG__REGISTRIES/02__REG_NAMING_RULES.md

- 03 — REGISTRY: PATH MAP  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/00_REG__REGISTRIES/03__REG_PATH_MAP.md

- 90 — REGISTRY: CHANGELOG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/00_REG__REGISTRIES/90__REG_CHANGELOG.md

- 91 — REGISTRY: DEPRECATION  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/00_REG__REGISTRIES/91__REG_DEPRECATION.md

---

## FINAL RULE (LOCK)
This INDEX is the only SoT for REG registries folder existence and navigation.

Any change must be logged in `90__REG_CHANGELOG.md`.

OWNER: SYSTEM  
LOCK: FIXED

--- END.
