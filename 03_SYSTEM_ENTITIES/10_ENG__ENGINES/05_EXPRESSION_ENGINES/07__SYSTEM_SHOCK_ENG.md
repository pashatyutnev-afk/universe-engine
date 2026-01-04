# System Shock Engine
FILE: 07__SYSTEM_SHOCK_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 05_EXPRESSION_ENGINES
CLASS: EXPRESSION (L3)
LEVEL: L3
STATUS: ACTIVE
VERSION: 2.0
ROLE: Models SYSTEM SHOCKS as multi-channel disruptions that cascade through resources, control, legitimacy, environment, and capability networks; produces Shock Specs, Cascade Graphs, Failure Modes, Recovery Phases, and New Baselines to ensure shocks have realistic propagation and lasting consequences

---

## PURPOSE

SYSTEM SHOCK — это удар по “операционной системе мира”.
Не просто событие, а **срыв стабильности**:
- ломается инфраструктура
- рушатся цепочки поставок
- падает контроль
- появляется хаос/паника/вера
- запускаются каскады (cascades)

Движок нужен, чтобы:
- шоки были правдоподобными и масштабируемыми
- последствия распространялись по каналам
- мир не “откатывался” обратно
- было ясно: фазы шока → фазы восстановления
- можно было проектировать арки “после катастрофы”

---

## NON-GOALS

- не заменяет Event (описание единичного события)
- не заменяет Cause–Effect (общие цепочки)
- не заменяет Environment hazards (перечень опасностей)
Он про **режим каскадного системного отказа**.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Trigger Event (ES) + initial state deltas (SCD)
- Resource/Flow constraints (RL/FM)
- Control map (CM) and legitimacy systems (if present)
- Environment hazards and cycles (HR/SCS)
- Capability availability (tech/magic) if relevant
- Continuity locks (post-state)

### PRODUCES
- SHOCK SPEC (SS) — canonical artifact
- CASCADE GRAPH (CG)
- FAILURE MODE REGISTER (FMR)
- RECOVERY PHASE PLAN (RPP)
- NEW BASELINE STATE (NBS-S) + SCAR REGISTRY entries
- “PANIC / INFO” dynamics notes

### DEPENDS_ON
- 05_EXPRESSION_ENGINES/01__EVENT_ENG.md
- 05_EXPRESSION_ENGINES/02__CAUSE_EFFECT_ENG.md
- 05_EXPRESSION_ENGINES/06__RESOLUTION_ENG.md (for post-state format)
- 00_GOVERNANCE_ENGINES/05__CONSISTENCY_ENG.md

### OUTPUT_TARGET
- Feeds:
  - conflict escalation and civil instability arcs
  - geopolitics (border shifts, coups)
  - economy (scarcity, black markets)
  - environment recovery/degradation
  - future projection (meta engines)

---

## CANON TERMS

### SHOCK TRIGGER
Первичный удар (катастрофа/удар/срыв/открытие).

### CASCADE
Цепь зависимых отказов:
- A ломает B → B ломает C → C ломает D

### CRITICAL NODE
Узел, от которого зависит много других:
- порт, мост, энергосеть, лидер, сервер, священный артефакт

### FAILURE MODE
Как именно система ломается:
- overload, shortage, panic, sabotage, misinformation

### RECOVERY PHASE
Фаза стабилизации:
- containment → triage → restoration → reform

---

## SHOCK RULES (CANON)

### SS1 — Multi-channel impact
Системный шок обязан бить минимум по 3 каналам:
- resources / control / legitimacy / environment / capability / information

### SS2 — Cascades must be explicit
Нельзя “всё развалилось” без каскадного графа:
- должны быть критические узлы и цепи отказов

### SS3 — Time realism
Шок имеет фазы и задержки:
- мгновенный удар → дни хаоса → недели адаптации → месяцы реформ

### SS4 — Panic & information dynamics
В системном шоке:
- слухи, пропаганда, дезинформация
- борьба за доверие
Это должно быть учтено.

### SS5 — No free recovery
Восстановление всегда имеет цену:
- ресурсы, репрессии, миграции, реформы, жертвы

### SS6 — New baseline required
После шока мир **обязан** получить новый baseline:
- часть систем не возвращается к прежнему уровню

---

## SHOCK TYPES (STANDARD)

- infrastructure collapse (энергия/вода/связь)
- leadership decapitation (смерть/плен лидера)
- supply shock (перекрытие логистики/ресурса)
- legitimacy shock (скандал/ересь/доказательство лжи)
- environmental shock (пожар, зима, пепел, эпидемия)
- capability shock (новое оружие/контр-магия)
- financial shock (крах доверия к обмену/ресурсам)
- invasion shock (внезапный фронт, падение столицы)

Rule:
- Type determines dominant failure modes and recovery phases.

---

## REQUIRED ARTIFACT A: SHOCK SPEC (SS)

### SS SCHEMA (CANON)

Header:
- SHOCK_ID:
- PROJECT_ID / WORLD_ID:
- EPOCH:
- VERSION:
- STATUS:
  - draft | canon | deprecated

Trigger:
- TRIGGER_EVENT_ID:
- TRIGGER TYPE:
- INITIAL TARGET:
  - what node/system got hit first
