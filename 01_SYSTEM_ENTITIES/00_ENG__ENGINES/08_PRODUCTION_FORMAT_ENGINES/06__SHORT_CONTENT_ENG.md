# ⚡ SHORT CONTENT ENGINE
## Canonical Engine Specification  
**LEVEL: L3 · PRODUCTION FORMAT ENGINE · MICRO/MINI PACKAGING · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 06__SHORT_CONTENT_ENG.md
- ENGINE_ID: L3-PROD-SHORT-CONTENT-ENGINE-006
- UID: UE.ENT.ENG.PROD.SHORT_CONTENT
- NAME: Short Content Engine
- CLASS: Production Format Engine
- LEVEL: L3
- STATUS: FINAL
- FAILURE_MODE: fail-closed (retention integrity)
- EDITABLE: true

### ABSOLUTE RULE
> Short content is a single spike. If you add more than one story, you lose them.

---

## 1. PURPOSE

Short Content Engine packages narrative into:
- micro format (6–22 seconds)
- mini format (1–3 minutes)
- hook-first architecture
- retention gates (no dead air, no slow ramp)
- beat budgets, caption rules, punchline/payoff scheduling

It produces:
- **SHORT_CONTENT_PACKAGE**
- format-specific constraints for production pipeline

This engine prevents “book pacing in shorts”.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define short format type (MICRO or MINI)
- Define runtime budget and beat budget
- Define hook policy (first-second obligation)
- Define cadence rules (cut frequency / change rate)
- Define caption/subtitle constraints (readability)
- Define payoff placement and escalation rules
- Map one narrative unit into a short container
- Validate retention integrity (no drift, no multi-plot)

### OUT-OF-SCOPE (FORBIDDEN)
- Changing canon facts
- Multi-thread plotting
- Long exposition
- Writing final script (engine emits package + constraints)

---

## 3. SHORT PACKAGE MODEL

### 3.1 Output — SHORT_CONTENT_PACKAGE (required fields)
- `scp_id`
- `mode` = MICRO | MINI
- `runtime_seconds` (required range)
- `beat_budget` (required)
- `hook_policy` (required)
- `beat_schema` (required)
- `cadence_rules` (required)
- `caption_rules` (required)
- `payoff_rules` (required)
- `allowed_content_types` (required)
- `forbidden_content_types` (required)
- `integrity_report` (issues + fixes)
- `trace_id` (optional)

Missing any required field → REJECT.

---

## 4. MODES

### 4.1 MICRO (6–22s)
- goal: single shock / reveal / micro-arc
- beat budget: 3–6 beats
- hook deadline: ≤ 1.0s
- payoff deadline: ≤ 80% runtime
- end: hard stop or punchline (no slow outro)

### 4.2 MINI (60–180s)
- goal: compact arc (setup → complication → payoff)
- beat budget: 7–14 beats
- hook deadline: ≤ 2.0s
- midpoint: must exist (shift or escalation)
- payoff deadline: ≤ 85% runtime
- end: resolution + tag (optional)

---

## 5. BEAT BUDGET MODEL

### 5.1 Beat Budget (required fields)
- `max_beats` (int)
- `min_beats` (int)
- `max_seconds_per_beat` (float)
- `must_have_beats` (list)
- `forbidden_beats` (list)

Hard rule:
- if average beat duration > `max_seconds_per_beat` → PARTIAL/INVALID (retention risk).

---

## 6. HOOK POLICY (HARD)

### 6.1 Hook Policy (required fields)
- `hook_deadline_seconds`
- `hook_types` (list)
- `forbidden_hooks` (list)
- `hook_must_define` (what must be established: question/stakes/contrast)

Allowed hook types:
- VISUAL_SHOCK
- QUESTION
- CONTRADICTION
- IMMEDIATE_THREAT
- IMPOSSIBLE_FACT (if tone permits)
- EMOTIONAL_SPIKE

Forbidden hooks:
- slow intro / branding first
- scene setting without question
- long greeting

---

## 7. BEAT SCHEMA (STANDARD)

### 7.1 MICRO default schema (editable)
1. HOOK
2. CONTEXT-ATOM (one line / one shot)
3. TWIST / REVEAL
4. PAYOFF
5. TAG (optional)

