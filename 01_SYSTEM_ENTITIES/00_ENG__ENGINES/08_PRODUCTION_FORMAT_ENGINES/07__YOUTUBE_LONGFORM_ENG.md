# ▶️ YOUTUBE LONGFORM ENGINE
## Canonical Engine Specification  
**LEVEL: L3 · PRODUCTION FORMAT ENGINE · LONGFORM PACKAGING · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 07__YOUTUBE_LONGFORM_ENG.md
- ENGINE_ID: L3-PROD-YOUTUBE-LONGFORM-ENGINE-007
- UID: UE.ENT.ENG.PROD.YOUTUBE_LONGFORM
- NAME: YouTube Longform Engine
- CLASS: Production Format Engine
- LEVEL: L3
- STATUS: FINAL
- FAILURE_MODE: fail-closed (retention integrity)
- EDITABLE: true

### ABSOLUTE RULE
> Longform on YouTube survives by open loops. If loops close too early, retention collapses.

---

## 1. PURPOSE

YouTube Longform Engine packages narrative into a **YouTube-ready longform**:
- hook + premise clarity
- open-loop strategy (questions held, promised, paid)
- segment/chapter structure
- retention dip control (no dead zones)
- CTA timing and constraints
- mid-roll pacing compatibility (optional)

It produces:
- **YOUTUBE_LONGFORM_PACKAGE**
- segment map and retention constraints for editing/montage

This engine prevents “lecture pacing” and early drop-off.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define runtime and segment budgets
- Define hook policy (first 5–15s)
- Define open-loop inventory and schedule
- Define chapter/segment structure and transitions
- Define retention dip mitigation rules (pattern interrupts)
- Define CTA policy (soft/hard, timing)
- Map narrative units into segments
- Validate retention integrity and payoff scheduling

### OUT-OF-SCOPE (FORBIDDEN)
- Changing canon facts
- Writing final script
- Excessive platform-gaming that breaks story trust

---

## 3. YT PACKAGE MODEL

### 3.1 Output — YOUTUBE_LONGFORM_PACKAGE (required fields)
- `ylp_id`
- `runtime_minutes_range` (required)
- `segment_budget` (required)
- `hook_policy` (required)
- `open_loop_inventory` (required)
- `segment_map` (required)
- `transition_rules` (required)
- `retention_gates` (hard rules)
- `cta_policy` (required)
- `midroll_policy` (optional)
- `integrity_report` (issues + fixes)
- `trace_id` (optional)

Missing any required field → REJECT.

---

## 4. BUDGETS

### 4.1 Segment Budget (required fields)
- `min_segments` (int)
- `max_segments` (int)
- `target_segment_minutes_range` (min/max)
- `max_dead_zone_seconds` (default 4–7 depending on style)
- `max_exposition_run_minutes` (default 2.0–3.5)
- `pattern_interrupt_interval_minutes` (default 1.5–3.0)

If min_segments > max_segments → INVALID.

---

## 5. HOOK POLICY (HARD)

### 5.1 Hook Policy (required fields)
- `hook_deadline_seconds` (default 5–15)
- `must_deliver` (list)
  - premise
  - primary question / promise
  - why-now relevance
- `allowed_hook_types` (list)
- `forbidden_hook_types` (list)

Forbidden:
- long intro branding
- vague “today we will talk”
- premise after 30s (unless documentary slow-burn mode explicitly declared)

---

## 6. OPEN LOOP INVENTORY

### 6.1 OPEN_LOOP (required fields)
- `loop_id`
- `question_or_promise`
- `introduced_at` (segment_id/time_ref)
- `hold_strategy` (how it stays alive)
- `payoff_deadline` (segment_id/time_ref)
- `payoff_type` = REVEAL | DEMO | CONSEQUENCE | TURN | TWIST
- `proof_of_payoff` (what counts)
- `severity_if_unpaid` = LOW | MEDIUM | HIGH | CRITICAL

Hard rule:
- loops with severity HIGH/CRITICAL must be paid by deadline or the package is INVALID.

---

## 7. SEGMENT MAP

### 7.1 SEGMENT_SPEC (required fields)
- `segment_id`
- `title` (optional)
- `goal` (what viewer gets)
- `covers_units` (refs)
- `must_contain` (facts/events/turning points)
- `open_loops_touched` (list loop_id)
- `payoffs_delivered` (list loop_id)
- `pattern_interrupts` (optional list)
- `transition_out` (required)
- `notes`

