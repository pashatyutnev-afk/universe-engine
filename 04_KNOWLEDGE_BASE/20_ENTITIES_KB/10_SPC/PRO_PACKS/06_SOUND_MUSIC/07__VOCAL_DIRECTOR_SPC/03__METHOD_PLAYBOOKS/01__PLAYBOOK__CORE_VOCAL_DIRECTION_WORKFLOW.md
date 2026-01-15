# SPC PRO PACK — PLAYBOOK (PB-01) — CORE VOCAL DIRECTION WORKFLOW (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/03__METHOD_PLAYBOOKS/01__PLAYBOOK__CORE_VOCAL_DIRECTION_WORKFLOW.md

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
UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.PB.CORE.001
OWNER: SYSTEM
ROLE: Default end-to-end workflow for VOCAL_DIRECTOR first-pass direction. Produces a complete Vocal Direction Pack: delivery profile, section arc, intelligibility gates, phrasing/timing + breath policy, stacking plan (high-level), take goals + QC.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created PB-01 core vocal direction workflow (first-pass)."
- REASON: "Need deterministic method replacing vague vocal feedback with measurable constraints and gate-ready outputs."
- IMPACT: "Consistent vocal direction packs and faster convergence to intelligible, repeatable takes."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.VOCAL_DIRECTOR.PB01.001

---

## 0) PURPOSE
Use this playbook when:
- you need the FIRST vocal direction pass for a track (no prior QA notes)
- you need a complete, recording-ready direction pack

Primary objective:
- INTELLIGIBILITY + PERFORMANCE ARC + REPEATABILITY under given lyric/structure constraints.

---

## 1) REQUIRED INPUTS (MINIMUM)
STOP/GAP if missing:
- LYRIC_DRAFT (at least chorus/hook lines + verse placeholders)
- SECTION STRUCTURE (Intro/Verse/Chorus/Bridge/Outro) OR LOOP PROFILE
- LANGUAGE (and any known pronunciation/stress risks)

Recommended (if available):
- LYRIC_DRAFT_VARIANTS
- METER_PATTERN_SPEC / STRESS_PHRASE_POLICY
- MELODY_HOOK_CANDIDATE_SET
- TEMPO_METER_POLICY / GROOVE_PALETTE
- VOCAL_REQUEST (A/B roles, genre delivery constraints, must-hear emphasis)
- ARRANGEMENT seat constraints (density / register masking notes)

---

## 2) REQUIRED OUTPUTS (MANDATORY)
This playbook MUST produce:
- VOCAL_STYLE_PROFILE (delivery profile principles + forbidden styles)
- PERFORMANCE_ARC_MAP (by section)
- MUST_HEAR_WORDS (priority list)
- INTELLIGIBILITY_GATES_CHECKLIST (pass/fail conditions)
- PHRASE_STRESS_ALIGNMENT_RULES (if stress/meter inputs exist; else GAP note)
- PHRASING_TIMING_NOTES (accent points + vowel length + cut/hold notes)
- BREATH_POLICY (where breaths allowed/forbidden; must-hear protected)
- STACKING_PLAN (high-level) OR N/A with reason
- TAKE_PLAN_SPEC (take goals per section + repeatability rules)
- VOCAL_GATES_REPORT (abstract: what fails the take and why)
- RECORDING_DIRECTION_PACK (assembled final packet)
- ESCALATION_NOTES (if text/structure/arrangement must change)
- TRACE (memory/web + applied UIDs + gaps)

NOT READY rule:
- If MUST_HEAR_WORDS or INTELLIGIBILITY_GATES_CHECKLIST is missing → NOT READY.

---

## 3) WORKFLOW (DETERMINISTIC STEPS)
### STEP 1 — Intake & GAP check
1) Confirm the three minimum inputs exist (lyrics + structure/loop + language).
2) If any are missing → STOP/GAP with exact missing fields list.

### STEP 2 — Define MUST-HEAR WORDS (target clarity)
1) Extract hook words from chorus/hook lines.
2) Add key nouns/verbs (meaning carriers).
3) Output MUST_HEAR_WORDS as ranked list (P0/P1/P2 priorities).

### STEP 3 — Draft VOCAL STYLE PROFILE (principles)
1) Choose delivery profile principles:
   - tone (warm/cold/neutral as principle)
   - attack (soft/firm)
   - breathiness (low/med/high)
   - articulation (legato/mixed/staccato as principle)
   - intensity proxy (0..100 by section)
2) Define FORBIDDEN styles (what must not happen).
3) Ensure no contradictions (single coherent profile).

