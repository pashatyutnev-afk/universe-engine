# 📝 LYRICS ENGINE
## Canonical Engine Specification  
**LEVEL: L3 · PRODUCTION ENGINE · LYRIC WRITING SYSTEM · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 07__LYRICS_ENG.md
- ENGINE_ID: L3-PROD-LYRICS-ENGINE-007
- UID: UE.ENT.ENG.PROD.LYRICS
- NAME: Lyrics Engine
- CLASS: Sound & Music Engine
- LEVEL: L3
- STATUS: FINAL
- FAILURE_MODE: fail-closed (prosody + meaning)
- EDITABLE: true

### ABSOLUTE RULE
> Lyrics must fit the prosody blueprint and carry meaning without breaking tone.

---

## 1. PURPOSE

Lyrics Engine produces **LYRICS_DRAFTS** and **LYRICS_FINAL**:
- mapped to song structure sections
- compliant with prosody (meter/stress/rhyme)
- aligned with tone/genre/world constraints
- supporting hook memorability and repeatability
- providing revision-ready variants

It can generate text, but output must remain **constraint-locked**.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Build lyric brief (theme, POV, imagery, taboo list)
- Write lyrics per section (verse/chorus/bridge/etc.)
- Enforce prosody blueprint (syllables/stress/rhyme)
- Enforce hook line constraints
- Generate variants and revisions
- Produce clean “performance-ready” lyric sheet
- Produce QA + repair plan

### OUT-OF-SCOPE (FORBIDDEN)
- melody/harmony composition
- arrangement and instrumentation
- mixing/mastering
- cultural/historical safety decisions beyond constraints (delegated to validation engines if needed)

---

## 3. INPUT / OUTPUT

### 3.1 INPUT — LYRICS_REQUEST
Required fields:
- `ly_req_id`
- `timestamp`
- `song_blueprint_ref` (sections, durations)
- `prosody_blueprint_ref` (required)
- `hook_blueprint_ref` (recommended)
- `tone_profile_ref`
- `genre_profile_ref` (optional)
- `language_mode` (must match prosody blueprint)
- `world_constraints_refs` (optional)
- `taboo_constraints` (optional)
- `trace_id` (optional)

Missing required input → REJECT.

### 3.2 OUTPUT — LYRICS_ARTIFACT
Required fields:
- `lyrics_id`
- `engine_id`
- `version`
- `status` = DRAFT | PARTIAL | FINAL
- `language_mode`
- `lyric_brief`
- `section_lyrics_map`
- `hook_lines` (primary + alternates)
- `rhyme_report`
- `meter_report`
- `stress_report`
- `meaning_coherence_report`
- `qa_gates`
- `repair_plan`

---

## 4. LYRIC BRIEF (MANDATORY)

### 4.1 LYRIC_BRIEF (required fields)
- `theme_statement` (1–2 lines)
- `emotional_target` (what it should feel like)
- `pov` (I/you/we/third)
- `story_mode` = NARRATIVE | IMAGERY | MANTRA | DIALOGUE
- `imagery_palette` (list)
- `keywords_lock` (list)
- `avoid_list` (clichés, forbidden phrases)
- `taboo_constraints` (if any)
- `notes`

Hard rule:
- hook line must reflect theme_statement directly or via keywords_lock.

---

## 5. SECTION LYRICS MAP

### 5.1 SECTION_LYRICS (required per section)
For each `sec_id`:
- `sec_type`
- `lines` (ordered list)
- `line_notes` (optional)
- `call_response` (optional)
- `adlibs` (optional)

Hard rule:
- number of lines must match prosody blueprint per section.

---

## 6. HOOK LINES

### 6.1 HOOK_LINES (required fields)
- `primary_hook_line`
- `alternate_hook_lines` (0..n)
- `chantable_version` (optional)
- `hook_end_word_lock` (if rhyme lock enabled)
- `notes`

Hard rule:
- primary hook line must satisfy prosody hook constraints (max words, syllables, stress targets).

---

## 7. RHYME COMPLIANCE

