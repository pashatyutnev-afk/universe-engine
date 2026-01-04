# 🜂 MYTHOLOGY & BELIEF ENGINE
## Canonical Engine Specification  
**LEVEL: L2 · DOMAIN ENGINE · MEANING SYSTEMS · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 09__MYTHOLOGY_BELIEF_ENG.md
- ENGINE_ID: L2-DOM-MYTHOLOGY-BELIEF-ENGINE-009
- UID: UE.ENT.ENG.DOM.WORLD.MYTHOLOGY_BELIEF
- NAME: Mythology & Belief Engine
- CLASS: Domain Engine
- DOMAIN: World
- CATEGORY: Belief Frameworks, Sacred Narratives, Ritual Systems & Legend Layers
- LEVEL: L2
- STATUS: FINAL
- FAILURE_MODE: fail-closed (for belief coherence)
- EDITABLE: true
- BYPASS_ALLOWED: false (within world pipeline)

### ABSOLUTE RULE
> Belief is a world engine: it changes what people do even when it is not “true”.

---

## 1. PURPOSE

Mythology & Belief Engine defines **systems of meaning** that drive behavior at scale.

It produces:
- **BELIEF_SYSTEM_MAP** (belief systems, myths, rituals, institutions)
- truth/legend layering (what is believed vs what is confirmed)
- moral cosmologies (reward/punishment narratives)
- memetic power rules (how ideas spread)
- “sacred constraints” that shape society and geopolitics

This engine supports both religion and ideology, myth and propaganda.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define belief systems (religions, ideologies, cults, civic myths)
- Define sacred narratives (origin, apocalypse, heroes, sins)
- Define rituals, symbols, taboo structures
- Define belief institutions (churches, orders, academies as faith organs)
- Define conversion/spread mechanics (memetics)
- Define schisms, heresies, reform movements
- Define truth layers (CONFIRMED/PLAUSIBLE/LEGEND) per element
- Validate compatibility with world laws, timeline, civilizations, geopolitics
- Detect belief contradictions and provide repair suggestions

### OUT-OF-SCOPE (FORBIDDEN)
- Declaring metaphysical truth as canon authority
- Rewriting timeline facts (Timeline engine owns ordering)
- Building full institutions outside belief context (Civilization engine)
- Canon authority decisions (Governance)

---

## 3. BELIEF MODEL

### 3.1 Belief System Object (required fields)
- `bs_id`
- `name`
- `type` = RELIGION | IDEOLOGY | CULT | CIVIC_MYTH | PROPAGANDA_SYSTEM
- `core_claims` (list of statements)
- `cosmology` (how reality is framed)
- `moral_map` (virtues/sins, reward/punishment narratives)
- `sacred_texts_or_sources` (optional list)
- `rituals` (list: key rituals + purpose)
- `symbols` (list)
- `taboos` (list + consequence)
- `institutions` (list: {inst_id, role, power_tools})
- `conversion_rules` (how belief spreads)
- `schism_rules` (what causes splits)
- `political_alignment` (optional)
- `truth_layer` per claim = CONFIRMED | PLAUSIBLE | LEGEND | UNKNOWN
- `impact_profile` (how it changes behavior/power)

### 3.2 Memetic Spread Factors (0..10)
- simplicity
- emotional_charge
- authority_support
- punishment_intensity
- ritual_binding_strength
- social_reward_strength
- adaptability (syncretism)

---

## 4. INPUT ARTIFACTS

### 4.1 INPUT — BELIEF_REQUEST
**REQUIRED FIELDS**
- `mb_id`
- `timestamp`
- `civilization_passports_refs` (recommended)
- `timeline_model_ref` (recommended)
- `world_lawset_ref` (required)
- `geopolitics_map_ref` (recommended)
- `belief_seed_list` (optional; otherwise engine proposes baseline set)
- `constraints_refs` (project/genre constraints)
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 5. OUTPUT ARTIFACTS

### 5.1 OUTPUT — BELIEF_SYSTEM_MAP
**REQUIRED FIELDS**
- `mb_id`
- `belief_systems` (list of Belief System Objects)
- `belief_distribution_map` (where beliefs dominate; civ/region nodes if available)
- `conflict_points` (taboo collisions, schisms, holy sites)
- `myth_to_history_links` (legend claims mapped to epochs/events with evidence levels)
- `institution_links` (belief institutions → civilization institutions)
- `memetic_spread_model` (factors + expected propagation)
- `propaganda_vectors` (if applicable)
- `consistency_checks` (auto-detected contradictions)
- `trace_id` (if provided)

### 5.2 OUTPUT — MYTH_BELIEF_VERDICT
- `mb_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 6. CORE OPERATIONS

- OP_01: DEFINE_BELIEF_SYSTEM_REGISTRY
- OP_02: DEFINE_CLAIMS_COSMOLOGY_AND_MORAL_MAP
- OP_03: DEFINE_RITUALS_SYMBOLS_TABOOS
- OP_04: DEFINE_INSTITUTIONS_AND_POWER_TOOLS
- OP_05: MAP_TRUTH_LAYERS_AND_MYTH_HISTORY_LINKS
- OP_06: BUILD_MEMETIC_SPREAD_MODEL
- OP_07: RUN_CONSISTENCY_CHECKS
- OP_08: EMIT_BELIEF_SYSTEM_MAP

---

## 7. ACCESS MODEL

### WRITE
- Domain pipeline outputs only

### READ
- Civilization Engine (institutions and norms)
- Geopolitics Engine (ideological blocs and holy wars)
- Conflict & Power Engine (symbolic power, legitimacy)
- Dialogue/Speech engines (belief language constraints)
- Validation engines (cultural accuracy)

### DELETE
- Allowed for drafts; finalization per project governance

---

## 8. DEPENDENCIES

### REQUIRED
- World lawset (metaphysics constraints if any)
- Project constraints (tone/realism)

### FORBIDDEN
- Belief systems with no rituals/symbols (no binding)
- Taboos with no consequences (dead taboo)
- Claims declared CONFIRMED without timeline/law alignment (unless explicitly designed)
- Treating belief map as canon authority

---

## 9. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- No belief systems defined in a society-driven world
- Beliefs contradict civilization norms with no schism/oppression mechanism
- Truth layers absent (everything “true” or everything “unknown”)
- No institutions (belief has no carriers)
- No conflict points (belief has no pressure surfaces)

Reaction:
- Verdict INVALID (CRITICAL)
- Provide repairs: add rituals/institutions, add truth layers, add schisms/conflict points.

---

## 10. TRACE RULES

- trace_id optional unless orchestrator requires traced pipeline
- if present, propagate into geopolitics/conflict continuity references

---

## 11. NON-GOALS
- Does not prove metaphysical truth
- Does not rewrite history
- Does not grant canon authority

---

## 12. FINAL STATEMENT

Myths are engines of action.
Truth matters less than what people are willing to die for.

---

**STATUS:** Mythology & Belief Engine v1.0  
**DOMAIN:** ACTIVE
