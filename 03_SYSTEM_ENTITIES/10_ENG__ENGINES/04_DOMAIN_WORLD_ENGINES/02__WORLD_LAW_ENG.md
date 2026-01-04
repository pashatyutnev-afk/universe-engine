# World Law Engine
FILE: 02__WORLD_LAW_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 04_DOMAIN_WORLD_ENGINES
CLASS: DOMAIN (L2)
LEVEL: L2
STATUS: ACTIVE
VERSION: 2.0
ROLE: Defines the governing laws of the world (physical/metaphysical/magical constraints, permissions, costs); produces a World Law Spec and Exception Registry ensuring consistent causality, limits, and rule-based problem-solving across narrative and production

---

## PURPOSE

Законы мира отвечают на главное:
- что возможно
- что невозможно
- что возможно, но с ценой
- что является исключением и почему

Движок нужен, чтобы:
- решения в сюжете были честными (не “бог из машины”)
- силы/тех/магия не ломали напряжение
- исключения не превращались в дырки

---

## NON-GOALS

- не описывает географию (World Structure)
- не описывает культуру/власть (Civilization/Geopolitics)
- не делает детальные техспеки устройств (Technology & Magic)
Он задаёт **правила причинности**, лимиты и цены.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- World Structure Spec (WSS) (layers, access constraints)
- Desired genre tone (optional)
- Known tech/magic components (if already defined)

### PRODUCES
- WORLD LAW SPEC (WLS) — canonical artifact
- PERMISSION MATRIX (what actions are allowed)
- COST & CONSEQUENCE TABLE
- EXCEPTION REGISTRY (ERX)
- “RULE CHECK” protocol for scenes

### DEPENDS_ON
- 04_DOMAIN_WORLD_ENGINES/01__WORLD_STRUCTURE_ENG.md
- 00_GOVERNANCE_ENGINES/05__CONSISTENCY_ENG.md
- 00_GOVERNANCE_ENGINES/06__DEPENDENCY_REGISTRY_ENG.md

### OUTPUT_TARGET
- Feeds:
  - 04_DOMAIN_WORLD_ENGINES/08__TECHNOLOGY_MAGIC_ENG.md
  - Narrative engines (stakes/tension/scene logic)
  - Knowledge production (VFX, depiction rules)
  - Continuity (rule locks + exceptions)

---

## CANON TERMS

### LAW
Жёсткое правило причинности:
- если X → тогда Y
- иначе невозможно

### LIMIT
Порог, выше которого механизм не работает.

### COST
Цена применения закона/силы:
- ресурс, здоровье, риск, мораль, социальная цена, время

### CONSEQUENCE
Следствие, которое обязательно происходит после применения.

### EXCEPTION
Отклонение от закона, которое:
- имеет источник
- имеет границы
- имеет цену
- зарегистрировано

---

## LAW CATEGORIES (STANDARD)

- PHYSICAL LAWS:
  - базовая физика/биология/энергия
- SYSTEM LAWS:
  - правила мира как “системы” (например, уровни реальности)
- POWER LAWS:
  - магия/пси/тех-способности (если применимо)
- INFORMATION LAWS:
  - знания, память, наблюдение (что можно знать)
- TRAVEL LAWS:
  - перемещение (скорость, порталы, запреты)
- DEATH/RECOVERY LAWS:
  - смерть/воскрешение/лечение (если есть)
- CANON ENFORCEMENT LAWS:
  - “что нельзя ретконить без governance”

---

## REQUIRED ARTIFACT A: WORLD LAW SPEC (WLS)

### WLS SCHEMA (CANON)

Header:
- WLS_ID:
- WORLD_ID:
- VERSION:
- STATUS:

Law Baseline:
- BASELINE REALISM:
  - hard | mixed | soft
- CAUSALITY MODE:
  - strict | elastic (declared)
- “NO FREE POWER” POLICY:
  - yes/no (recommended yes)

Law Set (repeat):
- LAW_ID:
- CATEGORY:
- NAME:
- STATEMENT (if X then Y):
- DOMAIN:
  - where it applies (layer/region/conditions)
