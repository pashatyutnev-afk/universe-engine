# ARCHITECTURE OVERVIEW (UNIVERSE ENGINE)
FILE: 02_STANDARDS/00_CANON/01__ARCHITECTURE_OVERVIEW.md

SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: CANON_REFERENCE
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.CANON.ARCH.OVERVIEW.001
OWNER: SYSTEM
ROLE: Canonical architecture overview: layers, entrypoints, authority, and build order (system map)

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Архитектура нормализована: один обзор системы с жёсткими entrypoints и порядком построения канона"
- REASON: "Нужно единое представление системы до переписывания движков/сущностей/KB"
- IMPACT: "Навигация и порядок разработки всего репозитория"

---

## 0) PURPOSE
Этот документ объясняет **как устроен Universe Engine**:
- какие есть слои (layers) и за что они отвечают
- где находятся **официальные входные точки** (entrypoints)
- какой порядок “строительства” канона считается правильным

Это обзор. Он **не заменяет** законы и стандарты.

---

## 1) LAYERS (SYSTEM MAP)

### 00_INDEX (Repo entry)
Назначение: вход в репозиторий и карта дерева.

### 01_SYSTEM_LAW (Highest Authority)
Назначение: законы системы (что считается каноном, как изменяется, как именуется, как версиями управлять).

**Правило:** если в SYSTEM_LAW сказано иначе — этот документ подчиняется.

### 02_STANDARDS (How it must be)
Назначение: спецификации, протоколы, технические шаблоны, термины.
Это “инженерные правила изготовления документов/сущностей/пайплайнов”.

### 03_SYSTEM_ENTITIES (System actors)
Назначение: системные сущности (ENG/ORC/SPC/CTL/VAL/QA), их реестры, шаблоны и внутренние контракты.

### 04_KNOWLEDGE_BASE (Knowledge realms)
Назначение: база знаний по ремеслу (нарратив, персонажи, визуал, звук и т.п.).
KB — это контент-знание, а не законы системы.

### 05_PROJECTS (Project layer)
Назначение: проекты/воркшоп/интейк/канонизация проекта/выходные артефакты.

### 06_ASSETS (Assets governance)
Назначение: артефакты производства (изображения/видео/звук/и т.п.) и их управляемость.

### 08_DATABASES (Reference DB)
Назначение: таблицы-справочники (типы сущностей, типы документов и т.п.) как “машиночитаемая” опора.

### 99_LOGS (Audit/Change history)
Назначение: след изменений, журнал канона.

---

## 2) CANON PRINCIPLE (CORE IDEA)
Канон существует только там, где:
1) есть **master-index слоя** (existence rule)
2) документ соответствует **Doc Control**
3) соблюдён **naming с номером NN__**
4) нет дубля смысла (SoT строго один)

Если что-то “лежит в репо”, но не проходит правила — это **ошибка/мусор/вне канона**.

---

## 3) OFFICIAL ENTRYPOINTS (WHERE TO START)

### System Law entry
- `01_SYSTEM_LAW/00__SYSTEM_LAW.md`
- `01_SYSTEM_LAW/00__INDEX__SYSTEM_LAW.md`

### Standards entry
- `02_STANDARDS/00__INDEX__STANDARDS.md`

### Entities entry
- `03_SYSTEM_ENTITIES/00__README__SYSTEM_ENTITIES.md`
- `03_SYSTEM_ENTITIES/02__INDEX__SYSTEM_ENTITIES.md`

### Knowledge Base entry
- `04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md`

---

## 4) BUILD ORDER (HOW WE BUILD FROM ZERO)
Правильный порядок укрепления фундамента:

S0 (foundation, mandatory):
1) SYSTEM_LAW (existence / canon / naming / uid / versioning)
2) STANDARDS (Doc Control / Index template / Entity passport / Terms)
3) Layer indexes (master-index каждого слоя)

S1 (system actors):
4) SYSTEM_ENTITIES: шаблоны и реестры, потом уже переписывание ENG/ORC/SPC/...

S2 (content knowledge):
5) KNOWLEDGE_BASE: реалмы приводятся к Doc Control + нумерации, затем наполнение

S3 (projects/outputs):
6) PROJECTS + ASSETS + OUTPUT pipelines

---

## 5) NAMING POLICY (OVERVIEW)
Общее правило:
- файлы внутри канона имеют префикс `NN__` (или `00__` для README/entrypoint по стандарту слоя)
- файлы без номера **не допускаются**
- один смысл → один SoT документ; остальное — ссылки/REL/XREF

---

## FINAL RULE (LOCK)
LOCK: FIXED
--- END.
