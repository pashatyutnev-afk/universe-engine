# KB — SPECIALIST SKILL TAG TAXONOMY (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/40__KB_SPECIALIST_SKILL_TAG_TAXONOMY.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: DICTIONARY
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.DICT.SKILL_TAGS.040
OWNER: SYSTEM
ROLE: Canonical taxonomy of skill tags used by competence packs and entity coverage validation. Ensures consistent labeling across domains (music, narrative, production, marketing, research, meta).

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created canonical skill tag taxonomy for competence packs and coverage checks."
- REASON: "Coverage validation needs a shared tag vocabulary; otherwise packs are not comparable and gaps cannot be detected."
- IMPACT: "Entities can be validated for skill coverage; packs become modular and composable."
- CHANGE_ID: UE.CHG.2026-01-14.KB.DICT.040

---

## 0) PURPOSE (KB)
Define a stable set of SKILL_TAGS used in:
- competence packs (capability labeling)
- entity coverage validation
- gap detection and planning

Rule:
- Only tags from this taxonomy are allowed for coverage checks.

---

## 1) TAG FORMAT (STRICT)
- Tag style: `domain.subdomain.capability`
- Lowercase, underscore allowed
- Examples:
  - `music.vocals.performance_direction`
  - `music.mix.translation_check`
  - `narrative.scene.turning_point`
  - `production.release.packaging`
  - `marketing.positioning.archetype`

---

## 2) DOMAIN TAG SETS (CANON)

### 2.1 MUSIC (SOUND/MUSIC)
music.structure.song_form
music.hook.hook_window
music.hook.hook_design
music.lyrics.rhyme_meter
music.lyrics.stress_safe_writing
music.vocals.performance_direction
music.vocals.role_contrast_ab
music.vocals.articulation_diction
music.arrangement.instrumentation
music.arrangement.dynamic_contrast
music.genre.fingerprint_markers
music.genre.fusion_balance
music.mix.balance_tight_lowend
music.mix.translation_check
music.mix.mono_safety
music.mix.frequency_management
music.master.loudness_consistency
music.master.distortion_guard
music.ugc.moment_engineering
music.ugc.loop_safe_edit
music.uniqueness.repeat_guard
music.uniqueness.collision_avoidance
music.prompt.negative_specs
music.prompt.phrasebook_deltas

### 2.2 NARRATIVE
narrative.scene.objective_obstacle
narrative.scene.turning_point
narrative.structure.beat_sheet
narrative.arc.dramatic_arc
narrative.pacing.rhythm_density
narrative.tension.stakes_ladder
narrative.tension.escalation
narrative.foreshadow.plant_payoff
narrative.twist.reveal_timing
narrative.continuity.consistency_check
narrative.dialogue.subtext
narrative.dialogue.voice_rhythm
narrative.cliffhanger.end_hook

### 2.3 CHARACTER
character.motivation.need_want
character.values.moral_axis
character.psychology.triggers_defenses
character.trauma.growth_map
character.behavior.habits_tells
character.relationship.conflict_loops
character.voice.speech_fingerprint
character.consistency.action_fit_check
character.evolution.change_over_time

### 2.4 WORLD
world.structure.physical_rules
world.laws.possible_impossible
world.timeline.epochs_transitions
world.civilization.governance_model
world.power.conflict_systems
world.geopolitics.alliances_borders
world.economy.resource_constraints
world.ecology.environment_hazards
world.technology.limits_failure_modes
world.consistency.contradiction_check

### 2.5 VISUAL
visual.composition.hierarchy_focal
visual.composition.balance_rhythm
visual.style.fingerprint_principles
visual.camera.shot_grammar
visual.camera.movement_constraints
visual.lighting.contrast_readability
visual.lighting.mood_logic
visual.storyboard.blocking_diagrams
visual.continuity.identity_motifs
visual.imagegen.constraints_negative
visual.risk.limitations_explicit

### 2.6 PRODUCTION
production.pipeline.step_handoffs
production.handoff.inputs_outputs
production.format.adaptation_rules
production.release.packaging
production.release.variant_strategy
production.qa.gates_rubrics
production.qa.regression_guard
production.versioning.change_note
production.delivery.naming_discipline

### 2.7 MARKETING
marketing.positioning.archetype
marketing.audience.segments_personas
marketing.packaging.titles_hooks
marketing.packaging.descriptions_hashtags
marketing.distribution.channel_strategy
marketing.launch.release_window
marketing.engagement.loop_design
marketing.seo.discovery_keywords
marketing.monetization.offer_ladder
marketing.monetization.funnel_mapping

### 2.8 META / GOVERNANCE
meta.kb.navigation_master_index
meta.kb.usage_no_fantasy
meta.kb.memory_anti_drift
meta.kb.gap_handling
meta.kb.qa_audit
meta.kb.deprecation_pointers
meta.kb.uid_only_xref

---

## 3) TAG USAGE RULES
- Competence pack capabilities MUST be tagged with 1–3 SKILL_TAGS.
- Coverage checks compare required tags to available pack tags.
- If a needed tag does not exist:
  - add it here (taxonomy update) before using it in packs.

---

## 4) HARD FAIL CONDITIONS
FAIL IF:
- pack uses tags not listed here (for coverage validation)
- tag format is violated
- tags mix multiple domains in one tag

---

## 5) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.STD.COMP_PACK.036 | WHY: competence pack standard requires capability labeling
- XREF: UE.KB.STD.ENTITY_COMP_BIND.039 | WHY: entity binding rules use tags for coverage targets

--- END.
