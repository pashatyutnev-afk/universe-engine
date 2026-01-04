# Growth & Trauma Engine
FILE: 09__GROWTH_TRAUMA_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 03_DOMAIN_CHARACTER_ENGINES
CLASS: DOMAIN (L2)
LEVEL: L2
STATUS: ACTIVE
VERSION: 2.0
ROLE: Models character growth, trauma, and scarring as stateful change systems; defines wounds, scar formation, healing conditions, relapse patterns, and growth nodes; produces Growth/Trauma Trackers that synchronize with continuity and feed evolution planning

---

## PURPOSE

Рост/травма — это “почему он стал другим”.
Движок нужен, чтобы:
- изменения были заслужены событиями
- травма имела последствия (шрамы) и повторяемые реакции
- исцеление не было “магией”
- рецидивы были логичны
- эволюция персонажа была управляемой и каноничной

---

## NON-GOALS

- не клиническая психология и не диагнозы
- не заменяет Psychology engine (механика текущей психики)
- не заменяет Evolution engine (общая эволюционная карта)
Он фиксирует **механизм изменения**: рана → шрам → адаптация → рост/деградация.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Character Spec (CS)
- Psychology Profile (PP)
- Value Framework (VF)
- Motivation Map (MM)
- Relationship Ledger (RLSL) (optional, growth often relationship-driven)
- Scene outcomes (SS) (recommended)

### PRODUCES
- GROWTH/TRAUMA TRACKER (GTT) — canonical artifact
- SCAR REGISTRY (SR) — persistent scars + triggers
- HEALING CONDITIONS (HC)
- RELAPSE PATTERNS (RP)
- “BRIDGE BEATS” requirements (scenes needed to justify change)

### DEPENDS_ON
- 03_DOMAIN_CHARACTER_ENGINES/04__CHARACTER_PSYCHOLOGY_ENG.md
- 02_DOMAIN_NARRATIVE_ENGINES/09__NARRATIVE_CONTINUITY_ENG.md (state)

### OUTPUT_TARGET
- Feeds:
  - 03_DOMAIN_CHARACTER_ENGINES/10__CHARACTER_EVOLUTION_ENG.md
  - 03_DOMAIN_CHARACTER_ENGINES/05__CHARACTER_BEHAVIOR_ENG.md (new patterns)
  - 03_DOMAIN_CHARACTER_ENGINES/07__DIALOGUE_ENG.md (voice shifts)
  - Continuity ledger (persistent changes)

---

## CANON TERMS

### TRAUMA EVENT
Событие, которое перепрошивает:
- безопасность
- доверие
- контроль
- идентичность

### SCAR
Долгосрочная “метка”:
- новый триггер
- ограничение
- автоматическая реакция
- искажённое убеждение

### HEALING
Процесс снижения силы шрама через:
- безопасные отношения
- повторяемые подтверждения
- смысловую переоценку
- выбор с ценой

### RELAPSE
Откат под стрессом (нормальная динамика, если прописана).

### BRIDGE BEAT
Мост-сцена, без которой изменение не верится.

---

## CHANGE TYPES (STANDARD)

- GROWTH: расширение диапазона, интеграция страха, появление нового выбора
- HARDENING: закрытие, контроль, цинизм
- BREAKDOWN: деградация функций, зависимость, потеря self
- REDEMPTION: возврат к ценности через цену
- CORRUPTION: предательство своих принципов ради цели

Rule:
- для каждого изменения выбрать тип.

---

## REQUIRED ARTIFACT A: SCAR REGISTRY (SR)

### SR SCHEMA (CANON)

Header:
- SR_ID:
- CHARACTER_ID:
- VERSION:
- STATUS:

Scars (repeat):
- SCAR_ID:
- ORIGIN EVENT:
  - scene/arc reference
- SCAR TYPE:
  - trust-scar | control-scar | abandonment-scar | guilt-scar | identity-scar
- TRIGGERS:
  - what reactivates it
