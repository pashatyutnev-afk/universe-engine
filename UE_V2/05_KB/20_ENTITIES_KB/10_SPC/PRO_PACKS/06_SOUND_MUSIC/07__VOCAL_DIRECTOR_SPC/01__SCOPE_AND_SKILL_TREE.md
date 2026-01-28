# SPC PRO PACK — SCOPE & SKILL TREE (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/01__SCOPE_AND_SKILL_TREE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: SCOPE_SKILL_TREE
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.SCOPE_SKILLS.DRAFT.001
OWNER: SYSTEM
ROLE: Defines exact scope + skill taxonomy for VOCAL_DIRECTOR_SPC. This file specifies what the specialist must be able to do (leaf skills), what evidence proves competence (observable outcomes), and what inputs are required to produce valid outputs.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created scope + skill tree for VOCAL_DIRECTOR Pro Pack (L3 target)."
- REASON: "Need deterministic capability map for vocal delivery, intelligibility, phrasing/timing, and take direction."
- IMPACT: "Vocal direction becomes repeatable: outputs are structured, testable, and compatible with lyrics/arrangement constraints."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.VOCAL_DIRECTOR.SKILLS.001

---

## 0) BOUND ENTITY (UID-ONLY)
SPC_ENTITY_UID: UE.SPC.SOUND_MUSIC.VOCAL_DIRECTOR.001

Primary ENG interfaces (UID-only):
- UE.ENG.SOUND.VOCAL.PERFORMANCE.001
- UE.ENG.SOUND.LYRICS.001

---

## 1) SCOPE (EXACT)
### 1.1 In scope (what this pack OWNS)
Owned responsibilities (must be deliverable-ready):
- Vocal Delivery Profile (principles: timbre/attack/vibrato/breathiness etc.)
- Emotion & Performance Arc (by sections: verse→chorus dynamics)
- Intelligibility Gates (key words/hook clarity; consonant/diction control)
- Timing & Phrasing guidance (stress, vowel length, cut points, accents)
- Harmony/Stacking Strategy (high-level: where/why backs/harmonies; not note-writing)
- Recording Direction Pack (take goals + risk lines + repeatability notes)
- Escalation notes when lyrics/structure/arrangement must change (ownership respected)

(Aligned to VOCAL_DIRECTOR responsibilities/boundaries.) 

### 1.2 Out of scope (hard boundaries)
Not owned by this pack:
- Writing lyrics / changing meaning (lyrics owner)
- Owning song structure (songwriter owner)
- Arrangement ownership (arranger owner)
- Mix/master processing chains (mix/master owner)
- Video montage decisions

(Aligned to VOCAL_DIRECTOR boundaries.) 

---

## 2) REQUIRED INPUT CONTRACT (MINIMUM)
This pack should refuse/mark GAP if critical inputs are missing.

### 2.1 Inputs (consumes)
Minimum viable inputs:
- LYRIC_DRAFT (at least: chorus/hook lines + verse placeholders)
- SONG STRUCTURE (section list: Intro/Verse/Chorus/Bridge/Outro) OR loop profile
- TARGET LANGUAGE + pronunciation risk notes (if any)

Strongly recommended inputs (for L3 performance-grade direction):
- LYRIC_DRAFT_VARIANTS (from lyrics pipeline)
- METER_PATTERN_SPEC / STRESS_PHRASE_POLICY (if available)
- MELODY_HOOK_CANDIDATE_SET (if available)
- TEMPO_METER_POLICY / GROOVE_PALETTE (if available)
- ARRANGEMENT seat constraints (vocal density, register conflicts) (if available)
- VOCAL_REQUEST (A/B roles, genre delivery constraints, “must-hear words”)

(Interface aligned to VOCAL_PERFORMANCE_ENG mini-contract consumes list; and LYRICS_ENG structured drafting inputs.) 

