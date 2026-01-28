# VISUAL — STORYBOARD METHOD & SHOTLIST (CANON)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/40_VISUAL/05__VISUAL__STORYBOARD_METHOD_SHOTLIST.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 10_TOPICS / 40_VISUAL
DOC_TYPE: KB_MODULE
KB_TYPE: TOPIC
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.VIS.TOPIC.STORYBOARD_SHOTLIST.005
OWNER: SYSTEM
ROLE: Deterministic method to translate a scene into storyboard beats and a practical shotlist: shot purpose, coverage planning, continuity notes, lighting intent, and risk notes. Provides a shotlist schema and mini QA checklist. No montage decisions.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created storyboard/shotlist method: scene→beats→coverage→shotlist schema with continuity + lighting intent + risks."
- REASON: "Entities need a repeatable way to plan visuals; without a method, shots become random and continuity breaks."
- IMPACT: "More coherent shot plans, clearer communication, fewer missing coverage issues."
- CHANGE_ID: UE.CHG.2026-01-14.KB.VIS.TOPIC.005

---

## 0) SCOPE (BOUNDARY)
COVERS:
- method: convert scene intent into shots
- storyboard beat planning
- shotlist schema (fields)
- continuity + lighting intent + risk notes
- mini QA checklist for shotlists

EXCLUDES:
- montage/editing decisions (out of scope)
- drawing technique (art skill)
- production scheduling/logistics

---

## 1) CORE IDEA
Storyboard is “thinking in frames”.
Shotlist is “operationalizing frames”.

Goal:
- make the scene understandable, emotional, and coherent
- with minimal but sufficient coverage
- without relying on “fix it in edit”

---

## 2) INPUTS (WHAT YOU NEED BEFORE SHOTLIST)
Minimum inputs:
- Scene purpose: what changes by end of scene
- Scene location/time context
- Primary conflict/tension beat (high-level)
- Who is in scene and what they want (high-level)

If any input is missing:
- you can still make a provisional shotlist, but mark unknowns.

---

## 3) SCENE → BEATS (DETERMINISTIC)
Break the scene into BEATS (micro changes), each beat should have:
- BEAT_INTENT: what shifts (info/emotion/power)
- BEAT_ACTION: what happens physically
- BEAT_STAKES: why it matters now (even small)

Rule:
- If a beat has no change, it’s not a beat (it’s filler).

---

## 4) BEATS → COVERAGE PLAN (MINIMAL SET)
For each beat, choose coverage by purpose:

### Orientation coverage
- Use when: entering a new space, changing geometry, introducing threats
- Typical: establishing/wide or readable master

### Interaction coverage
- Use when: dialogue, power exchange, negotiation
- Typical: two-shot and/or OTS pair + reactions

### Information coverage
- Use when: object/action detail matters
- Typical: insert/detail shot + confirmation reaction

### Emotion coverage
- Use when: reaction is the real event
- Typical: CU reaction + context anchor (MS/WS)

Rule:
- Choose the smallest set that answers:
  - where/who/what/how/why

---

## 5) SHOTLIST SCHEMA (CANON FIELD SET)
Use this schema for each shot entry.

SHOT_ENTRY:
- SHOT_ID: S-001
- BEAT_ID: B-01
- PURPOSE: ORIENT | INFO | EMOTION | TENSION | TRANSITION
- SHOT_TYPE: WS | MS | CU | INSERT | OTS | POV | TWO_SHOT | MASTER
- SUBJECT (PRIMARY):
- ACTION (what happens in this shot):
- KEY INFO (if any):
- CAMERA INTENT:
  - STATIC | PAN | TILT | DOLLY/TRACK | HANDHELD (intent-level)
- FRAMING NOTES:
  - composition hierarchy / negative space / focal point
- CONTINUITY NOTES:
  - axis side / eyeline / screen direction
  - prop state variables (if relevant)
- LIGHTING INTENT (principles):
  - local contrast target / separation method / motivation
- RISK NOTES (constraints/risks only):
  - readability risks / continuity risks / VFX constraints / crowd complexity
- SUCCESS CRITERIA (observable):
  - what viewer must understand/feel after 1–3 seconds

Notes:
- Do not prescribe edit/cut order here. Shotlist is capture plan.

---

## 6) STORYBOARD BEAT CARD (OPTIONAL, QUICK)
For quick storyboard planning, use a beat card:

STORYBOARD_BEAT_CARD:
- BEAT_ID:
- CHANGE:
- PRIMARY SUBJECT:
- VISUAL METAPHOR/MOTIF (optional):
- REQUIRED SHOTS:
  - <shot ids>
- CONTINUITY ANCHOR:
- RISK:

---

## 7) COMMON FAILURE MODES (AND FIXES)
### F1 — No orientation anchors
Symptoms:
- viewer doesn’t know where they are
Fix:
- add establishing/master for new location or geometry

### F2 — Coverage overload
Symptoms:
- too many redundant shots
Fix:
- remove shots that don’t add info/emotion; keep minimal set

### F3 — Missing critical insert
Symptoms:
- key action unclear (button, weapon, clue)
Fix:
- add insert + reaction confirming meaning

### F4 — Continuity not tracked
Symptoms:
- axis flips, props teleport, direction confusion
Fix:
- fill continuity notes per shot; set axis side per beat

### F5 — Lighting intent absent
Symptoms:
- later frames become muddy/flat by default
Fix:
- set separation method per shot (value/edge/background control)

### F6 — Success criteria missing
Symptoms:
- shots exist but no one knows why
Fix:
- write 1-line success criteria: what viewer must get

---

## 8) MINI CHECKLIST — SHOTLIST QA
SHOTLIST_QA_MINI:
- [ ] Every shot has a PURPOSE (not “because cool”)
- [ ] Every beat has a defined change (beat intent)
- [ ] Orientation anchors exist where needed (new space/geometry)
- [ ] Coverage is minimal but sufficient (no redundancy)
- [ ] Continuity notes exist for axis/eyeline/screen direction when relevant
- [ ] Prop state tracked for key props
- [ ] Lighting intent includes separation method + motivation (principles)
- [ ] Each shot has success criteria (observable)
- [ ] Risk notes capture constraints (not montage decisions)

Result:
- PASS if purpose+beats+continuity+success criteria are present
- REWORK if a few shots miss intent/notes
- FAIL if orientation/continuity is untracked or purpose is undefined

---

## 9) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.VIS.TOPIC.SHOT_GRAMMAR.002 | WHY: shot types + orientation rules underpin shotlists
- XREF: UE.KB.VIS.TOPIC.CONTINUITY.004 | WHY: continuity variables must be tracked in shot entries
- XREF: UE.KB.VIS.TOPIC.LIGHTING.003 | WHY: lighting intent uses contrast/separation principles
- XREF: UE.KB.VIS.TOPIC.COMPOSITION.001 | WHY: hierarchy and readability guide framing notes
- XREF: UE.KB.REF.GLOSSARY.CINEMA_SHOTS.002 | WHY: consistent terminology in shotlist fields

--- END.
