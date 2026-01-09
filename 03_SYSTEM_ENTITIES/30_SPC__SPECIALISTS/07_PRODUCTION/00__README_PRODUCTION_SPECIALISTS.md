# SPC FAMILY REALM — PRODUCTION SPECIALISTS (CANON)
FILE: 03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/07_PRODUCTION/00__README_PRODUCTION_SPECIALISTS.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: SPECIALISTS (SPC)
DOC_TYPE: README
INDEX_TYPE: FAMILY_REALM
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.SPC.REALM.PRODUCTION.001
OWNER: SYSTEM
ROLE: Family realm definition + boundaries + navigation rules for SPC family `07_PRODUCTION`

CHANGE_NOTE:
- DATE: 2026-01-09
- TYPE: MAJOR
- SUMMARY: "Established PRODUCTION SPC family realm: responsibilities, boundaries, KB scope, interfaces, quality rules, and delivery handoffs."
- REASON: "Need deterministic production ownership: executive producing, directing, content producing, transmedia, planning, adaptation, localization, release, and scheduling."
- IMPACT: "Production becomes controllable: clear owners, reliable handoffs, fewer gaps between creative intent and shipped outputs."
- CHANGE_ID: UE.CHG.2026-01-09.SPC.REALM.PRODUCTION.001

---

## 0) PURPOSE (LAW)
Семейство `07_PRODUCTION` отвечает за производство и выпуск как систему:
- управление производственным уровнем (ресурсы, решения, ограничения)
- режиссура (сцена/исполнение/постановка как реализация)
- контент-продюсирование (сбор артефактов и контроль готовности)
- трансмедиа (единая сеть выпусков)
- планирование эпизодов/глав (разбиение и порядок выпуска)
- адаптация под платформы (форматы и ограничения)
- локализация (переводы и культурные требования)
- релиз-менеджмент (выпуск, пакеты, версии)
- расписание (план-график и зависимости)

Цель семьи — “доставить” продукт: чтобы идеи превратились в **готовые артефакты** в нужной форме, в срок и без разрушения канона/качества.

---

## 1) EXISTENCE + NAV RULE (MANDATORY)
- Специалист существует для системы **только если**:
  1) зарегистрирован в глобальном SPC INDEX:
     `03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/02__INDEX_ALL_SPECIALISTS.md`
  2) и файл лежит по каноническому пути
- Любые файлы в папке без регистрации — **NON-CANON / ignored**
- Каноническая навигация по семье — через RAW ссылки глобального SPC INDEX

---

## 2) FAMILY SCOPE
**FAMILY NAME:** PRODUCTION SPECIALISTS  
**FAMILY PATH:** `03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/07_PRODUCTION/`

### 2.1 Covered domains (what we DO)
- Production governance (exec producing)
- Direction (scene execution)
- Content production management (assets, packages, readiness)
- Transmedia production (multi-platform coherence)
- Episode/chapter planning (release structure)
- Platform adaptation (format constraints)
- Localization management (language/culture delivery)
- Release management (versioned release packages)
- Schedule coordination (timeline + dependencies)

### 2.2 Hard boundaries (what we DO NOT do)
- Мы не пишем канон мира (это `04_WORLD` + lore/governance).
- Мы не заменяем Narrative/Character/World специалистов — мы **упаковываем и доставляем** их результаты.
- Мы не владеем “как звучит” (это `06_SOUND_MUSIC`) и “как выглядит” (это `05_VISUAL`), но координируем deliverables.
- Мы не принимаем монтажных решений за `Editing/Montage` — только управление рисками/ограничениями и выпуск артефактов.

---

## 3) KNOWLEDGE BASE (KB) SCOPE (MANDATORY)
### 3.1 KB INPUTS
- Production Pipeline realm  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/05__PRODUCTION_PIPELINE.md
- Marketing & Distribution realm (релизные рамки, если нужно)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/06__MARKETING_DISTRIBUTION.md
- Reference Glossary  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/07__REFERENCE_GLOSSARY.md

