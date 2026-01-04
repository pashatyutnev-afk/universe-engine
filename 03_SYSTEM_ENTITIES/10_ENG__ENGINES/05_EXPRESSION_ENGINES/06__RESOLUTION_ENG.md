# Resolution Engine
FILE: 06__RESOLUTION_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 05_EXPRESSION_ENGINES
CLASS: EXPRESSION (L3)
LEVEL: L3
STATUS: ACTIVE
VERSION: 2.0
ROLE: Converts climax outcomes into stable post-state: closes or transforms open threads, registers long-tail consequences, enforces continuity locks, and defines what becomes the new normal (or the next conflict seed); produces Resolution Specs, Closure Maps, Scar Registries, and Next-State Baselines

---

## PURPOSE

RESOLUTION — это не “всё закончилось”.
Это:
- фиксация исхода кульминации
- закрытие/трансформация открытых нитей
- разведение последствий по системам (долгий хвост)
- создание нового baseline мира

Движок нужен, чтобы:
- не было “победили и забыли”
- последствия жили дальше
- мир имел новую устойчивую конфигурацию
- оставались шрамы и семена следующего конфликта

---

## NON-GOALS

- не заменяет Climax engine (пиковый тест)
- не заменяет Continuity engine (общий контроль канона)
- не заменяет Character evolution (внутренние изменения)
Он формирует **пост-состояние** и правила закрытия.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Climax Spec (CLS), Outcome Delta (OD), Decision Gates (DGX)
- Conflict Spec (CS), WLC (win/lose conditions)
- Causal chain (CC), Consequence propagation list (CPL)
- Open threads list (from multiple engines)
- World constraints (WLS/ERX), environment hazards (HR/SCS) if impacted

### PRODUCES
- RESOLUTION SPEC (RS) — canonical artifact
- CLOSURE MAP (CMAP)
- SCAR REGISTRY (SR)
- NEW BASELINE STATE (NBS)
- NEXT CONFLICT SEED LIST (NCSL)
- “UNRESOLVED BUT TRACKED” registry

### DEPENDS_ON
- 05_EXPRESSION_ENGINES/05__CLIMAX_ENG.md
- 00_GOVERNANCE_ENGINES/05__CONSISTENCY_ENG.md
- 02_DOMAIN_NARRATIVE_ENGINES/09__NARRATIVE_CONTINUITY_ENG.md

### OUTPUT_TARGET
- Feeds:
  - next arcs/events
  - world state and registers
  - character evolution beats
  - economy/geopolitics/environment updated baselines

---

## CANON TERMS

### CLOSURE
Закрытие нити:
- solved (решено)
- transformed (перешло в другую проблему)
- deferred (отложено с условиями)
- declared permanent (остаётся навсегда)

### SCAR
Шрам — постоянное последствие:
- разрушенный город, потерянная репутация, травма, новый закон, дефицит

### NEW BASELINE
Новое “обычное состояние”, из которого мир живёт дальше.

### LONG-TAIL CONSEQUENCE
Долгий хвост:
- последствия, которые проявятся позже (недели/месяцы/годы)

---

## RESOLUTION RULES (CANON)

### R1 — Nothing resets for free
Если что-то сломали, оно:
- чинится временем/ресурсами
- или остаётся шрамом
Никаких “само починилось”.

### R2 — Threads must be classified
Каждая значимая нить должна получить статус:
- closed / transformed / deferred / permanent

### R3 — Consequences propagate
OD/CPL обязаны быть разнесены по системам:
- контроль, ресурсы, отношения, способности, легитимность, среда

### R4 — Baseline must be explicit
После развязки должен быть NBS:
- что теперь правда
- что теперь невозможно
- какие новые ограничения действуют

### R5 — Seeds are allowed but must be intentional
Новые конфликты/узлы допускаются, но:
- они не должны отменять payoff
- они должны вытекать из последствий (шрамы/дефициты/вражды)

---

## REQUIRED ARTIFACT A: RESOLUTION SPEC (RS)

### RS SCHEMA (CANON)

Header:
- RESOLUTION_ID:
- PROJECT_ID / WORLD_ID:
- SCOPE:
  - scene | episode | arc | epoch
- VERSION:
- STATUS:
  - draft | canon | deprecated

Links:
- LINKED_CLIMAX_ID:
- LINKED_CONFLICT_ID:
- KEY_EVENTS:
  - closure events
  - recovery events

Outcome summary:
- WHAT WAS WON/LOST (1–3 lines):
- WHO CLAIMS VICTORY (if propaganda):
- PRICE PAID:

Post-state:
- NEW BASELINE STATE (NBS_REF):
- SCARS CREATED (SR_REF):
- OPEN THREADS UPDATED (CMAP_REF):

