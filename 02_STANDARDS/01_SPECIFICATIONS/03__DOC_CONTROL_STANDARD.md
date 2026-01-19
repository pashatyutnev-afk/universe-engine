# DOC CONTROL STANDARD — CANON

FILE: 02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md
SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: STANDARD
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.STD.DOC_CONTROL.001
OWNER: SYSTEM
ROLE: Standardizes document header, structure, metadata rules, navigation discipline, interface formatting, KB scope discipline, and enforcement gates to prevent drift and conflicts.

CHANGE_NOTE:
- DATE: 2026-01-19
- TYPE: MINOR
- SUMMARY: "Added hard rules for INTERFACES (RAW-only), KB SCOPE block, SPC PEER ROLES separation (non-ENG), and domain discipline notes (VISUAL no montage decisions, color as principles). Expanded QC + enforcement."
- REASON: "Align doc control with runtime: RAW-only nav, artifact outputs, KB boundary discipline, and role separation to keep engines deterministic."
- IMPACT: "Docs become auditable and consistent across tasks; prevents hidden path guessing, KB boundary drift, and mixed-role contamination in ENG docs."
- CHANGE_ID: UE.CHG.2026-01-19.STD.DOC_CONTROL.002

---

## 0) PURPOSE
Этот стандарт задаёт единый формат и контроль документов:
- единая “шапка” для всех типов файлов
- единая структура (минимальный скелет)
- запрет на гуляющие метаданные (header-only truth)
- формат `INTERFACES` (RAW-only, no PATH)
- дисциплина `KNOWLEDGE BASE (KB) SCOPE` (границы, входы/выходы, raw refs)
- разделение “SPC peer roles” от ENG-секций (ENG остаётся детерминированным)
- чеклист качества и правила enforcement (STOP уровни)

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
- Header всегда расположен в начале файла, сразу после `# `.

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

### 5.1 Minimum skeleton (default)
Каждый документ должен иметь минимум следующие разделы (если применимо):
- `## 0) PURPOSE`
- `## 1) SCOPE` или `## 1) DEFINITIONS`
- `## N) RULES / PIPELINE / REQUIREMENTS` (по типу)
- `## REFERENCES` (если нужны ссылки)

### 5.2 ENGINE documents (additional mandatory)
ENGINE документы дополнительно должны иметь:
- `## MINI-CONTRACT (MANDATORY)` с:
  - CONSUMES
  - PRODUCES
  - DEPENDS_ON
  - OUTPUT_TARGET

### 5.3 INDEX / REGISTRY documents (additional mandatory)
INDEX/REGISTRY документы дополнительно должны иметь:
- `EXISTENCE RULE (ABSOLUTE)` (если это каноническая навигация)
- порядок/структуру/правила ссылок
- если ссылки требуются — только RAW (см. раздел 6)

---

## 6) NAVIGATION + INTERFACES STANDARD (RAW DISCIPLINE)

### 6.1 Navigation rule (when doc is navigation)
Если документ является индексом/реестром/навигацией и обязан вести по артефактам:
- ссылки на управляемые артефакты должны быть **RAW-only** (полный raw URL)
- запрещено ссылаться “PATH-only” (путь без raw URL), если этот документ выполняет роль навигации

### 6.2 INTERFACES block (mandatory when applicable)
Если документ взаимодействует с внешними файлами/сущностями/пайплайнами/шаблонами, он обязан иметь раздел:

`## INTERFACES`

Правила:
- В `INTERFACES` **запрещено** использовать только `PATH`.
- В `INTERFACES` **разрешено только RAW** (и при желании UID).
- Формат записи (рекомендуемый):
  - `NAME — RAW_URL`
  - опционально: `UID: ...`
- Любая ссылка из `INTERFACES` должна быть кликабельной и однозначной.

---

## 7) KNOWLEDGE BASE (KB) SCOPE (MANDATORY WHEN USING KB)

Если документ использует KB как источник правил/терминов/методов/проверок, он обязан иметь раздел:

`## KNOWLEDGE BASE (KB) SCOPE`

