# Scope & Impact Engine
FILE: 08__SCOPE_IMPACT_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 00_GOVERNANCE_ENGINES
LEVEL: L1
STATUS: ACTIVE
VERSION: 1.0
ROLE: Classifies changes by scope, computes impact, and determines required governance gates

---

## PURPOSE

Даёт системе **объективную оценку влияния изменений**:
- какие области затронуты
- насколько рискованно
- какие gates обязательны (audit, decision, validation)
- где ожидаются поломки (dependency + xref)

---

## DEFINITIONS

- Scope — конкретные зоны/пути/группы сущностей затронутые изменением.
- Impact Score — оценка масштаба (число/уровень).
- Blast Radius — сколько downstream объектов может затронуть.
- Gate Set — набор обязательных процедур.

---

## INPUTS

- diff/commit list of files
- change types (create/update/delete/move/rename)
- authority zones affected
- dependency graph
- presence of link changes / index changes

---

## OUTPUTS

- Impact Classification:
  - low / medium / high / critical
- Impact Notes:
  - what is affected
  - expected break risks
- Required Gates:
  - audit always
  - xref required?
  - decision required?
  - consistency validation required?

---

## IMPACT SCORING MODEL (CANONICAL)

Базовая логика:

### Factors
- F_paths: количество уникальных папок/зон
- F_files: количество изменённых файлов
- F_move: наличие move/rename (высокий вес)
- F_indexes: затронуты ли INDEX/REGISTRY
- F_law_std: затронуты ли SYSTEM_LAW/STANDARDS
- F_deps: сколько зависимостей затронуто
- F_break: есть ли breaking changes (формат/контракт)

### Classification (recommended)
- LOW:
  - 1–2 файла, нет индексов, нет переезда, нет смены контракта
- MEDIUM:
  - смысловые правки 1–N документов в рамках одной зоны
- HIGH:
  - затронуты индексы/папки/нумерация/переезды или несколько зон
- CRITICAL:
  - LAW/STANDARDS/глобальные реестры или массовые переезды/ломающие изменения

---

## MECHANICS (HOW IT WORKS)

1) Парсим change package и выделяем scope:
   - entity_group(s)
   - folder families
   - indexes/registries touched
2) Считаем фактор move/rename:
   - если есть → минимум HIGH
3) Если затронуты LAW/STANDARDS → CRITICAL
4) Строим dependency blast radius:
   - сколько downstream индексов/ссылок/проектов
5) Назначаем gates:
   - LOW: audit
   - MEDIUM: audit + (optional consistency)
   - HIGH: audit + xref + consistency + decision (если protected)
   - CRITICAL: audit + decision + migration plan + full validation

---

## RULES

- SI1: Move/rename всегда требует XREF mapping.
- SI2: Любые INDEX изменения требуют CONSISTENCY check.
- SI3: Любые LAW/STANDARDS изменения требуют Decision Approval.
- SI4: Если blast radius неизвестен — impact повышается на уровень (консервативно).

---

## FAILURE MODES

- F1: недооценка → ломаем систему незаметно.
- F2: переоценка всего подряд → система становится неповоротливой.
- F3: отсутствие scope → невозможно управлять изменениями.

---

## INTEGRATION

- With CHANGE_CONTROL_ENG: impact → gates.
- With DEPENDENCY_REGISTRY_ENG: blast radius.
- With CONSISTENCY_ENG: проверка инвариантов после high changes.
- With RISK_SAFETY_ENG: impact участвует в оценке риска.

---
OWNER: Universe Engine
STATUS: FIXED
