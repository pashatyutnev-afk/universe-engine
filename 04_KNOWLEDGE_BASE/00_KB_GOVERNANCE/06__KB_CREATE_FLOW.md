# KB CREATE FLOW (OPERATIONAL GUIDE) (CANON)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/06__KB_CREATE_FLOW.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: GUIDE
GUIDE_TYPE: OPERATIONAL_FLOW
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.KB.GOV.CREATE_FLOW.016
OWNER: SYSTEM
ROLE: Operational step-by-step flow for adding KB entities and KB knowledge (realm content). Ensures registry-first, UID-first, and no-dup compliance.

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MINOR
- SUMMARY: "KB Create Flow: два потока (Entity vs Knowledge), шаги, проверки, миграции дублей"
- REASON: "Чтобы KB пополнялась без хаоса и дублей"
- IMPACT: "Daily KB operations"

---

## XREF (UID-first)
XREF: UE.KB.GOV.RULES.011 | governs | KB creation rules | 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB.md
XREF: UE.KB.GOV.REGISTRY.012 | depends_on | registry-first existence | 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/02__INDEX__KB_GLOBAL_REGISTRY.md
XREF: UE.KB.GOV.ENTITY_TYPES.013 | depends_on | choose valid entity type | 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/03__INDEX__KB_ENTITY_TYPES.md
XREF: UE.KB.TPL.ENTITY_PASSPORT.015 | depends_on | passport template | 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/05__TEMPLATE__KB_ENTITY_PASSPORT.md

---

## 0) PURPOSE
Этот документ — рабочий протокол создания:
- KB Entity (через паспорт + реестр)
- KB Knowledge (через realm-файлы)

---

## 1) QUICK DECISION (ENTITY OR KNOWLEDGE?)
Если ты добавляешь:
- конкретный объект мира (персонаж/локация/фракция/объект/событие) → **ENTITY FLOW**
- правило/методику/справочник/системное знание → **KNOWLEDGE FLOW**

---

## 2) ENTITY FLOW (PASSPORT + REGISTRY) (MANDATORY)
### Step E0 — Check for duplicates (no-dup)
1) Ищи по имени/алиасам:
   - уже есть паспорт?
   - уже есть запись в Global Registry?
2) Если есть — НЕ создавай новую сущность. Обновляй существующую.

### Step E1 — Choose type
- выбери `ENTITY_TYPE` из KB Entity Types

### Step E2 — Create passport file
1) создай файл в:
   - `04_KNOWLEDGE_BASE/10_ENTITIES/<ENTITY_TYPE>/`
2) скопируй шаблон `KB Entity Passport`
3) заполни REQUIRED поля:
   - ENTITY_UID
   - ENTITY_TYPE
   - ENTITY_NAME
   - ENTITY_STATUS
   - ONE_LINE_SUMMARY

### Step E3 — Register entity (registry-first)
Добавь строку в:
- `00_KB_GOVERNANCE/02__INDEX__KB_GLOBAL_REGISTRY.md`

Заполни минимум:
- ENTITY_UID
- ENTITY_NAME
- ENTITY_TYPE
- ENTITY_STATUS
- PASSPORT_PATH

### Step E4 — Add relations (UID-first)
Добавь XREF связи в паспорте:
- member_of / located_in / relates_to / opposes / etc.

### Step E5 — Optional: add realm knowledge
Если нужно:
- упомяни сущность в соответствующем realm-файле
- обязательно через UID-first

---

## 3) KNOWLEDGE FLOW (REALM CONTENT)
### Step K0 — Choose realm
Определи realm:
- Narrative / Character / Visual / Sound / Production / Marketing / Glossary / Research

### Step K1 — Check for duplication
- Не повторяй уже существующее правило в другом месте.
- Если нужно повторить — делай XREF/ссылку.

### Step K2 — Add structured section
- Добавь секцию с понятным заголовком
- Внутри: тезисы/правила/примеры
- Если упоминаются сущности → ссылаться UID-first

### Step K3 — If new entities discovered
Если по ходу знания появилась новая сущность:
- остановись
- пройди ENTITY FLOW
- вернись и добавь XREF

---

## 4) DEPRECATION / MERGE FLOW (WHEN DUPLICATES FOUND)
Если обнаружены 2 сущности с одинаковым смыслом:
1) выбрать каноническую (оставить ACTIVE)
2) дубль → ENTITY_STATUS: deprecated
3) дубль должен иметь:
   - DEPRECATED_BY_ENTITY_UID
   - XREF deprecated_by → канон
4) Global Registry обновить:
   - для дубля поставить deprecated + NOTE с DEPRECATED_BY

---

## 5) VALIDATION CHECK (BEFORE COMMIT)
Для сущности:
- есть паспорт
- паспорт заполнен минимумом
- есть строка в Global Registry
- тип валиден
- нет второго UID на тот же смысл

Для знания:
- секция структурирована
- нет дубля смысла
- внутренние связи через UID-first

---

## 6) SHORT OPERATING LOOP (DAILY)
- добавил сущность → зарегистрировал → связал → (опционально) описал в realm
- добавил знание → проверил no-dup → добавил XREF на сущности

--- END.
