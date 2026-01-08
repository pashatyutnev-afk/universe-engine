# DOC CONTROL STANDARD — CANON
FILE: 02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md

SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: STANDARD
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.STD.DOC_CONTROL.001
OWNER: SYSTEM
ROLE: Standardizes document header, structure, metadata rules, and enforcement gates to prevent drift and conflicts.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Document control standardized: header-only truth, mandatory fields, anti-duplication, raw-link navigation, and QC checklist."
- REASON: "Eliminate inconsistent headers, duplicated metadata, broken navigation, and non-deterministic canon."
- IMPACT: "All docs become uniform, verifiable, and compatible with governance engines."
- CHANGE_ID: UE.CHG.2026-01-08.STD.DOC_CONTROL.001

---

## 0) PURPOSE

Этот стандарт задаёт единый формат и контроль документов:
- единая “шапка” для всех типов файлов
- единая структура
- запрет на гуляющие метаданные
- чеклист качества перед тем как документ считается каноническим

---

## 1) SCOPE

Применяется ко всем слоям:
- 00_INDEX
- 01_SYSTEM_LAW
- 02_STANDARDS
- 03_SYSTEM_ENTITIES
- 04_KNOWLEDGE_BASE
- 05_PROJECTS
- 06_ASSETS
- 08_DATABASES
- 99_LOGS

---

## 2) HEADER STANDARD (MANDATORY)

### 2.1 Header placement
- Header всегда расположен в начале файла, сразу после `# <TITLE>`.

### 2.2 Header truth
- Header = единственная точка истины о метаданных.
- Любые повторы метаданных ниже запрещены.

### 2.3 Mandatory base fields (must exist)
Каждый документ обязан иметь поля:

- FILE:
- SCOPE:
- LAYER:
- DOC_TYPE:
- LEVEL:
- STATUS:
- LOCK:
- VERSION:
- UID:
- OWNER:
- ROLE:
- CHANGE_NOTE:

### 2.4 Optional fields (only if applicable)
Допускаются дополнительные поля, если они реально нужны типу документа:
- ENTITY_GROUP:
- INDEX_TYPE:
- FAMILY:
- CLASS:
- TAGS:
- PARENT_UID:
- RELATED_UIDS:
Но они не заменяют обязательный набор.

---

## 3) ALLOWED VALUES (STRICT SET)

### 3.1 STATUS (strict)
Только одно значение и только из списка:
- DRAFT
- ACTIVE
- DEPRECATED
- ARCHIVED

### 3.2 LOCK (strict)
Только одно значение:
- OPEN
- FIXED

### 3.3 VERSION format
Рекомендуемый формат: `MAJOR.MINOR.PATCH` (например `1.0.0`).

---

## 4) ANTI-DUPLICATION RULES (HARD)

Запрещено:
- второй `STATUS:` в теле/в конце
- второй `LOCK:` в теле/в конце
- отдельный финальный блок типа “FINAL RULE (LOCK)” с повтором меты
- повтор `UID/VERSION/OWNER/ROLE` как “псевдо-мета” ниже

Разрешено:
- текстовые ссылки (“см. шапку”), без повторения ключей

Если обнаружен конфликт:
- истина берётся из Header
- дубликаты удаляются

---

## 5) STRUCTURE STANDARD (MINIMUM)

Каждый документ должен иметь минимум следующие разделы (если применимо):

- `## 0) PURPOSE`
- `## 1) SCOPE` или `## 1) DEFINITIONS` (если нужно)
- `## N) RULES / PIPELINE / REQUIREMENTS` (по типу)
- `## REFERENCES` (если нужны ссылки)

ENGINE документы дополнительно должны иметь:
- `## MINI-CONTRACT (MANDATORY)` с:
  - CONSUMES
  - PRODUCES
  - DEPENDS_ON
  - OUTPUT_TARGET

INDEX документы дополнительно должны иметь:
- `EXISTENCE RULE (ABSOLUTE)`
- порядок/структуру/правила ссылок

---

## 6) NAVIGATION STANDARD (RAW-ONLY WHEN REQUIRED)

Если документ является индексом/реестром/навигацией:
- ссылки на управляемые артефакты должны быть raw-only (если навигация обязательна по стандарту)

---

## 7) CHANGE NOTE STANDARD

CHANGE_NOTE обязателен и должен содержать минимум:
- DATE
- TYPE (PATCH/MINOR/MAJOR/MIGRATION/EMERGENCY)
- SUMMARY
- REASON
- IMPACT
- CHANGE_ID

---

## 8) QUALITY CHECKLIST (PRE-CANON)

Перед тем как документ считать ACTIVE/FIXED, проверь:

Header:
- [ ] все обязательные поля есть
- [ ] STATUS/LOCK только один раз
- [ ] VERSION в формате x.y.z
- [ ] UID уникален (без коллизий)

Structure:
- [ ] есть PURPOSE
- [ ] есть минимальные разделы
- [ ] нет пустых “заглушек” вместо правил

Navigation (если индекс/реестр):
- [ ] raw-links присутствуют
- [ ] порядок/номера соответствуют реальности

Governance:
- [ ] если LOCK: FIXED — изменение прошло change pipeline
- [ ] есть след в Audit/Memory (если требуется)

---

## 9) ENFORCEMENT

Нарушения S0 (STOP):
- отсутствует обязательное поле header
- дублирующий STATUS/LOCK/UID/VERSION/OWNER/ROLE
- индекс без raw-links там, где они обязательны
- канонический файл не зарегистрирован в каноническом индексе

При S0 документ считается non-canon до исправления.

---

## 10) REFERENCES

Canon Protocol (LAW):
- 01_SYSTEM_LAW/04__CANON_PROTOCOL.md