Time:
- IMMEDIATE AFTER (hours–days):
- MID AFTER (weeks):
- LONG AFTER (months+):

---

## REQUIRED ARTIFACT B: CLOSURE MAP (CMAP)

### CMAP SCHEMA (CANON)

- CMAP_ID:
- RESOLUTION_ID:

Threads (repeat):
- THREAD_ID:
- THREAD DESCRIPTION:
- ORIGIN:
  - which engine/artifact created it
- STATUS:
  - closed | transformed | deferred | permanent
- CLOSURE EVENT(S):
- IF DEFERRED:
  - trigger for revisit
  - deadline/window
  - cost of ignoring
- IF TRANSFORMED:
  - new thread ID + description
- EVIDENCE:
  - where in RS/ES it is handled

Rule:
- Major arc cannot end with more than 40% “deferred” threads.

---

## REQUIRED ARTIFACT C: SCAR REGISTRY (SR)

### SR SCHEMA (CANON)

- SR_ID:
- RESOLUTION_ID:

Scars (repeat):
- SCAR_ID:
- TYPE:
  - physical | social | political | psychological | ecological | economic
- DESCRIPTION:
- WHERE / WHO AFFECTED:
- PERSISTENCE:
  - permanent | long | mid
- RECOVERY PATH (if not permanent):
  - time/resources/counter-events
- STORY UTILITIES:
  - new norms, new fears, new opportunities
- CONTINUITY LOCK:
  - what must remain true until resolved

Rule:
- Every major resolution must create at least 1 scar (otherwise stakes were fake).

---

## REQUIRED ARTIFACT D: NEW BASELINE STATE (NBS)

### NBS SCHEMA (CANON)

- NBS_ID:
- RESOLUTION_ID:
- BASELINE STATEMENT (short):
  - “After X, the city is under Y control, trade is broken, trust is gone.”

Deltas by channel:
- CONTROL BASELINE:
- RESOURCE BASELINE:
- RELATIONSHIP BASELINE:
- CAPABILITY BASELINE:
- LEGITIMACY BASELINE:
- ENVIRONMENT BASELINE:

New constraints:
- NEW LAWS/TABOOS:
- NEW DEADLINES:
- NEW LIMITATIONS:
- NEW NORMAL RITUALS/BEHAVIORS:

Rule:
- If baseline is not stated, the world will drift and continuity will break.

---

## REQUIRED ARTIFACT E: NEXT CONFLICT SEED LIST (NCSL)

### NCSL SCHEMA (CANON)

- NCSL_ID:
- RESOLUTION_ID:

Seeds (repeat):
- SEED_ID:
- SOURCE SCAR / DELTA:
- WHAT IT WILL CAUSE:
- TIMEFRAME:
  - immediate | mid | long
- EARLY SIGNS:
- HOW IT COULD BE AVOIDED (optional):
- WHY IT’S FAIR:
  - derived from consequences, not random

Rule:
- Seeds must not nullify the payoff; they extend it.

---

## POST-RESOLUTION RECOVERY POLICY

### Recovery modes
- repair (resources + time)
- reform (institutional changes)
- mourning (social/psychological)
- relocation (migration)
- replacement (new leader/system)
- containment (hazard persists but bounded)

Rule:
- Choose at least one recovery mode for each major scar.

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- arc ends and nothing changed (no NBS)
- major damage disappears next scene
- no scars created despite high stakes
- threads vanish without classification
- deferred threads have no trigger or cost
- new conflict appears unrelated to outcomes

Fix options:
- create SR entries and continuity locks
- write NBS baseline and channel deltas
- classify threads via CMAP
- add recovery events and timelines
- derive seeds from scars and resource/control shifts

---

## PROCEDURE (HOW TO RUN)

1) Import CLS + OD from climax
2) Build CMAP: list threads and classify statuses
3) Build SR: convert irreversible deltas into scars
4) Build NBS: state new normal and channel baselines
5) Build NCSL: optional seeds derived from scars/deltas
6) Add recovery modes and events (time realism)
7) Register locks/deltas in continuity/governance
8) Hand off to next arc (Event + Conflict engines)

---

## QC CHECKLIST (MANDATORY)

- RS references CLS/OD and summarizes cost?
- CMAP classifies all major threads?
- SR contains at least one scar for major resolution?
- NBS explicitly states new normal and channel baselines?
- deferred threads have triggers + costs?
- seeds derive from scars/deltas and don’t nullify payoff?
- recovery events respect time/resource constraints?

---

## VALIDATION RULES

- RV1: Resolution produces explicit baseline, not reset.
- RV2: Threads are classified and tracked; nothing vanishes.
- RV3: Scars and long-tail consequences persist realistically.
- RV4: Seeds for next arcs are consequence-derived and fair.

---

OWNER: Universe Engine
LOCK: FIXED