- LIMITS:
  - thresholds, constraints
- COST:
  - resource/time/social/health
- CONSEQUENCES:
  - required aftermath
- DETECTION:
  - how others can notice it
- COUNTERS:
  - what stops/blocks it
- NARRATIVE FUNCTION:
  - tension, mystery, tool, horror, etc.
- VISUAL/AUDIO SIGNATURE (optional):
  - how it appears in media
- CONTINUITY LOCK:
  - must remain consistent forever?

Permission Matrix (mandatory):
- ACTION TYPES:
  - travel, heal, harm, create, destroy, conceal, reveal, resurrect, etc.
- PERMISSION:
  - allowed | allowed-with-cost | forbidden | unknown (must be defined)
- NOTE:
  - reference to LAW_ID(s)

Cost & Consequence Table (mandatory):
- COST TYPES:
  - energy, blood, sanity, time, status, currency (if used), reputation
- CONSEQUENCE TYPES:
  - injury, corruption, exposure, debt, escalation

---

## REQUIRED ARTIFACT B: EXCEPTION REGISTRY (ERX)

### ERX SCHEMA (CANON)

Header:
- ERX_ID:
- WORLD_ID:
- VERSION:
- STATUS:

Exceptions (repeat):
- EXC_ID:
- BREAKS WHICH LAW_ID:
- SOURCE:
  - artifact | entity | place | event | unknown (declared)
- CONDITIONS:
  - when it works
- LIMITS:
  - boundaries
- COST:
- CONSEQUENCES:
- COUNTERS:
- WHY IT EXISTS:
  - narrative function
- RISK:
  - how it can become a plot hole
- MITIGATION:
  - how we prevent abuse
- CONTINUITY LOCK:
  - what must be remembered

Rule:
- If an exception is used in a canon scene, it must be in ERX.

---

## WORLD LAW RULES (CANON)

### WL1 — Rule first, spectacle second
Сначала закон, потом эффект.
Если эффект без закона — это дырка.

### WL2 — No free wins
Любая мощная штука должна иметь:
- цену
- уязвимость
- counter
Иначе напряжение умирает.

### WL3 — Exceptions are not silent
Исключение без регистрации = неканон.
Каждый use-case должен иметь source/limits/cost.

### WL4 — Laws must be testable
Если закон нельзя проверить на 2–3 примерах, он расплывчатый.

### WL5 — Unknown is a declared state
Если что-то пока не определено, это должно быть:
- UNKNOWN (locked)
И сценарий не должен опираться на это как на “решатель”.

### WL6 — Scene rule-check mandatory
Любая сцена с:
- силой
- путешествием
- лечением
- раскрытием информации
Проходит rule-check: allowed? cost? consequence? counter?

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- characters do something previously impossible with no exception
- power used repeatedly with no cost/consequence
- counters never work (invincible rule)
- “unknown” used as solution
- exception expands without new limits

Fix options:
- formalize law statement + limits
- add explicit cost/consequence
- add counter and show it working sometimes
- register exception with mitigation
- mark unknown and forbid narrative reliance until defined

---

## PROCEDURE (HOW TO RUN)

1) Set baseline realism + causality mode
2) Draft minimal law set:
   - travel, power, info, death/recovery
3) For each law: define limits, cost, consequence, counter
4) Build permission matrix for common actions
5) Register all exceptions in ERX
6) Add rule-check protocol to scene writing workflow
7) Lock WLS + ERX via governance if changed

---

## QC CHECKLIST (MANDATORY)

- baseline realism + causality mode defined?
- each law has limits + cost + consequences + counter?
- permission matrix complete for key action types?
- exceptions registry exists and covers used exceptions?
- unknown states declared and protected?
- rule-check protocol described?

---

## VALIDATION RULES

- WLV1: WLS exists with testable law statements.
- WLV2: Costs and counters prevent free wins.
- WLV3: Exceptions are registered, bounded, and mitigated.
- WLV4: Scenes remain consistent under rule-check.

---

OWNER: Universe Engine
LOCK: FIXED
