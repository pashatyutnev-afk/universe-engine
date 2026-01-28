# SPC FAMILY REALM — WORLD SPECIALISTS (CANON)
FILE: 03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/04_WORLD/00__README_WORLD_SPECIALISTS.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: SPECIALISTS (SPC)
DOC_TYPE: README
INDEX_TYPE: FAMILY_REALM
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.SPC.REALM.WORLD.001
OWNER: SYSTEM
ROLE: Family realm definition + boundaries + navigation rules for SPC family `04_WORLD`

CHANGE_NOTE:
- DATE: 2026-01-09
- TYPE: MAJOR
- SUMMARY: "Established WORLD SPC family realm: purpose, boundaries, interfaces, quality rules, and creation gates."
- REASON: "Need deterministic world layer: coherent world logic, cultures, civilizations, geography, ecology, and myth systems aligned with narrative and canon."
- IMPACT: "World becomes a stable system that can be referenced safely by story, characters, and production."
- CHANGE_ID: UE.CHG.2026-01-09.SPC.REALM.WORLD.001

---

## 0) PURPOSE (LAW)
Семейство `04_WORLD` отвечает за мир как систему:
- фундаментальный каркас мира (что это за мир и как он “собран”)
- культуры и общества
- цивилизации и их развитие
- география и локационная логика
- экономика/ресурсы/энергия и системы власти (в рамках канона проекта)
- религии/мифы как мировые структуры
- экология/выживание/среда и её давление на жизнь

Цель семьи — сделать мир **логичным, непротиворечивым и пригодным для использования** в сценах, персонажах и продакшне.

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
**FAMILY NAME:** WORLD SPECIALISTS  
**FAMILY PATH:** `03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/04_WORLD/`

### 2.1 Covered domains (what we DO)
- World building system (структура мира)
- Culture & society (нормы, институты, быт, ценности как система)
- Civilizations (рост/упадок, стадии, взаимодействия)
- Geography & locations (пространственная логика, зоны, климатические/гео-факторы)
- Economy & power systems (ресурсы, энергия, контроль, инфраструктура) — **без валюты у великих цивилизаций**
- Religion & mythology (верования как система смыслов и практик)
- Ecology & survival (среда, угрозы, адаптация, пищевые цепи)

### 2.2 Hard boundaries (what we DO NOT do)
- Не владеем нарративной структурой и сценами (это `02_NARRATIVE`), но даём ограничения и “что возможно”.
- Не владеем персонажной психологией/отношениями (это `03_CHARACTER` и `08_PSYCHOLOGY`), но даём условия мира.
- Не владеем художественным стилем/атмосферой (это `01_CREATIVE`), но даём материальную/социальную основу.
- Не делаем фактчекинг реального мира как метод (это `09_RESEARCH` + VAL), но можем давать гипотезы/правдоподобие.
- Не утверждаем канон в одиночку (TOP Governance + change pipeline).

---

## 3) DEFAULT OUTPUT PHILOSOPHY
**Default mindset:** DEFINE LAWS → MAP SYSTEMS → TEST IN SCENES → STABILIZE  
**Primary quality priority:** coherence → constraints clarity → usability  
**Default outputs:**
- world law constraints (что возможно/нельзя)
- civilization & culture maps
- geography logic and location rules
- resource/power system maps
- myth/religion system notes
- ecology/survival pressure rules

---

## 4) INTERFACES (SYSTEM LINKS)
### 4.1 ENG (Engines) — typical support
- `04_DOMAIN_WORLD_ENGINES/*` (world structure/law/timeline/civ/economy/tech/ecology)
- `02_DOMAIN_NARRATIVE_ENGINES/*` (когда сцена зависит от законов мира)
- `03_DOMAIN_CHARACTER_ENGINES/*` (когда мотивации завязаны на среду/общество)
- `05_EXPRESSION_ENGINES/*` (конфликты/события как проявление систем мира)

### 4.2 ORC (Orchestrators) — typical usage
ORC вызывает WORLD SPC когда нужно:
- определить правила мира и ограничения
- построить культуры/цивилизации
- создать географическую/локационную логику
- определить системы ресурсов/власти
- создать религию/миф как работающую систему
- определить экологическое давление и выживание

### 4.3 VAL / QA (Gates)
Типовые гейты:
- consistency sanity (нет противоречий между системами мира)
- plausibility (внутренняя правдоподобность в рамках законов мира)
- doc-control (если фиксируется как канон-правило)
- lore continuity (через Lore Master при использовании в истории)

---

## 5) FAMILY STANDARDS (MANDATORY RULES)
### 5.1 Anti-overlap (role separation)
- World Builder: общий каркас мира и система “что это за мир”.
- Culture & Society Architect: нормы/институты/социальная структура.
- Civilization Designer: цивилизационные траектории и взаимодействия.
- Geography & Location Designer: пространство и локационная логика.
- Economy & Power Systems Designer: ресурсы/энергия/контроль/власть (с учётом канона).
- Religion & Mythology Designer: миф/вера как система смысла и практик.
- Ecology & Survival Designer: экология/давление среды/адаптация.

### 5.2 Constraint discipline (world laws first)
- Любая деталь мира должна быть:
  - совместима с законами мира
  - выражена через ограничения (что возможно/что нет)
  - пригодна для сцены (как проявляется)

### 5.3 Canon note (project law)
- Великие цивилизации во вселенной проекта **не используют валюту**.
- Если появляются элементы “валюты/денег” — это либо низшие/локальные общества, либо заменяется иной системой (ресурс/долг/обязательства/энергия/репутация/квоты).

---

## 6) WHEN TO CREATE A NEW WORLD SPECIALIST (GATE)
Новый WORLD SPC создаётся только если:
- появляется стабильный тип задач, который не закрывается текущими 7 ролями
- нужен отдельный контракт/гейты (например “tech-magic integration” как отдельная роль)
- роль становится постоянной дырой в пайплайнах

---

## 7) FAMILY NAV — SPECIALISTS (ORDER IS LAW)
01 — WORLD BUILDER  
02 — CULTURE & SOCIETY ARCHITECT  
03 — CIVILIZATION DESIGNER  
04 — GEOGRAPHY & LOCATION DESIGNER  
05 — ECONOMY & POWER SYSTEMS DESIGNER  
06 — RELIGION & MYTHOLOGY DESIGNER  
07 — ECOLOGY & SURVIVAL DESIGNER  

---

## FINAL RULE (LOCK)
Этот README задаёт границы семьи `04_WORLD`.  
Мир обязан быть системой с законами и ограничениями; иначе любые сцены и лор будут дрейфовать и противоречить друг другу.

--- END.
