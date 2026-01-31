# CORE ENGINES — REALM (README) (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/01_CORE_ENGINES/00__README__CORE_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: README_REALM
FAMILY: 01_CORE_ENGINES
CLASS: CORE (L1)
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.ENG.CORE.REALM.001
OWNER: SYSTEM
ROLE: Defines what CORE engines are, their strict boundaries, the family navigation law, and how CORE integrates with governance and other engine families without duplication.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "CORE family realm fixed: purpose/scope/boundaries, anti-duplication law, engine map, add/change procedure, S0 blockers."
- REASON: "Stop drift and conflicting definitions of identity/state/lifecycle across layers."
- IMPACT: "CORE becomes a stable prerequisite layer for all other families."
- CHANGE_ID: UE.CHG.2026-01-08.CORE.REALM.001

---

## 0) PURPOSE (LAW)

CORE engines — это фундаментальные движки, которые определяют **минимальные базовые примитивы** системы.

CORE гарантирует:
- единый смысл “кто/что существует” как системная сущность (identity primitives)
- единый смысл “какое состояние считается текущим” (state primitives)
- единый смысл “как сущность живёт и меняется” (lifecycle primitives)
- минимальные инварианты, на которые опираются все остальные слои и семьи

Non-goals (жёстко):
- CORE **не** устанавливает власть/правки канона/аудит/аппрувалы (это GOVERNANCE)
- CORE **не** занимается повествованием/миром/персонажами (это DOMAIN семьи)
- CORE **не** занимается продакшеном медиа/форматами/артом (это PRODUCTION семьи)
- CORE **не** является проектным документом (не про конкретный мир/сериал/проект)

---

## 1) SCOPE (STRICT)

IN SCOPE (что CORE имеет право определять):
- минимальный системный словарь: identity / state / lifecycle как базовые понятия
- минимальные инварианты, которые нельзя нарушать другим семьям без эскалации
- базовые требования к “ядру” сущностей (без доменных деталей)

OUT OF SCOPE (запрещено дублировать):
- процедуры изменения канона, approvals, audit/memory, dependency registry rules
- стандарты оформления документов (если они определены в STANDARDS и GOVERNANCE)
- доменные правила сцены/драматургии/характеров/мира
- правила продакшена и генерации артефактов (визуал/видео/звук)

---

## 2) BOUNDARIES (ANTI-DUPLICATION LAW)

CORE — это **инварианты**, а не “процесс”.

Если вопрос:
- “кто имеет право менять канон / как проходит правка / как фиксируем лог” → GOVERNANCE
- “как строить историю, сцены, напряжение, ритм” → DOMAIN NARRATIVE / EXPRESSION
- “как делать визуал/монтаж/звук под выпуск” → KNOWLEDGE PRODUCTION / SOUND & MUSIC
- “как устроен конкретный мир/цивилизация/персонаж” → соответствующие DOMAIN семьи

Правило столкновений:
- CORE формулирует **минимальный инвариант** (например: “сущность имеет UID и статус”),
  а все процессы и контроль соблюдения инварианта делегируются в GOVERNANCE и VALIDATION.

---

## 3) WHAT IS A “CORE ENGINE” (DEFINITION)

CORE engine — это ENG-движок L1, который:
- определяет базовую системную модель (identity/state/lifecycle)
- производит стабильные выходы, используемые другими семьями как prereq
- **не** пытается поглотить домены, продакшен или власть канона

Правило:
- CORE outputs должны быть **ссылочными** (на них ссылаются), а не “переопределяемыми копиями”.

---

## 4) FAMILY NAVIGATION (ENGINE MAP) (MANDATORY)

**Family Path:**
`03_SYSTEM_ENTITIES/10_ENG__ENGINES/01_CORE_ENGINES/`

🧩 **TEMPLATES (RAW ONLY):**
- ENGINE TEMPLATE — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/01_CORE_ENGINES/00__TEMPLATE__ENGINE__CORE_ENGINES.md
- README TEMPLATE — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/01_CORE_ENGINES/00__TEMPLATE__README__CORE_ENGINES.md

📌 **ENGINES (STRICT ORDER):**
01 — Core Identity Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/01_CORE_ENGINES/01__CORE_IDENTITY_ENG.md  
02 — Core State Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/01_CORE_ENGINES/02__CORE_STATE_ENG.md  
03 — Core Lifecycle Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/01_CORE_ENGINES/03__CORE_LIFECYCLE_ENG.md  

Naming law:
- Номер в списке == номер в имени файла == номер в INDEX_ALL_ENGINES.

---

## 5) HOW TO ADD / CHANGE A CORE ENGINE (MANDATORY)

### 5.1 Add new CORE engine (strict procedure)
1) Сначала зарегистрировать движок в:
   `03_SYSTEM_ENTITIES/10_ENG__ENGINES/02__INDEX_ALL_ENGINES.md`
2) Создать файл движка строго из ENGINE TEMPLATE.
3) Заполнить MINI-CONTRACT конкретикой (CONSUMES/PRODUCES/DEPENDS_ON/OUTPUT_TARGET).
4) Если появились зависимости — внести записи в Dependency Registry Engine.
5) Если затрагивается канон (ACTIVE/FIXED, индексы, законы) — пройти Change Control pipeline.

### 5.2 Change existing ACTIVE/FIXED CORE engine
- Любая правка — только через Change Control Engine.
- Никаких “тихих правок”, особенно для LOCK: FIXED.

---

## 6) DEPENDENCIES (EXPECTED SYSTEM STITCH)

CORE ожидаемо стыкуется с GOVERNANCE, но не дублирует его:

- Change Control → управляет изменениями CORE
- Canon Authority → утверждает CORE как канон
- Audit Log + Versioning Memory → фиксируют историю CORE
- Consistency → проверяет структуру, индексы, UID, номера, ссылки
- Dependency Registry → делает зависимости явными

CORE может ссылаться на governance движки raw-ссылками, но не копирует их правила.

---

## 7) INTEGRATION (HOW OTHER FAMILIES USE CORE)

Другие семьи обязаны:
- потреблять CORE как prereq (identity/state/lifecycle)
- ссылаться на CORE определения, а не создавать конкурирующие “single source of truth”
- расширять доменными правилами, не ломая CORE инварианты

Если расширение ломает CORE инвариант → это S0 blocker и эскалация в GOVERNANCE.

---

## 8) S0 BLOCKERS (STOP CONDITIONS)

S0-1 Любой ACTIVE документ вводит конкурирующее “ядро” identity/state/lifecycle как single source of truth.  
S0-2 Любой ACTIVE документ противоречит CORE инварианту без явного протокола override/эскалации.  
S0-3 Любая правка CORE (или списка CORE в индексах) сделана без audit + memory, когда это обязательно.  
S0-4 Нарушена нумерация/пути/UID правила для CORE движков или README.

---

## 9) REFERENCES (RAW ONLY) (OPTIONAL)

- Global ENG registry:
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/02__INDEX_ALL_ENGINES.md
- Change Control (Governance):
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md
- Dependency Registry (Governance):
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/06__DEPENDENCY_REGISTRY_ENG.md

--- END.

OWNER: SYSTEM
LOCK: FIXED
