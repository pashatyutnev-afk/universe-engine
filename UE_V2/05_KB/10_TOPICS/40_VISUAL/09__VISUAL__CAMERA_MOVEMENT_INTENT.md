# VISUAL — CAMERA MOVEMENT INTENT (WHEN/WHY/RISKS) (CANON)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/40_VISUAL/09__VISUAL__CAMERA_MOVEMENT_INTENT.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 10_TOPICS / 40_VISUAL
DOC_TYPE: KB_MODULE
KB_TYPE: TOPIC
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.VIS.TOPIC.CAMERA_MOVEMENT.009
OWNER: SYSTEM
ROLE: Intent-first camera movement guidance: when to move vs stay static, what each movement communicates, and how to avoid disorientation and readability loss. Focuses on principles, constraints, and risks (no choreography, no montage).

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created camera movement intent topic: decision rules, meaning of movement types, risk controls, and mini QA checklist."
- REASON: "Camera motion is powerful but easily degrades clarity; entities need intent rules and guardrails."
- IMPACT: "Fewer disorienting shots, better readability, more coherent visual language."
- CHANGE_ID: UE.CHG.2026-01-14.KB.VIS.TOPIC.009

---

## 0) SCOPE (BOUNDARY)
COVERS:
- decision rules: move vs static
- movement types as meaning (intent-level)
- risk management: clarity/orientation/motion sickness
- mini checklist

EXCLUDES:
- blocking choreography and exact camera paths
- montage/edit decisions
- hardware/rig tutorials

---

## 1) CORE RULE
Camera movement must answer:
- “Why must the camera move for this moment?”
If the answer is “to look cool” — default to static.

Movement is a meaning amplifier, not decoration.

---

## 2) WHEN TO STAY STATIC (DEFAULT)
Static is powerful when:
- dialogue clarity matters
- orientation must be stable
- tension comes from stillness (waiting, threat, ritual)
- you want the viewer to observe, not chase

Static supports:
- composition hierarchy
- readable action beats
- clean eyelines

---

## 3) WHEN TO MOVE (VALID INTENTS)
Move only when at least one intent exists:

### I1 — Reveal information
- uncover a new object/space/threat
Risk:
- reveal too fast → viewer misses meaning
Guardrail:
- keep a readable pause on reveal moment

### I2 — Follow action
- maintain subject readability during motion
Risk:
- shaky follow destroys clarity
Guardrail:
- keep subject centered/readable; avoid edge attraction

### I3 — Increase pressure / tension
- subtle push-in (intent: narrowing options, intensifying)
Risk:
- overuse becomes cliché and reduces impact
Guardrail:
- reserve for beats with real escalation

### I4 — Re-orient space
- move to establish geometry or axis
Risk:
- move without anchor makes it worse
Guardrail:
- start/end on clear frames with landmarks

### I5 — Express subjective state
- instability, fear, intoxication, urgency (handheld-like intent)
Risk:
- audience nausea; loss of narrative clarity
Guardrail:
- keep action readable; use in bursts; re-anchor often

---

## 4) MOVEMENT TYPES (MEANING-LEVEL)
These are categories of intent, not rig specs.

**Pan (горизонтальный поворот)**
- Meaning: scanning, revealing space, following subject laterally
- Risk: pan too fast → blur/lose focal point

**Tilt (вертикальный поворот)**
- Meaning: reveal scale/height, discovery, intimidation
- Risk: losing horizon/orientation

**Push-in / Pull-out (приближение/отъезд)**
- Meaning: intimacy, pressure, realization / relief, context reveal
- Risk: constant push-ins feel manipulative

**Track / Dolly (проезд)**
- Meaning: presence, pursuit, guided reveal, smooth following
- Risk: motion without purpose becomes “floating”

**Handheld / Instability intent**
- Meaning: chaos, realism, anxiety
- Risk: readability collapse; motion sickness

**Static with subject motion**
- Meaning: stable observer; subject reveals themselves via movement
- Often stronger than moving camera.

---

## 5) ORIENTATION & CONTINUITY GUARDRAILS
Movement easily breaks:
- axis coherence
- screen direction
- eyelines

Guardrails:
- define axis side before moving
- start/end on anchored frames (landmarks)
- keep screen direction consistent during follow moves
- avoid crossing axis during a move unless you re-establish

---

## 6) READABILITY GUARDRAILS
Movement can destroy readability by:
- smearing detail
- creating edge attraction
- changing focal priority

Guardrails:
- keep PRIMARY subject stable in frame or clearly dominant
- avoid fast motion across high-detail backgrounds
- ensure lighting separation remains during motion (subject doesn’t merge)
- keep edges quiet even while moving

---

## 7) COMMON FAILURE MODES (AND FIXES)
### F1 — “Float cam” (movement with no intent)
Fix:
- remove movement or assign a clear intent (reveal/follow/pressure)

### F2 — Disorientation
Symptoms:
- viewer loses where/who
Fix:
- add orientation anchors at start/end; enforce axis and screen direction

### F3 — Motion kills focal hierarchy
Fix:
- reduce speed; simplify background; re-center subject; add separation

### F4 — Handheld overuse
Fix:
- use in short bursts; alternate with static anchors; keep key beats readable

---

## 8) MINI CHECKLIST — CAMERA MOVEMENT QA
CAMERA_MOVEMENT_QA_MINI:
- [ ] Movement has a named intent (reveal/follow/pressure/orient/subjective)
- [ ] If no intent → default static
- [ ] Start and end frames are readable and anchored
- [ ] Movement does not break axis/eyeline/screen direction (or re-established)
- [ ] PRIMARY remains dominant during motion
- [ ] Edges do not steal attention during motion
- [ ] If subjective instability used: timeboxed and re-anchored
- [ ] Movement supports beat change (not filler)

Result:
- PASS if intent + anchors + readability hold
- REWORK if movement is useful but weakly controlled
- FAIL if movement causes disorientation or destroys readability

---

## 9) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.VIS.TOPIC.SHOT_GRAMMAR.002 | WHY: movement must preserve orientation logic
- XREF: UE.KB.VIS.TOPIC.CONTINUITY.004 | WHY: continuity risks increase with movement
- XREF: UE.KB.VIS.GATE.READABILITY.008 | WHY: movement must still pass readability gate
- XREF: UE.KB.VIS.TOPIC.COMPOSITION.001 | WHY: focal hierarchy must remain under motion

--- END.
