# TOPICS — PRODUCTION (README) (CANON)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/60_PRODUCTION/00__README__TOPICS_PRODUCTION.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 10_TOPICS / 60_PRODUCTION
DOC_TYPE: README
INDEX_TYPE: REALM_README
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.README.TOPICS.PRODUCTION.001
OWNER: SYSTEM
ROLE: Orientation for PRODUCTION topics scope: production workflow craft, constraints, pipelines, and operational QA. Includes deterministic roadmap for filling the realm. No navigation authority.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created PRODUCTION topics realm README: scope boundaries, usage order, and roadmap for pipeline planning, asset flow, and production QA."
- REASON: "Entities need a structured production knowledge layer so creative outputs can be executed consistently without drift."
- IMPACT: "More reliable pipelines, fewer missing assets, clearer constraints and handoffs."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPICS.PROD.README.001

---

## 0) PURPOSE (KB)
This realm contains PRODUCTION craft knowledge:
- pipeline planning (inputs/outputs, handoffs, gates)
- asset flow and version discipline (at knowledge level)
- production constraints and risk management (not montage)
- coordination structures (roles, sequencing, readiness)
- release packaging mechanics (operational)

Goal:
- make creative work executable and repeatable.

---

## 1) WHAT BELONGS HERE / WHAT DOES NOT
### BELONGS (IN-SCOPE)
- pipeline steps and handoff contracts (what each step must output)
- production scheduling logic (timeboxing, batching principles)
- asset requirements (what assets exist, minimal sets)
- QA for production readiness (not artistic taste)
- localization and format adaptation (operational rules)

### DOES NOT BELONG (OUT-OF-SCOPE)
- narrative craft (10_NARRATIVE)
- character craft (20_CHARACTER)
- worldbuilding craft (30_WORLD)
- cinematography principles (40_VISUAL) except constraints/risks
- music craft (50_SOUND_MUSIC)
- marketing strategies (70_MARKETING)
- governance laws and navigation maps (master index only)

---

## 2) NAVIGATION RULE (STRICT)
- This README is NOT navigation authority.
- KB navigation/existence authority is ONLY:
  - `04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md`
- Do not add RAW registries here.

---

## 3) HOW ENTITIES USE PRODUCTION TOPICS (DETERMINISTIC)
Order:
1) Load governance minimum set (no-fantasy, uid-only xref, trace).
2) Determine production task:
   - pipeline design
   - readiness check
   - asset requirements
   - handoff contract
3) Load minimal required modules:
   - constraints/gates first
   - then playbooks/protocols as needed
4) Execute with explicit handoffs.
5) Output RUN_TRACE.

---

## 4) FILL PLAN (ROADMAP: WHAT FILES WE MUST CREATE)
Roadmap list (not navigation authority).

### P1 — Core production mechanics
- PRODUCTION__PIPELINE_STEP_CONTRACTS (what each step must output)
- PRODUCTION__ASSET_MINIMUM_SETS (per format: book/series/game/music)
- PRODUCTION__READINESS_GATES_OVERVIEW
- PRODUCTION__RISK_REGISTER_METHOD (constraints/risks; no montage decisions)

### P1 — Execution discipline
- PRODUCTION__VERSIONING_AND_HANDOFF_DISCIPLINE (operational)
- PRODUCTION__TIMEBOX_BATCH_STRATEGY
- PRODUCTION__QA_BEFORE_RELEASE_CHECKLIST (pass/rework/fail)

### P2 — Adaptation and packaging
- PRODUCTION__FORMAT_ADAPTATION_RULES (book→episode→short)
- PRODUCTION__LOCALIZATION_PIPELINE
- PRODUCTION__RELEASE_PACK_BLUEPRINT

### P3 — Advanced
- PRODUCTION__MULTI_PROJECT_COORDINATION
- PRODUCTION__DEPENDENCY_MANAGEMENT_METHOD

---

## 5) STYLE RULES FOR PRODUCTION MODULES
- Define inputs/outputs.
- Make handoffs explicit.
- Include gates/checklists where possible.
- Keep “constraints/risks” separate from “creative decisions”.

---

## 6) HARD FAIL CONDITIONS
FAIL IF:
- realm becomes a second navigation index (RAW registries)
- modules prescribe montage/edit decisions
- pipeline steps have no defined outputs (non-executable)
- outputs claim compliance without trace

---

## 7) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.RULES.GOV.001 | WHY: governance rules apply everywhere
- XREF: UE.KB.STD.GATE_DEF.088 | WHY: production readiness gates must be measurable
- XREF: UE.KB.STD.RUN_TRACE_MIN.067 | WHY: trace discipline for any KB-driven run
- XREF: UE.KB.RULE.SCOPE_BOUNDARIES.076 | WHY: prevents domain mixing

--- END.
