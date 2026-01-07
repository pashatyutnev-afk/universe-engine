# KB ENTITY TYPES — INDEX
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/03__INDEX__KB_ENTITY_TYPES.md

SCOPE: Universe Engine / KB Entity Types
LEVEL: L1
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
OWNER: SYSTEM
ROLE: Список типов KB-сущностей и их минимальных полей (шаблонный контракт).

---

## 0) CORE LAW
- CATEGORY в UID = тип сущности.
- Тип обязан соответствовать минимальному контракту.

---

## 1) CANON TYPES (MINIMUM SET)
### CHR — Character
Минимум:
- UID
- SUMMARY
- ROLE_IN_WORLD
- FORM_PROFILE (BIO/MECH/ETHR/HYBRID)
- TRAITS (коротко)

### LOC — Location
Минимум:
- UID
- SUMMARY
- REGION/DOMAIN
- KEY_FEATURES

### OBJ — Object/Artifact
Минимум:
- UID
- SUMMARY
- PURPOSE
- OWNER/ORIGIN (если применимо)

### EVT — Event
Минимум:
- UID
- SUMMARY
- TIMEFRAME (если есть)
- CAUSE/EFFECT (если есть)

### SYS — System/Rule (правило мира)
Минимум:
- UID
- SUMMARY
- RULE_TEXT
- CONSTRAINTS

### CONCEPT — Concept
Минимум:
- UID
- SUMMARY
- DEFINITION
- CONTRASTS (опционально)

### REL — Relation
Минимум:
- UID
- SUMMARY
- FROM_UID
- TO_UID
- TYPE

### ARC — Arc (нарративная дуга)
Минимум:
- UID
- SUMMARY
- START/END (опционально)

### STYLE — Style / Tone reference
Минимум:
- UID
- SUMMARY
- STYLE_RULES (коротко)

---

## 2) EXTENSIONS
Доп. типы можно добавлять, но только через правила и регистрацию.

---
END.
