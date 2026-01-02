# ENGINE STANDARD
## Canonical Definition of System Engines

---

## 1. Definition / Определение

### EN
An Engine is a system mechanism that enforces rules, filters outputs,
and guarantees structural or logical consistency.

### RU
Движок — это системный механизм, обеспечивающий соблюдение правил,
фильтрацию результатов и логическую целостность.

---

## 2. Core Principle / Базовый принцип

- Engine = Rule + Filter + Constraint
- Engine does NOT create content
- Engine validates, restricts, structures

---

## 3. Mandatory Structure / Обязательная структура

Every engine MUST contain exactly two documents:

1. PASSPORT__<Engine_Name>.md
2. PROTOCOL__<Engine_Name>.md

No additional documents are allowed without canon approval.

---

## 4. Passport Role / Назначение паспорта

PASSPORT defines:
- Engine identity
- Purpose
- Scope
- Authority
- Integration boundaries

Answers:
**WHAT IS THIS ENGINE?**

---

## 5. Protocol Role / Назначение протокола

PROTOCOL defines:
- When engine is invoked
- What it checks or enforces
- Inputs and outputs
- Failure conditions

Answers:
**HOW DOES THIS ENGINE OPERATE?**

---

## 6. Knowledge Access / Доступ к знаниям

Engines:
- May reference canon rules
- May reference structural definitions
- Must NOT store domain knowledge

---

## 7. Interaction Rules / Взаимодействие

Engines:
- Are invoked by specialists or system
- Can block, validate, approve outputs
- Cannot override higher-level canon

---

## 8. Canon Status / Канон

- System-level entity
- Stable once approved
- Changes require global review

---

## 9. Final Note / Финал

Engines do not think.
They enforce.

Without engines,
systems collapse into chaos.
