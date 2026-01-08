# VISUAL COMPOSITION ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/08_KNOWLEDGE_PRODUCTION_ENGINES/01__VISUAL_COMPOSITION_ENG.md
SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: ENGINE
FAMILY: 08_KNOWLEDGE_PRODUCTION_ENGINES
CLASS: PRODUCTION (L3)
LEVEL: L3
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.PROD.KP.VISUAL.COMPOSITION.001
OWNER: SYSTEM
ROLE: Defines deterministic visual composition constraints: frame hierarchy, focal routing, balance/negative space, shape language constraints, and validation gates. Outputs composition artifacts consumable by camera/lighting/image/video engines without owning lens/movement implementation.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Visual Composition Engine created: composition guide schema, hierarchy map, ruleset, and drift gates."
- REASON: "Production needs a reusable constraint layer for composition separate from camera mechanics and art style."
- IMPACT: "Shots and generated imagery can stay composition-consistent across scenes and formats."
- CHANGE_ID: UE.CHG.2026-01-08.PROD.KP.VISUAL.COMPOSITION.001

---

## 0) PURPOSE (LAW)
This engine owns **VISUAL COMPOSITION constraints**:
- frame hierarchy (primary/secondary/tertiary focus)
- focal routing (how the eye moves through the frame)
- balance, negative space, symmetry/asymmetry rules
- depth layering as constraints (foreground/midground/background intent)
- shape language constraints (soft/rigid/chaotic silhouettes) as tags, not as art style
- composition gates that detect drift and clutter

Hard rule:
- This engine outputs *constraints and plans*, not camera lens/movement settings and not art style paint rules.

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- define lens choices, camera movement, focal length, camera grammar (belongs to `03__CAMERA_CINEMATOGRAPHY_ENG`)
- define lighting implementation (belongs to `04__LIGHTING_ENG`)
- define art style palette (belongs to `02__ART_STYLE_ENG`)
- generate images/video itself (belongs to `05__IMAGE_GENERATION_ENG` / `06__VIDEO_GENERATION_ENG`)
- define story structure, scene content, or meaning (narrative engines own)
- define character psyche/motivation (character engines own)
- define world laws/physics (world engines own)

FORBIDDEN:
- “composition = camera recipe” (lens/movement)  
- “composition = art style” (brushwork/palette)  
- “composition = plot beats”

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- SCENE_PACK (optional)
- EVENT_PACK (optional)
- TONE_PROFILE (optional)
- MOOD_PROFILE (optional)
- ATMOSPHERE_LAYER_SPEC (optional)
- VISUAL_CONTEXT_BRIEF (optional: locations/props/characters refs)

PRODUCES:
- COMPOSITION_GUIDE
- VISUAL_HIERARCHY_MAP
- SHOT_COMPOSITION_RULESET
- COMPOSITION_GATES_REPORT