### 2.2 Outputs (produces)
Minimum output set (always deliver):
- VOCAL_DELIVERY_PROFILE (principles)
- PERFORMANCE_ARC_MAP (by section)
- INTELLIGIBILITY_GATES_CHECKLIST (pass/fail)
- PHRASING_TIMING_NOTES (accent points + vowel length rules)
- HARMONY_STACKING_PLAN (high-level)
- RECORDING_DIRECTION_PACK (take goals + risk lines)
- ESCALATION_NOTES (if required)

Optional, when inputs allow:
- Stress alignment rules summary (if meter/stress info exists)
- Take plan structure aligned to performance QC (abstract)

(Aligned to VOCAL_DIRECTOR scope + VOCAL_PERFORMANCE_ENG produces set concepts.) 

---

## 3) SKILL TREE (L3 TARGET)
Structure:
- Each leaf skill has observable outcomes (what “done” looks like)
- Each leaf has common fail modes (what to catch)
- Each leaf has minimal evidence artifacts (what to output)

### A) DELIVERY PROFILE (FOUNDATION)
A1 — Define Vocal Delivery Profile (principles)
- Inputs: lyric draft + style intent + section map
- Outputs: delivery tags/principles (tone/attack/breath/breathiness/vibrato as principles), forbidden styles list
- Observable outcomes:
  - delivery profile is consistent (not contradictory)
  - “must not do” is explicit (prevents drift)
- Fail modes:
  - vague (“sing better”), contradictory (“clean + lo-fi grit” style conflicts)
  - over-detailed inventories instead of principles

A2 — Section-level delivery modulation
- Inputs: structure + performance intent
- Outputs: section-specific intensity/texture notes (principles)
- Observable outcomes:
  - verse vs chorus differentiation is deliberate and repeatable
- Fail modes:
  - same delivery everywhere; no arc; random intensity swings

### B) PERFORMANCE ARC (EMOTION + TENSION)
B1 — Map Emotion & Arc by sections
- Inputs: lyric concept + structure
- Outputs: arc map (verse→pre→chorus→bridge→final) with “hold/release” notes
- Observable outcomes:
  - emotional trajectory is readable and aligned to lyrics meaning
- Fail modes:
  - emotion stated but not actionable; arc contradicts section roles

B2 — Risk-line identification (where vocalist will fail)
- Inputs: lyric draft + tempo/groove if available
- Outputs: risk lines list (breath, diction, speed, range)
- Observable outcomes:
  - “hard spots” flagged before recording
- Fail modes:
  - no risk identification; fixes attempted only after failure

### C) INTELLIGIBILITY (TEXT MUST LAND)
C1 — Define “must-hear words” + hook intelligibility target
- Inputs: lyric draft
- Outputs: must-hear list (hook words, key nouns/verbs), priority ranking
- Observable outcomes:
  - intelligibility target is testable (what must be understood)
- Fail modes:
  - “make it clear” without specifying what must be heard

C2 — Build Intelligibility Gates checklist (pass/fail)
- Inputs: must-hear list + delivery profile
- Outputs: gate checklist (consonants, phrase breaks, mouth density, hook clarity)
- Observable outcomes:
  - checklist can produce PASS/FAIL with reasons
- Fail modes:
  - subjective only; no failure criteria

C3 — Diction repair protocol (non-lyric-changing)
- Inputs: detected failures (from QA or listening)
- Outputs: repair directives: articulation changes, breath points, vowel shaping (principles)
- Observable outcomes:
  - repairs do not change meaning; they change delivery/phrasing
- Fail modes:
  - rewriting lyrics instead of escalation note

### D) TIMING & PHRASING (STRESS + GROOVE FIT)
D1 — Accent & stress placement guidance
- Inputs: groove/tempo + lyric draft (+ stress policy if available)
- Outputs: where accents must land; stressed syllable alignment principles
- Observable outcomes:
  - phrasing is groove-compatible; hook hits strong positions
- Fail modes:
  - accent plan absent; “off-beat mush” unaddressed

