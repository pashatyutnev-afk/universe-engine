# ENG ENGINE TEMPLATE — EXPRESSION_ENGINES (FAMILY OVERLAY v2)
FILE: 00__TEMPLATE__ENGINE__EXPRESSION_ENGINES.md

SCOPE: Universe Engine
LAYER: ENG
DOC_TYPE: TEMPLATE
ENTITY_GROUP: ENGINES (ENG)
TEMPLATE_KIND: ENGINE_FAMILY_OVERLAY
LEVEL: L3
STATUS: ACTIVE
VERSION: 2.0
ROLE: Expression family overlay. Compatible with ENG ENGINE TEMPLATE (BASE v2). Adds event/beat/conflict/turn/climax/resolution schemas and mandatory cause-effect graph updates.

LOCK: FIXED
OWNER: Universe Engine

---

## 0) ENGINE IDENTITY (MANDATORY)

ENGINE_NAME: <UPPER_SNAKE_CASE>
ENGINE_ID: ENG.EXP.<NN>.<ENGINE_NAME>

FAMILY_CODE: EXP
ENGINE_NN_IN_FAMILY: <01..09>
ENGINE_CLASS: EXPRESSION
ENGINE_LEVEL: L3

ROLE_IN_FAMILY: <FOUNDATION|BUILDER|OUTPUT>
PIPELINE_STAGE: <DEFINE|BUILD|PRODUCE>

---

## 1) PURPOSE (WHAT THIS ENGINE DOES)

One paragraph:
- which expression atom it outputs (event/cause-effect/conflict/turning/climax/resolution/shock/scheduling/chaos)
- how Narrative consumes it

---

## 2) OWNERSHIP BOUNDARIES (ANTI-DUPLICATION)

OWNS:
- structured “mechanics units” and edges (cause/effect, conflict)

DOES NOT OWN (hard):
- arc/act structure (NAR)
- montage timing (PRD)
Rule:
> If you see seconds/frames/shots — wrong layer.

---

## 3) TRIGGERS (WHEN TO RUN)

TRIGGERS:
- scene requires a clear turning/climax/resolution
- continuity needs explicit cause-effect edges
- conflict feels flat or stakes unclear
- schedule logic is required (world time, not screen time)
- controlled chaos needed (randomness within constraints)

---

## 4) MINI-CONTRACT (MANDATORY)

CONSUMES:
- CORE_STATE_VALIDATION (required)
- NARRATIVE_CONTEXT (optional)
- CHARACTER_CONSTRAINTS (optional)
- WORLD_LAWS (optional)

PRODUCES:
- EXP_EVENT
- EXP_CAUSE_EFFECT_EDGE
- EXP_CONFLICT_UNIT
- EXP_TURNING_POINT
- EXP_CLIMAX
- EXP_RESOLUTION
- EXP_SYSTEM_SHOCK
- EXP_SCHEDULE_LOGIC
- EXP_CHAOS_POLICY

DEPENDS_ON:
- [] (or engine IDs)

OUTPUT_TARGET (canonical defaults):
- `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/06_EVENTS/<ENTITY_ID>/<LEVEL_FOLDER>/`
  where ENTITY_ID may be EVT_* / CON_* / SCN_* / SCH_* depending on your naming.

Rule:
> For canon atoms: update REG and XREF.

---

## 5) EXPRESSION SCHEMAS (MANDATORY)

### 5.1 EXP_EVENT

EVT_ID: <EVT_<NAME>>
TYPE: <INCIDENT|DECISION|ACTION|DISCOVERY|LOSS|GAIN|MEETING|BATTLE|REVEAL|...>
WHO: [<CHR_*|FAC_*|SYS_*>]
WHERE: [<LOC_*>]
WHEN: <world-time label or epoch ref>
CHANGE: <what changed?>
BEFORE_STATE: <...>
AFTER_STATE: <...>
STAKE: <optional>
CANON_STATUS: <DRAFT|CANON>
CANON_REFS: [ ... ]

---

### 5.2 EXP_CAUSE_EFFECT_EDGE (mandatory for multi-event chains)

CE_ID: <unique>
CAUSE_EVT: <EVT_*>
EFFECT_EVT: <EVT_*>
MECHANISM: <why does it cause it?>
LATENCY: <immediate|short|long>
STRENGTH: <LOW|MED|HIGH>
SCOPE: <CHARACTER|WORLD|NARRATIVE>
CANON_REF: <refs>

---

### 5.3 EXP_CONFLICT_UNIT

