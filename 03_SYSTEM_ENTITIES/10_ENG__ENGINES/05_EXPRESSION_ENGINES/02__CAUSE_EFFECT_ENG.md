# Cause–Effect Engine
FILE: 02__CAUSE_EFFECT_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 05_EXPRESSION_ENGINES
CLASS: EXPRESSION (L3)
LEVEL: L3
STATUS: ACTIVE
VERSION: 2.0
ROLE: Converts events into explicit causal chains and dependency graphs; validates that effects follow causes, delays are plausible, and consequences propagate across systems (resources, control, relationships, capabilities) without breaking world law or continuity

---

## PURPOSE

Причинно-следственная логика — это “скелет реальности”.
Движок нужен, чтобы:
- любое событие имело причины и последствия
- последствия появлялись с правильной задержкой (delay)
- цепочки можно было анализировать и масштабировать
- можно было ловить “магические” прыжки сюжета (deus ex)
- изменения мира проходили через явные зависимости

---

## NON-GOALS

- не придумывает сами события (Event engine)
- не решает эмоциональный ритм (Pacing/Rhythm)
- не заменяет Conflict engine (эскалация/столкновение)
Он строит **каузальную связность**.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Event Specs (ES) + State Change Deltas (SCD)
- Timeline anchors (TM) (optional but recommended)
- World Law checks (WLS/ERX) for mechanism validity
- Resource/Control/Capability registers (optional hooks)

### PRODUCES
- CAUSAL CHAIN (CC) — canonical artifact
- DEPENDENCY GRAPH (DG) — graph of prerequisites
- CONSEQUENCE PROPAGATION LIST (CPL)
- DELAY & LATENCY MODEL (DLM)
- “MISSING LINK” diagnostics

### DEPENDS_ON
- 05_EXPRESSION_ENGINES/01__EVENT_ENG.md
- 04_DOMAIN_WORLD_ENGINES/02__WORLD_LAW_ENG.md
- 04_DOMAIN_WORLD_ENGINES/03__TIMELINE_EPOCH_ENG.md
- 00_GOVERNANCE_ENGINES/05__CONSISTENCY_ENG.md

### OUTPUT_TARGET
- Feeds:
  - Conflict engine (drivers/escalation)
  - Turning point engine (why it flips)
  - Continuity engine (locks)
  - Economy/Geopolitics (shock propagation)

---

## CANON TERMS

### CAUSE
Предшествующий фактор/действие, без которого событие не произошло бы.

### EFFECT
Изменение состояния (SCD), возникающее из причины.

### PREREQUISITE
Условие, которое должно быть выполнено до события:
- ресурс, доступ, возможность, информация, время, позиция

### LATENCY / DELAY
Задержка между причиной и эффектом:
- мгновенно, часы, дни, недели, годы

### PROPAGATION
Распространение последствий на соседние системы:
- экономика, контроль, отношения, здоровье, вера, возможности

---

## CORE RULES (CANON)

### CE1 — No effect without cause
Любое значимое последствие должно иметь:
- причинный источник (событие/решение/условие)
или явную маркировку:
- coincidence (с условиями вероятности)
- unknown cause (как mystery, временно)

### CE2 — Mechanism must be declared
Нельзя писать “и вот оно случилось” без механизма:
- физический, социальный, технологический, магический

### CE3 — Time must pass realistically
Если эффект требует времени (логистика/болезнь/политика/обучение) —
должен быть delay, иначе фальшь.

### CE4 — Consequences must persist until resolved
Если событие сломало систему, она не “самопочинится”.
Нужно:
- ремонт/контр-событие
- восстановительный процесс
- цена и время

### CE5 — Strong causes create multi-channel effects
Большая причина обычно бьёт по нескольким каналам:
- ресурсы + отношения + контроль + психика
Если удар только “в одном месте”, это подозрительно.

---

## REQUIRED ARTIFACT A: CAUSAL CHAIN (CC)

### CC SCHEMA (CANON)

Header:
- CC_ID:
- PROJECT_ID / WORLD_ID:
- SCOPE:
  - scene | episode | arc | epoch
