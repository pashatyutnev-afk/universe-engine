# SPC PRO PACK — PLAYBOOK (PB-06) — TAKE DIRECTION PACK (GOALS + QC) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/03__METHOD_PLAYBOOKS/06__PLAYBOOK__TAKE_DIRECTION_PACK.md

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
UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.PB.TAKE_PACK.001
OWNER: SYSTEM
ROLE: Deterministic workflow to build a Take Direction Pack: what to capture per section, how to keep character consistent across takes, and how to QC takes with hard/soft fail rules. Produces comp-friendly, repeatable take guidance (no mixing chains, no lyric rewrites).

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created PB-06 take direction pack playbook (goals + QC)."
- REASON: "Without clear take goals and QC, vocal sessions drift and comping becomes inconsistent."
- IMPACT: "Faster recording cycles, fewer unusable takes, repeatable vocal character."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.VOCAL_DIRECTOR.PB06.001

---

## 0) PURPOSE
Use this playbook when:
- you need repeatable takes and a comp-friendly session plan
- vocalist drifts between takes / sections
- you need explicit QC rules (what fails a take)

Primary objective:
- Convert “vocal direction” into an executable take plan with pass/fail criteria.

---

## 1) REQUIRED INPUTS (MINIMUM)
STOP/GAP if missing:
- SECTION STRUCTURE
- VOCAL_STYLE_PROFILE (delivery principles + forbidden styles)
- MUST_HEAR_WORDS / MUST_HEAR_PHRASES (P0/P1)

Recommended:
- PERFORMANCE_ARC_MAP
- INTELLIGIBILITY_GATES_CHECKLIST
- known risk lines (from prior attempts) or density scan results

---

## 2) REQUIRED OUTPUTS (MANDATORY)
This playbook MUST produce:
- SESSION_INTENT (one paragraph: what “good” is)
- TAKE_GOALS_BY_SECTION (2–4 goals per section)
- RISK_LINES (where failure likely occurs)
- REPEATABILITY_RULES (keep character stable)
- QC_HARD_FAILS (take is rejected)
- QC_SOFT_FAILS (take is usable with notes)
- COMP_NOTES (how takes can be assembled safely)
- ESCALATION_NOTES (if needed)
- TRACE (memory/web + gaps)

NOT READY rule:
- If P0 must-hear targets are not defined → STOP (PB-02 first).

---

## 3) QC MODEL (STRICT)
Define:
- HARD FAIL: must discard take (cannot be fixed by comp without artifacts)
- SOFT FAIL: keep take but note issue (may be patched by comp or minor re-take)

Hard fail triggers (examples, must be customized):
- P0 must-hear word not understood on first listen
- breath breaks split P0 phrase
- delivery violates forbidden styles (identity drift)
- chorus fails to lift vs verse (if arc requires lift)

Soft fail triggers (examples):
- minor timing smear not on P0 word
- slight over/under energy in verse
- minor consonant blur on P2 words

---

## 4) WORKFLOW (DETERMINISTIC STEPS)
### STEP 1 — Define SESSION_INTENT
Write one tight paragraph:
- identity: what the vocal character is
- priorities: P0 clarity first, then arc, then texture
- forbidden drift: list 2–5 “must not”

### STEP 2 — Build TAKE_GOALS_BY_SECTION
For each section:
- Goal 1: arc lever execution (energy/delivery)
- Goal 2: must-hear clarity (P0 emphasis)
- Goal 3 (optional): timing/phrasing target
- Goal 4 (optional): texture/edge constraint (minimal)

Keep goals executable (no more than 4 per section).

### STEP 3 — Identify RISK_LINES
For each section:
- list the line(s) most likely to fail:
  - density
  - consonant cluster
  - breath trap
  - range/tension moment
Output: RISK_LINES with “why”.

### STEP 4 — Define REPEATABILITY_RULES (character lock)
Rules must be short and strict:
- keep consistent timbre principle
- keep consistent articulation policy
- keep consistent intensity band per section (± range)
- keep hook pronunciation stable across takes

### STEP 5 — Define QC_HARD_FAILS
Create a checklist of hard fails:
- HF-1: P0 understood? (YES/NO)
- HF-2: no breath split inside P0? (YES/NO)
- HF-3: forbidden drift occurred? (YES/NO)
- HF-4: chorus lift present? (YES/NO, if required)
- HF-5: consonant clarity on P0 adequate? (YES/NO)

### STEP 6 — Define QC_SOFT_FAILS
List soft fails with severity notes:
- SF-1: timing smear off P0 (minor)
- SF-2: energy slightly off but usable
- SF-3: minor backing collision (if stacking used)

### STEP 7 — COMP_NOTES (assembly rules)
Provide comp guidance:
- prefer comping within same character band (avoid mixing different delivery modes)
- keep chorus hook takes consistent (do not splice different pronunciations)
- if splicing, splice outside must-hear words (safe zones)
- prioritize takes with clean consonants on P0 targets

### STEP 8 — Escalation notes
Escalate if take quality cannot pass hard fails because:
- lyrics unsingable at tempo (PB-04 escalation)
- arrangement seat conflict masks P0 (arranger/producer request)
Do not prescribe mix chains; request seat changes only.

---

## 5) COMMON FAIL MODES
- Too many goals per section (>4) → performer overload.
- No hard fails → everything becomes subjective.
- Repeatability rules missing → takes drift.
- Comping across different pronunciations → obvious artifacts.
- Fix attempt uses mixing instead of performance correction.

---

## 6) OUTPUT TEMPLATE (COPY)
### SESSION_INTENT
- identity:
- priorities:
- forbidden:

### TAKE_GOALS_BY_SECTION
- section:
  - goals:

### RISK_LINES
- section:
  - line_id:
  - why:

### REPEATABILITY_RULES
- rule_1:
- rule_2:
- rule_3:

### QC_HARD_FAILS
- HF-1:
- HF-2:
- HF-3:
- HF-4:
- HF-5:

### QC_SOFT_FAILS
- SF-1:
- SF-2:
- SF-3:

### COMP_NOTES
- note_1:
- note_2:
- note_3:

### ESCALATION_NOTES
- to Lyricist/Songwriter:
- to Arranger/Producer:

### TRACE
- MEMORY_REUSE:
- WEB_LOOKUP_USED:
- GAPS:

--- END.
