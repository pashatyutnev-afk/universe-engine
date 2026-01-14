# VISUAL — CLARITY: COMMON FAILS & FAST FIXES (CANON)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/40_VISUAL/06__VISUAL__VISUAL_CLARITY_COMMON_FAILS.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 10_TOPICS / 40_VISUAL
DOC_TYPE: KB_MODULE
KB_TYPE: TOPIC
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.VIS.TOPIC.CLARITY_FAILS.006
OWNER: SYSTEM
ROLE: High-signal reference topic of common visual clarity failures across composition/shot grammar/lighting/continuity, with fast diagnosis and fixes. Designed for QA and rapid iteration. No montage decisions, no fixed palettes.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created visual clarity common fails: symptom→cause→fast fix patterns + quick diagnosis checklist."
- REASON: "Entities need a practical troubleshooting guide to improve visuals quickly and consistently."
- IMPACT: "Faster iteration, fewer unreadable frames, more stable visual quality."
- CHANGE_ID: UE.CHG.2026-01-14.KB.VIS.TOPIC.006

---

## 0) SCOPE (BOUNDARY)
COVERS:
- typical clarity failures and recognizable symptoms
- common root causes
- fast fixes and validation checks

EXCLUDES:
- montage/editing solutions (out of scope)
- fixed palettes/presets (use principles only)
- hardware lighting tutorials

---

## 1) HOW TO USE
- When a frame/shot “feels wrong”, identify the symptom.
- Apply the matching fast fix.
- Re-check with the validation bullet.

This is a troubleshooting module (high signal, short loops).

---

## 2) COMMON FAIL PATTERNS (SYMPTOM → CAUSE → FAST FIX)

### CF1 — “I don’t know what to look at” (no focal point)
Symptom:
- viewer’s eyes bounce; nothing feels primary
Likely cause:
- multiple equal-contrast elements
Fast fix:
- pick PRIMARY subject
- reduce background detail/contrast
- add separation (value/edge/negative space)
Validate:
- PRIMARY is obvious in 1 second

---

### CF2 — “Everything is equally sharp/detailed” (visual soup)
Symptom:
- frame looks busy and tiring
Cause:
- detail everywhere; no hierarchy
Fast fix:
- simplify background
- keep detail around subject, soften elsewhere
Validate:
- subject has highest local contrast/detail

---

### CF3 — “Edges are screaming” (edge attraction)
Symptom:
- bright corner steals attention
Cause:
- uncontrolled highlights at edges
Fast fix:
- quiet the edges (reduce highlight intensity/contrast)
- move attention back to center via leading lines/contrast around subject
Validate:
- eyes land on subject, not corners

---

### CF4 — “Subject merges with background” (no separation)
Symptom:
- silhouette unclear, face blends
Cause:
- similar value/texture behind subject
Fast fix:
- increase local value separation
- add rim/edge separation
- reduce background brightness behind subject
Validate:
- silhouette readable as a clean shape

---

### CF5 — “Flat / cheap look” (no shape)
Symptom:
- everything looks 2D and evenly lit
Cause:
- too much fill, no directional modeling
Fast fix:
- introduce directional key
- reduce fill
- add depth layers (foreground/mid/background)
Validate:
- subject has readable light/shadow modeling

---

### CF6 — “Too dark / unreadable faces”
Symptom:
- you can’t read expressions or action
Cause:
- crushed shadows, low local contrast on subject
Fast fix:
- add controlled fill ONLY where needed
- increase local contrast around face
Validate:
- face/action readable without killing mood

---

### CF7 — “Lighting feels fake / inconsistent”
Symptom:
- light direction changes between adjacent shots
Cause:
- unmotivated key direction, no lighting logic tracked
Fast fix:
- define implied light source direction
- align key direction across related shots
Validate:
- shadow direction consistent unless motivated change

---

### CF8 — “Geography confusion” (where is who?)
Symptom:
- viewer loses spatial map
Cause:
- no establishing/master; axis/eyeline mismatch
Fast fix:
- add orientation anchor (wide/master)
- enforce axis side and eyeline match
Validate:
- viewer can point “who is left/right” consistently

---

### CF9 — “Axis flip” (left/right swap)
Symptom:
- character sides swap unexpectedly
Cause:
- crossed 180° line without re-anchor
Fast fix:
- keep camera on one side of axis
- if crossing, insert re-orientation shot
Validate:
- positions consistent across shot group

---

### CF10 — “Eyeline mismatch”
Symptom:
- looks like characters stare past each other
Cause:
- eyelines not matched to screen position
Fast fix:
- set target position and correct eyeline direction
- use OTS for stable relation if needed
Validate:
- gaze directions plausibly connect

---

### CF11 — “Prop teleport / state mismatch”
Symptom:
- object changes hand/position/state
Cause:
- prop state not tracked
Fast fix:
- define PROP_STATE variables and enforce
- show transfer if it happens
Validate:
- object continuity holds within moment

---

### CF12 — “Movement feels wrong / disorienting”
Symptom:
- motion direction resets; chase feels like teleport
Cause:
- screen direction inconsistency; no anchor
Fast fix:
- keep screen direction consistent
- add landmarks/anchors to show turns
Validate:
- viewer understands direction of motion

---

### CF13 — “Too symmetrical / too centered unintentionally”
Symptom:
- frame feels staged or stiff
Cause:
- accidental symmetry, centered framing without intent
Fast fix:
- offset subject, introduce asymmetry, restore hierarchy
Validate:
- composition supports intent (stable vs tense)

---

### CF14 — “Too much stylization breaks scene”
Symptom:
- one shot looks like different project
Cause:
- style drift (contrast/texture/camera language)
Fast fix:
- define visual constraints for the sequence and enforce
Validate:
- style consistency across adjacent shots

---

## 3) QUICK DIAGNOSIS CHECKLIST (FAST)
CLARITY_DIAG_FAST:
- [ ] Can I name the PRIMARY subject in 2 seconds?
- [ ] Are edges quieter than center?
- [ ] Is silhouette readable against background?
- [ ] Is local contrast around subject sufficient?
- [ ] Do I understand where people/objects are (orientation anchor)?
- [ ] Are axis/eyeline/screen direction coherent?
- [ ] Is lighting direction motivated and consistent?
- [ ] Are props/state variables consistent?
- [ ] Is there a single dominant “visual rule” for this sequence (style consistency)?

If any item fails → map to CF pattern above and apply fast fix.

---

## 4) HARD FAIL CONDITIONS
FAIL IF:
- module becomes a long tutorial instead of symptom→fix reference
- montage/edit decisions are prescribed as solutions
- fixed palettes/presets are introduced as “must”
- fixes contradict visual continuity or governance rules

---

## 5) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.VIS.TOPIC.COMPOSITION.001 | WHY: hierarchy/edge management for focus
- XREF: UE.KB.VIS.TOPIC.SHOT_GRAMMAR.002 | WHY: orientation, axis, eyeline, coverage
- XREF: UE.KB.VIS.TOPIC.LIGHTING.003 | WHY: contrast, separation, motivation principles
- XREF: UE.KB.VIS.TOPIC.CONTINUITY.004 | WHY: continuity tracking for props/light/motion
- XREF: UE.KB.VIS.TOPIC.STORYBOARD_SHOTLIST.005 | WHY: shotlist schema includes continuity + lighting intent

--- END.