### STEP 4 — Build PERFORMANCE ARC MAP (by section)
1) For each section, define:
   - emotion label (short)
   - tension level (low/med/high)
   - intensity target (0..100)
   - delivery shift note (what changes vs previous section)
2) Enforce verse→chorus contrast with 1–3 clear levers.

### STEP 5 — Stress / phrasing alignment rules (if inputs exist)
IF METER_PATTERN_SPEC or STRESS_PHRASE_POLICY exists:
- derive PHRASE_STRESS_ALIGNMENT_RULES:
  - stressed syllables must land on strong positions
  - forbid stress collisions on weak positions for must-hear words
ELSE:
- mark GAP: “stress policy missing”; provide minimal safe notes:
  - protect hook words, avoid rushing consonant clusters.

### STEP 6 — Intelligibility gates (pass/fail checklist)
Create INTELLIGIBILITY_GATES_CHECKLIST with explicit fails:
- Gate A: Must-hear words understood (YES/NO)
- Gate B: consonant clarity adequate (YES/NO)
- Gate C: phrase breaks do not split must-hear words (YES/NO)
- Gate D: density not exceeding breath policy (YES/NO)
- Gate E: chorus hook clarity ≥ verse clarity (YES/NO)

### STEP 7 — Breath policy + singability scan
1) Identify risk lines (speed/density/breath/range).
2) Define BREATH_POLICY:
   - allowed breath points
   - forbidden breath breaks (must-hear protected)
3) If lines are unsingable at tempo:
   - do NOT rewrite lyrics
   - add ESCALATION_NOTES to Lyricist/Songwriter with minimal change request.

### STEP 8 — Stacking plan (high-level)
Default:
- keep lead clean in verses
- minimal doubling in chorus
- add backs only to emphasize hook (not mask it)
If stacking risks intelligibility → reduce or mark N/A with reason.

### STEP 9 — Take plan + QC hard fails
1) TAKE_PLAN_SPEC:
   - number of takes per section (abstract)
   - goals per take (diction/energy/phrasing)
   - repeatability constraints (keep character consistent)
2) VOCAL_GATES_REPORT:
   - list hard fails (e.g., must-hear words not understood)
   - list soft fails (e.g., minor timing smear)

### STEP 10 — Assemble RECORDING DIRECTION PACK
Assemble outputs into one packet in this order:
1) Vocal Style Profile
2) Must-hear targets
3) Performance arc
4) Phrasing/timing + breath policy
5) Stacking plan
6) Take goals + QC fails
7) Escalations
8) Trace

---

## 4) STOP / ESCALATE RULES
STOP (NOT READY) if:
- no lyrics or no structure/loop profile
- must-hear words not defined
- direction is vibe-only (no actionable constraints)

ESCALATE:
- To Lyricist/Songwriter: unsingable density, must-hear clarity impossible without text changes
- To Arranger/Producer: arrangement seat conflicts (masking must-hear)
- To Music Supervisor: delivery conflicts with sonic identity intent

---

## 5) COMMON FAIL MODES (WHAT TO AVOID)
- “Sing better” without constraints (forbidden).
- Too many levers at once (performer cannot execute).
- Stacking everywhere → destroys intelligibility.
- Breath breaks inside hook words.
- No explicit contrast between verse and chorus.
- Silent lyric rewrites instead of escalation.

---

## 6) OUTPUT TEMPLATE (COPY)
### VOCAL_STYLE_PROFILE
- delivery_principles:
- forbidden_styles:
- section_intensity_map:

### MUST_HEAR_WORDS
- P0:
- P1:
- P2:

### PERFORMANCE_ARC_MAP
- Intro:
- Verse:
- Chorus:
- Bridge:
- Outro:

### INTELLIGIBILITY_GATES_CHECKLIST
- Gate A:
- Gate B:
- Gate C:
- Gate D:
- Gate E:

### PHRASING_TIMING_NOTES
- accent points:
- vowel length rules:
- cut/hold notes:

### BREATH_POLICY
- allowed:
- forbidden:

### STACKING_PLAN (HIGH-LEVEL)
- Verse:
- Chorus:
- Bridge:

### TAKE_PLAN_SPEC
- takes_per_section:
- goals:
- repeatability_rules:

### VOCAL_GATES_REPORT
- hard fails:
- soft fails:

### ESCALATION_NOTES
- lyric changes requested:
- structure changes requested:
- arrangement seat requests:

### TRACE
- MEMORY_REUSE:
- WEB_LOOKUP_USED:
- UIDS_APPLIED:
- GAPS:

--- END.
