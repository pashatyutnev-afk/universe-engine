# 🌌 THEME & MEANING ENGINE
## Canonical Engine Specification  
**LEVEL: L2 · DOMAIN ENGINE · THEME CONTROL · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 10__THEME_MEANING_ENG.md
- ENGINE_ID: L2-DOM-THEME-MEANING-ENGINE-010
- UID: UE.ENT.ENG.DOM.NARRATIVE.THEME_MEANING
- NAME: Theme & Meaning Engine
- CLASS: Domain Engine
- DOMAIN: Narrative
- CATEGORY: Thesis, Themes, Motifs, Symbolic Coherence
- LEVEL: L2
- STATUS: FINAL
- FAILURE_MODE: fail-closed (for thematic coherence)
- EDITABLE: true
- BYPASS_ALLOWED: false (within narrative pipeline)

### ABSOLUTE RULE
> If the story has no thematic spine, events become noise without meaning.

---

## 1. PURPOSE

Theme & Meaning Engine defines and validates the story’s **meaning layer**.

It guarantees:
- explicit thesis (what the story says)
- theme set (what the story explores)
- motif registry (repeating elements that reinforce themes)
- symbolic coherence (symbols are consistent, not random)
- alignment checks between theme and structure/arc/reveals

It does not enforce real-world truth.
It enforces narrative meaning coherence.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define story thesis statement (1–2 sentences)
- Define primary/secondary themes
- Define motif & symbol registry (objects, phrases, images, actions)
- Validate that key beats support themes (not contradict without intent)
- Detect theme drift (story changes what it’s “about” mid-way unintentionally)
- Suggest theme reinforcement beats (non-binding)
- Ensure payoffs carry meaning, not only mechanics

### OUT-OF-SCOPE (FORBIDDEN)
- Causality proof (Narrative Logic Engine)
- Tension design (Tension & Stakes Engine)
- Reveal scheduling (Twist & Reveal Engine)
- Pacing budgets (Pacing & Rhythm Engine)
- Canon authority decisions (Governance)

---

## 3. THEME MODEL

### 3.1 Core Objects
- THESIS: central claim (what it ultimately says)
- THEME: topic explored (power, freedom, identity, faith, sacrifice)
- MOTIF: repeated element that signals theme presence
- SYMBOL: motif with layered meaning that changes through arc
- MEANING_BEAT: beat where thesis/theme crystallizes (explicit or implicit)

### 3.2 Theme Roles (fixed)
- PRIMARY_THEME
- SECONDARY_THEME
- CONTRAST_THEME (counter-theme used to sharpen meaning)

### 3.3 Thematic Coherence Rules
- Thesis must not be self-contradictory
- PRIMARY_THEME must be reinforced at:
  - setup region
  - midpoint region
  - climax/resolution region
- Motifs must appear ≥2 times to count (otherwise they are decoration)

---

## 4. INPUT ARTIFACTS

### 4.1 INPUT — THEME_REQUEST
**REQUIRED FIELDS**
- `theme_id`
- `timestamp`
- `story_goal`
- `structure_plan_ref`
- `arc_plan_ref` (recommended)
- `reveal_schedule_ref` (optional)
- `tension_map_ref` (optional)
- `motifs_seed_list` (optional; may be empty)
- `constraints_refs` (world/character)
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 5. OUTPUT ARTIFACTS

### 5.1 OUTPUT — THEME_PACKAGE
- `theme_id`
- `thesis_statement`
- `themes` (list: {theme, role, notes})
- `motif_registry` (list: {motif_id, motif, theme_link, planned_appearances})
- `symbol_registry` (optional list: {symbol_id, symbol, meaning_layers, evolution_notes})
- `meaning_beats_map` (segment_id → meaning notes)
- `theme_alignment_constraints` (rules for downstream scenes)
- `repair_suggestions` (non-binding)
- `trace_id` (if provided)

### 5.2 OUTPUT — THEME_VERDICT
- `theme_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 6. CORE OPERATIONS

- OP_01: DRAFT_THESIS
- OP_02: SELECT_THEME_SET (primary/secondary/contrast)
- OP_03: BUILD_MOTIF_AND_SYMBOL_REGISTRIES
- OP_04: MAP_MEANING_BEATS_TO_STRUCTURE
- OP_05: CHECK_THEME_DRIFT_AND_CONTRADICTIONS
- OP_06: EMIT_THEME_PACKAGE

---

## 7. ACCESS MODEL

### WRITE
- Domain pipeline outputs only

### READ
- Scene Construction Engine (meaning beats constraints)
- Genre/Style engines (symbolism/emotional resonance alignment)
- Continuity Engine (motif persistence, avoid accidental drop)

### DELETE
- Allowed for drafts; finalization per project governance

---

## 8. DEPENDENCIES

### REQUIRED
- Story Structure Engine (anchor regions)
- Dramatic Arc Engine (peak + resolution mapping)
- Optional: Twist & Reveal Engine (meaning-sensitive reveals)

### FORBIDDEN
- Treating theme package as canon authority
- Forcing moral judgement as system governance

---

## 9. FAILURE CONDITIONS (FAIL-CLOSED FOR THEME)

CRITICAL:
- No thesis statement
- PRIMARY_THEME has no reinforcement near midpoint and end
- Motifs listed but never appear in plan (0 planned_appearances)
- Theme drift: thesis changes to opposite without intention markers
- Climax/resolution contains no meaning beat (pure mechanics only)

Reaction:
- Verdict INVALID (CRITICAL)
- Provide repairs: add meaning beats, reinforce motif placement, clarify thesis.

---

## 10. TRACE RULES

- trace_id optional unless orchestrator requires traced pipeline
- if present, propagate to downstream outputs

---

## 11. NON-GOALS
- Does not validate truth
- Does not decide reveals
- Does not write prose
- Does not grant canon authority

---

## 12. FINAL STATEMENT

Theme is what the story means.
Meaning is what stays after the plot ends.

---

**STATUS:** Theme & Meaning Engine v1.0  
**DOMAIN:** ACTIVE
