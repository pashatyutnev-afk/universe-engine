# KB TAGS (SYSTEM)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/90__KB_TAGS.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_SYSTEM
SYSTEM_OBJ: TAGS
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.SYS.TAGS.001
OWNER: SYSTEM
ROLE: Canonical tag taxonomy for Knowledge Base + projects: naming, allowed classes, usage rules, and minimum tagging requirements

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Введена каноническая таксономия тегов KB: формат, классы, правила применения, минимальный набор"
- REASON: "Без единой таксономии теги превращаются в мусор и ломают поиск/навигацию"
- IMPACT: "KB passports, KB realms, project artifacts using tags"

---

## 0) PURPOSE
Этот файл задаёт единую систему тегов для:
- KB realms и KB entity passports
- проектных артефактов, если они используют KB-теги
- поиска/группировки/фильтрации

---

## 1) TAG FORMAT (HARD)
### 1.1 Canon tag string
Тег — строка формата:

`KB.<CLASS>.<NAME>`

Где:
- `KB` — фиксированный префикс слоя знаний
- `<CLASS>` — класс тега (строго из списка ниже)
- `<NAME>` — имя тега (UPPER_SNAKE_CASE, без пробелов)

Примеры:
- `KB.REALM.NARRATIVE`
- `KB.TYPE.CHECKLIST`
- `KB.TOPIC.CONFLICT`
- `KB.QA.READABILITY`

### 1.2 Forbidden
- пробелы, кириллица в тегах (только латиница/цифры/underscore)
- смешивание двух смыслов в одном теге
- “супер-общие” теги типа `KB.TOPIC.GENERAL`

---

## 2) TAG CLASSES (ALLOWED SET)
Допустимы только эти классы:

### 2.1 REALM (куда относится)
- `KB.REALM.NARRATIVE`
- `KB.REALM.CHARACTER`
- `KB.REALM.VISUAL`
- `KB.REALM.SOUND`
- `KB.REALM.PRODUCTION`
- `KB.REALM.MARKETING`
- `KB.REALM.GLOSSARY`
- `KB.REALM.RESEARCH`

### 2.2 TYPE (что это за артефакт/сущность)
- `KB.TYPE.PRACTICE`
- `KB.TYPE.METHOD`
- `KB.TYPE.CHECKLIST`
- `KB.TYPE.TEMPLATE`
- `KB.TYPE.REFERENCE`
- `KB.TYPE.CASE`
- `KB.TYPE.GUIDE`

### 2.3 TOPIC (о чём)
Примеры (расширяем по мере необходимости, но осмысленно):
- `KB.TOPIC.SCENE`
- `KB.TOPIC.EVENT`
- `KB.TOPIC.CONFLICT`
- `KB.TOPIC.STAKES`
- `KB.TOPIC.TENSION`
- `KB.TOPIC.PACING`
- `KB.TOPIC.DIALOGUE`
- `KB.TOPIC.LIGHTING`
- `KB.TOPIC.COMPOSITION`
- `KB.TOPIC.SOUND_DESIGN`
- `KB.TOPIC.MUSIC_USAGE`
- `KB.TOPIC.RELEASE`

### 2.4 QA (какой quality gate/проверка)
- `KB.QA.COHERENCE`
- `KB.QA.CONSISTENCY`
- `KB.QA.READABILITY`
- `KB.QA.CLARITY`
- `KB.QA.CONTINUITY`

### 2.5 CONF (уверенность — для research claims)
- `KB.CONF.C0`
- `KB.CONF.C1`
- `KB.CONF.C2`
- `KB.CONF.C3`

### 2.6 STATUS (жизненный статус контента KB)
- `KB.STATUS.DRAFT`
- `KB.STATUS.ACTIVE`
- `KB.STATUS.DEPRECATED`
- `KB.STATUS.ARCHIVED`

---

## 3) TAGGING RULES (MANDATORY)
### 3.1 Minimum tags for KB entity passport
Каждый KB Entity Passport обязан иметь минимум:
- 1 тег REALM (`KB.REALM.*`)
- 1 тег TYPE (`KB.TYPE.*`)
- 1–3 тега TOPIC (`KB.TOPIC.*`)
- 0–2 тега QA (`KB.QA.*`) если применимо
- 0–1 тег CONF (`KB.CONF.*`) только если это research claim/факт

### 3.2 Anti-spam limits
- максимум 8 тегов на один объект (иначе это не теги, а свалка)
- если хочется больше — делай нормальные поля/структуру в паспорте

### 3.3 No duplication by synonyms
Если есть `KB.TOPIC.PACING`, нельзя рядом вводить `KB.TOPIC.RHYTHM` как дубль.
Один смысл → один тег.

---

## 4) EXTENSION RULE (HOW TO ADD NEW TAGS)
Добавление новых тегов допускается только если:
- у тега есть чёткая цель (фильтрация/поиск/группировка)
- тег не дублирует существующий
- тег будет использоваться минимум в 3 объектах (иначе он не нужен)

---

## 5) EXAMPLES (REFERENCE)
### 5.1 Visual checklist example
- `KB.REALM.VISUAL`
- `KB.TYPE.CHECKLIST`
- `KB.TOPIC.COMPOSITION`
- `KB.QA.READABILITY`
- `KB.STATUS.ACTIVE`

### 5.2 Research note example
- `KB.REALM.RESEARCH`
- `KB.TYPE.REFERENCE`
- `KB.TOPIC.HISTORY` (если введёте такой топик)
- `KB.CONF.C2`
- `KB.STATUS.DRAFT`

--- END.
