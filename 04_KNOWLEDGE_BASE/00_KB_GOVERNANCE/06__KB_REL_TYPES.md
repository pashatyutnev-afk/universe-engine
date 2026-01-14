# KB REL TYPES — CANON RELATIONSHIP SYSTEM (KB)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/06__KB_REL_TYPES.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: SPEC
INDEX_TYPE: REL_TYPES_STANDARD (KB)
LEVEL: L1
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPEC.REL.001
OWNER: SYSTEM
ROLE: Define canonical REL types for KB modules; enforce PATH-only linking, meaning stability, and deterministic navigation without invention

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created KB REL types: strict semantics, PATH-only format, and anti-ambiguity rules."
- REASON: "KB must be machine-usable; relations must not be poetic or vague."
- IMPACT: "Cross-module linking becomes deterministic and auditable; scope maps can be derived without guessing."
- CHANGE_ID: UE.CHG.2026-01-14.KB.REL.001

---

## 0) PURPOSE (LAW)
REL — это типизированные **семантические связи** между KB-единицами:
- объясняют смысл “почему этот модуль связан с тем”,
- позволяют строить маршруты чтения и dependency графы,
- помогают сущностям подключать правильные источники без фантазии.

REL не заменяет NAV/EXISTENCE (это master-index) и не заменяет XREF maps (см. KB_XREF_RULES).

---

## 1) ABSOLUTE RULES
### 1.1 PATH-only (ABSOLUTE)
REL всегда записывается только через PATH (RAW допускается как дополнительная строка, но canonical идентификатор — PATH).

Формат:
- `REL: <rel_type> -> PATH: <path_to_target>`

### 1.2 Source-lock compatibility
REL нельзя использовать для “логических догадок”.
REL фиксирует только:
- факт зависимости/усиления/примерности и т.д. между существующими KB модулями.

### 1.3 Minimalism
REL должен быть минимальным и полезным:
- 0–8 связей на модуль (ориентир),
- никаких “списков всего подряд”.

### 1.4 No synonyms / stable meaning
Каждый rel_type имеет фиксированный смысл. Синонимы запрещены.

---

## 2) CANON REL TYPES (FULL LIST)
### R1) depends_on
**Смысл:** модуль требует другой модуль как предварительное знание/норму.  
**Правило:** без target нельзя корректно применять source.

Пример:
- `REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/20_RUBRICS/RUBRIC__MUSIC_HOOK.md`

---

### R2) derived_from
**Смысл:** модуль построен на основе другого (источник/родитель), но не обязательно требует его при каждом применении.

---

### R3) reinforces
**Смысл:** target усиливает/поддерживает применение source (best practice / чеклист / рубрика).

---

### R4) conflicts_with
**Смысл:** правила/рекомендации конфликтуют; требуется выбор/приоритизация через policy/gate.

Правило:
- если `conflicts_with`, рядом должна быть ссылка на policy/решение, которое разрешает конфликт.

---

### R5) supersedes
**Смысл:** target заменяет source как более новая/правильная версия (обычно при деприкации).

Правило:
- если `supersedes`, source должен быть помечен как DEPRECATED (state/мaturity).

---

### R6) complements
**Смысл:** target — соседний модуль, который расширяет coverage (не зависимость, а дополнение).

---

### R7) example_of
**Смысл:** source является примером применения target (обычно EXAMPLE__* указывает на TOPIC/RUBRIC/POLICY).

---

### R8) implements
**Смысл:** source реализует правило/политику target (например checklist реализует policy).

---

### R9) validated_by
**Смысл:** результат применения source должен проверяться target (обычно VAL/QA рубрики/валидаторы или checklist-гейт).

---

### R10) gated_by
**Смысл:** применение source обязано проходить через gate/рубрику/политику.

Примечание:
- gated_by отличается от validated_by:
  - gated_by = обязательный “проход” (режет FAIL)
  - validated_by = проверка качества/соответствия (может быть частью gate)

---

### R11) referenced_by
**Смысл:** target часто ссылается на source (обратная связь), используется редко (обычно строится автоматически).

---

## 3) RECOMMENDED REL PATTERNS (HOW TO USE)
### 3.1 TOPIC typical set
TOPIC обычно имеет:
- depends_on (если есть prerequisite)
- complements (соседние темы)
- gated_by / validated_by (если нужна проверка качества)
- example_of (если topic — пример чего-то, редко)

### 3.2 RUBRIC typical set
RUBRIC обычно имеет:
- depends_on (на policy/definitions)
- reinforces (на checklists/templates)
- validated_by (на test cases/examples)

### 3.3 TEMPLATE typical set
TPL обычно имеет:
- implements (policy)
- reinforces (checklists)
- complements (examples)

### 3.4 SPC PRO PACK usage
Файлы SPC PRO PACK:
- depends_on (на pillars/topics)
- gated_by (на rubrics/usage gate)
- validated_by (на examples)

---

## 4) ANTI-PATTERNS (FORBIDDEN)
Запрещено:
- `REL: related -> ...` (слишком размыто; нет такого типа)
- “поэтические” связи без смысла
- использовать REL как замену текста (“всё объясняет другой модуль” без минимальной сути)
- создавать циклы зависимостей без причины (A depends_on B и B depends_on A)

---

## 5) MINIMUM COMPLIANCE CHECK
REL считается корректным, если:
- rel_type из канон списка,
- ссылка в формате PATH,
- смысл подходит типу,
- нет “related/vague” типов,
- нет конфликтов без policy/решения.

--- END.
