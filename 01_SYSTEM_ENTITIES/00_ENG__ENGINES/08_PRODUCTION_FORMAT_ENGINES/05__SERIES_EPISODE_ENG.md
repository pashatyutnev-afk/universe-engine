# 📺 SERIES & EPISODE ENGINE
## Canonical Engine Specification  
**LEVEL: L3 · PRODUCTION FORMAT ENGINE · EPISODIC PACKAGING · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 05__SERIES_EPISODE_ENG.md
- ENGINE_ID: L3-PROD-SERIES-EPISODE-ENGINE-005
- UID: UE.ENT.ENG.PROD.SERIES_EPISODE
- NAME: Series & Episode Engine
- CLASS: Production Format Engine
- LEVEL: L3
- STATUS: FINAL
- FAILURE_MODE: fail-closed (episodic integrity)
- EDITABLE: true

### ABSOLUTE RULE
> Episodes must close a loop and open a new one. If they only loop, the series dies.

---

## 1. PURPOSE

Series & Episode Engine packages narrative assets into:
- seasons (optional) and episodes
- episode arcs (mini-structure)
- cold open / teaser rules
- act breaks and cliffhangers
- “previously on” policy (optional)
- thread tracking (A/B/C stories)

It produces:
- **SERIES_EPISODE_PACKAGE**
- episode map and rules for scripting/editing engines

This engine prevents “random scenes per episode” and thread chaos.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define season plan (if applicable)
- Define episode count and runtime budget
- Map adaptation units/windows into episodes
- Define episode arc schema (beats)
- Define A/B/C thread constraints and balancing rules
- Define cold open / teaser / recap policies
- Define act break and cliffhanger policies
- Enforce episodic continuity and escalation

### OUT-OF-SCOPE (FORBIDDEN)
- Changing canon facts
- Illegal causality reorder
- Writing scripts
- Deciding plot events

---

## 3. SERIES PACKAGE MODEL

### 3.1 Output — SERIES_EPISODE_PACKAGE (required fields)
- `sep_id`
- `format_adaptation_spec_ref` (required)
- `season_model` (required; can be SINGLE_SEASON)
- `episode_budgets` (required)
- `episode_arc_schema` (required)
- `thread_rules` (required)
- `cold_open_policy` (required)
- `recap_policy` (required)
- `act_break_policy` (required)
- `cliffhanger_policy` (required)
- `integrity_report` (issues + fixes)
- `trace_id` (optional)

Missing any required field → REJECT.

---

## 4. BUDGETS

### 4.1 Episode Budgets (required fields)
- `episode_count` (int)
- `runtime_range_min` (minutes)
- `runtime_range_max` (minutes)
- `max_scenes_per_episode` (optional)
- `max_locations_per_episode` (optional)
- `thread_limit` = 1 | 2 | 3 (A-only, A/B, A/B/C)

If runtime_min > runtime_max → INVALID.

---

## 5. SEASON MODEL

### 5.1 Season Model (required fields)
- `mode` = SINGLE_SEASON | MULTI_SEASON
- `season_count` (int; if MULTI_SEASON)
- `season_arc_rules` (setup/escalation/crisis/finish)
- `season_end_policy` = CLOSED | SEMI_CLOSED | OPEN

Hard rules:
- even OPEN season ends must pay at least one major promise.

---

## 6. EPISODE ARC SCHEMA (STANDARD)

### 6.1 EPISODE_ARC_SCHEMA (required fields)
- `schema_id`
- `beats` (ordered list)
- `minimum_requirements` (hard rules)

Default beat set (editable):
1. COLD_OPEN / TEASER (optional)
2. ORIENTATION (who/where/what changed)
3. INCITING_BEAT (episode-specific problem)
4. RISING_COMPLICATIONS
5. MIDPOINT_SHIFT
6. CRISIS_CHOICE
7. CLIMAX_BEAT
8. AFTERMATH / RESET_WITH_DELTA
9. TAG / HOOK (optional)

Hard rule:
- Every episode must include:
  - one episode loop closure (problem resolved or transformed)
  - one series loop advance (new information, escalation, or promise)

---

## 7. EPISODE MAP

### 7.1 EPISODE_SPEC (required fields)
- `ep_id`
- `season_id` (optional)
- `covers_units` (refs from adaptation unit map)
- `A_thread` (required)
- `B_thread` (optional)
- `C_thread` (optional)
- `must_contain` (events/turning points/obligations)
- `open_hook` (required)
- `close_hook` (required)
- `cliffhanger_level` = NONE | LOW | MEDIUM | HIGH
- `runtime_target` (minutes)
- `notes`

