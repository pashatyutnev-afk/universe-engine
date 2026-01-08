# KB REALM — README (CANON)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/00__README__KB_REALM.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: README
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.1
UID: UE.KB.README.REALM.001
OWNER: SYSTEM
ROLE: Описание KB и правила входа (без промежуточной навигации)

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: PATCH
- SUMMARY: "Removed path-based navigation. README now uses UID/file-name only. No extra header fields."
- REASON: "Совместимость с законом KB: навигация только в master-index."
- IMPACT: "README больше не создаёт промежуточные входы/переходы."

---

## PURPOSE
Knowledge Base (KB) — слой знаний, правил и практик Universe Engine.

---

## SINGLE ENTRYPOINT (ABSOLUTE)
Единственная точка входа и навигации по KB:
- FILE: `00__INDEX__KNOWLEDGE_BASE.md`
- UID: UE.KB.IDX.MASTER.001

Любые пути/RAW/URL и “куда идти” — только в этом master-index.

---

## WHAT LIVES IN KB
- Governance: правила, словари, шаблоны, контроль документов
- Realms: крупные области знаний
- Topics: конкретные прикладные темы/практики
- Aliases: legacy pointers (без контента)

---

## HARD BANS (REMINDER)
Запрещено:
- создавать sub-indexes (локальные реестры/оглавления)
- вставлять PATH/RAW/URL в любые KB документы кроме master-index
- делать цепочки навигации документ → документ → документ

Разрешено:
- XREF и REL строго по UID:
  - `XREF: <UID> | WHY: <reason>`
  - `REL: <TYPE> | TARGET: <UID> | WHY: <reason>`

--- END.
