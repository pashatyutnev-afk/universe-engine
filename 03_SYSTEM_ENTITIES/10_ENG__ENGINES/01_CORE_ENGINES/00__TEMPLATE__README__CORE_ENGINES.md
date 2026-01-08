# CORE ENGINES — README TEMPLATE (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/01_CORE_ENGINES/00__TEMPLATE__README__CORE_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: TEMPLATE
FAMILY: 01_CORE_ENGINES
CLASS: CORE (L1)
LEVEL: L1
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.CORE.TPL.README.001
OWNER: SYSTEM
ROLE: Mandatory template for the CORE family README. Defines boundaries, purpose, family navigation block, engine ordering rules, and the safe procedure to add/update CORE engines without drift.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "CORE README template standardized: family law block, scope/boundaries, engine map skeleton, and rules for adding engines."
- REASON: "Prevent family README divergence and enforce uniform navigation across CORE engines."
- IMPACT: "CORE family becomes machine-checkable and compatible with global engine registry."
- CHANGE_ID: UE.CHG.2026-01-08.CORE.TPL.README.001

---

## 0) HOW TO USE (MANDATORY)

1) Copy this template to create/update:
   `03_SYSTEM_ENTITIES/10_ENG__ENGINES/01_CORE_ENGINES/00__README__CORE_ENGINES.md`
2) Replace placeholders строго.
3) Keep structure and headings intact.
4) Maintain strict ordering of engines by number.
5) Only raw-links when referencing repo files.

Rule:
- Missing mandatory blocks => README considered incomplete.

---

## 1) README FILE TEMPLATE (COPY FROM HERE)

# CORE ENGINES — REALM (README) (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/01_CORE_ENGINES/00__README__CORE_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: README_REALM
FAMILY: 01_CORE_ENGINES
CLASS: CORE (L1)
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.ENG.CORE.REALM.001
OWNER: SYSTEM
ROLE: Defines what CORE engines are, their strict boundaries, and how they integrate with governance and all other engine families.

CHANGE_NOTE:
- DATE: YYYY-MM-DD
- TYPE: PATCH|MINOR|MAJOR|MIGRATION|EMERGENCY
- SUMMARY: "<what changed>"
- REASON: "<why>"
- IMPACT: "<impact>"
- CHANGE_ID: UE.CHG.YYYY-MM-DD.CORE.REALM.<SEQ>

---

## 0) PURPOSE (LAW)

CORE engines define “what the system is” at the foundational level.

This family guarantees:
- stable identity primitives (who/what exists as a system concept)
- stable state primitives (what is “current state” and how it is represented)
- stable lifecycle primitives (birth/change/deprecation of entities/processes)

Non-goals:
- does NOT define canon authority, approvals, audits (that is GOVERNANCE family)
- does NOT define narrative/domain rules (those are domain families)
- does NOT define production/media pipelines (production families)

---

## 1) SCOPE (STRICT)

IN SCOPE:
- base identity constructs (system-wide)
- base state constructs (system-wide)
- base lifecycle constructs (system-wide)
- minimal invariants that must hold across all layers

OUT OF SCOPE (HARD):
- governance pipeline rules (Change Control, Canon Authority, Audit, etc.)
- storytelling/narrative/world/character craft rules
- asset/art/production/format rules
- project-specific content decisions

---

## 2) BOUNDARIES (ANTI-DUPLICATION LAW)

- If a rule is about “who is allowed to change canon” → GOVERNANCE.
- If a rule is about “how to structure story/scenes” → DOMAIN NARRATIVE / EXPRESSION.
- If a rule is about “how to produce visual/audio/media outputs” → KNOWLEDGE PRODUCTION / SOUND & MUSIC.
- CORE owns only foundational primitives needed by every layer.

Collision handling:
- If overlap appears, CORE must declare the minimal invariant,
  and delegate process/approval/validation to GOVERNANCE engines.

---

## 3) WHAT IS A “CORE ENGINE” (DEFINITION)

A CORE engine is an L1 engine that defines base system primitives and invariants:
- canonical identity model (minimum fields / UID linkage policy)
- canonical state model (allowed states / transitions if applicable)
- canonical lifecycle model (create → active → deprecated → archived)

Rule:
- CORE outputs must be stable and referenced by other families, not duplicated.

---

## 4) FAMILY NAVIGATION (ENGINE MAP) (MANDATORY)

Family Path:
- `03_SYSTEM_ENTITIES/10_ENG__ENGINES/01_CORE_ENGINES/`

Templates (raw-only):
- ENGINE TEMPLATE:
  https://raw.githubusercontent.com/<ORG>/<REPO>/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/01_CORE_ENGINES/00__TEMPLATE__ENGINE__CORE_ENGINES.md
- README TEMPLATE:
  https://raw.githubusercontent.com/<ORG>/<REPO>/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/01_CORE_ENGINES/00__TEMPLATE__README__CORE_ENGINES.md

Engines (strict order):
01 — Core Identity Engine — 🔗 <RAW LINK>
02 — Core State Engine — 🔗 <RAW LINK>
03 — Core Lifecycle Engine — 🔗 <RAW LINK>

Rule:
- Engine numbering in this README must match filenames exactly:
  `NN__<ENGINE_NAME>_ENG.md`

---

## 5) HOW TO ADD / CHANGE A CORE ENGINE (MANDATORY)

To add a new CORE engine:
1) Register the engine in the global engine index (INDEX_ALL_ENGINES) in the correct family and number.
2) Create the engine file from ENGINE TEMPLATE.
3) Fill MINI-CONTRACT with concrete inputs/outputs.
4) Add dependency registry entries (if any).
5) Run governance pipeline if touching FIXED/ACTIVE canon.

To modify an ACTIVE/FIXED CORE engine:
- Must follow Change Control pipeline (no silent edits).

---

## 6) DEPENDENCIES (EXPECTED)

CORE typically depends on GOVERNANCE for:
- canon acceptance rules
- audit/memory and change tracking
- dependency registry consistency

But CORE must not re-define governance rules.
CORE may reference them via raw links.

---

## 7) INTEGRATION (HOW OTHER FAMILIES USE CORE)

Other families should:
- consume CORE definitions as prerequisites (identity/state/lifecycle)
- reference CORE outputs (schemas/invariants) instead of duplicating them
- extend at higher layers without breaking CORE invariants

If an extension breaks CORE invariant → S0 blocker, must be escalated to governance.

---

## 8) S0 BLOCKERS (STOP CONDITIONS)

S0-1 CORE invariant is contradicted by any ACTIVE canon doc without explicit override protocol.
S0-2 Two competing identity/state/lifecycle definitions exist in different files as “single source of truth”.
S0-3 CORE engine changes without audit + memory trace when required.

---

## 9) REFERENCES (RAW ONLY) (OPTIONAL)

- Global ENG index: <RAW LINK>
- Governance Change Control: <RAW LINK>
- Dependency Registry: <RAW LINK>

--- END.

---

## 2) README QUALITY CHECK (FAST)

Before setting README to LOCK: FIXED:
- [ ] Purpose + boundaries are explicit
- [ ] Engine list present and ordered
- [ ] Template links are raw-only
- [ ] No governance rules duplicated
- [ ] S0 blockers defined
