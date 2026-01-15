# SPC PRO PACK — PLAYBOOK (PB-05) — SECTION ARC & VERSE→CHORUS CONTRAST (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/03__METHOD_PLAYBOOKS/05__PLAYBOOK__SECTION_ARC_CONTRAST.md

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
UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.PB.SECTION_ARC.001
OWNER: SYSTEM
ROLE: Deterministic workflow to design performance arc by sections and enforce clear verse→chorus contrast using a minimal set of executable levers (1–3). Produces section arc map, contrast plan, and take goals without changing lyric meaning.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created PB-05 section arc & verse→chorus contrast playbook."
- REASON: "Flat performance and same-sounding sections are common failures; this playbook makes contrast deliberate, minimal, and repeatable."
- IMPACT: "Stronger hook perception, clearer emotional trajectory, consistent takes across sections."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.VOCAL_DIRECTOR.PB05.001

---

## 0) PURPOSE
Use this playbook when:
- verse and chorus sound too similar
- performance arc is flat or random
- hook lacks “lift” even if words are intelligible

Primary objective:
- Deliver an arc map with explicit, minimal contrast levers that a performer can execute reliably.

---

## 1) REQUIRED INPUTS (MINIMUM)
STOP/GAP if missing:
- SECTION STRUCTURE (sections list or loop profile)
- LYRIC_DRAFT (at least chorus/hook lines + verse placeholders)
- VOCAL_STYLE_PROFILE (if not present, derive a minimal profile in-line)

Recommended:
- MUST_HEAR_WORDS / MUST_HEAR_PHRASES (P0/P1)
- sonic identity / style intent notes
- any known constraints (tempo feel, performance restrictions)

---

## 2) REQUIRED OUTPUTS (MANDATORY)
This playbook MUST produce:
- PERFORMANCE_ARC_MAP (by section)
- CONTRAST_LEVERS (1–3 levers, explicit)
- SECTION_DELIVERY_NOTES (how delivery shifts per section)
- TAKE_GOALS_BY_SECTION (what to capture per section)
- QC_CHECKS (what fails the arc/contrast)
- ESCALATION_NOTES (if structure/lyrics must change; no rewrites)
- TRACE (memory/web + gaps)

NOT READY rule:
- If chorus/hook section cannot be identified → STOP (need structure clarified).

---

## 3) CONTRAST LEVER LIBRARY (ALLOWED SET)
Choose 1–3 levers max (performer-executable):

L1 — ENERGY / INTENSITY (0..100)
- change intensity between verse and chorus

L2 — DELIVERY MODE (principle)
- e.g., clipped/rhythmic vs sustained/open (still the same voice character)

L3 — ARTICULATION FOCUS
- consonant-forward vs vowel-sustain emphasis (must-hear protection)

L4 — DYNAMICS SHAPE
- narrow vs wide dynamic range; “push on hook words only”

L5 — TIMING FEEL
- more ahead-of-beat vs more laid-back phrasing (subtle, not tempo change)

FORBIDDEN as “contrast lever” in this pack:
- changing lyrics meaning
- adding new sections (structure ownership)
- prescribing mix/master processing

---

## 4) WORKFLOW (DETERMINISTIC STEPS)
### STEP 1 — Identify section roles
1) Label each section as one of:
- SETUP (context)
- BUILD (tension)
- RELEASE (hook/chorus)
- CONTRAST (bridge/break)
2) Confirm which section is the HOOK carrier.

### STEP 2 — Define target arc curve (simple)
Create a section intensity curve (0..100):
- verse: baseline (e.g., 45–60)
- chorus: lift (e.g., +15..+30)
- bridge: contrast (drop or spike, but deliberate)
Rule:
- the arc must have a clear “lift moment” at the hook.

### STEP 3 — Select 1–3 contrast levers
Pick levers that match the desired arc:
- always include at least one lever that is audible (energy or delivery mode).
Document them as:
- lever_name
- verse setting
- chorus setting
- bridge setting (if applicable)

### STEP 4 — Write SECTION_DELIVERY_NOTES
For each section:
- emotion label (1 line)
- intensity target (0..100)
- delivery mode note (short)
- must-hear emphasis note (if targets exist)
- breath policy note (only if critical)

### STEP 5 — Create TAKE_GOALS_BY_SECTION
For each section:
- take goal 1 (arc lever execution)
- take goal 2 (must-hear emphasis if relevant)
- risk line(s): where performer likely fails

### STEP 6 — QC checks (pass/fail)
Define QC rules:
- QC-A: chorus must feel like a lift vs verse (YES/NO)
- QC-B: contrast lever(s) are executed consistently across takes (YES/NO)
- QC-C: must-hear words remain clear during chorus lift (YES/NO)
- QC-D: bridge contrasts without breaking identity (YES/NO)

### STEP 7 — Escalation rules
Escalate to Songwriter if:
- hook section is missing or structure prevents lift
Escalate to Lyricist if:
- hook cannot lift without changing words (density/meaning constraints)
Escalate to Arranger/Producer if:
- arrangement density prevents audible contrast (seat conflict)

Never rewrite lyrics here; only request.

---

## 5) COMMON FAIL MODES
- Too many levers (>3) → performer cannot execute; arc becomes inconsistent.
- Chorus “lift” achieved by masking intelligibility (bad trade).
- Random intensity swings without section role logic.
- Bridge introduces a new identity (breaks continuity).

---

## 6) OUTPUT TEMPLATE (COPY)
### PERFORMANCE_ARC_MAP
- Intro:
- Verse:
- Chorus:
- Verse 2:
- Bridge:
- Final Chorus:
- Outro:

### CONTRAST_LEVERS (1–3)
- Lx:
  - verse:
  - chorus:
  - bridge:

### SECTION_DELIVERY_NOTES
- section:
  - emotion:
  - intensity(0..100):
  - delivery:
  - must-hear emphasis:
  - risks:

### TAKE_GOALS_BY_SECTION
- section:
  - goals:
  - risk_lines:

### QC_CHECKS (PASS/FAIL)
- QC-A:
- QC-B:
- QC-C:
- QC-D:

### ESCALATION_NOTES
- to Songwriter:
- to Lyricist:
- to Arranger/Producer:

### TRACE
- MEMORY_REUSE:
- WEB_LOOKUP_USED:
- GAPS:

--- END.
