# VISUAL — CONTINUITY RULES (SPATIAL / PROP / LIGHT / MOTION) (CANON)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/40_VISUAL/04__VISUAL__VISUAL_CONTINUITY_RULES.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 10_TOPICS / 40_VISUAL
DOC_TYPE: KB_MODULE
KB_TYPE: TOPIC
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.VIS.TOPIC.CONTINUITY.004
OWNER: SYSTEM
ROLE: Practical continuity rules to keep visuals coherent across shots: spatial orientation (axis/eyeline), screen direction, prop/costume continuity, lighting continuity, and motion continuity. Includes failure modes and mini QA checklist. No montage decisions.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created visual continuity topic: spatial, prop/costume, lighting, and motion continuity with failure modes and mini checklist."
- REASON: "Continuity breaks kill believability and clarity; entities need a deterministic baseline to avoid accidental contradictions."
- IMPACT: "More coherent scenes, fewer viewer confusion moments, stronger perceived production quality."
- CHANGE_ID: UE.CHG.2026-01-14.KB.VIS.TOPIC.004

---

## 0) SCOPE (BOUNDARY)
COVERS:
- continuity rules that prevent viewer confusion
- what must remain consistent across shots
- how to detect continuity breaks and fix them

EXCLUDES:
- montage/edit decisions (out of scope)
- narrative continuity (plot logic) beyond visual coherence
- deep production logistics (handled in production domain)

---

## 1) CONTINUITY = COHERENT MENTAL MAP
Viewer builds a mental map:
- who is where
- what is where
- what is happening now
Continuity keeps that map stable unless you intentionally break it.

---

## 2) SPATIAL CONTINUITY (ORIENTATION)
### 2.1 Axis (180°) coherence
- Keep camera on one side of the axis for a given interaction.
- If you must cross:
  - re-establish orientation (neutral/wide) before/after.

Failure symptom:
- characters swap sides unexpectedly.

### 2.2 Eyeline continuity
- gaze direction must match target position across shots.
Failure symptom:
- character looks left, target appears left, but later appears right.

### 2.3 Screen direction continuity
- movement direction should remain consistent:
  - left→right stays left→right unless you explicitly show a turn/reversal.
Failure symptom:
- chase feels like teleport or flip.

### 2.4 Spatial anchors
Use stable anchors to keep space readable:
- wide/master that shows geometry
- repeated landmark elements (doorway, window, sign)
- consistent foreground framing elements

---

## 3) PROP & COSTUME CONTINUITY
Continuity applies to:
- objects (prop position, orientation, state)
- wardrobe (open/closed, damaged/clean)
- hair/makeup (state changes)

Rules:
- if a prop changes state, show the change (cause) or accept it as a continuity break.

Failure symptom:
- object teleports or switches hand without motivation.

Practical:
- track “state variables”:
  - PROP_STATE: location, orientation, damage, held-by
  - COSTUME_STATE: open/closed, wet/dry, dirty/clean

---

## 4) LIGHTING CONTINUITY (DIRECTION & INTENSITY LOGIC)
Lighting continuity is not “same setup always”.
It means internal logic is consistent.

Track:
- key direction (where the main light comes from)
- shadow direction consistency
- intensity continuity within a moment (unless time passes)

Allowed changes:
- if you show time change (sun moved)
- if character moves relative to source
- if power/lighting changes are motivated in-scene

Failure symptom:
- shadows flip direction between adjacent shots.

---

## 5) MOTION CONTINUITY (MATCHING ACTION)
Motion continuity keeps action coherent:
- hand reaches → hand continues reach
- head turn direction consistent
- object movement consistent

Rules:
- action direction and speed should not reset across shots without cause.

Failure symptom:
- gesture starts, then “restarts” from a different position.

---

## 6) VISUAL IDENTITY CONTINUITY (MOTIFS, STYLE)
Across a scene/sequence:
- maintain consistent visual “rules”:
  - contrast level (overall)
  - texture realism level
  - camera language (static vs frantic) for that sequence intent

This is not a fixed palette; it’s consistency of principles.

Failure symptom:
- sudden style shift that feels like “different project”.

---

## 7) COMMON FAILURE MODES (AND FIXES)
### F1 — Spatial flip (axis crossed)
Symptoms:
- sides swap; dialogue geography breaks
Fix:
- re-establish with a wide/master
- keep camera on one side of axis for the block

### F2 — Eyeline mismatch
Symptoms:
- looking directions don’t align with target
Fix:
- re-anchor target position first
- use OTS or insert target shot with correct screen position

### F3 — Prop teleport
Symptoms:
- object changes hand/position between shots
Fix:
- show the transfer, OR keep consistent state

### F4 — Shadow direction flip
Symptoms:
- key direction changes with no motivation
Fix:
- align lighting direction logic across adjacent shots
- motivate change (source move, time shift, practical switch)

### F5 — Action mismatch
Symptoms:
- gesture discontinuity
Fix:
- define the “action beat” start/end and maintain it across framing variations

### F6 — Style drift
Symptoms:
- one shot looks like a different genre/engine
Fix:
- define scene visual constraints (contrast/texture/camera intent) and enforce

---

## 8) CONTINUITY TRACKING (LIGHTWEIGHT)
For scene packs / shotlists, track minimal variables:
- ORIENTATION:
  - axis side, screen direction, landmarks
- PROP_STATE:
  - key props location/state
- LIGHTING_LOGIC:
  - key direction + motivation
- ACTION_BEATS:
  - key action start/end positions

This is enough to prevent most accidental breaks.

---

## 9) MINI CHECKLIST — CONTINUITY QA
CONTINUITY_QA_MINI:
- [ ] Axis coherence maintained (or re-established if crossed)
- [ ] Eyelines match target positions
- [ ] Screen direction consistent for movement
- [ ] Landmark anchors preserve spatial map
- [ ] Key props keep state (location/orientation/held-by)
- [ ] Wardrobe/hair state consistent within moment
- [ ] Key light direction logic consistent (no shadow flip)
- [ ] Action beats match across adjacent shots
- [ ] No unmotivated style drift within a sequence

Result:
- PASS if orientation + props + lighting logic are coherent
- REWORK if minor state mismatches exist (fixable)
- FAIL if viewer likely loses spatial map or sees obvious teleport/flips

---

## 10) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.VIS.TOPIC.SHOT_GRAMMAR.002 | WHY: axis/eyeline/screen direction foundations
- XREF: UE.KB.VIS.TOPIC.LIGHTING.003 | WHY: lighting direction and separation principles
- XREF: UE.KB.VIS.TOPIC.COMPOSITION.001 | WHY: anchor hierarchy helps continuity readability
- XREF: UE.KB.README.TOPICS.VISUAL.001 | WHY: visual realm scope and roadmap

--- END.
