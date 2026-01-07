# DOC CONTROL STANDARD (SoT)
FILE: 02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md

SCOPE: Universe Engine / Standards
LEVEL: L0
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
OWNER: SYSTEM
ROLE: Минимальные обязательные требования к документам (структура, шапка, запреты дублей).

REFERENCES:
- Marking SoT: `02_STANDARDS/01_SPECIFICATIONS/01__UID_AND_MARKING_STANDARD.md`

---

## 1) REQUIRED HEADER
Док обязан содержать:
FILE / SCOPE / LEVEL / STATUS / LOCK / VERSION / OWNER / ROLE

---

## 2) FORBIDDEN
- два разных STATUS в одном документе
- два разных LOCK в одном документе
- “пустые заглушки” без ссылок/смысла в индексах

---

## 3) INDEX RULE
INDEX обязан быть читаем “без репозитория”:
- каждая строка имеет смысл
- у сущности есть UID (если ENT)
- у файла есть raw link (если в репо)

---
END.