Минимальный набор:
- `KB INPUTS:` что именно берём из KB (типы модулей/темы/пакеты)
- `KB OUTPUTS:` что документ производит на выходе (артефакты/правила/решения)
- `BOUNDARIES:` что **запрещено** делать/выводить из KB (границы домена)
- `RAW REFERENCES:` список RAW ссылок на реально используемые KB-элементы

Запрещено:
- “фантазировать” источники KB без RAW refs
- размывать границы (“берём всё подряд”)

---

## 8) ROLE SEPARATION RULE (SPC PEER ROLES VS ENG)

### 8.1 ENG purity law
В документах класса ENG запрещено смешивать:
- описание peer-ролей SPC внутри ENG секций метода/контракта

ENG должен оставаться:
- детерминированным
- метод-ориентированным
- без “организационных” вставок

### 8.2 SPC PEER ROLES (NON-ENG) block
Если нужно перечислить peer-ролей/взаимодействия специалистов, это делается отдельным разделом:

`## SPC PEER ROLES (NON-ENG)`

И он не входит в метод/контракт ENG.

---

## 9) DOMAIN DISCIPLINE NOTES (CONTENT LIMITS)

Эти правила применяются, когда документ относится к домену.

### 9.1 VISUAL (no montage decisions)
В домене VISUAL запрещено “принимать монтажные решения”.
Разрешено:
- фиксировать ограничения, риски, запреты, требования к читаемости/непротиворечивости
- формулировать проверяемые гейты/критерии
Запрещено:
- описывать конкретный монтаж/склейки как “единственно верное решение” (это не задача DOC CONTROL)

### 9.2 COLOR (principles only)
Про цвет можно писать только как principles:
- контраст, читаемость, иерархия, безопасность восприятия
Запрещено:
- жёстко задавать палитры “в каноне”, если это не отдельный контролируемый стандарт домена

### 9.3 UID / CHANGE_ID normalization (forward rule)
Если обнаружена неоднородность UID/CHANGE_ID, фиксируй как:
- GAP / TODO
- отдельный changelog item
Не делай “тихих” массовых замен без change-management.

---

## 10) CHANGE NOTE STANDARD
CHANGE_NOTE обязателен и должен содержать минимум:
- DATE
- TYPE (PATCH/MINOR/MAJOR/MIGRATION/EMERGENCY)
- SUMMARY
- REASON
- IMPACT
- CHANGE_ID

---

## 11) QUALITY CHECKLIST (PRE-CANON)

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

Interfaces (если есть взаимодействия):
- [ ] присутствует `INTERFACES`
- [ ] в `INTERFACES` нет PATH-only записей
- [ ] все ссылки в `INTERFACES` — RAW

KB scope (если KB используется):
- [ ] присутствует `KNOWLEDGE BASE (KB) SCOPE`
- [ ] есть INPUTS/OUTPUTS/BOUNDARIES
- [ ] есть RAW REFERENCES на реально используемые KB-элементы

Role separation:
- [ ] если документ ENG — peer roles вынесены в `SPC PEER ROLES (NON-ENG)` (если вообще нужны)

Navigation (если индекс/реестр):
- [ ] raw-links присутствуют там, где навигация обязательна
- [ ] порядок/номера соответствуют реальности

Governance:
- [ ] если LOCK: FIXED — изменение прошло change pipeline
- [ ] есть след в Audit/Memory (если требуется)

---

## 12) ENFORCEMENT

Нарушения S0 (STOP):
- отсутствует обязательное поле header
- дублирующий STATUS/LOCK/UID/VERSION/OWNER/ROLE
- канонический индекс/реестр без raw-links там, где они обязательны
- `INTERFACES` содержит PATH-only вместо RAW
- KB используется, но нет `KNOWLEDGE BASE (KB) SCOPE` + RAW REFERENCES
- канонический файл не зарегистрирован в каноническом индексе (если это требуется каноном)

При S0 документ считается non-canon до исправления.

Нарушения S1 (BLOCK):
- ENG документ смешивает peer-ролей внутри метода/контракта
- VISUAL документ делает “монтажные решения” вместо ограничений/рисков
- “цвет” задан как палитра без отдельного доменного стандарта

---

## 13) REFERENCES

Canon Protocol (LAW):
- 01_SYSTEM_LAW/04__CANON_PROTOCOL.md
