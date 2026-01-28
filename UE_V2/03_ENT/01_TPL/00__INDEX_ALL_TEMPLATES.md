# TPL TEMPLATES INDEX — GLOBAL REGISTRY (CANON)
FILE: 03_SYSTEM_ENTITIES/01_TPL__TEMPLATES/00__INDEX_ALL_TEMPLATES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: TEMPLATES (TPL)
DOC_TYPE: INDEX
INDEX_TYPE: GLOBAL_TEMPLATE_REGISTRY
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.TPL.IDX.ALL.001
OWNER: SYSTEM
ROLE: Canonical navigation law + existence registry for `01_TPL__TEMPLATES` (RAW-ONLY NAV)

CHANGE_NOTE:
- DATE: 2026-01-11
- TYPE: MAJOR
- SUMMARY: "Created TPL master index with RAW-only navigation and strict existence + alias enforcement."
- REASON: "Need deterministic navigation for template layer; prevent duplicate entrypoints."
- IMPACT: "Templates become discoverable and audit-compatible."
- CHANGE_ID: UE.CHG.2026-01-11.TPL.IDX.ALL.001

---

## 0) PURPOSE (LAW)
This INDEX is the single source of truth for NAV/EXISTENCE of:
`03_SYSTEM_ENTITIES/01_TPL__TEMPLATES/`

It fixes:
- what template files exist
- strict order (by numbering)
- RAW-only navigation (PATH is label only)

---

## 1) EXISTENCE RULE (ABSOLUTE)
- If a template is not registered in CANON MAP below — it does not exist for TPL layer.
- If a file exists in repo but not listed here — NON-CANON / ignored.
- NAV works only via RAW links.

---

## 2) BASE PATH
PATH: `03_SYSTEM_ENTITIES/01_TPL__TEMPLATES/`

---

## 3) HOW TO USE (OPERATIONAL)
1) Open this index.
2) Copy needed `RAW:` and paste into address bar.
3) Use templates as base when creating new entities (ENG/ORC/SPC/CTL/VAL/QA).

---

## 4) CANON MAP — 01_TPL__TEMPLATES (RAW-ONLY)

00 — INDEX: ALL TEMPLATES (THIS FILE)
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/01_TPL__TEMPLATES/00__INDEX_ALL_TEMPLATES.md

00 — README: TEMPLATES
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/01_TPL__TEMPLATES/00__README_TEMPLATES.md

00 — TEMPLATE SYSTEM STANDARD
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/01_TPL__TEMPLATES/00__TEMPLATE_SYSTEM_STANDARD.md

10 — TPL: ENGINE
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/01_TPL__TEMPLATES/10__TPL__ENGINE.md

20 — TPL: ORCHESTRATOR
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/01_TPL__TEMPLATES/20__TPL__ORCHESTRATOR.md

30 — TPL: SPECIALIST
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/01_TPL__TEMPLATES/30__TPL__SPECIALIST.md

40 — TPL: CONTROLLER
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/01_TPL__TEMPLATES/40__TPL__CONTROLLER.md

50 — TPL: VALIDATOR
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/01_TPL__TEMPLATES/50__TPL__VALIDATOR.md

60 — TPL: QA
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/01_TPL__TEMPLATES/60__TPL__QA.md

90 — TPL: INDEX TEMPLATE
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/01_TPL__TEMPLATES/90__TPL__INDEX.md

91 — TPL: README REALM TEMPLATE
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/01_TPL__TEMPLATES/91__TPL__README_REALM.md

---

## 5) ALIAS RULE (STRICT)
Any duplicate/alternate entrypoint file in this folder
(e.g. different naming of the index/README/template standard)
must be either:
- deleted, OR
- converted into a PURE POINTER to the canonical file.

Canonical entrypoint for this folder:
- `03_SYSTEM_ENTITIES/01_TPL__TEMPLATES/00__INDEX_ALL_TEMPLATES.md`

---

## FINAL RULE (LOCK)
This INDEX is the only SoT for existence and navigation of `01_TPL__TEMPLATES`.
Any change must be logged via governance/audit rules.

OWNER: SYSTEM
LOCK: FIXED

--- END.
