# KB — KB_SCOPE.TOPICS.WORLD: WHAT GOES THERE (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/19__KB_SCOPE_WORLD_WHAT_GOES_THERE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: STANDARD
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.STD.SCOPE.WORLD.019
OWNER: SYSTEM
ROLE: Define the boundaries and required content types for World topics: world structure, laws, timeline/epochs, civilizations, geopolitics/economy, ecology, technology systems; separated from narrative methods and character psychology.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Defined KB_SCOPE.TOPICS.WORLD boundaries: structure/laws/timeline/civilization/geopolitics/economy/ecology/technology."
- REASON: "World coherence requires structured knowledge modules; without boundaries worldbuilding mixes with plot or character craft and becomes inconsistent."
- IMPACT: "World specialists can build consistent settings and constraints used by narrative/character pipelines with deterministic procedures and checks."
- CHANGE_ID: UE.CHG.2026-01-14.KB.STD.019

---

## 0) PURPOSE (KB)
World topics define the setting and constraints:
- world structure and physical rules
- timeline, epochs, and historical causality
- civilizations and governance forms
- geopolitics and power dynamics
- economy/resources systems (as constraints)
- ecology/environment/survival constraints
- technology systems (and their limits)

World topics provide “facts/constraints” and construction methods for the setting.

---

## 1) ABSOLUTE BOUNDARIES
World topics must NOT:
- define how scenes are written (Narrative methods)
- define character psychology and relationships (Character methods)
- redefine KB governance/navigation (Meta/Governance)
- embed RAW links or act as an index

World topics MAY:
- reference Narrative/Character topics as consumers of world constraints
- include “how to validate world consistency” as a world QA gate (still world-focused)

---

## 2) ALLOWED WORLD TOPIC TYPES
Allowed:
- WORLD STRUCTURE (maps, layers, physics constraints)
- WORLD LAWS (what is possible/impossible; causal rules)
- TIMELINE & EPOCHS (era breakdown, key transitions)
- CIVILIZATION MODELS (culture, governance, values)
- CONFLICT & POWER SYSTEMS (power sources, control mechanisms)
- GEOPOLITICS (alliances, borders, strategic pressures)
- ECONOMY & RESOURCES (resource flows, scarcity constraints)
- ENVIRONMENT & ECOLOGY (climate, hazards, survival)
- TECHNOLOGY SYSTEMS (tech trees, limitations, failure modes)
- WORLD CONSISTENCY GATES (contradiction checks)

---

## 3) FORBIDDEN WORLD CONTENT
Forbidden:
- episode scripts and dramatic beats (narrative)
- character biographies and emotional arcs (character)
- marketing packaging/distribution (marketing)
- production workflows (production)
- essays without structure/templates/QA

---

## 4) REQUIRED STRUCTURE (MINIMUM)
Each World topic should include:
- Purpose
- When to use / when not
- Definitions (strict)
- Inputs/Outputs
- Procedure (step-by-step worldbuilding method)
- Templates (copy) (world card, epoch sheet, civ model sheet)
- QA gates (PASS/REWORK/FAIL)
- Related (UID-only if required)
- Compliance (no-fantasy + trace)

---

## 5) CORE QUALITY AXES (WORLD)
World topics should cover at least one axis explicitly:
- internal consistency (no contradictions)
- constraint clarity (limits explicit)
- causal plausibility (cause→effect)
- scalability (works beyond one scene)
- interaction rules (how tech/power affects society)
- timeline coherence

---

## 6) HOW ENTITIES USE WORLD TOPICS
- World SPC: load structure + timeline + civ/power modules, then produce setting constraints.
- Narrative SPC: load world constraints before writing scenes that depend on them.
- VAL/QA: validate continuity of world facts across outputs.

---

## 7) EXAMPLES
GOOD:
- "Epoch Timeline Template" (era sheet + transition rules)
- "Civilization Governance Model" (parameters + constraints + examples)
- "Technology Limits & Failure Modes" (rules + QA checks)

BAD:
- "Chapter 1 script" (narrative)
- "Character trauma arc" (character)

---

## 8) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.STD.SCOPE.TOPICS.011 | WHY: world is a domain topics scope
- XREF: UE.KB.TOPIC.META.USAGE.001 | WHY: no-fantasy and trace rule apply
- XREF: UE.KB.DICT.XREF_RULES.005 | WHY: uid-only crossrefs
- XREF: UE.KB.STD.SCOPE.NARRATIVE.017 | WHY: narrative consumes world constraints
- XREF: UE.KB.STD.SCOPE.CHARACTER.018 | WHY: character behavior is constrained by world conditions

--- END.