### 3.2 KB OUTPUTS
- Стандартизация “release package”, “readiness checks”, “handoff protocols” как чеклисты.
- Практики “platform adaptation constraints” и “localization QA”.

### 3.3 KB BOUNDARIES
- Не владеем креативными знаниями профессий (это их SPC семьи), но фиксируем производственные стандарты.

---

## 4) INTERFACES (SYSTEM LINKS) — RAW ONLY
### 4.1 ENG (Engines) — typical support
- Production format engines (book/series/short/youtube/game)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/07_PRODUCTION_FORMAT_ENGINES/00__README__PRODUCTION_FORMAT_ENGINES.md
- Knowledge production engines (image/video/editing/sound placement)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/08_KNOWLEDGE_PRODUCTION_ENGINES/00__README__KNOWLEDGE_PRODUCTION_ENGINES.md
- Governance engines (change control / audit / versioning)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/00__README__GOVERNANCE_ENGINES.md

### 4.2 ORC — typical usage
ORC вызывает PRODUCTION SPC когда нужно:
- зафиксировать производство как план/пакеты (Content Producer, Release Manager)
- принять исполнительские решения сцены (Director) в рамках канона
- спланировать эпизоды/главы (Episode-Chapter Planner)
- адаптировать под платформу (Platform Adaptation Specialist)
- локализовать (Localization Manager)
- собрать и выпустить версию (Release Manager)
- держать сроки и зависимости (Schedule Coordinator)
- держать бюджет/ресурсы/решения (Executive Producer)
- держать трансмедиа связность (Transmedia Producer)

### 4.3 QA / VAL gates
Типовые гейты:
- readiness (все артефакты на месте?)
- versioning/packaging sanity (версии и названия корректны?)
- canon safety (ничего не ломает канон?)
- platform compliance (форматы подходят?)
- localization sanity (перевод не ломает смысл?)

---

## 5) FAMILY STANDARDS (MANDATORY RULES)
### 5.1 Anti-overlap (role separation)
- Executive Producer: ресурсы/решения/границы производства.
- Director: постановка сцен (исполнение/стейджинг) в рамках готового смысла.
- Content Producer: сбор артефактов и readiness.
- Transmedia Producer: целостность выпусков между платформами.
- Episode-Chapter Planner: структура выпуска (главы/эпизоды/порядок).
- Platform Adaptation Specialist: адаптация под формат и ограничения.
- Localization Manager: перевод/локализация/культурные риски.
- Release Manager: релизные пакеты/версии/выкладка.
- Schedule Coordinator: календарь/зависимости/ритм производства.

### 5.2 Delivery law
Если артефакт не:
- упакован (package)
- версионирован (version tag)
- проверен (readiness)
то он **не считается существующим для выпуска**, даже если “контент готов”.

### 5.3 Non-editing decision boundary
PRODUCTION не принимает монтажных решений “как склеить кадры”.
Мы выдаём только:
- ограничения (constraints)
- риски (risks)
- требования синхрона/длины (requirements)

---

## 6) WHEN TO CREATE A NEW PRODUCTION SPECIALIST (GATE)
Новый PRODUCTION SPC создаётся только если:
- появляется устойчивый тип задач, не закрытый текущими 9 ролями
- нужен отдельный контракт (например “Legal/rights manager”)
- роль становится постоянной дырой в выпуске

---

## 7) FAMILY NAV — SPECIALISTS (ORDER IS LAW)
01 — EXECUTIVE PRODUCER  
02 — DIRECTOR  
03 — CONTENT PRODUCER  
04 — TRANSMEDIA PRODUCER  
05 — EPISODE / CHAPTER PLANNER  
06 — PLATFORM ADAPTATION SPECIALIST  
07 — LOCALIZATION MANAGER  
08 — RELEASE MANAGER  
09 — SCHEDULE COORDINATOR  

---

## FINAL RULE (LOCK)
Этот README задаёт границы семьи `07_PRODUCTION`.  
Если нет readiness, packaging и versioning дисциплины — выпуск не считается контролируемым и не проходит аудит.

--- END.
