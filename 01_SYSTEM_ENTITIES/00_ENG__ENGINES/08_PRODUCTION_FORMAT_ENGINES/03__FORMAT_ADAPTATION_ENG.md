# 🔁 FORMAT ADAPTATION ENGINE
## Canonical Engine Specification  
**LEVEL: L3 · PRODUCTION FORMAT ENGINE · CONTENT PACKAGING · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 03__FORMAT_ADAPTATION_ENG.md
- ENGINE_ID: L3-PROD-FORMAT-ADAPTATION-ENGINE-003
- UID: UE.ENT.ENG.PROD.FORMAT_ADAPTATION
- NAME: Format Adaptation Engine
- CLASS: Production Format Engine
- LEVEL: L3
- STATUS: FINAL
- FAILURE_MODE: fail-closed (causal integrity)
- EDITABLE: true

### ABSOLUTE RULE
> Adaptation may compress and repackage, but it may not break causality or the genre contract.

---

## 1. PURPOSE

Format Adaptation Engine converts narrative assets into **format-ready structure**:
- chooses structural unitization (chapter/episode/beat/quest)
- enforces length/runtime budgets
- defines compression rules (what may be cut/merged)
- defines reordering rules (only if causality remains valid)
- defines “keep list” (must survive adaptation)
- defines “loss tolerance” (allowed simplification)

It produces:
- **FORMAT_ADAPTATION_SPEC**
- adaptation plan and constraints for downstream engines

This engine prevents “copy-paste” across formats.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Select target format and structural units
- Define budgets: length/runtime/scenes/acts
- Define mapping from story windows → format units
- Define compression/merging strategies
- Define reorder gates (topological causality preserved)
- Define keep/cut priorities (must-keep vs optional)
- Emit adaptation spec for Book/Series/Short/YouTube/Game packaging engines

### OUT-OF-SCOPE (FORBIDDEN)
- Creating new canon facts
- Changing causal truth (cause-effect graph)
- Changing genre contract (genre engine owns it)
- Writing scripts/prose

---

## 3. ADAPTATION MODEL

### 3.1 Output — FORMAT_ADAPTATION_SPEC (required fields)
- `fas_id`
- `target_format` = BOOK | SERIES | SHORT | YOUTUBE_LONGFORM | GAME
- `structural_unit` = CHAPTER | EPISODE | BEAT | QUEST | SEGMENT
- `budgets` (required)
- `unit_map` (required)
- `compression_rules` (required)
- `reorder_rules` (required)
- `keep_list` (required)
- `cut_list` (optional)
- `loss_tolerance` (required)
- `integrity_report` (issues + fixes)
- `trace_id` (optional)

Missing any required field → REJECT.

### 3.2 Budgets (required fields)
- `max_units` (int)
- `target_unit_length` (range; minutes or words or beats)
- `total_length` (range)
- `max_scene_count` (optional)
- `max_character_threads` (optional)
- `max_locations_per_unit` (optional)

### 3.3 Unit Map — UNIT_MAP_ENTRY (required fields)
- `unit_id`
- `covers_windows` (refs: schedule windows or turning point windows)
- `must_contain` (list: events/turning points/obligations)
- `optional_contains` (list)
- `cliffhanger_policy` (optional; for episodic)
- `notes`

Missing any required field → REJECT.

### 3.4 Keep List Item (required fields)
- `keep_id`
- `type` = EVENT | TURNING_POINT | CHARACTER_ARC_BEAT | SYMBOL | PAYOFF | WORLD_RULE
- `ref_id`
- `reason` (why must survive)
- `minimum_representation` (what counts as preserved)

---

## 4. HARD RULES (ADAPTATION INTEGRITY)

- Causality must remain valid:
  - any reorder must preserve topological order of the cause-effect graph.
- Genre obligations must survive:
  - obligations cannot be cut; only remapped.
- Climax + resolution must exist in package:
  - format may alter pacing, not remove decisive closure (unless explicitly “serial ongoing” mode).
