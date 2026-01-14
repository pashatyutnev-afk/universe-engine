# TOPICS — VISUAL (README) (CANON)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/40_VISUAL/00__README__TOPICS_VISUAL.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 10_TOPICS / 40_VISUAL
DOC_TYPE: README
INDEX_TYPE: REALM_README
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.README.TOPICS.VISUAL.001
OWNER: SYSTEM
ROLE: Orientation for VISUAL topics scope: what belongs here, how entities use it, and what topic modules must be created (no navigation authority).

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created VISUAL topics realm README: scope boundaries, usage rules, and a deterministic roadmap for filling the folder."
- REASON: "Folder was empty; entities need a clear scope and a plan for what to load/create."
- IMPACT: "Visual knowledge becomes structured and fillable without turning into a second index."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPICS.VISUAL.README.001

---

## 0) PURPOSE (KB)
This realm contains VISUAL craft knowledge for entities:
- composition and readability
- camera/cinematography language
- lighting as principles (not hard palettes)
- storyboard logic (what to show, where to cut)
- continuity and visual identity motifs
- production art constraints/risks (not montage decisions)

This realm is content, not governance.

---

## 1) WHAT BELONGS HERE / WHAT DOES NOT
### BELONGS (IN-SCOPE)
- composition principles (hierarchy, framing, negative space)
- camera grammar (shot types, lens intent, movement intent)
- lighting principles (contrast, key/fill logic, mood constraints)
- storyboard method (shots list, beats, clarity rules)
- continuity rules (props, wardrobe, spatial continuity)
- art direction boundaries for scenes (constraints, risks)

### DOES NOT BELONG (OUT-OF-SCOPE)
- narrative structure (belongs to 10_NARRATIVE)
- character psychology (belongs to 20_CHARACTER)
- world law/economy/society (belongs to 30_WORLD)
- “how to edit/montage” as decisions (montage is separate; here only constraints/risks)
- RAW navigation maps (navigation is only master index)

---

## 2) HOW ENTITIES USE VISUAL TOPICS (DETERMINISTIC)
Order:
1) Load governance minimum set (rules/trace/no-fantasy).
2) Select scopes (entity→scope, task→scope).
3) If VISUAL scope is required:
   - load 1–2 constraint/standard modules first (if exist)
   - then load the specific topic module needed (minimal set)
4) Apply checklists/gates (if relevant).
5) Emit RUN_TRACE (UID-only sources).

---

## 3) FILL PLAN (ROADMAP: WHAT FILES WE MUST CREATE)
This list is a roadmap (not navigation authority).

### Core “always needed” topics (P1)
- VISUAL_COMPOSITION_FOUNDATIONS
- SHOT_GRAMMAR_AND_FRAMING
- LIGHTING_PRINCIPLES_CONTRAST
- VISUAL_CONTINUITY_RULES
- STORYBOARD_METHOD_SHOTLIST

### Production constraints (P1/P2)
- PRODUCTION_DESIGN_CONSTRAINTS_RISKS
- COLOR_AS_PRINCIPLES (contrast/readability/mood; no fixed palettes)
- CAMERA_MOVEMENT_INTENT (when/why; not choreography)

### Quality control topics (P1)
- VISUAL_CLARITY_COMMON_FAILS
- VISUAL_READABILITY_CHECKLIST (if checklist module lives here)

### Optional advanced topics (P2/P3)
- VISUAL_SYMBOLISM_MOTIFS
- LOCATION_BLOCKING_VISUALS (spatial readability)
- VFX/AUTO_GENERATION_LIMITS (constraints only)

---

## 4) STYLE RULES (FOR VISUAL TOPIC MODULES)
- Keep modules atomic (one purpose).
- Use principles over specific brand palettes.
- If including “camera” advice: describe intent, constraints, risks (not hard montage).
- Prefer measurable checks where possible (readability, continuity, clutter).

---

## 5) HARD FAIL CONDITIONS
FAIL IF:
- this realm becomes a second navigation index (adds RAW registries)
- visual modules mix narrative/world/character without split
- modules contain invented “facts” presented as sourced truth
- montage/editing decisions are mandated (allowed: only constraints/risks)

---

## 6) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.RULE.SCOPE_BOUNDARIES.076 | WHY: prevents domain mixing
- XREF: UE.KB.RULE.SCOPE_MODULE_LOAD.074 | WHY: minimal loading rules
- XREF: UE.KB.STD.RUN_TRACE_MIN.067 | WHY: trace discipline

--- END.