### 7.1 RHYME_REPORT (required fields)
- `scheme_expected` (from prosody blueprint)
- `scheme_observed`
- `family_usage_report`
- `near_rhyme_usage` (if allowed)
- `violations` (list)
- `fix_suggestions` (list)

Hard rule:
- if hook_rhyme_lock true, hook rhymes cannot drift across repeats.

---

## 8. METER COMPLIANCE

### 8.1 METER_REPORT (required fields)
- `syllable_targets` (per section)
- `observed_syllables` (per line)
- `tolerance`
- `violations`
- `fix_suggestions`

---

## 9. STRESS COMPLIANCE

### 9.1 STRESS_REPORT (required fields)
- `stress_targets` (per section/hook)
- `observed_stress_map` (approx or phonetic estimation)
- `violations`
- `fix_suggestions`

Hard rule:
- stress violations in hook line → HIGH severity.

---

## 10. MEANING COHERENCE

### 10.1 MEANING_COHERENCE_REPORT (required fields)
- `theme_alignment_score` (0–10)
- `pov_consistency` (ok/fail)
- `cliche_density` (0–10)
- `imagery_consistency` (ok/fail)
- `internal_contradictions` (list)
- `notes`

---

## 11. VARIANTS & REVISION LOOP

### 11.1 VARIATION MODES (allowed)
- LIGHT_REWRITE (same rhyme/meter)
- IMAGE_SWAP (new imagery, same constraints)
- HOOK_ALT (new hook line within constraints)
- VERSE_ALT (new verse with same scheme)
- TONE_SHIFT (requires new tone constraints)

If generating variants, each variant must include:
- `variant_id`
- `what_changed`
- `what_locked`
- `risk_notes`

Hard rule:
- cannot change meter/rhyme without updating prosody blueprint.

---

## 12. QA GATES

### 12.1 QA_GATES (required fields)
- `prosody_gate` (meter + stress + rhyme)
- `hook_gate` (hook constraints satisfied)
- `tone_gate` (matches tone profile)
- `meaning_gate` (theme + POV consistent)
- `taboo_gate` (no forbidden content)
- `edit_gate` (hook repeat sections consistent)

Fail rules:
- prosody_gate fail → INVALID (HIGH)
- hook_gate fail → INVALID (HIGH/CRITICAL)

---

## 13. REPAIR PLAN (MANDATORY)

### 13.1 REPAIR PLAN (required)
Common repairs:
- too many syllables → remove fillers, compress phrases
- stress clash → swap word order / synonyms
- rhyme forced → widen family (if allowed) or rewrite line
- hook weak → tighten words, add concrete image, simplify
- cliché high → replace with imagery_palette items
- POV drift → rewrite offending lines

Include:
- `recheck_gates`
- `max_revision_cycles`

---

## 14. CORE OPERATIONS

- OP_01: INGEST_REQUEST
- OP_02: BUILD_LYRIC_BRIEF
- OP_03: GENERATE_HOOK_LINES
- OP_04: GENERATE_SECTION_LYRICS (per sec)
- OP_05: RUN_RHYME_CHECK
- OP_06: RUN_METER_CHECK
- OP_07: RUN_STRESS_CHECK
- OP_08: RUN_MEANING_COHERENCE_CHECK
- OP_09: BUILD_QA_GATES
- OP_10: BUILD_REPAIR_PLAN
- OP_11: EMIT_LYRICS_ARTIFACT

---

## 15. FAILURE CONDITIONS (ENGINE)

CRITICAL:
- prosody_blueprint_ref missing
- language_mode mismatch with prosody blueprint
- structure missing

Reaction:
- reject (fail-closed)
- request missing/consistent inputs

---

## 16. NON-GOALS
- does not compose melody/harmony
- does not mix/master
- does not guarantee cultural safety without constraints (use validation engines)

---

## 17. FINAL STATEMENT

Lyrics are controlled meaning.
If they don’t fit the beat and the mouth — they don’t exist.

---

**STATUS:** Lyrics Engine v1.0  
**REALM:** ACTIVE