D2 — Breath policy + phrase length control
- Inputs: lyric density + tempo
- Outputs: breath points allowed/forbidden; max phrase length proxy
- Observable outcomes:
  - breath plan supports intelligibility and repeatability
- Fail modes:
  - impossible lines; breath breaks destroy hook words

### E) HARMONY / STACKING (HIGH-LEVEL, NOT COMPOSITION)
E1 — Decide where to keep solo vocal clean vs stacked
- Inputs: structure + sonic identity + intelligibility targets
- Outputs: stacking map (none / doubles / backs / harmony) by section
- Observable outcomes:
  - stacking decisions support intelligibility (not bury it)
- Fail modes:
  - stacking everywhere; harms clarity; no rationale

E2 — Backing strategy for hook emphasis (minimal)
- Inputs: hook words
- Outputs: where backing supports hook (call-response, short doubles)
- Observable outcomes:
  - hook becomes stronger without clutter
- Fail modes:
  - backing competes with lead; unintelligible hook

### F) RECORDING DIRECTION PACK (TAKES + QC)
F1 — Take goals (what to capture)
- Inputs: arc map + risk lines + delivery profile
- Outputs: take goals per section (energy, diction, phrasing)
- Observable outcomes:
  - performer knows what “good take” means
- Fail modes:
  - generic “do it better”; no section goals

F2 — Repeatability constraints (consistency across takes)
- Inputs: delivery profile
- Outputs: do/don’t list to keep character consistent across takes
- Observable outcomes:
  - multiple takes remain in same “character”
- Fail modes:
  - drift between takes; later comp becomes impossible

F3 — QC checks (what fails the take)
- Inputs: intelligibility gates + risk lines
- Outputs: QC list with severity notes (S0..S3 as labels; internal gate later)
- Observable outcomes:
  - hard fails are explicit (e.g., hook words not understood)
- Fail modes:
  - no hard fails; subjective only

### G) ESCALATION & OWNERSHIP DISCIPLINE
G1 — Escalate lyric change requests correctly
- Inputs: detected unsingable lines / density issues
- Outputs: escalation note: what to change, why, minimal suggestion; owner = Lyricist/Songwriter
- Observable outcomes:
  - no “silent rewrite”; ownership respected
- Fail modes:
  - changes meaning without escalation

G2 — Escalate arrangement seat conflicts (vocal seat)
- Inputs: density conflicts, register masking notes
- Outputs: request to Arranger/Producer: reduce density here/there (principles)
- Observable outcomes:
  - vocal seat requirements are explicit
- Fail modes:
  - prescribing mix chain instead of seat request

---

## 4) EVIDENCE OF COMPETENCE (WHAT “L3 DONE” LOOKS LIKE)
A VOCAL_DIRECTOR L3 output pack should include, at minimum:
- delivery profile (principles + forbidden styles)
- performance arc by section
- must-hear words list + intelligibility checklist (pass/fail)
- phrasing/timing notes + breath policy
- stacking plan (high-level)
- recording direction pack (take goals + QC)
- escalation notes (if needed)

If any of these is missing → NOT READY output (mark GAP).

---

## 5) KNOWN FAILURE MODES (GLOBAL)
Global red flags the pack must catch:
- contradictory delivery instructions
- no explicit intelligibility targets (“must-hear words” missing)
- “sing better” without constraints (forbidden by ENG constraints thinking)
- too many levers/notes that a performer cannot execute
- ownership violation (rewriting lyrics instead of escalating)

---

## 6) RELATED KB SCOPE (RAW REFERENCES FROM ENTITY)
KB Inputs / outputs / boundaries are defined by VOCAL_DIRECTOR entity KB SCOPE:
- Sound & Music realm RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/04__SOUND_MUSIC.md
- Narrative Craft realm RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/01__NARRATIVE_CRAFT.md
- Reference Glossary RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/07__REFERENCE_GLOSSARY.md

---

## 7) DOC CONTROL CHECK (READY RULE)
Before considering this file “ready”:
- Exactly one STATUS and one LOCK
- Version/UID present
- Scope and boundaries are explicit
- Leaf skills have observable outcomes
- No fictional UIDs used (placeholders clearly marked as GAP only)

