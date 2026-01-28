# KB — KB_SCOPE.TOPICS.VISUAL: WHAT GOES THERE (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/20__KB_SCOPE_VISUAL_WHAT_GOES_THERE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: STANDARD
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.STD.SCOPE.VISUAL.020
OWNER: SYSTEM
ROLE: Define the boundaries and required content types for Visual topics: visual composition, art style principles, camera/cinematography, lighting, scene visualization/storyboards, image generation constraints, and visual risk/limitations; separated from montage/editing decisions and narrative plot logic.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Defined KB_SCOPE.TOPICS.VISUAL boundaries: composition/style/camera/lighting/visualization/image-gen constraints + visual risk limits."
- REASON: "Visual quality requires repeatable craft modules and clear separation from editing/montage and narrative beats."
- IMPACT: "Visual specialists can generate consistent, high-quality visuals under explicit constraints with deterministic checks."
- CHANGE_ID: UE.CHG.2026-01-14.KB.STD.020

---

## 0) PURPOSE (KB)
Visual topics define how the audience sees the world:
- composition and framing principles
- art style principles and consistency rules
- camera language (lens/angles/movement rules)
- lighting principles and readability/contrast rules
- scene visualization and storyboard logic (visual-only)
- image generation constraints, risks, and guardrails
- continuity checks for visual identity

---

## 1) ABSOLUTE BOUNDARIES
Visual topics must NOT:
- prescribe montage/editing decisions (Editing scope)
- define plot structure or turning points (Narrative scope)
- define character psychology/motivation (Character scope)
- embed RAW links or act as an index
- hardcode a single palette if the system uses principles-first (use contrast/color principles, not fixed palettes)

Visual topics MUST:
- treat visuals as constraints and principles (what to do / what to avoid)
- include explicit risk/limitations section (no “montage solutions”; only constraints/risks)

---

## 2) ALLOWED VISUAL TOPIC TYPES
Allowed:
- VISUAL COMPOSITION (balance, hierarchy, focal points, rhythm)
- ART STYLE PRINCIPLES (style fingerprint, do/don’t, material language)
- CAMERA & CINEMATOGRAPHY (shot grammar, lens logic, movement constraints)
- LIGHTING PRINCIPLES (readability, contrast, mood logic)
- SCENE VISUALIZATION (blocking diagrams, storyboard beats as visuals)
- VISUAL CONTINUITY (identity rules, recurring motifs, prop consistency)
- IMAGE GENERATION CONSTRAINTS (prompt rules, negative specs, safety/risks)
- VISUAL RISK LIMITS (uncertainty zones, ambiguity handling)

---

## 3) FORBIDDEN VISUAL CONTENT
Forbidden:
- “how to edit/montage this scene” (editing)
- “write the scene” (narrative)
- “character backstory and trauma” (character)
- unbounded aesthetic fantasy without constraints/templates/QA
- purely subjective essays without procedures

---

## 4) REQUIRED STRUCTURE (MINIMUM)
Each Visual topic should include:
- Purpose
- When to use / when not
- Definitions (strict)
- Inputs/Outputs
- Procedure (step-by-step)
- Templates (copy) (shot card, style fingerprint card, lighting plan card)
- Constraints & Risks (mandatory)
- QA gates (PASS/REWORK/FAIL)
- Related (UID-only if required)
- Compliance (no-fantasy + trace)

---

## 5) CORE QUALITY AXES (VISUAL)
Visual topics should cover at least one axis explicitly:
- readability (clear focal point)
- style consistency (fingerprint holds across outputs)
- camera logic consistency (shots feel intentional, not random)
- lighting clarity (contrast principles, not arbitrary)
- continuity (motifs/props/wardrobe/setting stable)
- prompt controllability (constraints reduce drift)

---

## 6) HOW ENTITIES USE VISUAL TOPICS
- Visual SPC: loads composition + style + camera + lighting modules to produce visual plan.
- Narrative SPC: consumes visual constraints (shot grammar) but does not override them.
- QA/VAL: checks style continuity, readability, and prompt controllability.

---

## 7) EXAMPLES
GOOD:
- "Style Fingerprint: Industrial Neo-Noir" (principles + do/don’t + QA)
- "Camera Grammar for Tension Scenes" (constraints + shot cards)
- "Lighting Plan Template" (contrast principles + checks)
- "Image Gen Constraints + Negative Specs" (risk limits)

BAD:
- "Edit with fast cuts and whip pans" (editing/montage)
- "Episode plot beats" (narrative)

---

## 8) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.STD.SCOPE.TOPICS.011 | WHY: visual is a domain topics scope
- XREF: UE.KB.TOPIC.META.USAGE.001 | WHY: no-fantasy and trace rule apply
- XREF: UE.KB.DICT.XREF_RULES.005 | WHY: uid-only crossrefs
- XREF: UE.KB.STD.SCOPE.NARRATIVE.017 | WHY: narrative consumes visual constraints in scenes
- XREF: UE.KB.STD.SCOPE.WORLD.019 | WHY: world constraints shape visual design
- XREF: UE.KB.STD.SCOPE.CHARACTER.018 | WHY: character identity must be visually consistent

--- END.
