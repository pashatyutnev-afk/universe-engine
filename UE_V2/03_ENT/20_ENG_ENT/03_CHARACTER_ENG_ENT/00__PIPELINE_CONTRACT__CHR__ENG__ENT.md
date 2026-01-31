# DOMAIN CHARACTER ENGINES (ENG) — FAMILY REALM — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/03_DOMAIN_CHARACTER_ENGINES/00__README__DOMAIN_CHARACTER_ENGINES.md
SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: README
FAMILY: 03_DOMAIN_CHARACTER_ENGINES
CLASS: DOMAIN (L2)
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.ENG.DOM.CHARACTER.REALM.001
OWNER: SYSTEM
ROLE: Canonical realm file for DOMAIN CHARACTER engines.

Defines what this family owns, what it forbids, and how to navigate and compose character engines without duplicating other domains.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "03_DOMAIN_CHARACTER_ENGINES realm created: scope, non-goals, canon order, routing, S0 blockers, and raw-links."
- REASON: "Family README was empty; required for deterministic stamping and anti-duplication enforcement."
- IMPACT: "Character engines can be produced and composed without overlapping CORE/NARRATIVE/WORLD/EXPRESSION/PRODUCTION/GOVERNANCE."
- CHANGE_ID: UE.CHG.2026-01-08.DOM.CHR.REALM.001

---

## 0) PURPOSE (LAW)
This FAMILY exists to define character-domain engines:
- stable character model rules (who a character is)
- internal drivers (motivation/values/trauma/growth)
- external expression through behavior/speech/relationships
- consistency across scenes, arcs, and formats (without owning narrative structure)

This README is the boundary + navigation law for the family.

---

## 1) SCOPE (WHAT THIS FAMILY OWNS)
IN SCOPE (OWNED):
- character identity as a narrative entity (traits, core, invariants)
- motivation/desire systems
- moral/value systems
- psychology/inner state models (as character domain, not CORE state)
- behavior rulesets (decision heuristics, habits)
- relationship dynamics (maps, tensions, contracts)
- dialogue principles (content + intent)
- speech naturalization (style, realism gates for speech only)
- growth/trauma transformations (character change logic)

---

## 2) HARD NON-GOALS (FORBIDDEN OWNERSHIP)
This family does NOT own:

CORE:
- system identity/state/lifecycle for the whole project/repo/system

GOVERNANCE:
- canon authority, approval, audit, versioning, change pipeline

NARRATIVE:
- story structure, arcs as primary narrative architecture, continuity as system owner
  (character engines may provide constraints, but do not own narrative canon)

WORLD:
- world laws, economy, tech, ecology, geopolitics as primary owners

EXPRESSION:
- event mechanics primitives (cause/effect/conflict/climax scheduling)

PRODUCTION:
- camera, editing, acting, sound production, media implementation

Rule:
- If overlap happens, this README must declare routing to the owner family.

---

## 3) CANON ORDER (MANDATORY NAVIGATION)
Engines must be used in family order unless explicitly stated.

01 — Character Core Engine  
02 — Motivation & Desire Engine  
03 — Moral & Value Engine  
04 — Character Psychology Engine  
05 — Character Behavior Engine  
06 — Relationship Engine  
07 — Dialogue Engine  
08 — Speech Naturalization Engine  
09 — Growth & Trauma Engine  
10 — Character Evolution Engine  

---

## 4) RECOMMENDED COMPOSITION (HOW ENGINES FIT TOGETHER)
Typical build chain (example):
- Core → Motivation → Values → Psychology → Behavior
- Relationships (parallel) → Dialogue → Speech Naturalization
- Growth/Trauma → Evolution (update character over time)

Rule:
- Evolution never overwrites CORE invariants without explicit justification + memory record.

---

## 5) INPUT/OUTPUT PHILOSOPHY (FAMILY CONTRACT)
Family engines must:
- produce reusable artifacts (models, rulesets, constraints)
- avoid producing “final scenes” as the primary output
- prefer deterministic schemas over prose blobs

Family outputs are designed to be consumed by:
- NARRATIVE engines (structure/continuity)
- EXPRESSION engines (events)
- PRODUCTION engines (media realization)
- ORC pipelines (orchestration layer)

---

## 6) BOUNDARY COLLISION ROUTING (MANDATORY)
If a question belongs to:
- “plot order / what happens next” → NARRATIVE + EXPRESSION
- “world rules, economy, tech” → WORLD
- “editing rhythm / camera / staging” → PRODUCTION
- “approval / canon change / audit” → GOVERNANCE
- “system identity/state/lifecycle” → CORE

Character family only answers:
- “who is this person, why they act, how they speak, how they change, how they relate”.

---

## 7) FAMILY S0 BLOCKERS (STOP CONDITIONS)
S0-1: Engine duplicates ownership of CORE/NARRATIVE/WORLD/EXPRESSION/PRODUCTION/GOVERNANCE  
S0-2: Engine outputs contradict CORE invariants without routing + memory  
S0-3: Engine introduces hidden dependencies not declared in MINI-CONTRACT  
S0-4: Family order changed without updating canonical indexes + audit/memory  
S0-5: README loses “CANON ORDER” section format  

---

## 8) INTEGRATION HOOKS (SYSTEM FIT)
- CORE provides system-level invariants and identity context.
- GOVERNANCE controls any FIXED/ACTIVE canon changes.
- NARRATIVE consumes character constraints to keep story consistent.
- EXPRESSION consumes behavior/motivation constraints for event realism.
- PRODUCTION consumes dialogue/speech style to render media.
- ORC orchestrators assemble pipelines using these outputs.

---

## 9) RAW LINKS (MANDATORY IN REAL README, OPTIONAL IN TEMPLATE)
REALM FILE (this file):
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/03_DOMAIN_CHARACTER_ENGINES/00__README__DOMAIN_CHARACTER_ENGINES.md

ENGINE TEMPLATE:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/03_DOMAIN_CHARACTER_ENGINES/00__TEMPLATE__ENGINE__DOMAIN_CHARACTER_ENGINES.md

ENGINES (raw-links):
- 01 — https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/03_DOMAIN_CHARACTER_ENGINES/01__CHARACTER_CORE_ENG.md
- 02 — https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/03_DOMAIN_CHARACTER_ENGINES/02__MOTIVATION_DESIRE_ENG.md
- 03 — https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/03_DOMAIN_CHARACTER_ENGINES/03__MORAL_VALUE_ENG.md
- 04 — https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/03_DOMAIN_CHARACTER_ENGINES/04__CHARACTER_PSYCHOLOGY_ENG.md
- 05 — https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/03_DOMAIN_CHARACTER_ENGINES/05__CHARACTER_BEHAVIOR_ENG.md
- 06 — https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/03_DOMAIN_CHARACTER_ENGINES/06__RELATIONSHIP_ENG.md
- 07 — https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/03_DOMAIN_CHARACTER_ENGINES/07__DIALOGUE_ENG.md
- 08 — https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/03_DOMAIN_CHARACTER_ENGINES/08__SPEECH_NATURALIZATION_ENG.md
- 09 — https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/03_DOMAIN_CHARACTER_ENGINES/09__GROWTH_TRAUMA_ENG.md
- 10 — https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/03_DOMAIN_CHARACTER_ENGINES/10__CHARACTER_EVOLUTION_ENG.md

--- END.
