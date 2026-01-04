# 🎮 GAME NARRATIVE ENGINE
## Canonical Engine Specification  
**LEVEL: L3 · PRODUCTION FORMAT ENGINE · PLAYER AGENCY PACKAGING · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 08__GAME_NARRATIVE_ENG.md
- ENGINE_ID: L3-PROD-GAME-NARRATIVE-ENGINE-008
- UID: UE.ENT.ENG.PROD.GAME_NARRATIVE
- NAME: Game Narrative Engine
- CLASS: Production Format Engine
- LEVEL: L3
- STATUS: FINAL
- FAILURE_MODE: fail-closed (agency integrity)
- EDITABLE: true

### ABSOLUTE RULE
> A game narrative must respect player agency. If choices are fake, trust is lost.

---

## 1. PURPOSE

Game Narrative Engine packages narrative assets into a **game-ready structure**:
- quest/mission structure
- agency gates (where player choice matters)
- branching containment (bounded branching)
- fail states and recovery loops
- systemic story loops (repeatable gameplay + meaning)
- persistence and consequence tracking

It produces:
- **GAME_NARRATIVE_PACKAGE**
- quest map + choice/consequence constraints for design pipelines

This engine prevents “movie script disguised as gameplay”.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define quest model and progression rules
- Define agency points and their consequence scope
- Define branching strategy and limits
- Define fail states, retries, and narrative recovery
- Define systemic loops (explore/loot/fight/build) as narrative carriers
- Define persistence model (what the world remembers)
- Validate that narrative remains coherent across branches

### OUT-OF-SCOPE (FORBIDDEN)
- Implementing gameplay mechanics
- Infinite branching
- Changing canon truth (unless the project explicitly uses multiverse canon)
- Writing dialogue/scripts (engine sets structure + constraints)

---

## 3. GAME PACKAGE MODEL

### 3.1 Output — GAME_NARRATIVE_PACKAGE (required fields)
- `gnp_id`
- `mode` = LINEAR | HUB_AND_SPOKE | BRANCHING_BOUNDED | SYSTEMIC
- `quest_registry` (required)
- `agency_points` (required)
- `branching_policy` (required)
- `fail_state_model` (required)
- `persistence_model` (required)
- `systemic_loops` (required)
- `rejoin_strategy` (required)
- `integrity_report` (issues + fixes)
- `trace_id` (optional)

Missing any required field → REJECT.

---

## 4. QUEST MODEL

### 4.1 QUEST_SPEC (required fields)
- `quest_id`
- `name`
- `type` = MAIN | SIDE | FACTION | TUTORIAL | REPEATABLE
- `entry_conditions` (flags/items/reputation)
- `goals` (list)
- `stages` (ordered list)
- `required_events` (refs)
- `optional_events` (refs)
- `choice_points` (list agency_point_id)
- `fail_states` (list)
- `rewards` (narrative + systemic)
- `consequence_outputs` (flags/relationships/world changes)
- `notes`

Stage required fields:
- `stage_id`
- `objective`
- `success_criteria`
- `failure_criteria` (optional)
- `transition_out` (to next stage or exit)

---

## 5. AGENCY POINTS

### 5.1 AGENCY_POINT (required fields)
- `ap_id`
- `location_ref` (quest/stage)
- `choice_prompt` (what player decides)
- `options` (bounded list)
- `consequence_scope` = LOCAL | QUEST | FACTION | WORLD
- `consequence_rules` (what changes)
- `visibility` = EXPLICIT | IMPLICIT
- `reversibility` = REVERSIBLE | IRREVERSIBLE | LIMITED
- `fairness_gate` (must be understandable to player)
- `notes`

Hard rules:
- options must be bounded (default 2–4).
- at least one consequence must be real (non-cosmetic) for EXPLICIT choices.
- fairness_gate must pass: the player must have enough info to choose.

---

## 6. BRANCHING POLICY (BOUNDED)

### 6.1 BRANCHING_POLICY (required fields)
- `max_active_branches` (int)
- `max_branch_depth` (int)
- `branch_types_allowed` (cosmetic, tactical, moral, faction)
- `merge_deadline` (when branches must rejoin)
- `content_budget_per_branch` (range)
- `forbidden_branch_patterns` (infinite divergence, null choice)

Hard rule:
- branching must have a rejoin strategy unless mode is SYSTEMIC sandbox.

---

## 7. REJOIN STRATEGY

### 7.1 REJOIN_STRATEGY (required fields)
- `method` = HARD_MERGE | SOFT_MERGE | HUB_RETURN | WORLDSTATE_EQUIVALENCE
- `merge_points` (list of refs)
- `equivalence_rules` (how different outcomes become comparable)
- `preserved_differences` (what remains distinct)
- `notes`

