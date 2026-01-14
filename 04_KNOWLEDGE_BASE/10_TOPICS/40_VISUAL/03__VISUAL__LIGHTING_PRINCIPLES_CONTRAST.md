# VISUAL — LIGHTING PRINCIPLES (CONTRAST & READABILITY) (CANON)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/40_VISUAL/03__VISUAL__LIGHTING_PRINCIPLES_CONTRAST.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 10_TOPICS / 40_VISUAL
DOC_TYPE: KB_MODULE
KB_TYPE: TOPIC
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.VIS.TOPIC.LIGHTING.003
OWNER: SYSTEM
ROLE: Practical lighting principles for visual clarity and mood: contrast control, separation, key/fill/rim as concepts, motivated light, and common failure modes. Uses principles only (no fixed palettes/presets).

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created lighting principles topic: contrast/readability, separation, motivated light, and mini QA checklist."
- REASON: "Lighting drives readability and perceived production value; entities need a deterministic baseline without prescribing fixed palettes."
- IMPACT: "Cleaner silhouettes, stronger focal control, fewer muddy frames."
- CHANGE_ID: UE.CHG.2026-01-14.KB.VIS.TOPIC.003

---

## 0) SCOPE (BOUNDARY)
COVERS:
- lighting as a clarity + mood control system
- contrast principles (light/dark separation)
- key/fill/rim concepts (roles, not brands)
- motivated light (why light exists in scene)
- failure modes and practical fixes

EXCLUDES:
- specific color palettes and fixed looks (use color principles only)
- montage/edit decisions
- hardware-specific lighting tutorials

---

## 1) CORE IDEA
Lighting answers two questions:
1) Can the viewer read the frame fast? (readability)
2) What should the viewer feel? (mood)

If lighting does neither, it’s noise.

---

## 2) CONTRAST = READABILITY
### 2.1 Value contrast (light vs dark)
- Stronger value separation → faster recognition of shapes and faces.
- Low separation → “mud” (everything same value).

Practical principle:
- Keep PRIMARY subject separable from background by value OR edge OR detail.

### 2.2 Edge contrast (silhouette clarity)
Silhouette clarity matters more than internal detail:
- subject readable against background shape
- avoid merging outlines into similar-value background

### 2.3 Local contrast vs global contrast
- Global: overall scene bright/dark distribution
- Local: the subject vs nearby background

Rule:
- Even in “low key” scenes, keep local contrast for primary subject.

---

## 3) KEY / FILL / RIM (CONCEPT ROLES)
These are roles, not specific setups.

**Key light (ключ)**
- Role: defines the main shape and face modeling.
- Function: establishes direction and dominance.

**Fill light (заполнение)**
- Role: controls shadow density (how deep shadows go).
- Function: adjusts readability vs drama.
- Too much fill → flatness; too little → unreadable faces.

**Rim / edge light (контровой/обводка)**
- Role: separates subject from background.
- Function: creates outline clarity, especially in dark scenes.

Rule:
- You don’t always need all three, but you always need separation for PRIMARY.

---

## 4) LIGHT DIRECTION & INTENT
### 4.1 Direction shapes meaning
- top-down can feel oppressive/clinical
- side light emphasizes texture and tension
- front light is clearer but can be flatter

This is a principle:
- choose direction that supports the scene’s intent.

### 4.2 Shape before beauty
Before “pretty lighting”, ensure:
- face readability
- action readability
- space readability (if needed)

---

## 5) MOTIVATED LIGHT (WHY LIGHT EXISTS)
Motivation = plausible source logic (even stylized).
Examples (principle-level):
- window daylight direction
- lamp practical in scene
- screen/glow source
- streetlight, sign, fire

Rule:
- if light direction contradicts the scene’s implied sources, it feels fake.

Note:
- Motivation does not mean realism; it means internal logic.

---

## 6) SEPARATION TOOLS (NO PALETTES, ONLY PRINCIPLES)
Use one or more:
- value separation (subject brighter/darker than background)
- rim separation (edge highlight)
- background control (dim/soften background where needed)
- depth separation (foreground/mid/background values)
- specular control (avoid random shiny hotspots stealing focus)

---

## 7) COMMON FAILURE MODES (AND FIXES)
### F1 — “Muddy frame” (no separation)
Symptoms:
- subject blends into background
Fix:
- increase local value contrast
- add rim/edge separation
- simplify background values

### F2 — Flat lighting (no shape)
Symptoms:
- everything evenly lit, no depth
Fix:
- introduce directional key
- reduce fill
- use side angle for modeling

### F3 — Over-crushed shadows (unreadable)
Symptoms:
- face/action lost in black
Fix:
- add controlled fill
- increase local contrast around face rather than global brightening

### F4 — Random hotspots (edge attraction)
Symptoms:
- shiny bright spots at edges steal attention
Fix:
- reduce speculars, soften highlights
- keep edges quieter than primary

### F5 — Unmotivated direction
Symptoms:
- light seems to come from nowhere; feels “gamey” in wrong way
Fix:
- establish implied source direction
- align key direction with scene logic

### F6 — Rim abuse
Symptoms:
- neon outline everywhere, looks artificial
Fix:
- use rim only where needed for separation
- keep rim intensity subordinate to key clarity

---

## 8) PRACTICAL “LIGHTING INTENT” QUESTIONS
Ask before finalizing a frame:
- What is the PRIMARY subject?
- What must be readable (face, action, object, space)?
- What is the mood target (calm, threat, intimacy)?
- What is the implied light source direction?
- What is the separation method used (value/edge/background)?

If you can’t answer, lighting is not intentional yet.

---

## 9) MINI CHECKLIST — LIGHTING QA (CLARITY FIRST)
LIGHTING_QA_MINI:
- [ ] PRIMARY subject is readable (face/action/object)
- [ ] Subject is separated from background (value/edge/background control)
- [ ] Local contrast supports focus (even if global is low key)
- [ ] Shadows are intentional (not accidental loss of info)
- [ ] Edge hotspots are controlled (no random bright corners)
- [ ] Light direction has motivation / internal logic
- [ ] Mood is consistent with contrast choice (stable vs tense)
- [ ] No “preset look” forces illegible frame

Result:
- PASS if readability + separation are satisfied
- REWORK if 1–2 issues exist (fixable via contrast/separation)
- FAIL if subject/action is unreadable or focus is stolen by hotspots

---

## 10) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.VIS.TOPIC.COMPOSITION.001 | WHY: composition hierarchy + edge management works with lighting focus
- XREF: UE.KB.VIS.TOPIC.SHOT_GRAMMAR.002 | WHY: shot intent determines what must be readable
- XREF: UE.KB.RULE.SCOPE_BOUNDARIES.076 | WHY: keeps lighting module within visual domain
- XREF: UE.KB.README.TOPICS.VISUAL.001 | WHY: visual realm boundaries and roadmap

--- END.
