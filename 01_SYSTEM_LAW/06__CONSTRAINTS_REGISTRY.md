# CONSTRAINTS REGISTRY — HARD LIMITS (CANON)
FILE: 01_SYSTEM_LAW/06__CONSTRAINTS_REGISTRY.md

SCOPE: Universe Engine
LAYER: 01_SYSTEM_LAW
DOC_TYPE: REGISTRY
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.REG.CONSTRAINTS.MASTER.006
OWNER: SYSTEM
ROLE: Canonical registry of hard constraints that must never be violated. Used as validation gates across all layers.

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MINOR
- SUMMARY: "Единый список hard constraints: index/SoT/UID/Naming/DocControl/Versioning/Conflict rules"
- REASON: "Фиксация неотменяемых ограничений и подготовка к CI-валидации"
- IMPACT: "Все слои"

---

## 0) PRIME LAW (ABSOLUTE)
Constraints — это правила, нарушение которых делает документ/слой неканоничным.
Если constraint нарушен:
- объект помечается INVALID,
- канон не может быть зафиксирован до исправления,
- при необходимости выполняется откат/миграция по Canon Protocol.

---

## 1) CONSTRAINT FORMAT
Каждый constraint записывается как:

- `CID` — уникальный ID ограничения
- `SEVERITY` — S0 (critical) | S1 (high)
- `RULE` — формулировка
- `APPLIES_TO` — где действует (layers/docs)
- `VALIDATION` — как проверяется (CI/manual)
- `FIX` — краткое правило исправления

---

## 2) HARD CONSTRAINTS (REGISTERED)

### C-001 — One Master Index per Layer
- CID: C-001
- SEVERITY: S0
- RULE: В каждом слое может существовать ровно один канонический master-index (entrypoint).
- APPLIES_TO: all layers
- VALIDATION: CI (scan index patterns + registry)
- FIX: Все alt/legacy индексы убрать из канона (NON-CANON alias) или удалить.

### C-002 — Existence via Index
- CID: C-002
- SEVERITY: S0
- RULE: Если объект/документ не зарегистрирован в master-index слоя — он не существует для системы (NON-CANON).
- APPLIES_TO: all canon docs/entities/schemas/pipelines
- VALIDATION: CI/manual
- FIX: Либо зарегистрировать, либо считать non-canon.

### C-003 — Single Source of Truth
- CID: C-003
- SEVERITY: S0
- RULE: Один смысл → один SoT документ. Запрещены дубли SoT с одинаковым смыслом.
- APPLIES_TO: 02_STANDARDS, 04_KNOWLEDGE_BASE governance (если есть SoT)
- VALIDATION: manual/CI (rule-based + review)
- FIX: Слить в один SoT или сделать deprecation с ссылкой.

### C-004 — Modules are not SoT
- CID: C-004
- SEVERITY: S0
- RULE: Module не может объявлять себя SoT, если существует SoT по этому смыслу. Module обязан ссылаться на SoT.
- APPLIES_TO: modules (e.g., 06_MARKING_STANDARDS)
- VALIDATION: CI/manual (keyword checks + review)
- FIX: Убрать SoT-формулировки и добавить XREF на SoT.

### C-005 — UID Mandatory for Canon
- CID: C-005
- SEVERITY: S0
- RULE: Любой канонический документ/реестр/схема/пайплайн должен иметь UID в шапке.
- APPLIES_TO: all registered docs
- VALIDATION: CI (header lint)
- FIX: Добавить UID по UID Rules и зарегистрировать.

### C-006 — UID Uniqueness
- CID: C-006
- SEVERITY: S0
- RULE: UID должен быть уникален в пределах Universe Engine. Два файла не могут иметь один UID.
- APPLIES_TO: all canon objects
- VALIDATION: CI (UID index scan)
- FIX: Назначить новый UID одному объекту, миграция через Canon Protocol.

