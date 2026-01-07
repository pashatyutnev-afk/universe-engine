# KB STORAGE MAP (GOVERNANCE)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/04__KB_STORAGE_MAP.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_SYSTEM
SYSTEM_OBJ: STORAGE_MAP
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.KB.SYS.STORAGE_MAP.001
OWNER: SYSTEM
ROLE: Physical storage map for KB: where artifacts live, what is allowed, what is forbidden

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MINOR
- SUMMARY: "Синхронизировано с KB DOC CONTROL: system dictionaries 90..99 внутри governance; добавлен 10_TOPICS как делегированный subtree."
- REASON: "Убрать конфликт правил и дрейф структуры."
- IMPACT: "Storage rules + navigation correctness."

---

## ROOT ZONES (CANON)
1) Entry point (only one)
- `04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md`

2) Governance (laws / maps / templates / system dictionaries)
- `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/NN__*.md`
- System dictionaries live here:
  - `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/90__*..99__*.md`

3) Realms (core knowledge realms)
- `04_KNOWLEDGE_BASE/01__*..08__*.md`

4) Topics (delegated subtree)
- `04_KNOWLEDGE_BASE/10_TOPICS/`
- Existence SoT:
  - `04_KNOWLEDGE_BASE/10_TOPICS/00__INDEX__TOPICS.md`

5) Aliases (non-canon pointers only)
- `04_KNOWLEDGE_BASE/98__*.md`
- `04_KNOWLEDGE_BASE/99__*.md`

---

## PROHIBITED (HARD)
- Любые “system dictionaries” в корне `04_KNOWLEDGE_BASE/90__*.md` (они должны быть в governance).
- Любые дополнительные entrypoints кроме `00__INDEX__KNOWLEDGE_BASE.md`.
- Любой контент внутри alias-файлов (только pointer на master-index).

--- END.