- DEFAULT REACTION:
  - defense/tactic shift
- COST:
  - what it damages (relationship/goal/self)
- PERSISTENCE:
  - permanent | long | medium | short
- HEALING LEVERS:
  - what reduces intensity
- RELAPSE MODE:
  - how it returns under stress
- CONTINUITY LOCK:
  - must be remembered forever?

---

## REQUIRED ARTIFACT B: GROWTH/TRAUMA TRACKER (GTT)

### GTT SCHEMA (CANON)

Header:
- GTT_ID:
- CHARACTER_ID:
- SCOPE:
- VERSION:
- STATUS:

Baseline:
- BASELINE STATE:
  - before arc
- CORE WOUND LINK:
  - from PP

Growth Nodes (repeat):
- NODE_ID:
- CHANGE TYPE:
- TARGET CHANGE:
  - what new capability/shift appears
- REQUIRED BRIDGE BEATS (1–5):
  - events/scenes needed
- REQUIRED COST:
  - what they must pay (loss, shame, sacrifice)
- SUPPORT CONDITIONS:
  - relationship/support needed (optional)
- FAILURE RISK:
  - what can derail it
- SUCCESS INDICATOR:
  - behavior that proves change

Trauma Nodes (repeat):
- NODE_ID:
- TRAUMA EVENT:
- SCAR CREATED:
  - link to SR
- IMMEDIATE AFTERMATH:
  - shock behavior
- LONG-TERM SHIFT:
  - new belief/limit

Relapse Patterns:
- RELAPSE_01:
  - trigger + regression behavior
- RECOVERY ROUTE:
  - how they return to improved baseline

Moral Cost Integration (optional):
- VF COST TOKENS update (if used)

Continuity Hooks:
- REQUIRED CONTINUITY ENTRIES:
  - list of facts/state changes that must be recorded

---

## GROWTH/TRAUMA RULES (CANON)

### GT1 — Change must be earned
Никаких “вдруг стал смелым”.
Нужны bridge beats + cost.

### GT2 — Trauma leaves a scar
Если событие травматическое, оно должно:
- создать trigger
- изменить реакцию/тактику
- дать continuity lock

### GT3 — Healing is conditional
Исцеление требует условий:
- безопасность
- повторяемые подтверждения
- выборы с ценой
Если условия отсутствуют → healing slow or none.

### GT4 — Relapse is normal, but bounded
Рецидив допустим и делает реализм.
Но он должен:
- иметь триггеры
- иметь recovery route

### GT5 — Growth shows as new choice
Рост = появилось новое решение в ситуации, где раньше был один сценарий.

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- major trait change with no bridge beats
- trauma scene with no lasting scar
- healing occurs in 1 scene with no support/cost
- relapse happens randomly with no trigger
- continuity never updated after major events

Fix options:
- add bridge beats and cost
- register scar with triggers/reactions
- define healing conditions and slow it down
- define relapse triggers + recovery route
- write continuity entries and lock them

---

## PROCEDURE (HOW TO RUN)

1) Pull baseline from CS/PP/MM/VF
2) Identify likely trauma events in arc (or planned)
3) For each trauma: create scar in SR
4) For each growth shift: create node in GTT with bridge beats + cost
5) Define relapse patterns and recovery routes
6) Sync with continuity (required entries)
7) Lock tracker for scope and update per arc

---

## QC CHECKLIST (MANDATORY)

- do growth nodes have bridge beats + cost?
- do trauma nodes create scars in SR?
- are triggers and reactions defined for scars?
- are healing conditions explicit?
- are relapse patterns bounded by triggers?
- are continuity hooks listed?

---

## VALIDATION RULES

- GTV1: SR exists with triggers, reactions, persistence.
- GTV2: GTT exists with bridge beats + cost for growth.
- GTV3: Trauma nodes produce lasting scars and continuity locks.
- GTV4: Relapse + recovery routes defined where needed.

---

OWNER: Universe Engine
LOCK: FIXED
