# VISUAL — SHOT GRAMMAR & FRAMING (CANON)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/40_VISUAL/02__VISUAL__SHOT_GRAMMAR_AND_FRAMING.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 10_TOPICS / 40_VISUAL
DOC_TYPE: KB_MODULE
KB_TYPE: TOPIC
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.VIS.TOPIC.SHOT_GRAMMAR.002
OWNER: SYSTEM
ROLE: Practical shot grammar and framing language: shot sizes, coverage, orientation rules (180°/eyeline), POV/OTS usage, and framing intent. Includes failure modes and mini QA checklist. No montage decisions.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created shot grammar topic: framing vocabulary + coverage logic + orientation rules + failure modes + mini checklist."
- REASON: "Entities need a deterministic camera language to communicate shots and avoid orientation confusion."
- IMPACT: "Clearer storyboards/shotlists, fewer continuity/orientation errors, more intentional framing."
- CHANGE_ID: UE.CHG.2026-01-14.KB.VIS.TOPIC.002

---

## 0) SCOPE (BOUNDARY)
COVERS:
- shot sizes and when to use them
- shot purpose (information vs emotion vs orientation)
- coverage basics (what you need to capture, not how to edit)
- orientation coherence: 180° axis, eyeline match, screen direction
- framing patterns: OTS, two-shot, POV, insert

EXCLUDES:
- montage/edit decisions (out of scope)
- blocking/acting direction as performance coaching (separate domain)
- fixed lens prescriptions (use intent, not numbers)

---

## 1) SHOT GRAMMAR = VISUAL LANGUAGE
Every shot answers at least one:
- WHERE are we? (orientation)
- WHO is acting? (subject)
- WHAT changed? (event/turn)
- HOW does it feel? (emotion)
- WHY should we care? (stakes cue)

If a shot answers none — it’s noise.

---

## 2) SHOT SIZES (INFORMATION VS EMOTION)
### Wide / Establishing (WS / Establishing)
Intent:
- orient location, geography, distances, threats
Use when:
- scene begins or location changes
Fail mode:
- too busy wide: no primary subject (fix: composition hierarchy)

### Medium (MS)
Intent:
- balance emotion and context (body language + environment)
Use when:
- dialogue, decision-making, relationship dynamics
Fail mode:
- medium without clear eyeline/orientation: feels “floaty”

### Close-up (CU)
Intent:
- emotion, detail, decision, reveal
Use when:
- reaction matters, key object matters
Fail mode:
- overuse kills rhythm and context (needs occasional wide/medium for grounding)

### Insert / Detail
Intent:
- clarify information without dialogue (clue, action detail)
Use when:
- object interaction, evidence, mechanism
Fail mode:
- insert without context: viewer doesn’t know what it belongs to

---

## 3) COVERAGE (WHAT YOU NEED TO CAPTURE)
Coverage is the set of shots that makes the scene understandable.
It is NOT the edit.

### 3.1 Minimal coverage set (practical baseline)
- One orienting shot (wide or establishing)
- Two shots for interaction (two-shot / OTS pair / medium pair)
- Reactions (at least one reaction when emotional causality matters)
- Inserts (only when information needs it)

### 3.2 Coverage selection rule
Pick coverage based on:
- clarity needs (orientation/space)
- emotional causality (reaction)
- information payload (insert)
- tension (what to hide vs show)

If you don’t need it, don’t shoot it.

---

## 4) ORIENTATION RULES (COHERENCE)
### 4.1 180-degree rule (axis)
Purpose:
- maintain consistent left/right positions and movement direction
Use:
- dialogues, standoffs, chases, any spatial relation that matters
Break intentionally only if:
- you establish a re-orientation shot, OR
- you want disorientation as a deliberate effect

Common fail:
- crossing axis accidentally → viewer loses “who is where”.

### 4.2 Eyeline match
Purpose:
- if character looks screen-left, the object looked at must plausibly be screen-left in the next shot
Fail:
- eyes look “wrong direction” → feels fake and confusing

### 4.3 Screen direction
Purpose:
- keep consistent movement direction across cuts (left→right stays left→right)
Fail:
- character runs left→right then suddenly right→left without reason

---

## 5) FRAMING PATTERNS (WHEN/WHY)
### OTS (over-the-shoulder)
Use when:
- you need relationship context and orientation in dialogue
Strength:
- shows both speaker and listener’s spatial relation
Fail:
- shoulder blocks face, or both OTS look identical (no variation)

### Two-shot
Use when:
- relationship tension/distance is the point
Strength:
- shows dynamics and power distance
Fail:
- two-shot without hierarchy (both equal weight when one should lead)

### POV (subjective shot)
Use when:
- perception matters (fear, discovery, target focus)
Risk:
- can confuse orientation without prior establishing/eyeline logic

### Master shot
Use when:
- you need a stable baseline of whole action
Fail:
- master without readable staging → chaos

### Static vs moving frame (intent-level)
Static:
- stability, observation, control
Movement:
- reveal, follow, tension, instability
Rule:
- movement must have intent (follow/reveal/pressure), not “because cool”.

---

## 6) “WHAT TO SHOW” VS “WHAT TO HIDE”
Shot grammar controls information.
- Show to orient and confirm.
- Hide to create tension and curiosity.

Practical:
- use inserts/reveals to control timing of information
- use reactions to show consequences

This is still not montage; it’s shot intent.

---

## 7) COMMON FAILURE MODES (AND FIXES)
### F1 — No establishing orientation
Symptoms:
- viewer doesn’t know where people are
Fix:
- add establishing/wide or clear master with readable staging

### F2 — Axis crossed accidentally
Symptoms:
- sides swap; audience confused
Fix:
- re-anchor with neutral shot / move camera along axis; keep consistent side

### F3 — Eyeline mismatch
Symptoms:
- character looks left but “sees” something on right
Fix:
- correct eyelines; use OTS or establish object location first

### F4 — Coverage overload
Symptoms:
- too many shots, same info repeated
Fix:
- keep minimal coverage set; choose purpose for every shot

### F5 — Close-up spam
Symptoms:
- loss of spatial context; emotional monotony
Fix:
- alternate CU with MS/WS for grounding

### F6 — “Cool shot” without function
Symptoms:
- beautiful but pointless frame
Fix:
- define the shot question (where/who/what/how/why). If none → drop.

---

## 8) MINI CHECKLIST — SHOT GRAMMAR QA
SHOT_GRAMMAR_QA_MINI:
- [ ] Every shot answers at least one question (where/who/what/how/why)
- [ ] Orientation anchor exists (establishing or readable master)
- [ ] Axis (180°) coherence is maintained OR intentionally broken with re-orientation
- [ ] Eyeline match makes sense across related shots
- [ ] Screen direction is consistent when movement matters
- [ ] Coverage is minimal (no redundant repeated info)
- [ ] Inserts exist only when they clarify a necessary detail
- [ ] Movement has intent (follow/reveal/pressure), not decoration

Result:
- PASS if orientation + coherence items are satisfied
- REWORK if 1–2 mismatches exist but fixable
- FAIL if axis/eyeline confusion makes scene hard to parse

---

## 9) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.VIS.TOPIC.COMPOSITION.001 | WHY: hierarchy and edge management support framing clarity
- XREF: UE.KB.REF.GLOSSARY.CINEMA_SHOTS.002 | WHY: standard terms for shot types and camera movement
- XREF: UE.KB.README.TOPICS.VISUAL.001 | WHY: visual realm scope and rules
- XREF: UE.KB.RULE.SCOPE_BOUNDARIES.076 | WHY: prevents domain mixing inside visual topics

--- END.
