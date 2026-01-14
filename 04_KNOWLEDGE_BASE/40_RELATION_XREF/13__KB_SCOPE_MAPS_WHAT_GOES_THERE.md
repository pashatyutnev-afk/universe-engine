# KB — KB_SCOPE.MAPS: WHAT GOES THERE (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/13__KB_SCOPE_MAPS_WHAT_GOES_THERE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: STANDARD
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.STD.SCOPE.MAPS.013
OWNER: SYSTEM
ROLE: Define the purpose and strict content rules for KB MAP modules: deterministic selectors and scope matrices that choose which KB modules to load. Prevents turning maps into indexes or narrative docs.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Defined KB_SCOPE.MAPS boundaries and standards: maps are deterministic selection logic, not navigation indexes."
- REASON: "Entities need selection logic to pick the right KB scope; if maps become indexes, RAW-only navigation and existence rules break."
- IMPACT: "Predictable KB intake: tasks/entities select scopes deterministically; navigation stays centralized in master index."
- CHANGE_ID: UE.CHG.2026-01-14.KB.STD.013

---

## 0) PURPOSE (KB)
KB MAP modules exist to answer:
- "Given X (task/entity), which KB scope/modules are REQUIRED vs OPTIONAL?"
Maps provide:
- classification enums
- deterministic selection algorithm
- scope matrices
- hard fail conditions

Maps are not used to open files. They must not contain URLs/RAW.

---

## 1) ABSOLUTE BOUNDARIES (NO MIXING)
MAPS must NOT contain:
- RAW links
- file registries/existence maps (that is master index)
- long domain “how-to” methods (topics)
- governance protocols (meta)

MAPS MAY contain:
- scope labels
- selection rules
- matrix tables
- deterministic procedures
- fail conditions

---

## 2) ALLOWED MAP CONTENT TYPES
Allowed:
- Task classification enums (T0..Tn)
- Entity class selectors (SPC/ENG/...)
- Scope label dictionaries (KB_SCOPE.*)
- Deterministic selection algorithm (Step 1..N)
- Required/optional matrices
- Hard stop rules

---

## 3) FORBIDDEN MAP CONTENT TYPES
Forbidden:
- “Index of all modules” (registry)
- “How to do X professionally” (topic)
- “KB usage law” (meta)
- embedding any URL/PATH as navigation

---

## 4) REQUIRED MAP STRUCTURE (MINIMUM)
Every MAP module should include:
- Purpose (what selection problem it solves)
- Definitions
- Classification enum (if applicable)
- Selection matrix
- Deterministic selection algorithm
- Fail conditions
- Examples

Optional:
- scope label mapping section

---

## 5) HOW ENTITIES USE MAPS
Step 1: Load governance baseline.  
Step 2: Use MAP to select KB_SCOPE labels.  
Step 3: Return to KB master index to open actual KB modules (RAW-only).  
Step 4: Apply selected topics and produce output with KB_SOURCES trace.

---

## 6) QUALITY RULES (MAPS)
- Maps must be short and executable.
- Every rule must be unambiguous.
- Maps must define hard fail conditions.
- Maps must not become “second entrypoints”.

---

## 7) EXAMPLES
GOOD MAP:
- task → KB scope selection (T0..T7)
- entity class → KB scope selection
- scope → folder orientation (non-navigation)

BAD MAP:
- “all links to all KB files” (master index job)
- “guide to marketing” (topic)
- “KB usage protocol” (meta)

---

## 8) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.TOPIC.META.NAV.002 | WHY: master index navigation is required after map selection
- XREF: UE.KB.MAP.TASK_SCOPE.001 | WHY: task selection map is an example of MAP scope
- XREF: UE.KB.MAP.ENTITY_SCOPE.002 | WHY: entity selection map is an example of MAP scope
- XREF: UE.KB.MAP.SCOPE_TO_FOLDER.003 | WHY: orientation map complements selection maps

--- END.
