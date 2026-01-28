# VISUAL — COMPOSITION FOUNDATIONS (CANON)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/40_VISUAL/01__VISUAL__COMPOSITION_FOUNDATIONS.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 10_TOPICS / 40_VISUAL
DOC_TYPE: KB_MODULE
KB_TYPE: TOPIC
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.VIS.TOPIC.COMPOSITION.001
OWNER: SYSTEM
ROLE: Foundational composition principles for readable, intentional frames: hierarchy, focal control, visual flow, depth layers, balance, and common failure modes. Designed for storyboards, shotlists, and image generation constraints (no montage decisions).

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created VISUAL composition foundations topic: hierarchy, focal control, flow, depth, balance, and a practical mini-checklist."
- REASON: "Composition controls clarity and perceived quality; entities need a deterministic baseline to avoid clutter and unreadable frames."
- IMPACT: "More readable shots, stronger focus, fewer 'visual soup' outputs."
- CHANGE_ID: UE.CHG.2026-01-14.KB.VIS.TOPIC.001

---

## 0) SCOPE (BOUNDARY)
COVERS:
- composition principles that improve readability and intent
- practical checks for storyboard/frame evaluation
- common failure modes and fixes

EXCLUDES:
- montage/editing decisions (out of scope)
- fixed color palettes (use color principles only)
- narrative structure (handled elsewhere)

---

## 1) CORE IDEA
Composition is a control system for attention:
- you decide what the viewer notices first (PRIMARY)
- what they notice second (SECONDARY)
- and what supports context (BACKGROUND)

If you don’t decide — randomness decides, and the frame becomes noise.

---

## 2) COMPOSITION HIERARCHY (PRIMARY → SECONDARY → CONTEXT)
### 2.1 Define the PRIMARY subject
Ask:
- What is the single most important thing in this frame?
- If the viewer sees only 1 second, what must they understand?

Make PRIMARY unmistakable via:
- size / scale
- contrast (light/dark, sharp/soft, detail/no-detail)
- isolation (negative space)
- leading lines and framing
- motion (if present)
- focus and sharpness (if applicable)

### 2.2 Define the SECONDARY subject
SECONDARY supports the primary:
- reaction face
- key object
- threat location
- spatial relation cue

Rule:
- SECONDARY must not compete with PRIMARY in contrast and detail.

### 2.3 Context supports, not fights
Background must:
- provide orientation (where are we?)
- reinforce mood/meaning
- avoid stealing attention

---

## 3) VISUAL FLOW (WHERE EYES TRAVEL)
People scan:
- high-contrast edges
- faces/eyes/hands
- readable text shapes
- bright highlights
- sharp detail

Use flow tools:
- leading lines (roads, beams, shadows, gaze direction)
- framing devices (doorways, windows, arches, shoulders)
- repetition and rhythm (pattern guiding the eye)
- anchors (one clear focal point)

Anti-flow (bad):
- too many equal-contrast “anchors”
- busy texture everywhere
- random bright spots at edges (edge attraction)

---

## 4) DEPTH & LAYERS (FOREGROUND / MID / BACK)
Depth makes frames readable and cinematic.

### 4.1 Three-layer thinking
- FOREGROUND: framing element or texture (optional)
- MIDGROUND: main action/characters (often PRIMARY)
- BACKGROUND: context and scale

### 4.2 Separation techniques (principles)
- value separation (light/dark separation between subject and background)
- detail separation (subject more detailed than background)
- edge separation (rim highlights/shadow edges)
- atmospheric separation (softness/haze behind)
- geometry separation (subject silhouette against clean shape)

No fixed palette required — only separation principle.

---

## 5) BALANCE (STABLE VS UNSTABLE)
Balance is not symmetry. Balance is perceived weight.

### 5.1 Visual weight drivers
- brightness and contrast
- size
- saturation-like intensity (as a principle)
- sharpness/detail
- faces/text-like shapes

### 5.2 Stable vs unstable frames
- Stable: calm, control, safety, formality
- Unstable: tension, threat, imbalance, anxiety

Rule:
- Use instability intentionally (do not accidentally create it via clutter).

---

## 6) FRAMING & NEGATIVE SPACE
### 6.1 Negative space (empty space) is a tool
- isolates subject
- creates clarity
- supports mood (loneliness, calm, threat)

### 6.2 “Edge management”
Edges of the frame are powerful:
- bright edges steal attention
- cut-off limbs/objects feel wrong if unintentional
- tangents (object edge touching subject outline) create visual confusion

Practical:
- keep edges quieter than the center focus
- avoid accidental tangents
- avoid unmotivated cropping

---

## 7) COMPOSITION HEURISTICS (LABELED AS HEURISTIC)
These are tools, not laws:
- rule of thirds: a fast placement heuristic for focus points
- symmetry: use for order, ritual, authority
- centered framing: use for power, isolation, “locked” attention
- diagonal composition: use for motion and instability
- triangle composition: use for group dynamics

If a heuristic conflicts with clarity/hierarchy, clarity wins.

---

## 8) COMMON FAILURE MODES (AND FIXES)
### F1 — “Visual soup” (all details equal)
Symptoms:
- no clear primary
- viewer’s eyes jump randomly
Fix:
- reduce background detail
- isolate subject with negative space and value separation
- reduce competing highlights

### F2 — Competing focal points
Symptoms:
- two bright faces, two equally sharp objects
Fix:
- pick the one true primary
- reduce contrast/detail on the other

### F3 — Edge attraction
Symptoms:
- bright lamp at edge, blown highlight in corner
Fix:
- darken/soften edges
- move bright elements inward only if meaningful

### F4 — Tangents and silhouette confusion
Symptoms:
- object edge aligns with head/shoulder outline
Fix:
- separate shapes, adjust angle, create clear silhouette

### F5 — Flatness (no depth cues)
Symptoms:
- everything in one plane, hard to parse space
Fix:
- add layering, overlap, perspective cues, separation by value/detail

---

## 9) MINI CHECKLIST (FAST QA) — COMPOSITION READABILITY
COMPOSITION_QA_MINI:
- [ ] PRIMARY subject is obvious in 1 second
- [ ] SECONDARY supports and does not compete
- [ ] Background gives context without stealing attention
- [ ] Eye flow leads toward PRIMARY (not to edges)
- [ ] At least one separation principle is present (value/detail/edge/geometry)
- [ ] Edges are quiet (no unmotivated bright corners)
- [ ] No accidental tangents; silhouette is readable
- [ ] Frame feels intentionally stable/unstable (not accidental)

Result:
- PASS if all critical items (PRIMARY, competition, edges, silhouette) are OK
- REWORK if 1–2 items fail
- FAIL if PRIMARY unclear or competition/edge attraction dominates

---

## 10) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.README.TOPICS.VISUAL.001 | WHY: visual realm boundaries and usage order
- XREF: UE.KB.REF.GLOSSARY.CINEMA_SHOTS.002 | WHY: framing language terms used in shotlists/storyboards
- XREF: UE.KB.RULE.SCOPE_BOUNDARIES.076 | WHY: prevents mixing domains inside visual topics
- XREF: UE.KB.RULE.SCOPE_MODULE_LOAD.074 | WHY: load constraints/gates before topics when applicable

--- END.
