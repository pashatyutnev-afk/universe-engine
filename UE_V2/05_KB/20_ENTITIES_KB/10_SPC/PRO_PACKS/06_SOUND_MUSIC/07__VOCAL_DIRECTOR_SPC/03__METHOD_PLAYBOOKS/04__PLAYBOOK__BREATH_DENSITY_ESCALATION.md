# SPC PRO PACK — PLAYBOOK (PB-04) — BREATH & DENSITY FIX + ESCALATION (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/03__METHOD_PLAYBOOKS/04__PLAYBOOK__BREATH_DENSITY_ESCALATION.md

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
UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.PB.BREATH_DENSITY.001
OWNER: SYSTEM
ROLE: Deterministic workflow to detect unsingable lyric density / breath problems, apply performance-safe fixes (breath policy + phrasing grouping) WITHOUT changing lyric meaning, and produce escalation notes when text revision is required.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created PB-04 breath & density fix + escalation workflow."
- REASON: "Many intelligibility failures are caused by unsingable density; need a clear fix-vs-escalate decision path."
- IMPACT: "Prevents impossible takes; protects must-hear words; keeps ownership discipline (no lyric rewrites)."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.VOCAL_DIRECTOR.PB04.001

---

## 0) PURPOSE
Use this playbook when:
- lines are physically hard to sing at tempo (dense syllables)
- breath breaks are forced inside must-hear phrases
- vocalist runs out of air, diction collapses, hook words smear

Primary objective:
- Make the text singable and intelligible by breath/phrasing policy first; escalate for lyric change only if unavoidable.

---

## 1) REQUIRED INPUTS (MINIMUM)
STOP/GAP if missing:
- LYRIC_DRAFT (with section labels or at least chorus/hook lines)
- LANGUAGE
- MUST_HEAR_WORDS / MUST_HEAR_PHRASES (P0/P1)

Strongly recommended:
- TEMPO / groove feel (if known)
- Structure (section list)
- Any known “fast lines” or observed failures from takes

---

## 2) REQUIRED OUTPUTS (MANDATORY)
This playbook MUST produce:
- DENSITY_SCAN (lines flagged)
- BREATH_POLICY (allowed/forbidden points)
- PHRASING_GROUPING_NOTES (how to group words without changing meaning)
- MUST_HEAR_PROTECTION_RULES (do not split these)
- FIX_VS_ESCALATE_DECISION (per line)
- ESCALATION_NOTES (if needed; to Lyricist/Songwriter)
- TRACE (memory/web + gaps)

NOT READY rule:
- If must-hear targets are missing → STOP (need PB-02 first).

---

## 3) DENSITY MODEL (PRACTICAL HEURISTICS)
Since exact syllable timing may be unknown, use conservative heuristics:

Flag a line as DENSE when:
- it has many consonant clusters or long multi-syllable chains
- it contains multiple must-hear words packed without pauses
- it is intended for fast delivery (rap-like) but no breath plan exists

Flag a line as UNSINGABLE-RISK when:
- must-hear phrase would require a breath mid-phrase
- consonant clarity fails even after articulation-focused repair attempts
- repeated attempts force swallow/blur of P0 targets

Output is not a metric; it is a deterministic flagging rule with evidence notes.

---

## 4) WORKFLOW (DETERMINISTIC STEPS)
### STEP 1 — Build DENSITY_SCAN
For each section line:
- line_id (section + index)
- contains must-hear targets? (yes/no)
- density flags:
  - cluster-heavy
  - long phrase
  - fast delivery implied
- risk level:
  - R0: ok
  - R1: dense
  - R2: unsingable-risk

### STEP 2 — Define MUST_HEAR_PROTECTION_RULES
Rules:
- never place breath inside P0 phrase
- never cut the core hook phrase across breaths
- prioritize clarity of P0 over decorative words

### STEP 3 — Construct BREATH_POLICY
For each risky line:
- allowed breath points (before phrase / after phrase)
- forbidden breath points (inside must-hear)
- “micro-breath” allowance (only outside must-hear words)
- breath budget note (short)

### STEP 4 — PHRASING_GROUPING_NOTES (NO TEXT CHANGE)
Provide grouping rules that keep words unchanged:
- regroup into 2–4 word chunks
- slow micro-timing on consonant clusters
- shorten vowels before must-hear consonants
- define “land consonants early” points for P0 words

### STEP 5 — FIX VS ESCALATE DECISION
For each R2 line, decide:
- FIX (performance-safe) if:
  - breath can be moved outside must-hear
  - grouping resolves density without breaking meaning
- ESCALATE if:
  - even with optimal breath policy, P0 targets cannot be delivered intelligibly
  - the line requires fewer words / different phrasing to be singable

### STEP 6 — ESCALATION_NOTES (IF NEEDED)
Escalation note format:
- owner: Lyricist/Songwriter
- line_id:
- problem:
  - “unsingable density at tempo; must-hear word clarity fails”
- constraint:
  - “preserve meaning intent”
- request:
  - “shorten / split into two lines / reduce clusters”
- must-keep:
  - list P0 words that must remain

Important:
- Do NOT rewrite the lyric here.

---

## 5) COMMON FAIL MODES
- Breath points inserted inside must-hear phrase.
- “Fix” attempts that change words (ownership violation).
- No per-line decision (fix vs escalate).
- Over-noting (too many micro-rules performer can’t execute).

---

## 6) OUTPUT TEMPLATE (COPY)
### DENSITY_SCAN
- line_id:
  - contains_P0:
  - flags:
  - risk_level:
  - evidence:

### MUST_HEAR_PROTECTION_RULES
- rule_1:
- rule_2:

### BREATH_POLICY
- line_id:
  - allowed:
  - forbidden:
  - micro_breath:

### PHRASING_GROUPING_NOTES
- line_id:
  - grouping:
  - timing_notes:

### FIX_VS_ESCALATE_DECISION
- line_id:
  - decision: FIX | ESCALATE
  - why:

### ESCALATION_NOTES (if any)
- owner:
- line_id:
- problem:
- request:
- must_keep:

### TRACE
- MEMORY_REUSE:
- WEB_LOOKUP_USED:
- GAPS:

--- END.
