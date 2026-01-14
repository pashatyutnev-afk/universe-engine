# KB — KB_SCOPE.TOPICS.NARRATIVE: WHAT GOES THERE (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/17__KB_SCOPE_NARRATIVE_WHAT_GOES_THERE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: STANDARD
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.STD.SCOPE.NARRATIVE.017
OWNER: SYSTEM
ROLE: Define the boundaries and required content types for Narrative topics: scene craft, dramatic structure, pacing, tension/stakes, continuity, and dialogue methods; keeps narrative operational and separated from world lore and character domain scopes.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Defined KB_SCOPE.TOPICS.NARRATIVE boundaries: scene craft, structure, pacing, tension, continuity, and dialogue methods."
- REASON: "Narrative quality depends on repeatable craft; without boundaries narrative drifts into lore dumps or vague advice."
- IMPACT: "Narrative specialists can generate consistent scenes/episodes with deterministic procedures, templates, and QA gates."
- CHANGE_ID: UE.CHG.2026-01-14.KB.STD.017

---

## 0) PURPOSE (KB)
Narrative topics define how story is constructed:
- scene design and objectives
- dramatic arcs and turning points
- pacing and rhythm
- tension and stakes
- foreshadowing and reveal mechanics
- continuity rules (within narrative)
- dialogue methods (as craft, not character biography)

---

## 1) ABSOLUTE BOUNDARIES
Narrative topics must NOT:
- store world lore facts (belongs to World scope)
- store character biographies/psychology deep-dive (belongs to Character scope)
- redefine KB governance/navigation (Meta/Governance)
- embed RAW links or act as an index

Narrative topics MAY:
- reference Character/World topics by UID-only as inputs to a scene,
  but narrative method remains the focus.

---

## 2) ALLOWED NARRATIVE TOPIC TYPES
Allowed:
- SCENE CONSTRUCTION (objective/obstacle/turn)
- STORY STRUCTURE (acts, episode beats)
- DRAMATIC ARC (setup→confrontation→resolution)
- PACING & RHYTHM (tempo control, density rules)
- TENSION & STAKES (stakes ladder, escalation)
- FORESHADOWING (plant/payoff)
- TWIST & REVEAL (rules, timing)
- NARRATIVE CONTINUITY (what must remain consistent)
- DIALOGUE METHODS (subtext, rhythm, voice control)
- CLIFFHANGERS (end hooks)

---

## 3) FORBIDDEN NARRATIVE CONTENT
Forbidden:
- encyclopedic lore databases (world)
- “full character sheet” content (character)
- “marketing packaging” content (marketing)
- “production release packs” content (production)
- essays without procedure/templates/QA

---

## 4) REQUIRED STRUCTURE (MINIMUM)
Each Narrative topic should include:
- Purpose
- When to use / when not
- Definitions (strict)
- Inputs/Outputs
- Procedure (step-by-step)
- Templates (copy) (scene card, beat sheet, arc map)
- QA gates (PASS/REWORK/FAIL)
- Related (UID-only if required)
- Compliance (no-fantasy + trace)

---

## 5) CORE QUALITY AXES (NARRATIVE)
Narrative topics should cover at least one axis explicitly:
- scene objective clarity
- turning point presence
- pacing control
- stakes escalation
- continuity integrity
- dialogue naturalness and purpose

---

## 6) HOW ENTITIES USE NARRATIVE TOPICS
- SPC narrative: open scene craft + pacing + tension modules, then write scene.
- ORC: orchestrate episodes using structure/arc modules.
- VAL/QA: validate scenes using continuity and naturalness gates (if present).

---

## 7) EXAMPLES
GOOD:
- "Scene Objectives & Obstacles" (scene card + pass/fail)
- "Foreshadowing Plant/Payoff" (rules + examples + QA)

BAD:
- "All history of the world" (world lore)
- "Character biography of X" (character scope)

---

## 8) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.STD.SCOPE.TOPICS.011 | WHY: narrative is a domain topics scope
- XREF: UE.KB.TOPIC.META.USAGE.001 | WHY: no-fantasy and trace rule apply
- XREF: UE.KB.DICT.XREF_RULES.005 | WHY: uid-only crossrefs
- XREF: UE.KB.MAP.TASK_SCOPE.001 | WHY: task→scope selection (when classifying narrative tasks)

--- END.