Hard rule:
- merge must preserve meaningful differences (at least one flag/relationship delta) or it becomes fake choice.

---

## 8. FAIL STATE MODEL

### 8.1 FAIL_STATE (required fields)
- `fs_id`
- `trigger` (death, timeout, detection, resource depletion)
- `severity` = SOFT | HARD
- `response` = RELOAD | CHECKPOINT | DIEGETIC_RECOVERY | WORLD_PENALTY
- `narrative_cost` (what changes)
- `recovery_path` (how player continues)
- `notes`

Hard rules:
- fail states must not erase major narrative progress without clear checkpointing rules.
- soft fails preferred for exploration; hard fails allowed for high-stakes missions.

---

## 9. PERSISTENCE MODEL

### 9.1 PERSISTENCE_MODEL (required fields)
- `memory_units` (flags/reputation/relationship meters)
- `write_rules` (when state is written)
- `read_rules` (what systems consult state)
- `decay_rules` (optional)
- `save_policy` (auto/manual/checkpoint)
- `anti_corruption_rules` (no contradictory states)

Hard rule:
- persistence must be internally consistent (no mutually exclusive flags simultaneously true).

---

## 10. SYSTEMIC LOOPS

### 10.1 SYSTEMIC_LOOP (required fields)
- `loop_id`
- `type` = EXPLORE | COMBAT | CRAFT | TRADE | STEALTH | SOCIAL | BUILD
- `narrative_role` (how it carries meaning)
- `entry_trigger`
- `exit_trigger`
- `reward_cycle`
- `fatigue_gate` (avoid grind)
- `notes`

Hard rule:
- repeatable loops must have narrative role or they become grind-only filler.

---

## 11. HARD RULES (AGENCY INTEGRITY)

- No null choices:
  - if options converge immediately with no preserved difference → INVALID unless explicitly cosmetic.
- Choice readability:
  - player must understand stakes (fairness gate).
- Branch budget discipline:
  - if branches exceed budget, must merge or cut.
- World coherence:
  - consequences must not contradict canon rules.

---

## 12. INPUT ARTIFACTS

### 12.1 INPUT — GAME_NARRATIVE_REQUEST
**REQUIRED FIELDS**
- `gn_req_id`
- `timestamp`
- `genre_profile_ref` (required)
- `tone_profile_ref` (required)
- `platform_constraints_ref` (required)
- `target_mode` (required)
- `story_unit_set_ref` (required)
- `constraints_refs` (required)
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 13. OUTPUT ARTIFACTS

### 13.1 OUTPUT — GAME_NARRATIVE_PACKAGE
(see model above)

### 13.2 OUTPUT — GAME_NARRATIVE_VERDICT
- `gn_req_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 14. CORE OPERATIONS

- OP_01: INGEST_GENRE_TONE_PLATFORM_AND_STORY_UNITS
- OP_02: SELECT_GAME_NARRATIVE_MODE
- OP_03: BUILD_QUEST_REGISTRY (main/side/repeatable)
- OP_04: DEFINE_AGENCY_POINTS (bounded options + scopes)
- OP_05: DEFINE_BRANCHING_POLICY (budgeted + merge)
- OP_06: DEFINE_FAIL_STATE_MODEL (recovery loops)
- OP_07: DEFINE_PERSISTENCE_MODEL (flags/reputation)
- OP_08: DEFINE_SYSTEMIC_LOOPS (meaningful repetition)
- OP_09: DEFINE_REJOIN_STRATEGY (preserve differences)
- OP_10: RUN_INTEGRITY_CHECKS (no null choices, coherence)
- OP_11: EMIT_GAME_NARRATIVE_PACKAGE

---

## 15. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- branching unbounded
- merge strategy missing (non-systemic modes)
- null choices detected
- fairness gate fails (choices unreadable)
- persistence contradictions possible by design
- fail states erase progress without checkpoint logic

Reaction:
- Verdict INVALID (CRITICAL)
- Emit repair plan:
  - bound branches
  - add merge points
  - preserve meaningful deltas
  - tighten persistence rules
  - redesign fail recovery

---

## 16. TRACE RULES

- trace_id optional unless pipeline requires traced execution
- if present, propagate into project design docs and production orchestrator

---

## 17. NON-GOALS
- Does not implement mechanics
- Does not write dialogue
- Does not change canon

---

## 18. FINAL STATEMENT

A game story is a contract of consequences.
Give real choices — or don’t offer choices at all.

---

**STATUS:** Game Narrative Engine v1.0  
**REALM:** ACTIVE
