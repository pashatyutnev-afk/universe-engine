# SYSTEM STANDARDS INDEX
00__INDEX.md

SCOPE: Universe Engine
TYPE: Canonical Standards Registry
LEVEL: L0 (Above all systems)
STATUS: FINAL
ROLE: Single source of system rules, definitions and protocols

---

## PURPOSE

Папка `_STANDARDS` содержит **абсолютные правила**, по которым существует и развивается Universe Engine.

Эти документы:
- не обсуждаются
- не интерпретируются
- не переопределяются движками, специалистами или проектами
- используются как **закон** всей системы

Если правило не описано здесь —  
оно **не считается существующим**.

---

## STANDARDS STRUCTURE

### 00_CANON
**Назначение:** философский и системный фундамент  
**Уровень:** L0 — абсолютный

Документы:
- `SYSTEM_CANON.md`  
  → что такое Universe Engine, его границы и принципы
- `ARCHITECTURE_OVERVIEW.md`  
  → общая архитектура системы, уровни, сущности, связи

---

### 01_SPECIFICATIONS
**Назначение:** формальные определения и схемы  
**Уровень:** L0–L1

Документы:
- `UID_AND_MARKING_SPEC.md`  
  → правила маркировки папок, файлов, сущностей, движков
- `ENTITY_MODEL_SPEC.md`  
  → что такое сущность, её поля, роли и жизненный цикл
- `INDEX_STRUCTURE_SPEC.md`  
  → как строятся INDEX-файлы и как они связывают систему

---

### 02_PROTOCOLS
**Назначение:** правила взаимодействия и изменений  
**Уровень:** L1

Документы:
- `CHAT_PROTOCOL.md`  
  → как ИИ и человек работают через чаты и INDEX
- `CHANGE_MANAGEMENT_PROTOCOL.md`  
  → как вносятся изменения без разрушения системы

---

### 03_TECHNICAL_TEMPLATES
**Назначение:** унифицированные шаблоны  
**Уровень:** L1–L2

Документы:
- `ENTITY_PASSPORT_TEMPLATE.md`  
  → паспорт любой сущности (движок, спец, модель)
- `INDEX_TEMPLATE.md`  
  → шаблон любого INDEX-файла

---

### 04_TERMS_DEFINITIONS
**Назначение:** единый язык системы  
**Уровень:** L0

Документы:
- `GLOSSARY.md`  
  → определения всех терминов, используемых в системе

---

## ABSOLUTE RULES

1. `_STANDARDS` выше любых движков, проектов и баз знаний  
2. Движки **не могут** менять или трактовать стандарты  
3. Все INDEX-файлы **обязаны** ссылаться на стандарты  
4. Любое нарушение стандартов = системная ошибка  

---

## RELATION TO OTHER PARTS

- `_ENGINES` → подчиняются стандартам  
- `_SPECIALISTS` → действуют в рамках стандартов  
- `_PROJECTS` → используют стандарты как контракт  
- `INDEX__UNIVERSE_ENGINE.md` → ссылается на этот пакет

---

## FINAL PRINCIPLE

> STANDARD ≠ DOCUMENT  
> STANDARD = LAW

---

STATUS: LOCKED  
CHANGES: ONLY VIA CHANGE_MANAGEMENT_PROTOCOL  
OWNER: Universe Engine