- VERSION:
- STATUS:

Chain entries (repeat, ordered):
- LINK_ID:
- CAUSE_EVENT_ID / CAUSE_FACTOR:
- EFFECT_EVENT_ID / EFFECT_STATE:
- MECHANISM:
- PREREQUISITES:
- DELAY:
- CONFIDENCE:
  - high | med | low
- EVIDENCE:
  - which ES fields support it
- NOTES:
  - what would break this link

Rule:
- CC must include at least 3 links for any arc-level chain.

---

## REQUIRED ARTIFACT B: DEPENDENCY GRAPH (DG)

### DG SCHEMA (CANON)

Nodes:
- Event nodes (EVENT_ID)
- Condition nodes (resource/access/info/capability)
- Actor nodes (who must act)

Edges:
- requires
- enables
- blocks
- replaces
- counters

For each key event:
- EVENT_ID:
- REQUIRED:
- OPTIONAL:
- BLOCKERS:
- COUNTERS:

Rule:
- If a plan “should fail” but succeeds, DG usually shows missing blockers.

---

## REQUIRED ARTIFACT C: DELAY & LATENCY MODEL (DLM)

### DLM SCHEMA (CANON)

Delay classes:
- instant (0–1 min)
- short (minutes–hours)
- mid (hours–days)
- long (weeks–months)
- epochal (years+)

Common delay templates:
- travel delay (terrain/season)
- communication delay (tech level)
- production delay (build/repair)
- political delay (negotiation/bureaucracy)
- biological delay (disease/incubation/healing)
- training delay (skill acquisition)

Rule:
- Any event involving travel, production, politics, disease, training must choose a delay template.

---

## REQUIRED ARTIFACT D: CONSEQUENCE PROPAGATION LIST (CPL)

### CPL SCHEMA (CANON)

For each major event:
- EVENT_ID:
- PRIMARY EFFECT:
- SECONDARY EFFECTS:
  - economy (RL/FM)
  - control (CM)
  - relations (character/faction)
  - capability availability (AM)
  - belief legitimacy (BSP)
  - environment hazards (HR)
- TERTIARY EFFECTS:
  - long tail
- RESOLUTION EVENTS:
  - which events can close the loop

Rule:
- “Major” event must have at least 2 secondary effects registered.

---

## COINCIDENCE & MYSTERY POLICY

Allowed:
- coincidence ONLY if:
  - probability conditions exist
  - and it introduces cost/new risk
- unknown cause ONLY if:
  - it is tracked as open thread
  - and must be resolved by later events

Forbidden:
- coincidence that solves the main problem with no price

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- effects appear earlier than any cause (time paradox)
- miracle fix happens without resources/capability
- political shifts happen overnight with no triggers
- war supply appears from nowhere
- injuries/healing ignore biology/tech limits
- destroyed infrastructure works next day

Fix options:
- insert prerequisite events (supply, negotiation, repair)
- add delay template and show time passing
- add capability costs/counters from Tech/Magic engine
- add resource flows from Economy engine
- add continuity locks and unresolved threads

---

## PROCEDURE (HOW TO RUN)

1) Pick target event set (scene/arc)
2) For each event, list direct causes and prerequisites
3) Build DG (requires/enables/blocks)
4) Build CC in chronological order (with delays)
5) Build CPL for major events (propagation)
6) Validate with WLS and timeline anchors
7) Mark open mysteries and schedule resolution events
8) Lock chain and handoff to Conflict/Turning Point engines

---

## QC CHECKLIST (MANDATORY)

- every major effect has a cause or is tagged mystery?
- mechanism declared for each link?
- delays are plausible (DLM templates used)?
- consequences persist until resolved?
- propagation captured for major events?
- DG includes blockers/counters where needed?

---

## VALIDATION RULES

- CEV1: No effects without causes; mechanisms are explicit.
- CEV2: Time delays respect world constraints.
- CEV3: Consequences propagate across systems realistically.
- CEV4: Mystery/coincidence never acts as free problem-solver.

---

OWNER: Universe Engine
LOCK: FIXED