- Budgets must be explicit:
  - no spec without unit and total length ranges.
- Keep list must exist:
  - otherwise adaptation becomes uncontrolled loss.

---

## 5. COMPRESSION RULES (STANDARD SET)

Allowed compression:
- merge adjacent low-impact scenes
- summarize travel/transition (unless atmosphere requires it)
- compress repeated attempts into montage
- remove redundant exposition if shown elsewhere
- consolidate minor characters into composites (if canon allows)

Forbidden compression:
- removing causal prerequisites
- removing setup while keeping payoff
- cutting emotional prerequisites to catharsis
- deleting world law explanations when they are required for comprehension

---

## 6. REORDER RULES (STANDARD SET)

Reorder allowed if:
- causal dependencies remain preserved
- anchors (hard-locked schedule anchors) remain fixed
- reveal-order does not create contradiction (mystery can reorder reveals, not facts)

Reorder forbidden if:
- it creates “effect before cause” in story truth
- it breaks turning point progression
- it makes climax occur before escalation windows

---

## 7. LOSS TOLERANCE MODEL

### 7.1 Loss Tolerance (required fields)
- `allowed_loss_types` (list: minor subplots, secondary motifs, minor locations)
- `forbidden_loss_types` (list: keep_list categories)
- `max_loss_ratio` (0.0–1.0)
- `quality_floor` (what must remain: clarity, stakes, catharsis)

If max_loss_ratio > 0.35 without explicit approval → PARTIAL/INVALID.

---

## 8. INPUT ARTIFACTS

### 8.1 INPUT — FORMAT_ADAPTATION_REQUEST
**REQUIRED FIELDS**
- `fa_req_id`
- `timestamp`
- `genre_profile_ref` (required)
- `genre_blend_profile_ref` (optional)
- `tone_profile_ref` (required)
- `constraints_refs` (required)
- `event_schedule_ref` (recommended)
- `turning_point_map_ref` (recommended)
- `climax_blueprint_ref` (recommended)
- `emotional_resonance_map_ref` (recommended)
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 9. OUTPUT ARTIFACTS

### 9.1 OUTPUT — FORMAT_ADAPTATION_SPEC
(see model above)

### 9.2 OUTPUT — FORMAT_ADAPTATION_VERDICT
- `fa_req_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 10. CORE OPERATIONS

- OP_01: INGEST_GENRE_TONE_CONSTRAINTS_AND_STORY_MAPS
- OP_02: SELECT_TARGET_FORMAT_AND_UNITIZATION
- OP_03: DEFINE_BUDGETS (units + length ranges)
- OP_04: BUILD_UNIT_MAP (windows → units)
- OP_05: DEFINE_COMPRESSION_RULES
- OP_06: DEFINE_REORDER_RULES (topological preserved)
- OP_07: BUILD_KEEP_LIST (must survive)
- OP_08: DEFINE_LOSS_TOLERANCE
- OP_09: RUN_INTEGRITY_CHECKS (obligations/causality/payoffs)
- OP_10: EMIT_FORMAT_ADAPTATION_SPEC

---

## 11. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- no budgets
- no keep list
- reorder breaks causality
- obligations cannot be mapped into units
- compression removes prerequisites or setups
- climax/resolution missing or unmapped

Reaction:
- Verdict INVALID (CRITICAL)
- Emit repair plan:
  - rebuild unit map
  - restore keep items
  - adjust budgets
  - remove illegal reorders
  - reinsert prerequisites

---

## 12. TRACE RULES

- trace_id optional unless pipeline requires traced execution
- if present, propagate into Book/Series/Short/YouTube/Game packaging engines

---

## 13. NON-GOALS
- Does not write content
- Does not change canon
- Does not choose genre (only consumes)

---

## 14. FINAL STATEMENT

Adaptation is compression with integrity.
Keep the spine — and the form can change safely.

---

**STATUS:** Format Adaptation Engine v1.0  
**REALM:** ACTIVE