- WHY THIS NODE WAS CRITICAL:

Impact channels:
- RESOURCE IMPACT:
- CONTROL IMPACT:
- LEGITIMACY IMPACT:
- ENVIRONMENT IMPACT:
- CAPABILITY IMPACT:
- INFORMATION IMPACT:

Scope:
- AFFECTED REGIONS:
- AFFECTED POPULATIONS:
- TIME WINDOW:
  - shock onset + expected duration
- SEVERITY:
  - high | catastrophic

Immediate symptoms:
- FAILURES OBSERVED (first 24h):
- PANIC LEVEL:
- SECURITY RESPONSE:

Outputs:
- CASCADE GRAPH (CG_REF)
- FAILURE MODES (FMR_REF)
- RECOVERY PLAN (RPP_REF)
- NEW BASELINE (NBS_REF)

---

## REQUIRED ARTIFACT B: CASCADE GRAPH (CG)

### CG SCHEMA (CANON)

Nodes:
- critical nodes (ports, grids, leaders, institutions)
- dependent nodes (markets, clinics, squads, farms)

Edges:
- depends_on
- supplies
- controls
- legitimizes
- communicates

For each cascade chain:
- CHAIN_ID:
- START NODE:
- STEP 1..N (node failure sequence)
- STOP CONDITION:
  - what stops the cascade
- ACCELERATORS:
  - panic, sabotage, weather
- DAMPENERS:
  - reserves, redundancy, institutions

Rule:
- At least one chain must include “information/panic” as an accelerator.

---

## REQUIRED ARTIFACT C: FAILURE MODE REGISTER (FMR)

### FMR SCHEMA (CANON)

Entries (repeat):
- FM_ID:
- SYSTEM:
  - water | energy | transport | governance | health | food | defense | belief | comms
- FAILURE MODE:
  - shortage | overload | corruption | panic | sabotage | collapse
- TRIGGER CONDITION:
- EARLY SIGNS:
- PRIMARY DAMAGE:
- SECONDARY DAMAGE:
- MITIGATION OPTIONS:
- COST OF MITIGATION:
- WHO BENEFITS (opportunists):

Rule:
- Each dominant channel in SS must have at least one FM entry.

---

## REQUIRED ARTIFACT D: RECOVERY PHASE PLAN (RPP)

### RPP SCHEMA (CANON)

Phases (ordered):
1) CONTAINMENT (stop bleeding)
2) TRIAGE (prioritize survival)
3) RESTORATION (bring minimal functionality)
4) REFORM (prevent repeat)
5) MEMORY (canon locks + narrative scars)

For each phase:
- GOALS:
- ACTIONS:
- REQUIRED RESOURCES:
- TIME RANGE:
- TRADE-OFFS:
- WHO LOSES / WHO GAINS:
- MEASURABLE STABILITY SIGNALS:

Rule:
- If no “reform” phase exists, shock will repeat (mark as unstable baseline).

---

## REQUIRED ARTIFACT E: NEW BASELINE + SCARS (NBS-S / SR-S)

Use formats from Resolution engine:
- NBS: channel baselines after shock
- SR: persistent scars and recovery paths

Mandatory:
- at least 2 scars for catastrophic shocks.

---

## PANIC / INFORMATION MODULE (MANDATORY)

### PI SCHEMA
- RUMOR VECTORS:
  - marketplaces, networks, priests, radios
- TRUST ANCHORS:
  - institutions/figures people believe
- DISINFO ACTORS:
- INFO BOTTLENECKS:
- STABILIZATION MESSAGE:
  - what stops panic
- COST OF PANIC:
  - riots, hoarding, witch hunts

Rule:
- If shock severity is high, PI module must exist.

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- shock impacts only one channel (not a system shock)
- “everything collapses” but no cascade graph exists
- recovery happens instantly with no resources
- panic dynamics ignored despite scarcity and uncertainty
- post-shock world returns to exact baseline with no scars
- institutions react unrealistically (no triage/prioritization)

Fix options:
- add multi-channel impacts and FM entries
- identify critical nodes and dependency edges
- require RPP phases with time windows and costs
- create PI module and rumor/trust map
- enforce NBS and SR with persistent locks

---

## PROCEDURE (HOW TO RUN)

1) Choose trigger event + identify critical node
2) Declare impacted channels (>=3)
3) Build cascade graph chains (CG)
4) Register failure modes per channel (FMR)
5) Write panic/info module (PI)
6) Draft recovery phase plan (RPP)
7) Produce new baseline and scars (NBS/SR)
8) Register continuity locks and propagate to economy/geopolitics/env

---

## QC CHECKLIST (MANDATORY)

- impacts cover >= 3 channels?
- CG exists and includes accelerators/dampeners?
- FMR covers all dominant channels?
- PI module present for high severity?
- RPP has containment→triage→restoration→reform?
- NBS/SR created with persistent scars?
- recovery costs/time realism enforced?

---

## VALIDATION RULES

- SSV1: Shock is multi-channel and cascades are explicit.
- SSV2: Recovery is phased, costly, and time-realistic.
- SSV3: Panic/information dynamics are modeled and affect outcomes.
- SSV4: Post-shock baseline changes persist via scars and locks.

---

OWNER: Universe Engine
LOCK: FIXED
