# UNIVERSE ENGINE — CONSTRAINTS REGISTRY (LAW)
FILE: 01_SYSTEM_LAW/06__CONSTRAINTS_REGISTRY.md

SCOPE: Universe Engine
LAYER: SYSTEM LAW
LEVEL: L0
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
OWNER: SYSTEM
ROLE: Закон-реестр ограничений. Фиксирует обязательные запреты/условия системы и вселенных. Любое обязательное правило должно жить здесь (или ссылаться сюда).

---

## 0) PURPOSE
Constraints Registry нужен чтобы:
- все “нельзя/обязательно” были в одном месте
- движки/спецы/QA могли ссылаться на одно правило
- не было потери важных законов в переписке

---

## 1) CONSTRAINT ID (CANON)
Каждое ограничение имеет ID:

CST.<DOMAIN>.<NAME>

DOMAIN:
- SYS (система)
- DOC (документы)
- ENT (сущности)
- NAR (сюжет/нарратив)
- WRD (мир/законы мира)
- CHR (персонажи)
- VIS (визуал)
- SND (звук/музыка)
- OUT (финальный продукт)

NAME: UPPER_SNAKE_CASE

Пример:
- CST.WRD.NO_CURRENCY_FOR_GREAT_CIVILIZATIONS

---

## 2) REGISTRY ROW FORMAT (MANDATORY)
Одна запись:

ID | PRIORITY | STATUS | RULE | APPLIES_TO | ENFORCED_BY | NOTES

Где:
- PRIORITY: S0 (абсолютно) / S1 / S2 / S3
- STATUS: ACTIVE / DEPRECATED / PLANNED
- RULE: формулировка “MUST / FORBIDDEN”
- APPLIES_TO: LAYERS or entity groups
- ENFORCED_BY: UID сущностей (QA/VAL/CTL) или “MANUAL”

---

## 3) PRIORITY SEMANTICS
- S0: нарушение ломает канон (fail gate)
- S1: критично, но может быть оправдано (нужна явная причина)
- S2: желательно, но можно отступить
- S3: рекомендация

---

## 4) CANON CONSTRAINTS (START SET)

### A) SYSTEM CONSTRAINTS
CST.SYS.NO_HIDDEN_DEPENDENCIES | S0 | ACTIVE | FORBIDDEN: скрытые зависимости без DEPENDS_ON | ENT, STANDARDS, PRJ | MANUAL/VAL | must declare deps  
CST.SYS.EXISTENCE_RULE | S0 | ACTIVE | MUST: элемент существует только если в INDEX | ALL | MANUAL/VAL | existence law  
CST.SYS.SINGLE_SOT | S0 | ACTIVE | MUST: один Source of Truth на один тип правил | LAW/STANDARDS | MANUAL | no duplicates  

### B) DOCUMENT CONTROL
CST.DOC.HEADER_REQUIRED | S0 | ACTIVE | MUST: корректная шапка (STATUS/LOCK/VERSION/OWNER/ROLE) | ALL DOCS | VAL | doc control  
CST.DOC.NAMING_REQUIRED | S0 | ACTIVE | MUST: имена по Naming Rules | ALL | VAL | naming law  
CST.DOC.XREF_FORMAT | S1 | ACTIVE | MUST: ссылки оформляются по REL/XREF policy | INDEX/REGISTRY | VAL | readable without repo  

### C) WORLD / CANON (пример из твоего канона)
CST.WRD.NO_CURRENCY_FOR_GREAT_CIVILIZATIONS | S0 | ACTIVE | MUST: великие цивилизации не используют валюту | WRD/NAR/CHR | QA/ENG | universe canon

---

## 5) ADDING NEW CONSTRAINT (FLOW)
1) Создаёшь новый CST.* ID
2) Добавляешь запись сюда (одной строкой)
3) Если нужен детальный документ — создаёшь отдельный SoT и даёшь ссылку в NOTES

Запрещено:
- держать “обязательные правила” только в чатах

---

## 6) FINAL LAW
> Constraint — это закон.  
> Нет записи в реестре = правило не считается обязательным.

OWNER: Universe Engine  
LOCK: FIXED

---
END.
