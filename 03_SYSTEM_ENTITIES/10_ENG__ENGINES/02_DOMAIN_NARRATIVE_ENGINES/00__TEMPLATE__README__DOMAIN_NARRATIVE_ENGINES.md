# DOMAIN NARRATIVE ENGINES — README TEMPLATE (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/02_DOMAIN_NARRATIVE_ENGINES/00__TEMPLATE__README__DOMAIN_NARRATIVE_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: TEMPLATE
FAMILY: 02_DOMAIN_NARRATIVE_ENGINES
CLASS: DOMAIN (L2)
LEVEL: L2
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.DOM.NARRATIVE.TPL.README.001
OWNER: SYSTEM
ROLE: Mandatory template for the DOMAIN NARRATIVE family README. Enforces boundaries, canon order, navigation block (raw-only), and a consistent workflow to add/change engines without drift.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Domain Narrative README template standardized: family law block, boundaries, engine map skeleton, add/change procedure, and S0 blockers."
- REASON: "Prevent family README divergence and enforce uniform navigation across domain families."
- IMPACT: "Narrative family becomes consistent, auditable, and compatible with CORE + GOVERNANCE."
- CHANGE_ID: UE.CHG.2026-01-08.DOM.NARR.TPL.README.001

---

## 0) HOW TO USE (MANDATORY)

1) Copy this template to create/update:
   `03_SYSTEM_ENTITIES/10_ENG__ENGINES/02_DOMAIN_NARRATIVE_ENGINES/00__README__DOMAIN_NARRATIVE_ENGINES.md`
2) Replace placeholders strictly.
3) Keep structure and section titles intact.
4) Keep engines ordered by number (01..NN).
5) Use raw-only links when referencing repo files.

Rule:
- Missing mandatory blocks => README is incomplete.

---

## 1) README FILE TEMPLATE (COPY FROM HERE)

# DOMAIN NARRATIVE ENGINES — FAMILY README (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/02_DOMAIN_NARRATIVE_ENGINES/00__README__DOMAIN_NARRATIVE_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: README
FAMILY: 02_DOMAIN_NARRATIVE_ENGINES
CLASS: DOMAIN (L2)
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.ENG.DOM.NARRATIVE.README.001
OWNER: SYSTEM
ROLE: Defines what Domain Narrative engines are, their strict boundaries, canon order, and navigation map. Prevents overlap with Expression, Character, World, Production, and Governance/CORE laws.

CHANGE_NOTE:
- DATE: YYYY-MM-DD
- TYPE: PATCH|MINOR|MAJOR|MIGRATION|EMERGENCY
- SUMMARY: "<what changed>"
- REASON: "<why>"
- IMPACT: "<impact>"
- CHANGE_ID: UE.CHG.YYYY-MM-DD.DOM.NARR.README.<SEQ>

---

## 0) PURPOSE (LAW)

Domain Narrative engines define narrative structure and continuity primitives, such as:
- narrative logic, story structure, dramatic arc
- scene construction (as narrative blueprint, not event mechanics)
- pacing/rhythm (story-time)
- foreshadowing, twist/reveal, theme/meaning
- narrative continuity control

They must remain compatible with:
- CORE invariants (identity/state/lifecycle)
- GOVERNANCE pipeline (no silent canon edits)
- other domain families (Character/World)
- Expression family (event mechanics)
- Production families (media implementation)

---

## 1) NON-GOALS (HARD)

This family does NOT:
- define system identity/state/lifecycle (CORE)
- define authority/approvals/pipeline/audit/memory (GOVERNANCE)
- define event mechanics primitives (EXPRESSION owns event/cause/conflict primitives)
- define character psychology/behavior as primary (CHARACTER owns)
- define world laws/economy/tech as primary (WORLD owns)
- define editing rhythm / screen-time rhythm (PRODUCTION owns)
- define production sound/music composition (PRODUCTION + SOUND families own)

---

## 2) BOUNDARIES (ANTI-DUPLICATION LAW)

Narrative vs Expression:
- Narrative family defines **story-time meaning and structure**.
- Expression family defines **event mechanics and causal primitives**.

Narrative vs Production:
- Narrative pacing/rhythm is **story-time**.
- Editing/montage rhythm is **screen-time** (Production).

Narrative vs Character/World:
- Narrative sets structural needs.
- Character/World provide constraints and content primitives.

Collision handling:
- If overlap appears, declare the owner family and route work accordingly (no duplication).

---

## 3) CANON ORDER (DO NOT REORDER)

Engines must be listed and used in strict numeric order.
Number in README must match filename number.

---

## 4) FAMILY NAVIGATION (ENGINE MAP) (MANDATORY)

Family Path:
- `03_SYSTEM_ENTITIES/10_ENG__ENGINES/02_DOMAIN_NARRATIVE_ENGINES/`

Templates (raw-only):
- ENGINE TEMPLATE:
  https://raw.githubusercontent.com/<ORG>/<REPO>/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/02_DOMAIN_NARRATIVE_ENGINES/00__TEMPLATE__ENGINE__DOMAIN_NARRATIVE_ENGINES.md
- README TEMPLATE:
  https://raw.githubusercontent.com/<ORG>/<REPO>/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/02_DOMAIN_NARRATIVE_ENGINES/00__TEMPLATE__README__DOMAIN_NARRATIVE_ENGINES.md

Engines (strict order):
01 — <Engine Name> — 🔗 <RAW LINK>
02 — <Engine Name> — 🔗 <RAW LINK>
...
NN — <Engine Name> — 🔗 <RAW LINK>

---

## 5) HOW TO ADD / CHANGE ENGINES (MANDATORY)

Add new engine:
1) Register in global ENG index (INDEX_ALL_ENGINES) under this family with correct number.
2) Create file from ENGINE TEMPLATE.
3) Fill MINI-CONTRACT with concrete artifacts.
4) Declare boundaries + S0 blockers.
5) If touching ACTIVE/FIXED canon or indexes → Change Control pipeline required.

Change existing engine:
- No silent edits. Use governance pipeline when required.

---

## 6) EXPECTED INPUTS / OUTPUTS (HIGH-LEVEL)

Inputs typically:
- story premise, constraints from character/world
- previous canon narrative artifacts

Outputs typically:
- story structure blueprint
- scene blueprint (narrative)
- theme map and continuity constraints

Rule:
- Outputs must be reusable artifacts, not “just prose”.

---

## 7) INTEGRATION (SYSTEM FIT)

- This family consumes CORE and must not contradict it.
- This family feeds Expression engines (events) and Production engines (implementation).
- Orchestrators may sequence Narrative engines before Expression/Production steps.

---

## 8) S0 BLOCKERS (STOP CONDITIONS)

S0-1: Engine output contradicts CORE invariants.
S0-2: Engine duplicates governance authority/pipeline rules.
S0-3: Narrative engine claims ownership of Expression event mechanics.
S0-4: Screen-time editing rhythm is defined here (belongs to Production).
S0-5: Engine list numbering mismatch vs filenames.

---

## 9) REFERENCES (RAW ONLY) (OPTIONAL)

- Global ENG index: <RAW LINK>
- CORE family README: <RAW LINK>
- Expression family README: <RAW LINK>

--- END.

---

## 2) README QUALITY CHECK (FAST)

Before setting README LOCK: FIXED:
- [ ] Header schema correct
- [ ] Boundaries explicit
- [ ] Engine list complete + ordered
- [ ] Template links are raw-only
- [ ] S0 blockers listed