DEPENDS_ON:
- [] (base production constraint; may consume style outputs but not required)

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/PRODUCTION/VISUAL/COMPOSITION/
OPTIONAL:
- KB/PRODUCTION/VISUAL/COMPOSITION (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Composition: arrangement of elements inside a frame to control attention and meaning-carrying focus (as constraints).
- Frame Hierarchy: ranked attention targets (P1/P2/P3).
- Focal Routing: path of attention (entry -> anchor -> exit) expressed as rules/tags.
- Balance: distribution of visual weight (left/right/top/bottom).
- Negative Space: intentional emptiness used as pressure/clarity tool.
- Depth Layers: foreground/midground/background intent tags (FG/MG/BG).
- Clutter: too many competing focal anchors (gate-detectable).

Enums (baseline):
- scope: GLOBAL|ARC|SCENE_WINDOW|SHOT
- severity: S0|S1|S2|S3

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- composition constraints (hierarchy, balance, routing, negative space, depth intent)
- shot composition templates (not camera settings)
- validation gates for clutter/drift and hierarchy violations

OUT OF SCOPE (HARD):
- camera implementation (lens/movement/angles)
- lighting design specifics
- art style palette and rendering rules
- image/video generation execution

COLLISION RULE:
- If request is “choose lens/movement” → `03__CAMERA_CINEMATOGRAPHY_ENG`
- If request is “light setup / key-fill ratios” → `04__LIGHTING_ENG`
- If request is “render style / brushwork / palette” → `02__ART_STYLE_ENG`
- If request is “generate final image/video” → `05__IMAGE_GENERATION_ENG` / `06__VIDEO_GENERATION_ENG`

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: COMPOSITION_GUIDE defines hierarchy rules (P1/P2/P3) and allowed routing patterns.
R2 (HARD) MUST: VISUAL_HIERARCHY_MAP declares per-scope focus anchors and their weight bounds.
R3 (HARD) MUST: SHOT_COMPOSITION_RULESET contains MUST/FORBIDDEN constraints (clutter caps, negative space policy, balance policy).
R4 (HARD) MUST: gates detect clutter and hierarchy violation (multiple P1s without intent).
R5 (HARD) FORBIDDEN: embedding camera/lens/movement settings as composition rules.
R6 (SOFT) SHOULD: include a small set of reusable “composition templates” (e.g., TRIANGLE, DIAGONAL, CENTER_VOID) as tags.
R7 (HARD) MUST: produced artifacts have schemas (section 6) and storage targets.

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: COMPOSITION_GUIDE
- MUST:
  - guide_id
  - version
  - scope (GLOBAL|ARC)
  - hierarchy_policy (required)
  - routing_patterns[] (non-empty)
  - balance_policy (required)
  - negative_space_policy (required)
  - depth_layer_policy (required)
  - anti_clutter_rules[] (non-empty)
  - validation_checks[] (non-empty)
- HIERARCHY POLICY (minimum):
  - max_primary_anchors (default 1)
  - allow_multi_primary (bool)
  - allow_multi_primary_conditions (required if allow=true)
  - priority_resolution_rule (required)
- BALANCE POLICY (minimum):
  - preferred_balance (SYMMETRIC|ASYMMETRIC|DYNAMIC)
  - weight_tolerance (0..100 proxy)
- NEGATIVE SPACE POLICY (minimum):
  - min_negative_space (0..100 proxy)
  - when_to_expand (testable)
  - when_to_compress (testable)
- DEPTH LAYER POLICY (minimum):
  - require_layers (FG/MG/BG flags)
  - allowed_layer_absence_conditions (optional)
- VALIDATION:
  - routing_patterns non-empty
  - anti_clutter_rules non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/PRODUCTION/VISUAL/COMPOSITION/COMPOSITION_GUIDE.md

---

ARTIFACT: VISUAL_HIERARCHY_MAP
- MUST:
  - hierarchy_map_id
  - version
  - entries[] (non-empty)
  - checks[] (non-empty)
- ENTRY (minimum):
  - entry_id
  - scope (ARC|SCENE_WINDOW|SHOT)
  - context_ref (scene_id/shot_id optional)
  - primary_anchor (P1) (required)
  - secondary_anchors[] (P2) (optional)
  - tertiary_anchors[] (P3) (optional)
  - weight_bounds:
    - P1_min (0..100)
    - P1_max (0..100)
  - routing_hint (optional)
  - negative_space_target (optional 0..100)
  - notes
- VALIDATION:
  - each entry has primary_anchor
  - P1 bounds valid
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/PRODUCTION/VISUAL/COMPOSITION/VISUAL_HIERARCHY_MAP.md

---

ARTIFACT: SHOT_COMPOSITION_RULESET
- MUST:
  - ruleset_id
  - version
  - rules[] (non-empty)
  - template_tags[] (optional)
  - checks[] (non-empty)
- RULE (minimum):
  - rule_id
  - type (MUST|FORBIDDEN|ALLOWED)
  - scope (GLOBAL|ARC|SCENE_WINDOW|SHOT)
  - statement (testable)
  - severity_if_broken (S0|S1|S2|S3)
- TEMPLATE TAG (optional):
  - tag_id
  - name (e.g., TRIANGLE, DIAGONAL_FLOW, CENTER_VOID)
  - when_to_use (testable)
  - when_forbidden (optional)
- VALIDATION:
  - rules non-empty
  - at least one FORBIDDEN rule (anti-style / anti-clutter)
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/PRODUCTION/VISUAL/COMPOSITION/SHOT_COMPOSITION_RULESET.md

---

ARTIFACT: COMPOSITION_GATES_REPORT
- MUST:
  - report_id
  - version
  - gates[] (non-empty)
  - issues[] (can be empty)
  - overall (PASS|WARN|FAIL)
- Minimum required gates:
  - G1_GUIDE_MISSING (S0)
  - G2_HIERARCHY_EMPTY (S0)
  - G3_MULTI_PRIMARY_WITHOUT_CONDITION (S0)
  - G4_CLUTTER_OVER_CAP (S1)
  - G5_NEGATIVE_SPACE_VIOLATION (S2)
  - G6_RULESET_VAGUE (S1)
- VALIDATION:
  - FAIL if any S0 fails
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/PRODUCTION/VISUAL/COMPOSITION/COMPOSITION_GATES_REPORT.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Load optional style context (tone/mood/atmosphere) and scene/event packs if present.
2) Build COMPOSITION_GUIDE:
   - hierarchy policy, routing patterns, balance/negative space/depth policies
3) Build VISUAL_HIERARCHY_MAP:
   - per scope (arc/scene/shot) define P1/P2/P3 anchors
4) Build ruleset:
   - clutter caps, forbidden patterns, template tags
5) Run gates:
   - missing guide/map, multi-primary without condition, clutter
6) Emit artifacts to output targets.

---

## 8) S0 BLOCKERS (STOP)
- S0-1: COMPOSITION_GUIDE missing or empty required sections.
- S0-2: VISUAL_HIERARCHY_MAP entries[] empty or missing P1 anchors.
- S0-3: multi-primary allowed without explicit conditions and resolution rule.
- S0-4: outputs missing schemas / storage targets.
- S0-5: camera/lens/movement implementation leaks into composition rules.

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream (typical):
- style engines (tone/mood/atmosphere) provide feel context
- narrative/scene packs provide what needs to be framed (optional)

Downstream (typical):
- `03__CAMERA_CINEMATOGRAPHY_ENG` implements composition constraints via camera grammar
- `04__LIGHTING_ENG` supports hierarchy using light emphasis (as implementation)
- `05__IMAGE_GENERATION_ENG` / `06__VIDEO_GENERATION_ENG` use constraints for prompt/spec generation
- editing/montage may respect focal clarity but does not own composition rules

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Family template:
  08_KNOWLEDGE_PRODUCTION_ENGINES/00__TEMPLATE__ENGINE__KNOWLEDGE_PRODUCTION_ENGINES.md
- Family README:
  08_KNOWLEDGE_PRODUCTION_ENGINES/00__README__KNOWLEDGE_PRODUCTION_ENGINES.md

--- END.

LOCK: OPEN