### 7.2 MINI default schema (editable)
1. HOOK
2. ORIENTATION (fast)
3. INCITING BEAT
4. COMPLICATIONS (1–3)
5. MIDPOINT SHIFT
6. CRISIS CHOICE (micro)
7. PAYOFF / RESOLUTION
8. TAG / NEXT PROMISE (optional)

Hard rule:
- schema must include exactly one primary question (one-plot rule).

---

## 8. CADENCE RULES

### 8.1 Cadence Rules (required fields)
- `change_rate_policy` (how often something changes: shot/angle/topic)
- `max_dead_air_seconds` (default 0.3 MICRO, 0.6 MINI)
- `allowed_pauses` (rare; must be purposeful)
- `cut_density_guidance` (symbolic ok)
- `audio_pacing_guidance` (beats tied to sound cues)

Hard rule:
- dead air beyond max without purpose → INVALID.

---

## 9. CAPTION / SUBTITLE RULES

### 9.1 Caption Rules (required fields)
- `mode` = REQUIRED | OPTIONAL
- `max_chars_per_line` (default 28–34)
- `max_lines` (default 2)
- `min_on_screen_ms` (default 700)
- `safe_area_requirements` (avoid UI overlays)
- `language_policy` (single language or dual)
- `forbidden_caption_patterns` (wall of text)

Hard rule:
- captions must not exceed readability budget.

---

## 10. PAYOFF RULES

### 10.1 Payoff Rules (required fields)
- `payoff_deadline_ratio` (e.g., 0.8)
- `payoff_types` (reveal / punchline / consequence / beauty spike)
- `must_be_earned_by` (refs: event/contrast)
- `end_state_policy` = HARD_STOP | LOOPABLE | CTA_ALLOWED
- `cta_constraints` (if allowed)

Hard rule:
- payoff cannot be postponed to “part 2” unless explicitly declared series-short mode.

---

## 11. ALLOWED / FORBIDDEN CONTENT TYPES

Allowed:
- single event/reveal
- single character choice
- single demonstration (cause→effect)
- single world rule display
- micro-conflict

Forbidden:
- multi-plot
- long exposition dumps
- complex cast introductions
- slow establishing travel
- unrelated montage without payoff

---

## 12. INPUT ARTIFACTS

### 12.1 INPUT — SHORT_CONTENT_REQUEST
**REQUIRED FIELDS**
- `sc_req_id`
- `timestamp`
- `format_adaptation_spec_ref` (optional)
- `genre_profile_ref` (required)
- `tone_profile_ref` (required)
- `platform_constraints_ref` (required)
- `target_mode` = MICRO | MINI (required)
- `story_unit_ref` (required: one unit only)
- `constraints_refs` (required)
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 13. OUTPUT ARTIFACTS

### 13.1 OUTPUT — SHORT_CONTENT_PACKAGE
(see model above)

### 13.2 OUTPUT — SHORT_CONTENT_VERDICT
- `sc_req_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 14. CORE OPERATIONS

- OP_01: INGEST_GENRE_TONE_PLATFORM_AND_UNIT
- OP_02: SELECT_MODE_AND_RUNTIME_BUDGET
- OP_03: SET_BEAT_BUDGET
- OP_04: DEFINE_HOOK_POLICY (deadline + types)
- OP_05: SELECT_BEAT_SCHEMA (micro/mini)
- OP_06: DEFINE_CADENCE_RULES (dead air + change rate)
- OP_07: DEFINE_CAPTION_RULES (readability)
- OP_08: DEFINE_PAYOFF_RULES (deadline + types)
- OP_09: RUN_RETENTION_GATES (one-plot, dead air, payoff)
- OP_10: EMIT_SHORT_CONTENT_PACKAGE

---

## 15. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- hook deadline not met by design
- more than one plot/thread
- dead air violations
- no payoff scheduled inside budget
- caption rules unreadable for platform
- beat budget inconsistent with runtime

Reaction:
- Verdict INVALID (CRITICAL)
- Emit repair plan:
  - collapse to one question
  - move hook earlier
  - tighten beats
  - relocate payoff before deadline
  - simplify captions

---

## 16. TRACE RULES

- trace_id optional unless pipeline requires traced execution
- if present, propagate into editing/montage and captioning pipeline

---

## 17. NON-GOALS
- Does not write final script
- Does not change canon
- Does not build long arcs

---

## 18. FINAL STATEMENT

Shorts are precision.
One spike. One question. One payoff.

---

**STATUS:** Short Content Engine v1.0  
**REALM:** ACTIVE
