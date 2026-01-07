# KB DOC CONTROL (KB-LAYER STANDARD)
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
ROLE: KB layer doc-control rules: required header fields, allowed values, naming ranges, and alias policy

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Введён Doc Control для KB: обязательная шапка, допустимые STATUS/LOCK, naming ranges, alias policy"
- REASON: "Без Doc Control KB не валидируется и расползается"
- IMPACT: "Все KB файлы (governance/realms/topics/passports)"

---

## REQUIRED HEADER (MANDATORY)
Каждый канонический KB-файл обязан иметь шапку:

SCOPE / LAYER / DOC_TYPE / LEVEL / STATUS / LOCK / VERSION / UID / OWNER / ROLE

---

## ALLOWED VALUES (STRICT)
STATUS: DRAFT | ACTIVE | DEPRECATED | ARCHIVED  
LOCK: OPEN | FIXED  
VERSION: X.Y.Z (SemVer)

---

## NAMING RANGES (HARD)
- Governance: `00_KB_GOVERNANCE/NN__*` (00..99)
- Realms (root KB): `01__*` .. `08__*`
- Topics: `10_TOPICS/NN__*` (00..99)
- Aliases (non-canon): `98__*` and `99__*` only

---

## ALIAS POLICY (HARD)
Alias-файлы:
- не являются каноном
- содержат только pointer на `00__INDEX__KNOWLEDGE_BASE`
- запрещено хранить в alias любые правила или контент

---

## NO DUPLICATION
Запрещено дублировать OWNER/LOCK/VERSION/STATUS в конце файла отдельными строками.
Одна истина — в шапке.

---

## FINAL RULE (LOCK)
Этот документ — SoT по Doc Control для KB слоя.
--- END.
