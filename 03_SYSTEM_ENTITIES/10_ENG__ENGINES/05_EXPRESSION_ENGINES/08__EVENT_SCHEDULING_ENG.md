# Event Scheduling Engine
FILE: 08__EVENT_SCHEDULING_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 05_EXPRESSION_ENGINES
CLASS: EXPRESSION (L3)
LEVEL: L3
STATUS: ACTIVE
VERSION: 2.0
ROLE: Turns causal event sets into a consistent schedule/timeline by enforcing temporal constraints, windows, dependencies, resource availability, travel/time realism, and pacing; produces Event Timelines, Constraint Maps, Feasibility Checks, and Canon Time Locks

---

## PURPOSE

События сами по себе не работают, если их нельзя **расположить во времени**.
SCHEDULING нужен, чтобы:
- причинность не ломалась (“это произошло после того, что ещё не случилось”)
- персонажи и ресурсы физически успевали
- окна возможностей (window) были соблюдены
- таймлайн не конфликтовал с эпохой/календарём/логистикой
- ритм (pacing) и эскалация были управляемыми

---

## NON-GOALS

- не заменяет Timeline & Epoch (историческая сетка мира)
- не заменяет Pacing & Rhythm (эмоциональный ритм)
- не заменяет Continuity engine (общий контроль канона)
Он делает **согласованное расписание** для набора событий.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Event Specs (ES)
- Cause–Effect links (CC/DG)
- Conflict stages and escalation thresholds (CS/EL)
- World timeline constraints (Timeline/Epoch)
- Resource/flow constraints (ERX) and travel time rules (if defined)
- Platform/format duration targets (if production content)

### PRODUCES
- EVENT TIMELINE (ETL) — canonical artifact
- DEPENDENCY & WINDOW MAP (DWM)
- FEASIBILITY CHECK (FC)
- CANON TIME LOCKS (CTLK)
- “SLACK / BUFFER” notes (SB)

### DEPENDS_ON
- 05_EXPRESSION_ENGINES/01__EVENT_ENG.md
- 05_EXPRESSION_ENGINES/02__CAUSE_EFFECT_ENG.md
- 04_DOMAIN_WORLD_ENGINES/03__TIMELINE_EPOCH_ENG.md
- 02_DOMAIN_NARRATIVE_ENGINES/05__PACING_RHYTHM_ENG.md (optional alignment)

### OUTPUT_TARGET
- Feeds:
  - scene lists and arc plans
  - continuity locks
  - production format constraints (episode/short)

---

## CANON TERMS

### EVENT WINDOW
Окно, когда событие может произойти:
- по времени, погоде, доступности, закону, расписанию

### DEPENDENCY
Зависимость:
- событие B требует, чтобы A произошло раньше

### SLACK / BUFFER
Запас времени, который предотвращает “невозможные” цепочки.

### TIME LOCK
Каноническая фиксация даты/порядка:
- чтобы потом не сломать эпизодами/ретконами

### FEASIBILITY
Проверка, что это вообще возможно:
- физика, логистика, ресурс, информация

---

## SCHEDULING RULES (CANON)

### ES1 — Dependencies must be acyclic (or explicit loop)
Цепочки зависимостей не должны иметь скрытых циклов.
Если цикл нужен — он описывается как “time-loop system” явно.

### ES2 — Windows are mandatory for key events
Ключевые события должны иметь окна:
- earliest start
- latest start
- duration
- hard deadline (if any)

### ES3 — Travel/time realism
Если персонаж/ресурс должен переместиться:
- travel time обязателен
- нельзя быть в двух местах одновременно

### ES4 — Resource contention
Если один ресурс нужен двум событиям одновременно:
- должна быть очередь, параллельный ресурс или конфликт

### ES5 — Pacing alignment
Даже идеальный таймлайн может быть “скучным”:
- должны быть пики/паузы по ритму
Scheduling обязан учитывать pacing constraints.

### ES6 — Canon time locks for non-movable anchors
Если событие является якорем эпохи/истории:
- оно получает TIME LOCK
- остальные события подстраиваются вокруг

---

## REQUIRED ARTIFACT A: EVENT TIMELINE (ETL)

### ETL SCHEMA (CANON)

Header:
- ETL_ID:
- PROJECT_ID / WORLD_ID:
- SCOPE:
  - episode | arc | epoch
- CALENDAR SYSTEM:
  - Gregorian | internal calendar name
- VERSION:
- STATUS:
  - draft | canon | deprecated

Timeline entries (ordered):
For each event:
- EVENT_ID:
- TITLE:
- START TIME (or relative index):
- END TIME / DURATION:
- LOCATION:
- PARTICIPANTS:
- REQUIRED RESOURCES:
- DEPENDS_ON (event ids):
- WINDOW:
  - earliest_start
  - latest_start
  - hard_deadline (optional)
