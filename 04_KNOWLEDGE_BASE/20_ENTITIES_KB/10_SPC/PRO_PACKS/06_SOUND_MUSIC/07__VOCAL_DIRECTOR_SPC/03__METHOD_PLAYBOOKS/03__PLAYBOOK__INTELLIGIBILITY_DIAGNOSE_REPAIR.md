# SPC PRO PACK — PLAYBOOK (PB-03) — INTELLIGIBILITY DIAGNOSE & REPAIR (NO LYRIC CHANGE) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/03__METHOD_PLAYBOOKS/03__PLAYBOOK__INTELLIGIBILITY_DIAGNOSE_REPAIR.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: PLAYBOOK
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.PB.INTELLIGIBILITY.001
OWNER: SYSTEM
ROLE: Deterministic workflow to diagnose why words are not understood and apply repairs via delivery/phrasing/breath/articulation changes WITHOUT changing lyric meaning. Produces repair directives, updated gates, and escalation notes when repairs cannot solve the issue.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created PB-03 intelligibility diagnose & repair playbook (no lyric change)."
- REASON: "Most clarity failures are performance/phrasing issues; this playbook fixes them without violating lyric ownership."
- IMPACT: "Reduces rework cost and protects meaning; makes intelligibility pass/fail testable."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.VOCAL_DIRECTOR.PB03.001

---

## 0) PURPOSE
Use this playbook when:
- MUST_HEAR targets exist but are not understood
- hook words blur, consonants vanish, phrases smear
- you need a repair plan without rewriting lyrics

Primary objective:
- Make P0/P1 targets intelligible by changing HOW they’re delivered, not WHAT they are.

---

## 1) REQUIRED INPUTS (MINIMUM)
STOP/GAP if missing:
- MUST_HEAR_WORDS / MUST_HEAR_PHRASES (P0/P1)
- FAILURE OBSERVATION (at least one):
  - what is not understood (which P0/P1 items)
  - where (section + line)
  - when (first listen / later)
- SECTION STRUCTURE (to localize repairs)

Recommended:
- audio notes from takes (textual observations)
- tempo/groove info (if known)
- pronunciation risk notes (from PB-02)

---

## 2) REQUIRED OUTPUTS (MANDATORY)
This playbook MUST produce:
- FAILURE_MAP (targets → where they fail)
- ROOT_CAUSE_CLASSIFICATION (which failure type)
- REPAIR_DIRECTIVES (actionable, no lyric edits)
- UPDATED_INTELLIGIBILITY_GATES (pass/fail tuned to targets)
- TAKE_ADJUSTMENTS (what to change in next take)
- ESCALATION_NOTES (if lyric rewrite is required)
- TRACE (memory/web + gaps)

NOT READY rule:
- If repairs require changing words → do NOT change words; escalate.

---

## 3) ROOT CAUSE TAXONOMY (STRICT)
Classify each failure into one or more types:

T1 — CONSONANT LOSS
- plosives/fricatives disappear; words become vowel soup

T2 — OVER-SPEED / DENSITY
- too many syllables per beat; mouth cannot articulate at tempo

T3 — BAD STRESS / ACCENT MISPLACEMENT
- stress falls on weak syllables; meaning carrier loses emphasis

T4 — BREATH BREAKS INSIDE TARGETS
- breathing splits must-hear phrase; target becomes unreadable

T5 — MASKING BY DELIVERY
- growl/scream/overdrive makes words unintelligible (performance mode issue)

T6 — COMPETITION WITH STACKING
- doubles/backs/harmonies cover consonants; lead loses clarity

T7 — MIX/ARRANGEMENT SEAT (NOTE ONLY)
- instrumental density masks words (VOCAL_DIRECTOR: escalate seat request, not processing chain)

---

## 4) WORKFLOW (DETERMINISTIC STEPS)
### STEP 1 — Build FAILURE_MAP
For each failed target:
- target item (P0/P1)
- section + line
- symptom (what listener hears)
- severity:
  - S0: P0 target not understood (hard fail)
  - S1: P1 not understood (soft fail)
  - S2: occasional blur (minor)

### STEP 2 — Assign ROOT CAUSE types
For each FAILURE_MAP entry, tag it with T1..T7.

### STEP 3 — Choose repair strategy per type (NO LYRIC CHANGE)
Repair strategies (allowed):
- articulation emphasis (consonant shaping)
- timing adjustments (micro-delays, “land consonants early”)
- stress re-targeting (move emphasis to meaning syllable)
- breath relocation (move breath before/after phrase)
- delivery mode adjustment (reduce distortion on critical words)
- stacking reduction (remove doubles on target phrases)
- phrasing simplification (same words, cleaner grouping)

FORBIDDEN:
- rewriting words to easier synonyms (meaning change)
- inventing new lyrics

### STEP 4 — Generate REPAIR_DIRECTIVES (actionable)
For each failed target, produce:
- directive:
  - “do X on word/phrase Y in section Z”
- constraint:
  - “do not change text”
- test:
  - “PASS when target understood on first listen”

Examples (principles):
- “Hit consonant on the downbeat; shorten preceding vowel.”
- “Move breath before the phrase; keep phrase uninterrupted.”
- “Reduce grit only on the target words; keep grit elsewhere.”

### STEP 5 — Update gates checklist for next run
Produce UPDATED_INTELLIGIBILITY_GATES:
- Gate A: all P0 targets understood on first listen
- Gate B: P0 in chorus clearer than verse
- Gate C: no breath splits inside P0 phrases
- Gate D: stacking does not cover consonants on P0

### STEP 6 — Take adjustments (next take plan)
Produce TAKE_ADJUSTMENTS:
- what changes this take (one-axis if possible):
  - articulation OR breath OR delivery-mode OR stacking
- what stays fixed:
  - lyrics text
  - overall delivery profile (unless delivery-mode is chosen axis)

---

## 5) ESCALATION RULES (WHEN REPAIR IS NOT ENOUGH)
Escalate to Lyricist/Songwriter if:
- T2 density makes P0 phrase unsingable at tempo even with articulation/breath fixes
- stress pattern cannot fit groove without changing words
- must-hear phrase requires shortening/rephrasing to be intelligible

Escalate to Arranger/Producer if:
- T7 seat conflict: instrumental density masks P0 targets
Note:
- request “reduce density” / “leave space” as principles; do not prescribe mix chains.

---

## 6) COMMON FAIL MODES
- Repairs are generic (“make clearer”) with no per-target directives.
- Too many axes changed at once; cannot learn what worked.
- Stacking used to “sound big” but destroys consonants.
- Breath breaks added inside hook words.
- Delivery mode kept “extreme” on critical phrases (masking).

---

## 7) OUTPUT TEMPLATE (COPY)
### FAILURE_MAP
- target:
  - where:
  - symptom:
  - severity:
  - types (T1..T7):

### ROOT_CAUSE_CLASSIFICATION
- T1:
- T2:
- T3:
- T4:
- T5:
- T6:
- T7:

### REPAIR_DIRECTIVES (NO LYRIC CHANGE)
- target:
  - directive:
  - do_not_change:
  - pass_test:

### UPDATED_INTELLIGIBILITY_GATES
- Gate A:
- Gate B:
- Gate C:
- Gate D:

### TAKE_ADJUSTMENTS
- axis_changed:
- changed:
- unchanged:

### ESCALATION_NOTES
- to Lyricist/Songwriter:
- to Arranger/Producer:

### TRACE
- MEMORY_REUSE:
- WEB_LOOKUP_USED:
- GAPS:

--- END.