---

## 8. TRANSITION RULES

### 8.1 Transition Rules (required fields)
- `allowed_methods` (contrast, question, escalation, reveal, visual reset)
- `forbidden_methods` (hard topic jump without bridge)
- `bridge_requirements` (one sentence: why next segment follows)

Hard rule:
- every segment must end with a reason to continue (open loop touch or new promise).

---

## 9. RETENTION GATES (HARD)

- No dead zones:
  - if a segment has > `max_dead_zone_seconds` with no value change, INVALID.
- Exposition cap:
  - continuous exposition cannot exceed `max_exposition_run_minutes` without a demo/story beat.
- Open loops must be alive:
  - at least one loop must be active at all times after hook.
- Payoff schedule integrity:
  - cannot stack all payoffs in last 10% (fatigue + distrust).
- Pattern interrupts:
  - must occur at least every interval unless “meditative doc” mode is declared.

---

## 10. CTA POLICY

### 10.1 CTA Policy (required fields)
- `mode` = NONE | SOFT | STANDARD | AGGRESSIVE_FOR_ALLOWED_CHANNELS
- `allowed_positions` (time refs)
- `forbidden_positions` (e.g., before premise clarity)
- `max_cta_count` (default 1–3)
- `cta_style_rules` (trust-preserving)

Hard rule:
- CTA cannot break the open-loop promise (must not interrupt a peak moment).

---

## 11. MID-ROLL POLICY (OPTIONAL)

### 11.1 Midroll Policy (optional fields)
- `allowed` (bool)
- `preferred_slots` (segment boundaries)
- `forbidden_slots` (mid-reveal, mid-climax)
- `recovery_rule` (how to re-hook after mid-roll)

---

## 12. INPUT ARTIFACTS

### 12.1 INPUT — YOUTUBE_LONGFORM_REQUEST
**REQUIRED FIELDS**
- `yl_req_id`
- `timestamp`
- `genre_profile_ref` (required)
- `tone_profile_ref` (required)
- `platform_constraints_ref` (required)
- `target_runtime_minutes_range` (required)
- `story_unit_set_ref` (required)
- `constraints_refs` (required)
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 13. OUTPUT ARTIFACTS

### 13.1 OUTPUT — YOUTUBE_LONGFORM_PACKAGE
(see model above)

### 13.2 OUTPUT — YOUTUBE_LONGFORM_VERDICT
- `yl_req_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 14. CORE OPERATIONS

- OP_01: INGEST_GENRE_TONE_PLATFORM_AND_STORY_UNITS
- OP_02: SET_RUNTIME_AND_SEGMENT_BUDGETS
- OP_03: DEFINE_HOOK_POLICY
- OP_04: BUILD_OPEN_LOOP_INVENTORY (deadlines + severity)
- OP_05: BUILD_SEGMENT_MAP (goals + loops)
- OP_06: DEFINE_TRANSITION_RULES
- OP_07: DEFINE_RETENTION_GATES (dead zones, exposition caps)
- OP_08: DEFINE_CTA_POLICY (+ midroll optional)
- OP_09: RUN_INTEGRITY_CHECKS (loop payments + pacing)
- OP_10: EMIT_YOUTUBE_LONGFORM_PACKAGE

---

## 15. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- hook missing or late
- open loops unpaid beyond deadlines
- dead zones detected by design
- exposition overrun without demo/story beat
- CTA breaks peak moments
- payoffs stacked at the end

Reaction:
- Verdict INVALID (CRITICAL)
- Emit repair plan:
  - move premise earlier
  - add loop touches per segment
  - split exposition with demos
  - reschedule payoffs
  - relocate CTA to safe slots

---

## 16. TRACE RULES

- trace_id optional unless pipeline requires traced execution
- if present, propagate into editing/montage and sound pacing

---

## 17. NON-GOALS
- Does not write final script
- Does not change canon
- Does not guarantee algorithm performance (only retention integrity)

---

## 18. FINAL STATEMENT

Longform is a chain of promises.
Open loops create the chain — payoffs keep it unbroken.

---

**STATUS:** YouTube Longform Engine v1.0  
**REALM:** ACTIVE
