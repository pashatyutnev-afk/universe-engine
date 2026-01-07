# KB ENTITY TYPES (INDEX)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/03__INDEX__KB_ENTITY_TYPES.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: INDEX
INDEX_TYPE: ENTITY_TYPES
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.GOV.IDX.ENTITY_TYPES.001
OWNER: SYSTEM
ROLE: Canonical registry of KB entity types used by KB Entity Passports and KB registries (standardizes classification)

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Справочник типов KB-сущностей: введён каноничный набор типов + правила выбора типа"
- REASON: "Без типов паспорта становятся несопоставимыми и ломают реестры/поиск"
- IMPACT: "Все KB entity passports, KB registry, KB create flow"

---

## 0) PURPOSE
Этот документ фиксирует **канонический набор типов KB-сущностей**.

Важно:
- Это справочник типов для KB-паспортов.
- Он НЕ объявляет existence для слоя (это делает master-index KB).

---

## 1) HOW TO CHOOSE ENTITY_TYPE (RULE)
Выбирай тип по намерению:

- Хочу описать **практику/приём/паттерн** → `KB_PRACTICE`
- Хочу описать **процесс/пайплайн** → `KB_PROCESS`
- Хочу описать **чеклист/гейт/валидатор** → `KB_CHECKLIST`
- Хочу описать **понятие/термин** → `KB_CONCEPT`
- Хочу описать **артефакт/выход** (шаблон результата) → `KB_ARTIFACT`
- Хочу описать **пример/кейс** → `KB_CASE`
- Хочу описать **инструмент/метод** (в широком смысле) → `KB_METHOD`
- Хочу описать **системный справочник** KB → `KB_SYSTEM_REF`

---

## 2) CANON ENTITY TYPES (STRICT SET)
Формат записи:
`ENTITY_TYPE: <CODE> — <one-line meaning>`

### 2.1 Core KB types
ENTITY_TYPE: KB_PRACTICE — практика/паттерн “как делать” (повторяемый приём)
ENTITY_TYPE: KB_PROCESS — процесс/поток шагов (create/review/qa)
ENTITY_TYPE: KB_CHECKLIST — чеклист/гейт/критерии проверки
ENTITY_TYPE: KB_CONCEPT — понятие/термин/концепт (без лишней философии)
ENTITY_TYPE: KB_METHOD — метод/техника (набор действий, применимый в разных местах)
ENTITY_TYPE: KB_ARTIFACT — описание результата/выходного артефакта (структура/формат)
ENTITY_TYPE: KB_CASE — кейс/пример (конкретная ситуация + выводы)

### 2.2 System reference KB types
ENTITY_TYPE: KB_SYSTEM_REF — системный справочник KB (словарь/таблица/каталог)

---

## 3) RECOMMENDED FIELDS BY TYPE (GUIDE)
Это рекомендации (не закон), но помогают унифицировать паспорта.

### KB_PRACTICE
- purpose
- steps
- do/dont
- examples
- xref to realms

### KB_PROCESS
- входы/выходы
- шаги
- роли (кто делает)
- gate criteria
- где применяется

### KB_CHECKLIST
- checklist items
- severity / priority
- pass/fail rules
- common failures

### KB_CONCEPT
- definition
- boundaries (in/out)
- examples
- common confusion

### KB_ARTIFACT
- schema / structure
- required sections
- validation rules
- storage target

### KB_CASE
- context
- decision
- outcome
- lessons learned

---

## 4) VALIDATION RULES (HARD)
- ENTITY_TYPE в паспорте обязан быть одним из списка (раздел 2)
- один паспорт = один ENTITY_TYPE
- если смысл не подходит ни под один тип — это ошибка: нужно либо уточнить смысл, либо расширить справочник через governance change

---

## FINAL RULE (LOCK)
Этот индекс — SoT по типам KB-сущностей для паспортов.
LOCK: FIXED
--- END.
