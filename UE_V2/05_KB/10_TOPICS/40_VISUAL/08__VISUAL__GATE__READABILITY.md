# VISUAL — GATE: READABILITY (CANON)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/40_VISUAL/08__VISUAL__GATE__READABILITY.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 10_TOPICS / 40_VISUAL
DOC_TYPE: KB_MODULE
KB_TYPE: STANDARD
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.VIS.GATE.READABILITY.008
OWNER: SYSTEM
ROLE: Measurable-ish visual readability gate definition for a frame/shot plan: focal clarity, separation, edge control, and orientation coherence (when needed). Produces PASS/REWORK/FAIL. Derived from visual readability checklist but expressed as a gate.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created VISUAL Readability gate definition: test method + pass/rework/fail criteria + examples + linkage to checklist."
- REASON: "Checklist is useful, but gates require explicit criteria and repeatable evaluation for QA/certification."
- IMPACT: "Consistent PASS/REWORK/FAIL decisions for visual clarity across entities."
- CHANGE_ID: UE.CHG.2026-01-14.KB.VIS.GATE.008

---

## 0) SCOPE (BOUNDARY)
COVERS:
- readability evaluation for a single frame/shot/shotlist entry
- fast gate test method and explicit criteria

EXCLUDES:
- montage/edit decisions
- fixed palettes/presets
- acting/performance evaluation

---

## 1) GATE_IDENTITY
GATE_DEFINITION:
- GATE_UID: UE.KB.VIS.GATE.READABILITY.008
- DOMAIN: VISUAL
- TARGET_OUTPUT: Frame / Shot / Shotlist Entry (single unit)
- SKILL_TAGS:
  - visual.readability.primary_subject
  - visual.readability.separation
  - visual.readability.edge_control
  - visual.continuity.orientation (conditional)

Note:
- Skill tags are used as labels; if a canonical skill-tag taxonomy exists elsewhere, map these tags later.

---

## 2) TEST_METHOD
### WHAT_TO_CHECK
Does the viewer instantly understand:
- what is PRIMARY (focus)
- what the subject is doing / what matters
- where they are (if spatial understanding matters)
without being distracted by edges or confusion.

### HOW_TO_CHECK (PROCEDURE)
1) 1-SECOND TEST (focal clarity):
   - Look at the frame for ~1 second.
   - Question: “What is the PRIMARY subject?”
2) SILHOUETTE TEST (separation):
   - Squint / blur mentally: is the subject silhouette still readable?
3) EDGE SCAN (edge control):
   - Scan corners/edges for bright hotspots or tangents.
4) ORIENTATION CHECK (conditional):
   - If the shot requires space understanding:
     - verify axis/eyeline/screen direction anchor exists.
5) RESULT:
   - classify PASS / REWORK / FAIL by criteria below.

### REQUIRED_INPUTS
- the frame itself OR a textual shot description with framing + lighting intent + continuity notes
- SPACE_MATTERS flag (YES/NO)

### TIMEBOX
- 60–120 seconds per shot entry (fast gate)

---

## 3) CRITERIA (PASS / REWORK / FAIL)
### PASS
All of the following:
- PRIMARY is identifiable in ≤ 1 second (single clear answer).
- Subject is separated from background by at least one clear method (value/edge/detail/background control).
- No dominant edge attraction (corners/edges do not steal focus).
- If SPACE_MATTERS = YES:
  - orientation anchor exists AND axis/eyeline/screen direction are coherent.

### REWORK
Any of the following (but no critical failure):
- PRIMARY is identifiable, but SECONDARY competes mildly.
- Separation exists but weak (subject blends slightly).
- Minor edge attraction exists (fixable by quieting edges).
- If SPACE_MATTERS = YES:
  - orientation is mostly understandable but has 1 inconsistency (eyeline or direction) that can be fixed.

### FAIL
Any critical condition:
- PRIMARY is not identifiable in ≤ 1 second OR multiple competing focal points dominate.
- Subject silhouette is unreadable (merges with background) and no clear separation exists.
- Strong edge attraction dominates attention (viewer pulled to corners/edges).
- If SPACE_MATTERS = YES:
  - viewer likely loses spatial map (axis flip/eyeline mismatch/ no anchor).

---

## 4) THRESHOLDS (OPERATIONAL)
- PRIMARY_CLARITY:
  - PASS: “single obvious primary”
  - FAIL: “two+ competing primaries” OR “cannot name primary”
- SEPARATION:
  - PASS: “silhouette readable with squint test”
  - FAIL: “silhouette collapses into background”
- EDGE_ATTRACTION:
  - PASS: “no bright corner draws attention first”
  - FAIL: “edge hotspot wins over primary”
- ORIENTATION (conditional):
  - PASS: “left/right positions + gaze direction coherent”
  - FAIL: “positions swap or gaze logic breaks”

---

## 5) EXAMPLES (SHORT)
PASS_EXAMPLE (textual):
- “A single character face is clearly primary; background subdued; rim/value separation makes silhouette pop; no bright corners; orientation clear.”

FAIL_EXAMPLE (textual):
- “Two equally bright faces compete; background has bright window on edge; silhouette merges; viewer can’t tell where the threat is.”

---

## 6) NOTES (COMMON PITFALLS)
- Passing composition but failing edges: corners can quietly destroy readability.
- Passing lighting mood but failing local contrast: mood is allowed; unreadability is not.
- SPACE_MATTERS must be explicit: some shots are “emotion-only” where geography is irrelevant.

---

## 7) RELATED_UIDS (UID-ONLY)
RELATED_UIDS (UID-ONLY):
- UE.KB.VIS.CHK.READABILITY.007 | WHY: checklist operationalizes the same checks as ordered items
- UE.KB.VIS.TOPIC.COMPOSITION.001 | WHY: hierarchy and edge control principles behind the gate
- UE.KB.VIS.TOPIC.LIGHTING.003 | WHY: separation via contrast principles
- UE.KB.VIS.TOPIC.SHOT_GRAMMAR.002 | WHY: orientation logic (axis/eyeline) when SPACE_MATTERS
- UE.KB.STD.GATE_DEF.088 | WHY: gate definition standard structure

--- END.
