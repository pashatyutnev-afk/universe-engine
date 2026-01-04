# 📚 BOOK FORMAT ENGINE
## Canonical Engine Specification  
**LEVEL: L3 · PRODUCTION FORMAT ENGINE · CHAPTER PACKAGING · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 04__BOOK_FORMAT_ENG.md
- ENGINE_ID: L3-PROD-BOOK-FORMAT-ENGINE-004
- UID: UE.ENT.ENG.PROD.BOOK_FORMAT
- NAME: Book Format Engine
- CLASS: Production Format Engine
- LEVEL: L3
- STATUS: FINAL
- FAILURE_MODE: fail-closed (chapter integrity)
- EDITABLE: true

### ABSOLUTE RULE
> A book is sustained attention. Chapters must carry forward motion, not just scenes.

---

## 1. PURPOSE

Book Format Engine packages narrative assets into a **book-ready structure**:
- acts + chapters + internal beats
- word budgets per chapter/act
- POV and voice constraints per chapter
- chapter hooks (open/close rules)
- recap/foreshadow placement rules (optional)
- continuity constraints (no “episode drift”)

It produces:
- **BOOK_FORMAT_PACKAGE**
- chapter map and rules for writing engines

This engine prevents “series pacing” inside book chapters.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define act structure and chapter count ranges
- Define word budgets (chapter + act + total)
- Define POV policy (single/multi; switching rules)
- Define chapter open/close hooks
- Define recap/foreshadow policy
- Map FORMAT_ADAPTATION_SPEC units into chapters
- Enforce book continuity rules (threads, stakes, promises)

### OUT-OF-SCOPE (FORBIDDEN)
- Changing canon facts
- Changing causal order illegally
- Writing the book prose itself

---

## 3. BOOK PACKAGE MODEL

### 3.1 Output — BOOK_FORMAT_PACKAGE (required fields)
- `bfp_id`
- `format_adaptation_spec_ref` (required)
- `structure` (acts + chapters)
- `budgets` (required)
- `pov_policy` (required)
- `chapter_hook_rules` (required)
- `recap_policy` (required)
- `foreshadow_policy` (required)
- `continuity_rules` (required)
- `integrity_report` (issues + fixes)
- `trace_id` (optional)

Missing any required field → REJECT.

### 3.2 Budgets (required fields)
- `total_word_range` (min/max)
- `act_word_ranges` (list)
- `chapter_word_range` (min/max)
- `max_chapters` (int)
- `min_chapters` (int)

If min_chapters > max_chapters → INVALID.

### 3.3 Structure (required fields)
- `act_count` (int; default 3 unless declared otherwise)
- `acts` (list of ACT_SPEC)

ACT_SPEC required fields:
- `act_id`
- `purpose` (setup/escalation/crisis/climax+resolution)
- `chapter_ids` (ordered list)
- `key_obligations` (list)
- `notes`

CHAPTER_SPEC required fields:
- `chapter_id`
- `title_policy` = NUMBERED | NAMED | MIXED
- `covers_units` (refs from adaptation unit map)
- `must_contain` (events/turning points/obligations)
- `pov` (one or allowed set per policy)
- `open_hook` (required)
- `close_hook` (required)
- `tension_floor` (0–10)
- `notes`

---

## 4. POV POLICY (STANDARD)

### 4.1 POV_POLICY object (required fields)
- `mode` = SINGLE | MULTI | OMNISCIENT_LIMITED | EPISTOLARY
- `switch_rules` (when switches are allowed)
- `forbidden_switches` (list)
- `voice_distance` (inherit or override tone profile)
- `reliability_mode` = RELIABLE | UNRELIABLE | MIXED
- `notes`

Hard rules:
- POV switch inside a chapter is forbidden unless explicitly allowed (rare).
- Multi-POV must declare max active POVs (default 3–5 depending on total length).

---

## 5. CHAPTER HOOK RULES (HARD)

Each chapter must have:
- OPEN_HOOK: orientation + tension seed within first window
- CLOSE_HOOK: either
  - cliff edge (question)
  - promise (next action)
  - emotional aftershock (earned)

Forbidden:
- chapter that ends with “nothing changed”
- chapter that opens with disorientation without intent

---

## 6. RECAP & FORESHADOW POLICIES

### 6.1 Recap Policy (required fields)
- `recap_mode` = NONE | LIGHT | CHAPTER_OPEN | SECTION_OPEN
- `max_recap_ratio` (0.0–1.0; default 0.03)
- `allowed_recap_types` (memory echo / summary line / object reminder)
- `forbidden_recap_types` (full plot dump)

### 6.2 Foreshadow Policy (required fields)
- `foreshadow_density` = NONE | SPARSE | MEDIUM
- `allowed_devices` (symbol, dialogue seed, detail cue)
- `forbidden_devices` (explicit spoilers)
- `payoff_alignment_required` = true

---

## 7. CONTINUITY RULES (BOOK-SPECIFIC)

- Threads must persist across chapters:
  - no “reset episode” behavior.
- Stakes must escalate or deepen:
  - tension floor must not stay flat for long.
- Setups must be paid:
  - if foreshadowed, payoff window must be mapped.

---

## 8. INPUT ARTIFACTS

### 8.1 INPUT — BOOK_FORMAT_REQUEST
**REQUIRED FIELDS**
- `bf_req_id`
- `timestamp`
- `format_adaptation_spec_ref` (required)
- `genre_profile_ref` (required)
- `tone_profile_ref` (required)
- `mood_curve_ref` (recommended)
- `pacing_rhythm_ref` (recommended)
- `constraints_refs` (required)
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 9. OUTPUT ARTIFACTS

### 9.1 OUTPUT — BOOK_FORMAT_PACKAGE
(see model above)

### 9.2 OUTPUT — BOOK_FORMAT_VERDICT
- `bf_req_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 10. CORE OPERATIONS

- OP_01: INGEST_ADAPTATION_GENRE_TONE_CONSTRAINTS
- OP_02: SELECT_ACT_AND_CHAPTER_RANGES (budgeted)
- OP_03: DEFINE_POV_POLICY (mode + switches)
- OP_04: MAP_UNITS_TO_CHAPTERS (ordered)
- OP_05: DEFINE_CHAPTER_OPEN_CLOSE_HOOKS
- OP_06: DEFINE_RECAP_AND_FORESHADOW_POLICIES
- OP_07: DEFINE_BOOK_CONTINUITY_RULES
- OP_08: RUN_INTEGRITY_CHECKS (hooks, budgets, obligations)
- OP_09: EMIT_BOOK_FORMAT_PACKAGE

---

## 11. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- budgets missing or inconsistent
- chapters missing open/close hooks
- POV policy undefined
- adaptation units unmapped
- obligations missing delivery mapping
- recap ratio too high without intent
- continuity rules violated by structure

Reaction:
- Verdict INVALID (CRITICAL)
- Emit repair plan:
  - rebuild budgets
  - rebuild chapter map
  - define POV switches
  - add hooks
  - prune recap

---

## 12. TRACE RULES

- trace_id optional unless pipeline requires traced execution
- if present, propagate into production orchestrator and writing pipeline

---

## 13. NON-GOALS
- Does not write chapters
- Does not change canon
- Does not set genre

---

## 14. FINAL STATEMENT

A book is momentum in long form.
Map chapters like engines — and the reader stays.

---

**STATUS:** Book Format Engine v1.0  
**REALM:** ACTIVE