### C-007 — UID is Primary in XREF/REL
- CID: C-007
- SEVERITY: S1
- RULE: Межслойные ссылки и реестры используют UID как primary. Local ID не может быть единственной ссылкой.
- APPLIES_TO: all cross-references
- VALIDATION: manual/CI (pattern scan)
- FIX: Добавить UID мост (passport/registry mapping).

### C-008 — Naming Pattern Compliance
- CID: C-008
- SEVERITY: S0
- RULE: Канонические файлы должны соответствовать Naming Rules (номер, паттерн, допустимые суффиксы).
- APPLIES_TO: all layers
- VALIDATION: CI
- FIX: Переименовать файлы + обновить индексы, UID сохраняется.

### C-009 — Index Number Must Match File Number
- CID: C-009
- SEVERITY: S0
- RULE: Номер в индексе должен совпадать с номером в имени файла.
- APPLIES_TO: all master-index docs
- VALIDATION: CI
- FIX: Исправить индекс или переименовать файл.

### C-010 — No Number Collisions in Same Folder
- CID: C-010
- SEVERITY: S0
- RULE: В одной папке не может быть двух канонических файлов с одним и тем же `NN*` префиксом.
- APPLIES_TO: all layers
- VALIDATION: CI
- FIX: Переименовать/перенумеровать/вынести в подпапку + обновить индексы.

### C-011 — Doc Control Header Required
- CID: C-011
- SEVERITY: S0
- RULE: Канонический документ обязан иметь единый Doc Control header (SCOPE/LAYER/STATUS/LOCK/VERSION/UID/OWNER/ROLE/FILE).
- APPLIES_TO: all canon docs
- VALIDATION: CI
- FIX: Добавить/нормализовать шапку.

### C-012 — No Duplicate Meta Truth
- CID: C-012
- SEVERITY: S0
- RULE: Запрещено дублировать OWNER/LOCK/VERSION/STATUS внизу файла отдельными строками (одна истина — в шапке).
- APPLIES_TO: all canon docs
- VALIDATION: CI/manual
- FIX: Удалить нижние дубли, оставить только шапку.

### C-013 — SemVer Only
- CID: C-013
- SEVERITY: S0
- RULE: Версия канонического документа должна быть SemVer `MAJOR.MINOR.PATCH`.
- APPLIES_TO: all canon docs
- VALIDATION: CI
- FIX: Привести версию к SemVer, зафиксировать Change Note.

### C-014 — Canon Change Requires Protocol
- CID: C-014
- SEVERITY: S1
- RULE: Любая канон-правка проходит Canon Protocol (proposal → gates → version bump → index updates).
- APPLIES_TO: all canon changes
- VALIDATION: process/manual (+ CI checks)
- FIX: Оформить change package и привести к протоколу.

### C-015 — Raw Links Must Be Valid (If Used as Canon)
- CID: C-015
- SEVERITY: S1
- RULE: Если индекс использует raw-ссылки как canonical refs — ссылки должны быть валидны (не 404).
- APPLIES_TO: indices with raw links
- VALIDATION: CI (HTTP check)
- FIX: Исправить путь/файл или обновить ссылку.

### C-016 — Authority Must Not Conflict
- CID: C-016
- SEVERITY: S1
- RULE: Документы не должны объявлять приоритет, который противоречит `00__SYSTEM_LAW.md` и index authority.
- APPLIES_TO: LAW layer + governance docs
- VALIDATION: manual
- FIX: Привести statements к authority chain.

---

## 3) ENFORCEMENT POLICY
- Нарушение S0 = объект/слой INVALID, мёрдж запрещён.
- Нарушение S1 = мёрдж запрещён до исправления или явного waiver (через Canon Protocol).

---

## 4) WAIVERS (EXCEPTIONS)
Waiver (исключение) допускается только через Canon Protocol и должен:
- иметь срок действия (если временный),
- иметь владельца,
- иметь миграционный план.

---

## FINAL RULE (LOCK)
Этот реестр — жёсткая “стена” системы.
Любая правка — изменение канона и проходит Canon Protocol.
--- END.
