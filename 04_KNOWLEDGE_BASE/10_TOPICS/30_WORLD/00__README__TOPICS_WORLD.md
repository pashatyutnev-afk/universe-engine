# TOPICS — WORLD (README) (CANON)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD/00__README__TOPICS_WORLD.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 10_TOPICS / 30_WORLD
DOC_TYPE: README
INDEX_TYPE: REALM_README
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.README.TOPICS.WORLD.001
OWNER: SYSTEM
ROLE: Orientation for WORLD topics scope: what belongs here, how entities use it, and a deterministic roadmap to populate the realm with high-signal worldbuilding modules (laws/constraints, lore consistency, tech level impact). No navigation authority.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created WORLD topics realm README: scope boundaries, usage order, and roadmap for world laws/constraints, lore consistency, and tech-level impact modules."
- REASON: "Entities need a structured worldbuilding knowledge base to avoid contradictions and uncontrolled scope creep."
- IMPACT: "More coherent worlds, fewer lore breaks, more believable constraints."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPICS.WORLD.README.001

---

## 0) PURPOSE (KB)
This realm contains WORLD craft knowledge:
- world laws and constraints (what is possible / impossible)
- lore consistency rules and contradiction prevention
- technology level impact on society/conflict/story
- geography/ecology principles as constraints
- civilization/system design principles (when needed)

Goal:
- keep the world consistent and causally believable within its own rules.

---

## 1) WHAT BELONGS HERE / WHAT DOES NOT
### BELONGS (IN-SCOPE)
- explicit world constraints and internal logic
- consistency frameworks (lore bible discipline)
- tech level implications (power, economy, warfare, communication, culture)
- environment/ecology constraints that shape behavior
- civilization rules (institutions, stability, conflict drivers)

### DOES NOT BELONG (OUT-OF-SCOPE)
- scene craft/pacing (belongs to 10_NARRATIVE)
- character psychology (belongs to 20_CHARACTER)
- cinematography/lighting (belongs to 40_VISUAL)
- music production (belongs to SOUND_MUSIC)
- governance laws and navigation maps (master index only)

---

## 2) NAVIGATION RULE (STRICT)
- This README is NOT navigation authority.
- KB navigation/existence authority is ONLY:
  - `04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md`
- Do not add RAW registries here.

---

## 3) HOW ENTITIES USE WORLD TOPICS (DETERMINISTIC)
Order:
1) Load governance minimum set (no-fantasy, uid-only xref, trace).
2) Identify world scope needed:
   - define constraints
   - validate lore consistency
   - evaluate tech-level consequences
3) Load minimal required modules:
   - constraints/standards first (if any)
   - then the specific topic module(s)
4) Apply contradiction protocol if world rules conflict.
5) Output RUN_TRACE (UID-only sources + memory reuse).

---

## 4) FILL PLAN (ROADMAP: WHAT FILES WE MUST CREATE)
Roadmap list (not navigation authority).

### P1 — Core world integrity
- WORLD__WORLD_LAWS_CONSTRAINTS
- WORLD__LORE_CONSISTENCY_RULES
- WORLD__TECH_LEVEL_IMPACT

### P1 — QA / consistency operations
- WORLD__CONTRADICTION_DETECTION_CHECKLIST (PASS/REWORK/FAIL)
- WORLD__SCOPE_BOUNDARY_RULES (what counts as canon world rule vs flavor)

### P2 — Environment shaping systems
- WORLD__ECOLOGY_ENVIRONMENT_PRESSURES
- WORLD__GEOGRAPHY_AND_DISTANCE_IMPLICATIONS
- WORLD__RESOURCE_LOGIC (as constraints, not economy “currency” unless allowed by canon)

### P2 — Civilization/system design
- WORLD__INSTITUTION_STABILITY_AND_CONFLICT
- WORLD__POWER_STRUCTURES_AND_FEEDBACK_LOOPS

### P3 — Advanced
- WORLD__MYTHOLOGY_BELIEF_AS_SYSTEM
- WORLD__TECH_MAGIC_INTERFACE_RULES (if applicable)

---

## 5) STYLE RULES FOR WORLD MODULES
- Always define “rules” as constraints:
  - what is allowed
  - what is forbidden
  - what is costly/rare
- Prefer causal reasoning:
  - if X is true, what must follow?
- When using real-world knowledge:
  - label it as “reference principles” unless canon says otherwise.
- Keep modules atomic and scope-bounded.

---

## 6) HARD FAIL CONDITIONS
FAIL IF:
- realm becomes a second navigation index (RAW registries)
- modules mix narrative/character/visual without split
- world “laws” become vague vibes without constraints
- outputs claim compliance without trace

---

## 7) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.RULES.GOV.001 | WHY: governance rules apply to all KB usage
- XREF: UE.KB.PROC.CONTRADICTIONS.065 | WHY: contradictions must be handled deterministically
- XREF: UE.KB.RULE.SCOPE_BOUNDARIES.076 | WHY: prevents domain mixing
- XREF: UE.KB.RULE.SCOPE_MODULE_LOAD.074 | WHY: minimal loading order

--- END.
