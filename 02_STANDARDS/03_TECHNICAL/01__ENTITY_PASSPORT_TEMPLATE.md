# ENTITY PASSPORT TEMPLATE (CANON)

FILE: 02_STANDARDS/03_TECHNICAL/01__ENTITY_PASSPORT_TEMPLATE.md
SCOPE: Universe Engine
LAYER: 02_STANDARDS/03_TECHNICAL
DOC_TYPE: TEMPLATE
TEMPLATE_TYPE: ENTITY_PASSPORT
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.1
UID: UE.TPL.ENTITY_PASSPORT.001
OWNER: SYSTEM
ROLE: Single canonical template for entity passport documents (SPC/ORC/ENG/CTL/VAL/QA/XREF and other entity types).

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Removed embedded INDEX template (SoT moved to 02__INDEX_TEMPLATE.md). Cleaned forbidden meta-duplication patterns. Kept entity passport structure intact."
- REASON: "Template SoT must be single; embedded duplicates cause drift. Doc Control forbids meta repetition outside header."
- IMPACT: "Entity passport template becomes stable; index template is maintained in its dedicated file."
- CHANGE_ID: UE.CHG.2026-01-20.TPL.ENTITY_PASSPORT.002

---

## 0) PURPOSE (LAW)
Этот TEMPLATE задаёт единый канонический формат **паспорта сущности**.

Паспорт сущности:
- фиксирует назначение и границы ответственности;
- задаёт интерфейсы и входы/выходы;
- описывает правила применения;
- содержит ссылки на применимые стандарты и шаблоны (RAW-only если система в RAW режиме).

---

## 1) ABSOLUTE RULES (MUST)

### 1.1 Header truth (ABSOLUTE)
- Вся мета документа живёт **только в header**.
- Запрещено дублировать метаданные ниже шапки.

### 1.2 Scope discipline (ABSOLUTE)
- Паспорт обязан явно указать:
  - что входит в ответственность (IN SCOPE),
  - что не входит (OUT OF SCOPE),
  - условия STOP.

### 1.3 RAW-only navigation
- Если система работает в RAW-only режиме, любые ссылки даются в RAW формате.
- PATH можно указывать только как label.

---

## 2) REQUIRED HEADER (COPY AS BASE)

# <ENTITY TITLE>

FILE: <path/to/file.md>
SCOPE: <scope text>
SERIAL: <optional volume serial>
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: ENTITY
ENTITY_TYPE: <SPC | ORC | ENG | CTL | VAL | QA | XREF | REG | DB | OTHER>
ENTITY_REALM: <realm folder label>
LEVEL: <L1/L2... or role level if defined>
MODE: <REPO (USAGE-ONLY, NO-EDIT) | EDIT>
ROLE: <one-line role>
STATUS: <ACTIVE | DRAFT | DEPRECATED>
LOCK: <FIXED | OPEN>
VERSION: <semver>
UID: <canonical UID>
OWNER: <SYSTEM | team>

CHANGE_NOTE:
- DATE: YYYY-MM-DD
- TYPE: <PATCH | MINOR | MAJOR>
- SUMMARY: "<short summary>"
- REASON: "<why>"
- IMPACT: "<impact>"
- CHANGE_ID: <id>

---

## 3) ENTITY PASSPORT BODY TEMPLATE (REQUIRED SECTIONS)

## 3.1 PURPOSE (LAW)

- Зачем сущность существует.
    
- Какой результат она производит (в терминах артефактов/решений/проверок).
    

## 3.2 RESPONSIBILITY (SCOPE)

### IN SCOPE

- список задач/решений, за которые сущность отвечает.
    

### OUT OF SCOPE

- что делать нельзя/что не относится к сущности.
    

## 3.3 INPUTS / OUTPUTS (INTERFACES)

### INPUTS (MINIMUM)

- какие входы требуются для запуска
    
- какие данные обязательны
    

### OUTPUTS

- какие артефакты/решения выдаёт
    
- формат результата (если стандартизирован)
    

## 3.4 CONSTRAINTS & POLICIES

- ограничения, правила, лимиты
    
- ссылки на CTL/LAW/STD, если применимо
    

## 3.5 WORKFLOW (HOW TO USE)

- как вызывается сущность (кто её назначает)
    
- типичный порядок действий
    
- типичный handoff (к кому передаёт дальше)
    

## 3.6 GATES & VALIDATION

- какие проверки применяются к её выходу
    
- где находится CTL/VAL/QA в цепочке
    

## 3.7 FAILURE MODES

- типовые ошибки
    
- как чинить
    
- когда эскалировать
    

## 3.8 DEPENDENCIES (RAW / UID)

- список ключевых зависимостей (законы/стандарты/шаблоны)
    
- RAW ссылки (если разрешено), иначе UID-only
    

## 3.9 CHANGE CONTROL

- как обновляется сущность
    
- какие протоколы применяются
    
- как фиксируются изменения
    

---

## 4) RELATED CANON TEMPLATES (REFERENCE LINKS)

(Это справочный блок. Здесь нет метаданных, только ссылки/UID.)

### INDEX TEMPLATE (SoT)

- FILE: `02_STANDARDS/03_TECHNICAL/02__INDEX_TEMPLATE.md`
    
- UID: `UE.TPL.INDEX.001`
    
- RAW: [https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/03_TECHNICAL/02__INDEX_TEMPLATE.md](https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/03_TECHNICAL/02__INDEX_TEMPLATE.md)
    

---

## 5) END