- STATE DELTA SUMMARY:
- LOCK:
  - none | soft | hard (time lock)
- NOTES:
  - pacing / emotional beat

Rule:
- If exact dates aren’t known, use relative indices (T0, T+1, T+3d).

---

## REQUIRED ARTIFACT B: DEPENDENCY & WINDOW MAP (DWM)

### DWM SCHEMA (CANON)

- DWM_ID:
- ETL_ID:

Dependencies (repeat):
- EDGE:
  - A -> B
- WHY:
- TYPE:
  - causal | resource | info | legal | environmental

Windows (repeat):
- EVENT_ID:
- EARLIEST:
- LATEST:
- DURATION:
- DEADLINE:
- WINDOW SOURCE:
  - calendar | weather | law | resource | character availability

Rule:
- Any event with “hard deadline” must have at least one dependency or stakes rationale.

---

## REQUIRED ARTIFACT C: FEASIBILITY CHECK (FC)

### FC SCHEMA (CANON)

- FC_ID:
- ETL_ID:

Checks (repeat):
- CHECK TYPE:
  - travel | resource | info | law | capability | fatigue | environment
- SUBJECT:
  - who/what
- ASSUMPTION:
- RESULT:
  - pass | fail | risk
- FIX:
  - buffer, move event, add resource, add travel segment, change dependency

Rule:
- If any “fail” exists, ETL cannot be canonized until fixed.

---

## REQUIRED ARTIFACT D: CANON TIME LOCKS (CTLK)

### CTLK SCHEMA (CANON)

- CTLK_ID:
- ETL_ID:

Locks (repeat):
- EVENT_ID:
- LOCK TYPE:
  - hard_date | hard_order | seasonal_anchor | institutional_schedule
- LOCK STATEMENT:
- WHY LOCKED:
  - epoch anchor / legal schedule / world physics / contract
- WHAT MUST NOT CHANGE:
- WHAT CAN CHANGE:
  - surrounding events within windows

Rule:
- Use locks sparingly (too many locks kills flexibility).

---

## REQUIRED ARTIFACT E: SLACK / BUFFER NOTES (SB)

### SB SCHEMA (CANON)

- SB_ID:
- ETL_ID:

Buffers (repeat):
- BETWEEN:
  - event A and event B
- BUFFER AMOUNT:
- WHY NEEDED:
  - travel, recovery, cooldown, resupply, info spread
- WHAT HAPPENS IN BUFFER:
  - downtime, montage, planning, healing

Rule:
- Major arcs require at least one buffer; otherwise timeline becomes “robotic”.

---

## COMMON SCHEDULING PATTERNS

### Pattern 1: Deadline race
- hard deadline + decreasing windows
- buffers become “cuts” or “montage”

### Pattern 2: Parallel fronts
- two or more streams with occasional sync points
- requires resource contention checks

### Pattern 3: Domino cascade
- tight dependencies with little slack
- high risk of infeasibility: needs explicit buffers

### Pattern 4: Seasonal anchor
- events tied to winter/monsoon/ritual calendar
- locks are seasonal rather than exact dates

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- a dependency loop appears (A needs B needs A)
- a character is in two places at once
- travel time is zero with long distances
- an event happens outside its window
- resources are double-booked
- too many locks prevent pacing adjustments
- pacing is flat (no peaks/pause) despite correct schedule

Fix options:
- add buffer segments
- split event into smaller sub-events
- introduce parallel resources or force conflict
- soften locks (hard -> soft) where possible
- change windows via world constraints (e.g., weather changes)
- restructure dependencies (swap causal links with info links)

---

## PROCEDURE (HOW TO RUN)

1) Collect candidate events (ES) for scope (episode/arc)
2) Build dependency graph (DWM edges)
3) Assign windows (earliest/latest/duration) for key events
4) Place anchors (hard locks) first
5) Schedule remaining events within windows using slack
6) Run feasibility check (FC) for travel/resource/info/law
7) Add buffers and sync points
8) Output ETL and time locks
9) Canonize via governance pipeline

---

## QC CHECKLIST (MANDATORY)

- dependency map has no hidden cycles?
- each key event has window?
- anchors locked explicitly?
- feasibility check has no “fail”?
- travel/resource contention resolved?
- at least one meaningful buffer exists?
- pacing notes attached to timeline entries?

---

## VALIDATION RULES

- ESV1: Timeline respects dependencies and event windows.
- ESV2: Feasibility is verified (travel/resource/info/law).
- ESV3: Time locks are explicit and minimal.
- ESV4: Schedule supports pacing and escalation, not just logic.

---

OWNER: Universe Engine
LOCK: FIXED