--- END.
# SPC PRO PACK — SCOPE & SKILL TREE (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/01__SCOPE_AND_SKILL_TREE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: SCOPE_SKILL_TREE
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.SCOPE_SKILLS.DRAFT.001
OWNER: SYSTEM
ROLE: Defines exact scope + skill taxonomy for VOCAL_DIRECTOR_SPC. This file specifies what the specialist must be able to do (leaf skills), what evidence proves competence (observable outcomes), and what inputs are required to produce valid outputs.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created scope + skill tree for VOCAL_DIRECTOR Pro Pack (L3 target)."
- REASON: "Need deterministic capability map for vocal delivery, intelligibility, phrasing/timing, and take direction."
- IMPACT: "Vocal direction becomes repeatable: outputs are structured, testable, and compatible with lyrics/arrangement constraints."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.VOCAL_DIRECTOR.SKILLS.001

---

## 0) BOUND ENTITY (UID-ONLY)
SPC_ENTITY_UID: UE.SPC.SOUND_MUSIC.VOCAL_DIRECTOR.001

Primary ENG interfaces (UID-only):
- UE.ENG.SOUND.VOCAL.PERFORMANCE.001
- UE.ENG.SOUND.LYRICS.001

---

## 1) SCOPE (EXACT)
### 1.1 In scope (what this pack OWNS)
Owned responsibilities (must be deliverable-ready):
- Vocal Delivery Profile (principles: timbre/attack/vibrato/breathiness etc.)
- Emotion & Performance Arc (by sections: verse→chorus dynamics)
- Intelligibility Gates (key words/hook clarity; consonant/diction control)
- Timing & Phrasing guidance (stress, vowel length, cut points, accents)
- Harmony/Stacking Strategy (high-level: where/why backs/harmonies; not note-writing)
- Recording Direction Pack (take goals + risk lines + repeatability notes)
- Escalation notes when lyrics/structure/arrangement must change (ownership respected)

(Aligned to VOCAL_DIRECTOR responsibilities/boundaries.) 

### 1.2 Out of scope (hard boundaries)
Not owned by this pack:
- Writing lyrics / changing meaning (lyrics owner)
- Owning song structure (songwriter owner)
- Arrangement ownership (arranger owner)
- Mix/master processing chains (mix/master owner)
- Video montage decisions

(Aligned to VOCAL_DIRECTOR boundaries.) 

---

## 2) REQUIRED INPUT CONTRACT (MINIMUM)
This pack should refuse/mark GAP if critical inputs are missing.

### 2.1 Inputs (consumes)
Minimum viable inputs:
- LYRIC_DRAFT (at least: chorus/hook lines + verse placeholders)
- SONG STRUCTURE (section list: Intro/Verse/Chorus/Bridge/Outro) OR loop profile
- TARGET LANGUAGE + pronunciation risk notes (if any)

Strongly recommended inputs (for L3 performance-grade direction):
- LYRIC_DRAFT_VARIANTS (from lyrics pipeline)
- METER_PATTERN_SPEC / STRESS_PHRASE_POLICY (if available)
- MELODY_HOOK_CANDIDATE_SET (if available)
- TEMPO_METER_POLICY / GROOVE_PALETTE (if available)
- ARRANGEMENT seat constraints (vocal density, register conflicts) (if available)
- VOCAL_REQUEST (A/B roles, genre delivery constraints, “must-hear words”)

(Interface aligned to VOCAL_PERFORMANCE_ENG mini-contract consumes list; and LYRICS_ENG structured drafting inputs.) 

### 2.2 Outputs (produces)
Minimum output set (always deliver):
- VOCAL_DELIVERY_PROFILE (principles)
- PERFORMANCE_ARC_MAP (by section)
- INTELLIGIBILITY_GATES_CHECKLIST (pass/fail)
- PHRASING_TIMING_NOTES (accent points + vowel length rules)
- HARMONY_STACKING_PLAN (high-level)
- RECORDING_DIRECTION_PACK (take goals + risk lines)
- ESCALATION_NOTES (if required)

