# UNIVERSE ENGINE — SYSTEM LAW (CORE)
FILE: 01_SYSTEM_LAW/00__SYSTEM_LAW.md

SCOPE: Universe Engine
LAYER: SYSTEM LAW
LEVEL: L0
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
OWNER: SYSTEM
ROLE: Верховный закон системы. Определяет что такое канон, что считается источником истины (SoT), как устроены слои, и какие правила обязательны везде.

---

## 0) PURPOSE (CORE)
Этот документ фиксирует базовые принципы:
- как устроена система слоёв (LAW → STANDARDS → ENTITIES → KB/PROJECTS/ASSETS/OUT)
- что считается “существующим” в системе
- что такое Source of Truth (SoT)
- какая иерархия правил действует при конфликте
- какие требования обязательны для всех документов и сущностей

---

## 1) LAYERS (CANON MAP)
Система разделена на слои:

1) SYSTEM LAW — верховные законы (что такое канон и как жить системе)
2) STANDARDS — стандарты форматов/маркировок/процессов (как именно делать)
3) SYSTEM ENTITIES (ENT) — движки/оркестраторы/спецы/контроллеры/валидаторы/QA (кто делает)
4) KNOWLEDGE BASE (KB) — знания/правда/справочники/выжимки (что знаем)
5) PROJECTS (PRJ) — рабочие материалы и сборка продукта (что делаем сейчас)
6) ASSETS (AST) — медиа-артефакты (изображения/звук/видео/модели и т.д.)
7) OUTPUT (OUT) — финальные результаты (книга/серия/видео/игра)
8) DATABASES (DB) — структурные базы/таблицы/хранилища
9) LOGS — журналы изменений/решений/проверок

---

## 2) SOURCE OF TRUTH (SoT) LAW
### 2.1 Single SoT Rule
Для каждого типа правил/реестра существует ровно один Source of Truth (SoT) файл.
Любые копии/дубли считаются неканоном.

### 2.2 SoT Marking
SoT документ обязан иметь в шапке:
- LEVEL
- STATUS
- LOCK
- VERSION
- OWNER
- ROLE

---

## 3) EXISTENCE RULE (ABSOLUTE)
> Если элемент/сущность/документ не зарегистрирован в своём каноническом INDEX — он не существует для системы.

Применяется ко всем слоям:
- LAW / STANDARDS / ENT / KB / PRJ / AST / OUT / DB / LOGS

---

## 4) INDEX LAW (NAVIGATION)
INDEX — это закон навигации.
INDEX обязан содержать:
- строгий порядок (по номеру)
- канонический путь
- (если в репо) raw-ссылку на файл

Запрещено:
- “молчаливые файлы” без регистрации в индексах
- ссылки без смысла (без названия/номера/контекста)

---

## 5) AUTHORITY ORDER (CONFLICT RESOLUTION)
При конфликте правил действует порядок:

1) SYSTEM LAW (этот слой)
2) CANON PROTOCOL (как меняется канон)
3) VERSIONING/CHANGE POLICY
4) STANDARDS (SoT документы)
5) ENT RULES (ruleset соответствующей группы)
6) PROJECT/KB локальные правила (если не противоречат вышестоящим)

---

## 6) UNIVERSAL REQUIREMENTS (MANDATORY FOR ALL)
Любой документ, который считается частью системы, обязан иметь:
- валидное имя по Naming Rules
- валидную шапку (STATUS/LOCK/VERSION/OWNER/ROLE)
- регистрацию в индексе своего слоя (Existence Rule)
- корректные ссылки и связи (XREF/REL policy)
- если это ENT: mini-contract (consumes/produces/depends_on/output_target)

---

## 7) NO HIDDEN MECHANICS (ANTI-CHAOS)
Запрещено:
- скрытые зависимости (depend without mention)
- скрытые правила (“мы так договорились в чате” без фиксации в SoT)
- неявные форматы (если формат используется — он обязан быть стандартом)

---

## 8) CHANGE LAW (HIGH LEVEL)
Любое изменение канона:
- фиксируется через Canon Protocol
- имеет версию
- имеет причину и следствие (impact)
- не ломает совместимость без явного объявления breaking change

---

## 9) FINAL LAW (LOCK)
> Система управляется правилами и индексами, а не “памятью” и “догадками”.

OWNER: Universe Engine  
LOCK: FIXED

---
END.