THREAD_SPEC required fields:
- `thread_id`
- `goal`
- `stakes`
- `complication`
- `resolution_or_transform`
- `carryover_to_next` (what remains open)

---

## 8. THREAD RULES (A/B/C)

### 8.1 Thread Rules (required fields)
- `thread_limit`
- `balance_rules` (time share guidance)
- `carryover_rules` (how threads persist)
- `forbidden_patterns` (e.g., B-thread disappears for 4 eps)
- `escalation_rules` (series growth)

Hard rules:
- A-thread must exist in every episode.
- If B-thread exists in a run, it must appear at least every 2 episodes unless explicitly paused.
- C-thread allowed only if runtime budget supports it.

---

## 9. POLICIES

### 9.1 Cold Open Policy (required fields)
- `mode` = NONE | ALWAYS | SOMETIMES
- `allowed_types` (action hook / mystery hook / emotional hook)
- `max_duration_ratio` (0.0–1.0; default 0.12)
- `forbidden_types` (tone-breaking hooks)

### 9.2 Recap Policy (required fields)
- `mode` = NONE | LIGHT | PREVIOUSLY_ON
- `max_recap_duration_ratio` (default 0.06)
- `allowed_content` (must-know only)
- `forbidden_content` (full summary dumps)

### 9.3 Act Break Policy (required fields)
- `mode` = NONE | STANDARD_ACTS | STREAMING_SOFT
- `break_points` (if STANDARD_ACTS)
- `break_requirements` (turning question / reversal / spike)

### 9.4 Cliffhanger Policy (required fields)
- `allowed_levels`
- `required_frequency` (e.g., every N episodes)
- `forbidden_patterns` (constant HIGH cliffhangers)
- `resolution_deadline` (max episodes before payoff)

Hard rule:
- If cliffhanger HIGH, payoff must occur within `resolution_deadline`.

---

## 10. HARD RULES (EPISODIC INTEGRITY)

- No “pure filler”:
  - every episode must advance series loop.
- No “reset-without-delta”:
  - aftermath must change something measurable.
- Runtime fit:
  - if episode contains too many obligations, split or compress.
- Obligations delivery:
  - genre obligations must be scheduled across season, not stacked randomly.

---

## 11. INPUT ARTIFACTS

### 11.1 INPUT — SERIES_EPISODE_REQUEST
**REQUIRED FIELDS**
- `se_req_id`
- `timestamp`
- `format_adaptation_spec_ref` (required)
- `genre_profile_ref` (required)
- `genre_blend_profile_ref` (optional)
- `tone_profile_ref` (required)
- `mood_curve_ref` (recommended)
- `event_schedule_ref` (recommended)
- `turning_point_map_ref` (recommended)
- `constraints_refs` (required)
- `platform_constraints_ref` (required)
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 12. OUTPUT ARTIFACTS

### 12.1 OUTPUT — SERIES_EPISODE_PACKAGE
(see model above)

### 12.2 OUTPUT — SERIES_EPISODE_VERDICT
- `se_req_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 13. CORE OPERATIONS

- OP_01: INGEST_ADAPTATION_GENRE_TONE_PLATFORM_CONSTRAINTS
- OP_02: SET_EPISODE_BUDGETS (count/runtime/thread_limit)
- OP_03: DEFINE_SEASON_MODEL
- OP_04: DEFINE_EPISODE_ARC_SCHEMA (beats)
- OP_05: DEFINE_THREAD_RULES (A/B/C)
- OP_06: MAP_UNITS_TO_EPISODES
- OP_07: APPLY_POLICIES (cold open/recap/acts/cliffhangers)
- OP_08: RUN_INTEGRITY_CHECKS (delta, filler, payoff deadlines)
- OP_09: EMIT_SERIES_EPISODE_PACKAGE

---

## 14. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- episodes missing open/close hooks
- no series advancement rule
- cliffhangers without payoff deadlines
- thread rules undefined
- episode budgets missing/inconsistent
- obligations cannot be scheduled without overload

Reaction:
- Verdict INVALID (CRITICAL)
- Emit repair plan:
  - rebalance threads
  - split episodes
  - adjust cliffhanger frequency/deadlines
  - rebuild episode map

---

## 15. TRACE RULES

- trace_id optional unless pipeline requires traced execution
- if present, propagate into production orchestrator and editing engines

---

## 16. NON-GOALS
- Does not write scripts
- Does not change canon
- Does not decide plot

---

## 17. FINAL STATEMENT

Episodes are contracts inside a contract.
Close a loop, open a door — repeat until the season lands.

---

**STATUS:** Series & Episode Engine v1.0  
**REALM:** ACTIVE