CON_ID: <CON_<NAME>>
FORCES:
- side_A: <who/what>
- side_B: <who/what>
GOALS:
- A: ...
- B: ...
STAKE: ...
PRESSURE: <what escalates?>
RESOLUTION_PATHS: [ ... ]
CANON_REFS: [ ... ]

---

### 5.4 EXP_TURNING_POINT

TURN_ID: <TURN_<NAME>>
EVENT_REF: <EVT_* or SCN_*>
BEFORE: <expected path>
AFTER: <new path>
PRICE: <what is paid?>
SIGNAL: <how audience learns?>
CANON_REFS: [ ... ]

---

### 5.5 EXP_CLIMAX

CLX_ID: <CLX_<NAME>>
CONFLICT_REF: <CON_*>
PEAK_ACTION: ...
DECISIVE_CHOICE: ...
IRREVERSIBILITY: <what cannot be undone?>
CANON_REFS: [ ... ]

---

### 5.6 EXP_RESOLUTION

RES_ID: <RES_<NAME>>
WHAT_IS_CLOSED: ...
NEW_NORMAL: ...
LEFT_OPEN: [ ... ]
CANON_REFS: [ ... ]

---

### 5.7 EXP_SYSTEM_SHOCK

SHK_ID: <SHK_<NAME>>
TARGET: <WORLD|CIV|CHARACTER|SYSTEM>
TRIGGER_EVT: <EVT_*>
DELTA: <what drastically shifts?>
AFTERSHOCKS: [ ... ]
CANON_REFS: [ ... ]

---

### 5.8 EXP_SCHEDULE_LOGIC (world-time, not screen-time)

SCH_ID: <SCH_<NAME>>
TIME_MODEL: <epoch|calendar|sequence|resource-cycle>
CONSTRAINTS: [ ... ]
WINDOWS: [ ... ]
TRIGGERS: [ ... ]
NOTES: ...

---

### 5.9 EXP_CHAOS_POLICY

CHS_ID: <CHS_<NAME>>
RANDOM_SOURCE: <dice|noise|agent|unknown>
BOUNDS:
- allowed_outcomes: [ ... ]
- forbidden_outcomes: [ ... ]
WEIGHTS: <optional>
SAFETY: <how chaos won't break canon>
NOTES: ...

Rule:
> Chaos is constrained. If it breaks world laws — it's invalid.

---

## 6) SYSTEM INTERFACE (MANDATORY) — ORC/CTL/VAL/QA/REG/XREF

ORCHESTRATED_BY (ORC): []
CONTROLLED_BY (CTL): []

VALIDATED_BY (VAL):
- <VAL.EXP.01.CAUSALITY> (placeholder) or []

QA_BY (QA):
- <QA.EXP.01.MECHANICS_COHERENCE> (placeholder) or []

REGISTRY_UPDATES:
- REQUIRED: YES for L2 canon atoms
- TARGETS:
  - `00_REG__REGISTRIES/REG.PRJ.<PROJECT_ID>.ENTITIES.md`
  - `00_REG__REGISTRIES/REG.PRJ.<PROJECT_ID>.CANON_L2.md`

XREF_UPDATES:
- REQUIRED: YES for cause-effect/conflict/turn
- TARGETS:
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CAUSE_EFFECT_GRAPH.md`
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CONFLICT_GRAPH.md`
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__TURNING_POINTS.md`
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__ENTITY_GRAPH.md`
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__PROVENANCE.md`
  - `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CANON_REFS.md`

Rule:
> Cause-effect edges must always update XREF__CAUSE_EFFECT_GRAPH.

---

## 7) PROCESS (HOW TO EXECUTE)

1) Validate CORE state for involved entities.
2) Define events and changes (before/after).
3) Create cause-effect edges for chains.
4) Define conflict and turning/climax/resolution as needed.
5) Store in routing paths.
6) Update REG + XREF graphs.
7) Validate causality and mechanics coherence.

---

## 8) QUALITY GATES (MANDATORY)

PASS if:
- event has clear change and state delta
- cause-effect edges exist for chains
- conflict/turn/climax/resolution are structured
- chaos is bounded and lawful
- no montage timing inside

FAIL if:
- pure prose without units
- missing CE edges in chains
- seconds/shots/frames appear
- chaos violates world laws

---

## 9) RAW LINK (MANDATORY)

RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/05_EXPRESSION_ENGINES/00__TEMPLATE__ENGINE__EXPRESSION_ENGINES.md

---

## FINAL RULE (LOCK)

> Expression units are structured mechanics, not story structure and not montage.

LOCK: FIXED