Optional, when inputs allow:
- Stress alignment rules summary (if meter/stress info exists)
- Take plan structure aligned to performance QC (abstract)

(Aligned to VOCAL_DIRECTOR scope + VOCAL_PERFORMANCE_ENG produces set concepts.) 

---

## 3) SKILL TREE (L3 TARGET)
Structure:
- Each leaf skill has observable outcomes (what “done” looks like)
- Each leaf has common fail modes (what to catch)
- Each leaf has minimal evidence artifacts (what to output)

### A) DELIVERY PROFILE (FOUNDATION)
A1 — Define Vocal Delivery Profile (principles)
- Inputs: lyric draft + style intent + section map
- Outputs: delivery tags/principles (tone/attack/breath/breathiness/vibrato as principles), forbidden styles list
- Observable outcomes:
  - delivery profile is consistent (not contradictory)
  - “must not do” is explicit (prevents drift)
- Fail modes:
  - vague (“sing better”), contradictory (“clean + lo-fi grit” style conflicts)
  - over-detailed inventories instead of principles

A2 — Section-level delivery modulation
- Inputs: structure + performance intent
- Outputs: section-specific intensity/texture notes (principles)
- Observable outcomes:
  - verse vs chorus differentiation is deliberate and repeatable
- Fail modes:
  - same delivery everywhere; no arc; random intensity swings

### B) PERFORMANCE ARC (EMOTION + TENSION)
B1 — Map Emotion & Arc by sections
- Inputs: lyric concept + structure
- Outputs: arc map (verse→pre→chorus→bridge→final) with “hold/release” notes
- Observable outcomes:
  - emotional trajectory is readable and aligned to lyrics meaning
- Fail modes:
  - emotion stated but not actionable; arc contradicts section roles

B2 — Risk-line identification (where vocalist will fail)
- Inputs: lyric draft + tempo/groove if available
- Outputs: risk lines list (breath, diction, speed, range)
- Observable outcomes:
  - “hard spots” flagged before recording
- Fail modes:
  - no risk identification; fixes attempted only after failure

### C) INTELLIGIBILITY (TEXT MUST LAND)
C1 — Define “must-hear words” + hook intelligibility target
- Inputs: lyric draft
- Outputs: must-hear list (hook words, key nouns/verbs), priority ranking
- Observable outcomes:
  - intelligibility target is testable (what must be understood)
- Fail modes:
  - “make it clear” without specifying what must be heard

C2 — Build Intelligibility Gates checklist (pass/fail)
- Inputs: must-hear list + delivery profile
- Outputs: gate checklist (consonants, phrase breaks, mouth density, hook clarity)
- Observable outcomes:
  - checklist can produce PASS/FAIL with reasons
- Fail modes:
  - subjective only; no failure criteria

C3 — Diction repair protocol (non-lyric-changing)
- Inputs: detected failures (from QA or listening)
- Outputs: repair directives: articulation changes, breath points, vowel shaping (principles)
- Observable outcomes:
  - repairs do not change meaning; they change delivery/phrasing
- Fail modes:
  - rewriting lyrics instead of escalation note

### D) TIMING & PHRASING (STRESS + GROOVE FIT)
D1 — Accent & stress placement guidance
- Inputs: groove/tempo + lyric draft (+ stress policy if available)
- Outputs: where accents must land; stressed syllable alignment principles
- Observable outcomes:
  - phrasing is groove-compatible; hook hits strong positions
- Fail modes:
  - accent plan absent; “off-beat mush” unaddressed

D2 — Breath policy + phrase length control
- Inputs: lyric density + tempo
- Outputs: breath points allowed/forbidden; max phrase length proxy
- Observable outcomes:
  - breath plan supports intelligibility and repeatability
