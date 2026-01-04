# 🧩 STORY STRUCTURE ENGINE
## Canonical Engine Specification  
**LEVEL: L2 · DOMAIN ENGINE · STRUCTURE SCAFFOLDING · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 02__STORY_STRUCTURE_ENG.md
- ENGINE_ID: L2-DOM-STORY-STRUCTURE-ENGINE-002
- UID: UE.ENT.ENG.DOM.NARRATIVE.STORY_STRUCTURE
- NAME: Story Structure Engine
- CLASS: Domain Engine
- DOMAIN: Narrative
- CATEGORY: Acts, Sequences, Beats & Structural Plans
- LEVEL: L2
- STATUS: FINAL
- FAILURE_MODE: fail-closed (for structure validity)
- EDITABLE: true (domain evolution allowed)
- BYPASS_ALLOWED: false (within narrative pipeline)

### ABSOLUTE RULE
> If the story has no structure, it cannot be paced, escalated, or resolved deterministically.

---

## 1. PURPOSE

Story Structure Engine produces the **structural blueprint** of a narrative.

It guarantees:
- explicit segmentation (acts / sequences / scenes / beats)
- role assignment for segments (setup / escalation / reversal / resolution)
- placement of key structural anchors (inciting incident, midpoint, etc.)
- compatibility with downstream engines (arc/pacing/tension/continuity)

This engine does not write prose.
It writes the **plan**.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Choose a structure template (3-act, 5-act, episodic, quest, heist, etc.)
- Decompose story into acts → sequences → scenes → beats
- Assign function tags to segments
- Produce structure constraints for pacing/tension engines
- Detect missing anchors (no inciting, no midpoint, no climax)
- Provide structural repair suggestions (non-binding)

### OUT-OF-SCOPE (FORBIDDEN)
- Causality validation (Narrative Logic Engine)
- Emotional escalation design (Dramatic Arc Engine)
- Micro-scene composition (Scene Construction Engine)
- Reveal strategy (Twist/Reveal Engine)
- Canon authority (Governance)

---

## 3. STRUCTURE MODEL

### 3.1 Hierarchy (fixed)
- STORY
  - ACT
    - SEQUENCE
      - SCENE
        - BEAT

### 3.2 Segment Fields (minimum)
Every segment (act/sequence/scene/beat) must include:
- `id`
- `type`
- `summary`
- `function_tag` (see below)
- `stakes_level` (LOW/MEDIUM/HIGH)
- `inputs` (what must already be true)
- `outputs` (what becomes true after)
- `dependencies` (refs to events/constraints)

### 3.3 Canonical Function Tags (fixed set)
- SETUP
- INCITING_INCIDENT
- LOCK_IN
- PROGRESS
- COMPLICATION
- REVERSAL
- MIDPOINT_SHIFT
- CRISIS
- CLIMAX
- RESOLUTION
- DENOUEMENT

Tags may repeat, but anchors must exist (see section 9).

---

## 4. INPUT ARTIFACTS

### 4.1 INPUT — STRUCTURE_REQUEST
**REQUIRED FIELDS**
- `structure_id`
- `timestamp`
- `format_target` (film/series/short/mini-episode/book/etc.)
- `structure_template` (if omitted → engine selects)
- `story_goal`
- `constraints_refs` (world/character)
- `event_set_ref` (recommended; from Narrative Logic Engine)
- `trace_id` (optional)

Missing any required fields → REJECT.

### 4.2 INPUT — STRUCTURE_TEMPLATE (optional)
A template defines:
- act count
- expected anchors
- typical sequence pattern

---

## 5. OUTPUT ARTIFACTS

### 5.1 OUTPUT — STRUCTURE_PLAN
- `structure_id`
- `template_used`
- `acts` (list)
- `anchors` (map: tag → segment_id)
- `open_threads` (list; continuity inputs for later)
- `constraints` (structural constraints for downstream)
- `trace_id` (if provided)

### 5.2 OUTPUT — STRUCTURE_VERDICT
- `structure_id`
- `verdict` = VALID | INVALID | PARTIAL
- `missing_anchors` (list)
- `gaps` (list)
- `repair_suggestions` (list; non-binding)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 6. CORE OPERATIONS

- OP_01: SELECT_TEMPLATE
- OP_02: DECOMPOSE_TO_HIERARCHY
- OP_03: ASSIGN_FUNCTION_TAGS
- OP_04: PLACE_STRUCTURAL_ANCHORS
- OP_05: CHECK_ANCHORS_AND_GAPS
- OP_06: EMIT_STRUCTURE_PLAN

---

## 7. ACCESS MODEL

### WRITE
- Domain pipeline only (structure plans are domain artifacts)

### READ
- Dramatic Arc Engine (arc mapping)
- Scene Construction Engine (scene specs)
- Pacing & Rhythm Engine (timing constraints)
- Tension & Stakes Engine (escalation curve)
- Continuity Engine (thread tracking)

### DELETE
- Allowed for drafts; finalization depends on project governance

---

## 8. DEPENDENCIES

### REQUIRED
- Narrative Logic Engine output (recommended) for cause/effect grounding
- World/Character constraint references

### FORBIDDEN
- Treating structure plans as canon authority
- Overriding governance locks

---

## 9. VALIDITY RULES (FAIL-CLOSED FOR STRUCTURE)

A STRUCTURE_PLAN is INVALID (CRITICAL) if:
- Missing INCITING_INCIDENT anchor
- Missing MIDPOINT_SHIFT or equivalent pivot
- Missing CLIMAX
- Missing RESOLUTION
- No escalation segments (no COMPLICATION/REVERSAL/CRISIS)

Reaction:
- Verdict INVALID
- Provide repair suggestions (minimal additions or re-tagging)

---

## 10. TRACE RULES

- trace_id optional unless required by orchestrator pipeline
- if present, must propagate to downstream engines’ outputs

---

## 11. NON-GOALS
- Does not write dialogue/prose
- Does not optimize pacing timings (only constraints)
- Does not decide reveals (twists)
- Does not validate truth

---

## 12. FINAL STATEMENT

Structure is the story’s skeleton.
Without a skeleton, nothing downstream can align.

---

**STATUS:** Story Structure Engine v1.0  
**DOMAIN:** ACTIVE
