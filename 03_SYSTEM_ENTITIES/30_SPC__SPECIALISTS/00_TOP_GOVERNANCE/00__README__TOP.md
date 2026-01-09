# SPC FAMILY REALM — TOP GOVERNANCE (CANON)
FILE: 03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/00__README__TOP.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: SPECIALISTS (SPC)
DOC_TYPE: README
INDEX_TYPE: FAMILY_REALM
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.SPC.REALM.TOP.001
OWNER: SYSTEM
ROLE: Family realm definition + boundaries + governance authority for SPC family `00_TOP_GOVERNANCE`

CHANGE_NOTE:
- DATE: 2026-01-09
- TYPE: MAJOR
- SUMMARY: "Established TOP Governance SPC family realm: boundaries, authority chain, interfaces, and creation gates."
- REASON: "Need deterministic governance layer specialists for canon, standards, pipelines, and integration packaging."
- IMPACT: "Top governance roles become explicit, non-overlapping, and audit-compatible."
- CHANGE_ID: UE.CHG.2026-01-09.SPC.REALM.TOP.001

---

## 0) PURPOSE (LAW)
Это семейство определяет **верхний контур управления Universe Engine**.

`00_TOP_GOVERNANCE` отвечает за:
- архитектурные инварианты системы (границы слоёв / интерфейсы / стыки)
- власть канона (как принимаются изменения, что считается существующим)
- стандарты (форматы, маркировка, naming/uid/status/lock)
- doc-control (гигиена документов и индексов, борьба с drift)
- пайплайны (как строятся и исполняются цепочки ENG↔SPC↔VAL/QA)
- интеграционную упаковку (как выдача становится применимой без “копания”)

---

## 1) EXISTENCE + NAV RULE (MANDATORY)
- SPC-специалист существует для системы **только если**:
  1) зарегистрирован в глобальном реестре SPC:
     `03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/02__INDEX_ALL_SPECIALISTS.md`
  2) и файл специалиста лежит по каноническому пути
- Любые файлы в папке без регистрации в глобальном SPC INDEX — **NON-CANON / ignored**
- Навигация по SPC слою считается каноничной **только через RAW-ссылки глобального SPC INDEX**

---

## 2) FAMILY SCOPE
**FAMILY NAME:** TOP GOVERNANCE  
**FAMILY PATH:** `03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/`  
**WHO THIS FAMILY IS FOR:** управление каноном, стандартами, контролем документов и производственным контуром системы.

### 2.1 Covered domains (what we DO)
- Canon / System Law / Authority
- Standards / Marking / Naming / UID rules
- Doc-control enforcement (структура, индексы, версии, статусы)
- Pipeline architecture (handoffs, gates, targets, orchestration)
- Cross-layer stitching (ENG / ORC / SPC / CTL / VAL / QA / KB / PRJ / OUT / AST)
- Integration packaging (output packs)

### 2.2 Hard boundaries (what we DO NOT do)
- Не создаём доменный контент мира/сюжета/персонажей как “творчество” (это DOMAIN SPC семьи).
- Не заменяем валидаторы (VAL) и QA-гейты: мы задаём требования, но не “делаем проверку за них”.
- Не допускаем “скрытых правил”: любое правило должно быть выражено документом/индексом/стандартом.

---

## 3) AUTHORITY CHAIN (WHO DECIDES WHAT)
Внутри семьи действует цепочка власти (anti-chaos):

- `MACHINE ARCHITECT` — архитектурные инварианты, границы, интерфейсы слоёв
- `GOVERNANCE OWNER` — утверждение/отклонение канон-изменений (решение “в закон / не в закон”)
- `STANDARDS OWNER` — стандарты формата/маркировки/шаблонов
- `DOC CONTROLLER` — контроль соответствия стандартам и устранение drift
- `PIPELINE ARCHITECT` — формализация пайплайнов и handoff-правил
- `INTEGRATION PACKER` — упаковка результатов в применимые пакеты

---

## 4) DEFAULT OUTPUT PHILOSOPHY
**Default mindset:** CONSTRAIN + STRUCTURE  
**Primary quality priority:** Canon safety → determinism → auditability → clarity  
**Typical outputs:** правила, индексы, реестры, протоколы, карты зависимостей/пайплайнов, интеграционные пакеты.

---

## 5) INTERFACES (SYSTEM LINKS)
### 5.1 ENG (Engines)
TOP Governance SPC чаще всего взаимодействует с:
- `03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/*` (audit/change/authority/dependency)
- `03_SYSTEM_ENTITIES/10_ENG__ENGINES/01_CORE_ENGINES/*` (identity/state/lifecycle framing)
- `03_SYSTEM_ENTITIES/10_ENG__ENGINES/10_META_EVOLUTION_ENGINES/*` (evolution only through governance gates)

### 5.2 ORC (Orchestrators)
ORC обязан вызывать TOP SPC когда:
- создаётся/меняется индекс, реестр, entrypoint, правило существования
- добавляется новый класс сущностей / новый слой / новое семейство
- меняются naming/uid/status/lock правила
- строится/меняется пайплайн производства артефактов
- требуется выдача “готовым пакетом” (integration output)

### 5.3 VAL / QA (Gates)
TOP Governance задаёт обязательные гейты для принятия изменений:
- Consistency / dependency sanity
- Doc-control compliance (формат/структура/версия/статус/lock)
- При необходимости: Language/Naturalness (если затронут язык) и Fact/Logic (если есть факто-утверждения)

---

## 6) FAMILY STANDARDS (MANDATORY RULES)
### 6.1 Anti-duplication (SoT discipline)
- Один закон → одна точка истины (SoT).
- Любые “дубли entrypoint/индексов” допускаются только как POINTER на SoT.

### 6.2 Determinism
- Любая структура/порядок/существование фиксируются индексом.
- Любые зависимости фиксируются явно (никаких “скрытых”).

### 6.3 Change discipline
- Любая канон-правка должна быть оформлена как изменение с CHANGE_NOTE и проходить governance-пайплайн.
- Любые изменения индексов и структуры должны быть аудируемы.

---

## 7) WHEN TO CREATE A NEW TOP SPECIALIST (GATE)
Новый специалист в `00_TOP_GOVERNANCE` создаётся **только если**:
- появляется новая “ось власти” (новый слой, новый контур контроля, новый класс сущностей)
- появляется новая обязательная дисциплина контроля, которую нельзя встроить в текущие роли без размывания границ
- возникает повторяющийся тип решений, который сейчас не имеет владельца

Создание “на всякий случай” запрещено.

---

## 8) FAMILY NAV — SPECIALISTS (ORDER IS LAW)
01 — MACHINE ARCHITECT  
02 — GOVERNANCE OWNER  
03 — STANDARDS OWNER  
04 — DOC CONTROLLER  
05 — PIPELINE ARCHITECT  
06 — INTEGRATION PACKER  

---

## FINAL RULE (LOCK)
Этот README задаёт **границы и власть** семьи `00_TOP_GOVERNANCE`.  
Нарушение границ ролей считается ошибкой канона.

--- END.