- Fail modes:
  - impossible lines; breath breaks destroy hook words

### E) HARMONY / STACKING (HIGH-LEVEL, NOT COMPOSITION)
E1 — Decide where to keep solo vocal clean vs stacked
- Inputs: structure + sonic identity + intelligibility targets
- Outputs: stacking map (none / doubles / backs / harmony) by section
- Observable outcomes:
  - stacking decisions support intelligibility (not bury it)
- Fail modes:
  - stacking everywhere; harms clarity; no rationale

E2 — Backing strategy for hook emphasis (minimal)
- Inputs: hook words
- Outputs: where backing supports hook (call-response, short doubles)
- Observable outcomes:
  - hook becomes stronger without clutter
- Fail modes:
  - backing competes with lead; unintelligible hook

### F) RECORDING DIRECTION PACK (TAKES + QC)
F1 — Take goals (what to capture)
- Inputs: arc map + risk lines + delivery profile
- Outputs: take goals per section (energy, diction, phrasing)
- Observable outcomes:
  - performer knows what “good take” means
- Fail modes:
  - generic “do it better”; no section goals

F2 — Repeatability constraints (consistency across takes)
- Inputs: delivery profile
- Outputs: do/don’t list to keep character consistent across takes
- Observable outcomes:
  - multiple takes remain in same “character”
- Fail modes:
  - drift between takes; later comp becomes impossible

F3 — QC checks (what fails the take)
- Inputs: intelligibility gates + risk lines
- Outputs: QC list with severity notes (S0..S3 as labels; internal gate later)
- Observable outcomes:
  - hard fails are explicit (e.g., hook words not understood)
- Fail modes:
  - no hard fails; subjective only

### G) ESCALATION & OWNERSHIP DISCIPLINE
G1 — Escalate lyric change requests correctly
- Inputs: detected unsingable lines / density issues
- Outputs: escalation note: what to change, why, minimal suggestion; owner = Lyricist/Songwriter
- Observable outcomes:
  - no “silent rewrite”; ownership respected
- Fail modes:
  - changes meaning without escalation

G2 — Escalate arrangement seat conflicts (vocal seat)
- Inputs: density conflicts, register masking notes
- Outputs: request to Arranger/Producer: reduce density here/there (principles)
- Observable outcomes:
  - vocal seat requirements are explicit
- Fail modes:
  - prescribing mix chain instead of seat request

---

## 4) EVIDENCE OF COMPETENCE (WHAT “L3 DONE” LOOKS LIKE)
A VOCAL_DIRECTOR L3 output pack should include, at minimum:
- delivery profile (principles + forbidden styles)
- performance arc by section
- must-hear words list + intelligibility checklist (pass/fail)
- phrasing/timing notes + breath policy
- stacking plan (high-level)
- recording direction pack (take goals + QC)
- escalation notes (if needed)

If any of these is missing → NOT READY output (mark GAP).

---

## 5) KNOWN FAILURE MODES (GLOBAL)
Global red flags the pack must catch:
- contradictory delivery instructions
- no explicit intelligibility targets (“must-hear words” missing)
- “sing better” without constraints (forbidden by ENG constraints thinking)
- too many levers/notes that a performer cannot execute
- ownership violation (rewriting lyrics instead of escalating)

---

## 6) RELATED KB SCOPE (RAW REFERENCES FROM ENTITY)
KB Inputs / outputs / boundaries are defined by VOCAL_DIRECTOR entity KB SCOPE:
- Sound & Music realm RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/04__SOUND_MUSIC.md
- Narrative Craft realm RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/01__NARRATIVE_CRAFT.md
- Reference Glossary RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/07__REFERENCE_GLOSSARY.md

---

## 7) DOC CONTROL CHECK (READY RULE)
Before considering this file “ready”:
- Exactly one STATUS and one LOCK
- Version/UID present
- Scope and boundaries are explicit
- Leaf skills have observable outcomes
- No fictional UIDs used (placeholders clearly marked as GAP only)

--- END.
