# KB GOVERNANCE — README (CANON)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/00__README__KB_REALM.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 00_KB_GOVERNANCE
DOC_TYPE: README
INDEX_TYPE: REALM_README
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.README.REALM.GOV.001
OWNER: SYSTEM
ROLE: Explain what KB Governance is, what files it contains, and how entities must use it (orientation only, not navigation authority).

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created KB governance realm README: purpose, contents map, usage order, and strict boundaries (not a second index)."
- REASON: "Governance is the control plane for KB quality; entities must load it first and apply it consistently."
- IMPACT: "Less drift, fewer broken runs, more deterministic KB usage."
- CHANGE_ID: UE.CHG.2026-01-14.KB.GOV.README.001

---

## 0) PURPOSE (WHY THIS REALM EXISTS)
`00_KB_GOVERNANCE` — это **контрольная плоскость** базы знаний.

Она отвечает за:
- правила использования KB (без фантазии, без дрейфа)
- стандарты структуры KB-доков
- типы связей (REL) и кросс-ссылок (XREF)
- хранение / карта папок / паспорт KB-сущностей
- дисциплину создания и контроля документации

---

## 1) WHAT THIS REALM IS / IS NOT
### IS
- Набор базовых управляющих документов, которые **должны загружаться первыми** при работе через KB.
- Источник правил “как пользоваться KB правильно”.

### IS NOT
- Это **НЕ** мастер-индекс KB.
- Это **НЕ** альтернативная навигация.
- Это **НЕ** место для доменных знаний (музыка/сюжет/визуал) — домены живут в `10_TOPICS` и доменных овервью-файлах слоя.

---

## 2) NAVIGATION RULE (STRICT)
- Единственная точка навигации по KB: `04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md`.
- Этот README — ориентация: что за документы и зачем, **без роли “истины навигации”**.
- Любое открытие файлов делается через RAW-ссылку из мастер-индекса KB.

---

## 3) REQUIRED USAGE ORDER (DETERMINISTIC)
Любой запуск, который опирается на KB, обязан соблюдать порядок:

1) Загрузить KB master index (в качестве навигации).
2) Загрузить минимум governance (это realm):
   - RULES KB
   - KB XREF rules
   - KB REL types
   - KB tags (если нужно)
3) Дальше — выбрать scope (topics / домены) и грузить доменные модули.
4) Всегда выдавать trace (источники/память/статусы/lookup).

---

## 4) CONTENTS (WHAT FILES LIVE HERE)
Ниже — “карта содержимого” (описания, не навигация).

### 00__README__KB_REALM.md
- Этот документ. Ориентация по governance realm.

### 01__RULES__KB.md
- Базовые правила пользования KB: дисциплина, запреты, обязательные блоки.

### 02__INDEX__KB_GLOBAL_REGISTRY.md
- Глобальные определения сущностей/типов KB-объектов (реестр понятий).

### 03__INDEX__KB_ENTITY_TYPES.md
- Типология KB документов/модулей (policy/standard/map/checklist/template/…).

### 04__KB_STORAGE_MAP.md
- Карта хранения: как организованы папки KB, где что должно лежать.

### 05__TEMPLATE__KB_ENTITY_PASSPORT.md
- Шаблон паспорта KB-сущности (чтобы любой модуль был аудируемым).

### 06__KB_CREATE_FLOW.md
- Процедура создания KB-модуля: от идеи → до регистрации в мастер-индексе.

### 07__KB_DOC_CONTROL.md
- Контроль документации: версии, change_note, статусы, депрекейты, alias/pointer.

### 90__KB_TAGS.md
- Канонические теги KB (не skill tags доменов; именно governance tagging).

### 91__KB_REL_TYPES.md
- Типы отношений (REL): depends_on, governed_by, validated_by, supersedes, …

### 92__KB_XREF_RULES.md
- Правила XREF: UID-only ссылки, запрет URL/PATH в operational crossref, формат блоков.

---

## 5) “GOVERNANCE MINIMUM SET” (PRACTICAL)
Минимум, который должен быть “в голове” у любой сущности (и загружаться в первую очередь):
- RULES KB
- XREF rules
- REL types
- Doc control (если идёт создание/редактирование/сертификация)

---

## 6) HARD BOUNDARIES (DO NOT CROSS)
Запрещено:
- размещать доменные знания (музыка/сюжет/визуал) в governance realm
- превращать этот realm в “второй индекс” с RAW-реестром
- добавлять новые “законы” в README — только ориентация
- писать правила, которые конфликтуют с мастер-индексом и system law

---

## 7) COMMON FAILS (AND FIXES)
FAIL: сущность начинает работу без governance
- FIX: всегда загружай governance minimum set первым шагом

FAIL: появляются “скрытые правила” вне governance
- FIX: переносить правила в RULES KB или нужный policy/standard модуль

FAIL: ссылки в XREF начинают быть URL/PATH
- FIX: только UID-only XREF (NAV — только в master index)

---

## FINAL RULE (LOCK)
Этот realm — контроль качества KB.
Он должен быть минимальным, строгим и неизменным по смыслу.

OWNER: SYSTEM
LOCK: FIXED

--- END.
