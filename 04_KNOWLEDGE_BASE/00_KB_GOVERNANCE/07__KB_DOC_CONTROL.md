# KB DOC CONTROL (GOVERNANCE)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/07__KB_DOC_CONTROL

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_SYSTEM
SYSTEM_OBJ: DOC_CONTROL
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.SYS.DOC_CONTROL.001
OWNER: SYSTEM
ROLE: KB-layer doc control: required header fields, allowed values, naming ranges, and alias policy

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Зафиксирован Doc Control KB: обязательная шапка, SemVer, status/lock, naming ranges, alias policy"
- REASON: "Без Doc Control KB невалидируем и расползается"
- IMPACT: "Все KB файлы: governance/realms/topics/aliases"

---

## REQUIRED HEADER (MANDATORY)
Каждый канонический KB-файл обязан иметь шапку (в начале файла):

SCOPE / LAYER / DOC_TYPE / LEVEL / STATUS / LOCK / VERSION / UID / OWNER / ROLE

Допускается добавлять поля типа `INDEX_TYPE`, `REALM`, `SYSTEM_OBJ`, если это уместно.

---

## ALLOWED VALUES (STRICT)
STATUS: DRAFT | ACTIVE | DEPRECATED | ARCHIVED  
LOCK: OPEN | FIXED  
VERSION: X.Y.Z (SemVer)

---

## NAMING RANGES (HARD)
- Governance: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/NN__*` (00..99)
- Realms (root): `04_KNOWLEDGE_BASE/01__*` .. `04_KNOWLEDGE_BASE/08__*`
- Topics: `04_KNOWLEDGE_BASE/10_TOPICS/NN__*` (00..99)
- Aliases (non-canon): `04_KNOWLEDGE_BASE/98__*` и `04_KNOWLEDGE_BASE/99__*` только

---

## ALIAS POLICY (HARD)
Alias-файлы (98/99):
- НЕ канон
- содержат только CANON_TARGET (path + raw)
- запрещено хранить правила, списки, контент, реестры

---

## NO DUPLICATION (HARD)
Запрещено дублировать OWNER/LOCK/VERSION/STATUS в конце файла отдельными строками.
Одна истина — в шапке.

---

--- END.
